---
title: "Read Complex Barcodes"
description: "Learn how to recognize carrier symbologies, decode structured payloads, access business fields, and handle unsupported data."
type: docs
weight: 30
url: /java/developer-guide/complex-barcode/read/
---

# Read Complex Barcodes

Reading a complex barcode is a two-stage operation. First, recognize the physical carrier symbology. Then pass the recognized text to the appropriate complex codetext decoder.

The complete source code for this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/complex/read/ReadComplexBarcodes.java" target="_blank">View ReadComplexBarcodes.java</a>

## Recognize the carrier barcode

```java
BarCodeReader reader = new BarCodeReader(
        outputPath,
        DecodeType.QR
);

BarCodeResult[] results = reader.readBarCodes();
```

For Swiss QR, the reader reports `DecodeType.QR`. At this stage, the result contains the standardized text but not yet the typed payment model.

## Decode the recognized text

```java
SwissQRCodetext decodedCodetext =
        ComplexCodetextReader.tryDecodeSwissQR(
                results[0].getCodeText()
        );
```

For HIBC LIC:

```java
HIBCLICComplexCodetext decodedBase =
        ComplexCodetextReader.tryDecodeHIBCLIC(
                results[0].getCodeText()
        );
```

Check the returned subtype before accessing format-specific fields.

## Access business fields

After decoding, application code can access typed properties:

```java
String account =
        decodedCodetext.getBill().getAccount();

double amount =
        decodedCodetext.getBill().getAmount();

String creditorName =
        decodedCodetext.getBill()
                .getCreditor()
                .getName();
```

## Handle unsupported text

The `tryDecode...` methods return `null` when text does not conform to the requested format:

```java
String unsupported =
        "NOT-A-SUPPORTED-COMPLEX-BARCODE";

Assert.assertNull(
        ComplexCodetextReader.tryDecodeSwissQR(
                unsupported
        )
);
```

This allows an application to try another decoder or report unsupported content without interrupting the workflow.

## Choose the correct decoder

Use the method that matches the expected standard:

- `tryDecodeSwissQR`;
- `tryDecodeHIBCLIC`;
- `tryDecodeHIBCPAS`;
- `tryDecodeMailmark`;
- `tryDecodeMailmark2D`;
- `tryDecodeMaxiCode`;
- `tryDecodeUSADriveId`.

The carrier type alone may not uniquely identify the business format.

## Recommendations

- Check the number of recognition results before accessing them.
- Confirm the carrier `DecodeType`.
- Pass recognized text to the matching complex decoder.
- Handle `null` results from `tryDecode...` methods.
- Validate important business fields after decoding.
- Keep recognition failures separate from parsing failures.
