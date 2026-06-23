---
title: "Barcode Symbology and Text"
description: "Learn how to select a barcode symbology and provide plain text, Unicode text, or raw binary data in Aspose.BarCode for Java."
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/set-barcode-symbology-and-text/
---

# Set Barcode Symbology and Text

Aspose.BarCode for Java generates a barcode from two primary inputs:

- a symbology selected through `EncodeTypes`;
- the payload supplied as a Java `String` or a raw `byte[]` array.

The selected symbology determines the supported data, capacity, structure, and available generation parameters. Text and binary payloads should be handled as separate scenarios because character encoding rules do not apply to arbitrary raw bytes.

The complete source code for the examples in this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/symbology_codetext/SetBarcodeSymbologyAndText.java" target="_blank">View SetBarcodeSymbologyAndText.java</a>

You can also browse all barcode generation examples in the <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation" target="_blank">Generation examples directory</a>.

## Select a barcode symbology

Create a `BarcodeGenerator` with one of the constants exposed by `EncodeTypes`.

```java
String codeText = "PRODUCT-2026";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        codeText
);

generator.save("code128_text.png", BarCodeImageFormat.PNG);
```

Use a symbology that matches the application requirements. For example:

- Code 128 is suitable for compact alphanumeric linear barcodes;
- QR Code supports larger text and binary payloads;
- Data Matrix is commonly used for compact two-dimensional marking.

For additional background, see the <a href="https://docs.aspose.com/barcode/info-cards/code-128/" target="_blank">Code 128 standard overview</a>, <a href="https://docs.aspose.com/barcode/info-cards/qr-code/" target="_blank">QR Code standard overview</a>, and <a href="https://docs.aspose.com/barcode/info-cards/data-matrix/" target="_blank">Data Matrix standard overview</a>.

## Set the payload after construction

You can create the generator without payload data and set it later.

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR);
generator.setCodeText("Updated payload");
generator.save("qr_updated_payload.png", BarCodeImageFormat.PNG);
```

Use `setCodeText(String)` for text data and `setCodeText(byte[])` for a raw byte sequence.

## Encode Unicode text with UTF-8 ECI

Use `QREncodeMode.ECI` when the payload is text and the QR Code must declare an explicit character encoding such as UTF-8.

```java
String codeText = "Aspose — データ";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        codeText
);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setQrEncodeMode(QREncodeMode.ECI);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setQrECIEncoding(ECIEncodings.UTF8);

generator.save("qr_unicode.png", BarCodeImageFormat.PNG);
```

In this scenario, the source value remains a Java `String`. The generator converts the text by using the selected ECI encoding and writes the corresponding ECI designator into the QR Code.

The scanning application must support the selected ECI encoding to reconstruct the original text correctly.

## Encode raw binary data

Use `QREncodeMode.BYTES` when the source payload is already a byte array and must be encoded without text transcoding.

```java
byte[] payload = {
        0x42, 0x49, 0x4E, 0x41, 0x52, 0x59,
        0x2D,
        0x01, 0x02, 0x03,
        0x7F
};

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR);
generator.setCodeText(payload);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setQrEncodeMode(QREncodeMode.BYTES);

generator.save("qr_bytes.png", BarCodeImageFormat.PNG);
```

Do not combine `QREncodeMode.BYTES` with `setQrECIEncoding(ECIEncodings.UTF8)` merely because the byte array originally came from a UTF-8 string. In bytes mode, the supplied array is treated as the payload itself rather than as text that needs character encoding.

The receiving application is responsible for interpreting the decoded byte sequence according to the application protocol.

## Text mode and bytes mode

Use the following rule when selecting the QR encoding mode:

- use `QREncodeMode.ECI` with a Java `String` when an explicit text encoding such as UTF-8 must be declared;
- use `QREncodeMode.BYTES` with `byte[]` when the exact raw byte sequence must be stored without text conversion.

These scenarios should be tested independently. A Unicode text test verifies character encoding and decoding, while a raw-bytes test verifies byte-for-byte payload preservation.

## Verify the generated barcode

The example class saves each generated image and reads it back to verify the symbology and payload.

For text payloads, compare the decoded text:

```java
ExampleAssist.assertImageHasBarcodes(
        outputPath,
        1,
        List.of(
                ExampleAssist.expected(
                        DecodeType.QR,
                        codeText
                )
        )
);
```

For raw binary payloads, compare the decoded bytes:

```java
ExampleAssist.assertImageHasBarcodes(
        outputPath,
        1,
        List.of(
                ExampleAssist.expected(
                        DecodeType.QR,
                        payload
                )
        )
);
```

Byte comparison is preferable for binary content because `getCodeText()` may apply a character interpretation that is not meaningful for arbitrary binary data.

## Recommendations

- Select a symbology that supports the required payload type and capacity.
- Use Java `String` values for text-oriented scenarios.
- Use UTF-8 ECI only when explicit character encoding is required.
- Use `byte[]` with `QREncodeMode.BYTES` for exact binary payloads.
- Do not assume that arbitrary binary data can be represented reliably through decoded text.
- Read generated barcodes back during tests to verify both the barcode type and payload.
