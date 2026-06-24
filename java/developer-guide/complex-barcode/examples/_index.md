---
title: "Complete Complex Barcode Examples"
description: "Explore complete end-to-end workflows for generating, recognizing, decoding, and validating complex barcodes."
type: docs
weight: 40
url: /java/developer-guide/complex-barcode/examples/
---

# Complete Complex Barcode Examples

Complete workflows combine typed data creation, image generation, recognition, complex decoding, and field-by-field validation.

The complete source code for this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/complex/examples/CompleteComplexBarcodeExamples.java" target="_blank">View CompleteComplexBarcodeExamples.java</a>

## Generate, read, and decode Swiss QR

```java
SwissQRCodetext sourceCodetext =
        createSwissQRCodetext();

ComplexBarcodeGenerator generator =
        new ComplexBarcodeGenerator(sourceCodetext);

generator.save(outputPath, BarCodeImageFormat.PNG);
```

Recognize and decode the result:

```java
BarCodeReader reader =
        new BarCodeReader(outputPath, DecodeType.QR);

BarCodeResult[] results = reader.readBarCodes();

SwissQRCodetext decoded =
        ComplexCodetextReader.tryDecodeSwissQR(
                results[0].getCodeText()
        );
```

## Process multiple complex barcodes

The example places a Swiss QR symbol and an HIBC QR LIC symbol into one composite image.

```java
BufferedImage swissImage =
        new ComplexBarcodeGenerator(
                swissCodetext
        ).generateBarCodeImage();

BufferedImage hibcImage =
        new ComplexBarcodeGenerator(
                hibcCodetext
        ).generateBarCodeImage();
```

Read all supported carrier types and route each result to the corresponding complex decoder.

## Verify round-trip business data

A strong regression test compares typed fields after decoding:

```java
Assert.assertEquals(
        decodedCodetext.getPrimaryData(),
        sourceCodetext.getPrimaryData()
);

Assert.assertEquals(
        decodedCodetext.getSecondaryAndAdditionalData(),
        sourceCodetext.getSecondaryAndAdditionalData()
);
```

This detects data loss that a simple recognition check might miss.

## Use end-to-end tests

Complete tests can detect:

- missing required fields;
- serialization errors;
- image generation regressions;
- carrier recognition regressions;
- complex parsing regressions;
- field conversion errors.

## Recommendations

- Validate both recognition and structured decoding.
- Compare business fields, not only raw codetext.
- Test documents that contain several complex barcodes.
- Route each carrier to the appropriate decoder.
- Keep representative end-to-end cases in automated tests.
