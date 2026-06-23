---
title: "Set Barcode Symbology and Text"
description: "Select a barcode symbology and provide text, Unicode, or binary data."
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/set-barcode-symbology-and-text/
---

# Set Barcode Symbology and Text

Create `BarcodeGenerator` with one of the constants exposed by `EncodeTypes`. The selected symbology determines the supported character set, capacity, structure, and available generation parameters.

## Select a symbology

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "PRODUCT-2026"
);
```

Use an encode type that matches the application requirements. For example, Code 128 is suitable for compact alphanumeric linear barcodes, while QR Code and Data Matrix can store larger payloads and binary data.

For background information, see the <a href="https://docs.aspose.com/barcode/info-cards/code-128/" target="_blank">Code 128 standard overview</a>, <a href="https://docs.aspose.com/barcode/info-cards/qr-code/" target="_blank">QR Code standard overview</a>, and <a href="https://docs.aspose.com/barcode/info-cards/data-matrix/" target="_blank">Data Matrix standard overview</a>.

## Set text after construction

You can construct the generator without data and set the payload later.

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR);
generator.setCodeText("Updated payload");
```

## Encode Unicode text

Use explicit ECI encoding when interoperability requires the scanner to interpret the payload as UTF-8.

```java
String codeText = "Aspose — データ";
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, codeText);

generator.getParameters().getBarcode().getQR()
        .setQrEncodeMode(QREncodeMode.ECI);
generator.getParameters().getBarcode().getQR()
        .setQrECIEncoding(ECIEncodings.UTF8);
```

## Encode binary data

```java
byte[] payload = "Binary payload 🚀".getBytes(StandardCharsets.UTF_8);

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR);
generator.setCodeText(payload);
generator.getParameters().getBarcode().getQR()
        .setQrEncodeMode(QREncodeMode.BYTES);
```

The receiving application must know how to interpret the decoded bytes. ECI can be added when the bytes represent text in a specific character encoding.

## Complete example

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/symbology_codetext/SetBarcodeSymbologyAndText.java" target="_blank">View SetBarcodeSymbologyAndText.java</a>

You can also browse the <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation" target="_blank">Generation examples directory</a>.
