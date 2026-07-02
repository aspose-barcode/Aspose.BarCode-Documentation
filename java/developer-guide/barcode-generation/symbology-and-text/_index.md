---
title: "Barcode Symbology and Text"
description: "Learn how to select a barcode symbology and provide plain text, Unicode text, or raw binary data in Aspose.BarCode for Java."
type: docs
weight: 80
url: /java/developer-guide/barcode-generation/set-barcode-symbology-and-text/
---

# Set Barcode Symbology and Text

Aspose.BarCode for Java generates a barcode from two primary inputs:

- a symbology selected through `EncodeTypes`;
- the payload supplied as a Java `String` or a raw `byte[]` array.

The selected symbology determines the supported data, capacity, structure, and available generation parameters. Text and binary payloads should be handled as separate scenarios because character encoding rules do not apply to arbitrary raw bytes.

The runnable TestNG example for this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/symbology_codetext/SymbologyAndCodeTextExample.java" target="_blank">View SymbologyAndCodeTextExample.java</a>

## Select a barcode symbology

Create a `BarcodeGenerator` with one of the constants exposed by `EncodeTypes`.

```java
String codeText = "PRODUCT-2026";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        codeText
);

generator.save(
        "code128_text.png",
        BarCodeImageFormat.PNG
);
```

Use a symbology that matches the application requirements. For example:

- Code 128 is suitable for compact alphanumeric linear barcodes;
- QR Code supports larger text and binary payloads;
- Data Matrix is commonly used for compact two-dimensional marking.

For additional background, see the <a href="https://docs.aspose.com/barcode/info-cards/code-128/" target="_blank">Code 128 standard overview</a>, <a href="https://docs.aspose.com/barcode/info-cards/qr-code/" target="_blank">QR Code standard overview</a>, and <a href="https://docs.aspose.com/barcode/info-cards/data-matrix/" target="_blank">Data Matrix standard overview</a>.

## Set the payload after construction

You can create the generator without payload data and set it later.

```java
BarcodeGenerator generator =
        new BarcodeGenerator(EncodeTypes.QR);

generator.setCodeText("Updated payload");

generator.save(
        "qr_updated_payload.png",
        BarCodeImageFormat.PNG
);
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
        .setEncodeMode(QREncodeMode.ECI);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setECIEncoding(ECIEncodings.UTF8);

generator.save(
        "qr_unicode.png",
        BarCodeImageFormat.PNG
);
```

In this scenario, the source value remains a Java `String`. The generator converts the text by using the selected ECI encoding and writes the corresponding ECI designator into the QR Code.

The scanning application must support the selected ECI encoding to reconstruct the original text correctly.

## Encode Unicode text with a BOM

Use `setCodeText(String, Charset, boolean)` when the encoded text must include a byte-order mark.

```java
BarcodeGenerator generator =
        new BarcodeGenerator(EncodeTypes.QR);

generator.setCodeText(
        "車種名",
        StandardCharsets.UTF_8,
        true
);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setECIEncoding(ECIEncodings.UTF8);

generator.save(
        "qr_utf8_bom.png",
        BarCodeImageFormat.PNG
);
```

The final boolean argument controls whether the BOM is added.

## Encode raw binary data

Use `QREncodeMode.BYTES` when the source payload is already a byte array and must be encoded without text transcoding.

```java
byte[] payload = {
        0x42, 0x49, 0x4E, 0x41, 0x52, 0x59,
        0x2D,
        0x01, 0x02, 0x03,
        0x7F
};

BarcodeGenerator generator =
        new BarcodeGenerator(EncodeTypes.QR);

generator.setCodeText(payload);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setEncodeMode(QREncodeMode.BYTES);

generator.save(
        "qr_bytes.png",
        BarCodeImageFormat.PNG
);
```

Do not combine `QREncodeMode.BYTES` with `setECIEncoding(ECIEncodings.UTF8)` merely because the byte array originally came from a UTF-8 string. In bytes mode, the supplied array is treated as the payload itself rather than as text that needs character encoding.

The receiving application is responsible for interpreting the decoded byte sequence according to the application protocol.

## Text mode and bytes mode

Use the following rule when selecting the QR encoding mode:

- use `QREncodeMode.ECI` with a Java `String` when an explicit text encoding such as UTF-8 must be declared;
- use `QREncodeMode.BYTES` with `byte[]` when the exact raw byte sequence must be stored without text conversion.

These scenarios should be tested independently. A Unicode text test verifies character encoding and decoding, while a raw-bytes test verifies byte-for-byte payload preservation.

## Configure symbology-specific parameters

The consolidated example also demonstrates where selected barcode-specific settings are configured.

For QR Code, set the error correction level and version through `getQR()`:

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "QR-PARAMS"
);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setErrorLevel(QRErrorLevel.LEVEL_H);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setVersion(QRVersion.VERSION_05);
```

For Data Matrix, configure ECC and encoding mode through `getDataMatrix()`:

```java
generator.getParameters()
        .getBarcode()
        .getDataMatrix()
        .setDataMatrixEcc(DataMatrixEccType.ECC_200);

generator.getParameters()
        .getBarcode()
        .getDataMatrix()
        .setDataMatrixEncodeMode(DataMatrixEncodeMode.AUTO);
```

The example class also includes Macro PDF417 rows, columns, and macro-segmentation fields, together with a GS1 Code 128 payload based on Application Identifiers.

## Verify a text payload

Use `BarCodeReader` to recognize the generated barcode and compare the public recognition result with the expected symbology and text.

```java
BarCodeReader reader = new BarCodeReader(
        "qr_unicode.png",
        DecodeType.QR
);

BarCodeResult[] results =
        reader.readBarCodes();

if (results.length != 1) {
        throw new IllegalStateException(
            "Expected exactly one QR barcode."
);
}

        if (!results[0].getCodeType().equals(
        DecodeType.QR
        )) {
        throw new IllegalStateException(
            "Unexpected barcode type: "
                    + results[0].getCodeType()
    );
            }

            if (!results[0].getCodeText().equals(
        codeText
        )) {
        throw new IllegalStateException(
            "Decoded text does not match "
                    + "the source text."
);
}
```

This example uses only the public Aspose.BarCode API.

## Verify a binary payload

For raw binary data, compare `getCodeBytes()` rather than `getCodeText()`.

```java
BarCodeReader reader = new BarCodeReader(
        "qr_bytes.png",
        DecodeType.QR
);

BarCodeResult[] results =
        reader.readBarCodes();

if (results.length != 1) {
    throw new IllegalStateException(
            "Expected exactly one QR barcode."
    );
}

        if (!results[0].getCodeType().equals(DecodeType.QR)) {
        throw new IllegalStateException("Unexpected barcode type: " + results[0].getCodeType());}

            if (!Arrays.equals(results[0].getCodeBytes(), payload)) {
        throw new IllegalStateException("Decoded bytes do not match the source payload.");
}
```

Byte comparison is preferable for binary content because `getCodeText()` may apply a character interpretation that is not meaningful for arbitrary binary data.

The binary verification example requires:

```java
import java.util.Arrays;
```

## Recommendations

- Select a symbology that supports the required payload type and capacity.
- Use Java `String` values for text-oriented scenarios.
- Use UTF-8 ECI only when explicit character encoding is required.
- Use `byte[]` with `QREncodeMode.BYTES` for exact binary payloads.
- Do not assume that arbitrary binary data can be represented reliably through decoded text.
- Use `BarCodeReader` to verify both the recognized barcode type and payload.
- Compare `getCodeText()` for text and `getCodeBytes()` for binary data.
