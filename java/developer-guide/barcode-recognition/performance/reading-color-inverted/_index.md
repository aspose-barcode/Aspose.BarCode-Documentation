---
title: "Reading Color-Inverted Barcodes"
description: "Learn how to enable and use InverseImageMode to read barcodes on color-inverted (white-on-black) images in Aspose.BarCode for Java."
type: docs
weight: 90
url: /java/developer-guide/barcode-recognition/performance/reading-color-inverted
---

# Reading color-inverted barcodes

In many real-world scenarios barcodes are printed **white on black** (or light on dark) instead of the usual dark bars on a light background.  
Such *color-inverted* symbols may appear on:

- dark product labels
- UI screenshots with dark themes
- reversed graphics from design tools or printers

By default, most recognition pipelines are tuned for dark-on-light images.  
Aspose.BarCode for Java lets you explicitly enable **inverse image processing** for such cases by using:

- `QualitySettings.setInverseImage(InverseImageMode.ENABLED)` on the reader

This article shows how to:

- enable inverted image handling for common symbologies
- apply the same setting to user-supplied images and various bitmap formats
- generate normal and inverted test fixtures used in the example class

All code samples are based on the test class:

`com.aspose.barcode.guide.recognition.performance.ReadingColorInvertedExample`

You can find the full source on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/ReadingColorInvertedExample.java" target="_blank" rel="noopener noreferrer">ReadingColorInvertedExample.java</a>

In the snippets below, `folderPath` represents the path where you store test images in your application.

---

## 1. Enabling inverse image mode for recognition

To read inverted images, you keep the usual `BarCodeReader` configuration (path + `DecodeType`) and then enable inverse processing in `QualitySettings`:

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "Code128Invert.png");

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

// Enable inverse image handling for white-on-black barcodes
barCodeReader.getQualitySettings().setInverseImage(InverseImageMode.ENABLED);

ExampleAssist.assertRecognizedWithText(
        barCodeReader,
        "Code128Invert.png",
                1,
                "INVERT IMAGE TEST"
);
```

What this does:

- `InverseImageMode.ENABLED` tells the engine to consider that bars may be lighter than the background.
- The engine performs an internal inversion step (or equivalent logic) before decoding.
- The rest of your code stays the same: you still pass the file path and target `DecodeType`.

When you have a mix of positive and inverted images in the same flow, it is usually safe to keep inverse mode enabled throughout the session.

---

## 2. Applying inverse mode to 2D barcodes

The same setting works uniformly for common 2D symbologies:

- QR (`DecodeType.QR`)
- PDF417 (`DecodeType.PDF_417`)
- Data Matrix (`DecodeType.DATA_MATRIX`)

The tests in `ReadingColorInvertedExample` demonstrate this pattern:

```java
// QR, inverted
@Test
public void QRInvert() {
    String imagePath = ExampleAssist.pathCombine(FOLDER, "QRInvert.png");

    BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);
    barCodeReader.getQualitySettings().setInverseImage(InverseImageMode.ENABLED);

    ExampleAssist.assertRecognizedWithText(
            barCodeReader,
            "QRInvert.png",
            1,
            "INVERT IMAGE TEST"
    );
}

// PDF417, inverted
@Test
public void PDF417Invert() {
    String imagePath = ExampleAssist.pathCombine(FOLDER, "PDF417Invert.png");

    BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.PDF_417);
    barCodeReader.getQualitySettings().setInverseImage(InverseImageMode.ENABLED);

    ExampleAssist.assertRecognizedWithText(
            barCodeReader,
            "PDF417Invert.png",
            1,
            "INVERT IMAGE TEST"
    );
}

// Data Matrix, inverted
@Test
public void DMInvert() {
    String imagePath = ExampleAssist.pathCombine(FOLDER, "DMInvert.png");

    BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.DATA_MATRIX);
    barCodeReader.getQualitySettings().setInverseImage(InverseImageMode.ENABLED);

    ExampleAssist.assertRecognizedWithText(
            barCodeReader,
            "DMInvert.png",
            1,
            "INVERT IMAGE TEST"
    );
}
```

Notes:

- The only difference between these tests is the `DecodeType` and the file name.
- All of them rely on the same quality setting: `InverseImageMode.ENABLED`.

---

## 3. Working with user images and different formats

In many applications, you do not control how the barcode image is produced.  
The same inverse image configuration works for user-supplied images regardless of their source (screenshots, scans, exported graphics, and so on).

### 3.1 Data Matrix from a user image

The example below shows how to recognize a color-inverted Data Matrix symbol from an arbitrary image file:

```java
String imagePath = "/path/to/your/datamatrix-inverted.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.DATA_MATRIX);
barCodeReader.getQualitySettings().setInverseImage(InverseImageMode.ENABLED);

BarCodeResult[] results = barCodeReader.readBarCodes();
// process results[0].getCodeText(), etc.
```
The important part is that `InverseImageMode.ENABLED` is applied in the same way as for test fixtures created in code.

### 3.2 Using inverse mode with different formats and bit depths

Inverse image handling is orthogonal to the file format.  
You can use the same approach for PNG, BMP, or other supported formats, including indexed and 1-bit-per-pixel images:

```java
String bmpPath = "/path/to/your/DMInvert4bpp.bmp";

BarCodeReader barCodeReader = new BarCodeReader(bmpPath, DecodeType.DATA_MATRIX);
barCodeReader.getQualitySettings().setInverseImage(InverseImageMode.ENABLED);

BarCodeResult[] results = barCodeReader.readBarCodes();
```
This shows that:
- the same inverse mode configuration works across formats (PNG, BMP, etc.),
- you can still rely on `InverseImageMode.ENABLED` when working with low-bit-depth images, as long as the barcode itself is well-formed.

---

## 4. Practical guidelines

When you need to support reversed or color-inverted barcodes in your application:

1. **Enable inverse image mode** whenever you expect white-on-black or light-on-dark barcodes:

   ```java
   barCodeReader.getQualitySettings().setInverseImage(InverseImageMode.ENABLED);
   ```

2. **Keep your DecodeType specific** (for example, `CODE_128`, `QR`, `PDF_417`, `DATA_MATRIX`) to minimize unnecessary work on unrelated symbologies.

3. **Reuse the same setting** across different parts of your workflow. Inverse mode is transparent for normal images and only helps when inversion is actually present.

4. **Test with your real inputs** (PNG, BMP, screenshots, scanned PDFs converted to images) to ensure that your pipeline and image pre-processing preserve enough contrast and resolution.

---

## Summary

- Color-inverted barcodes are common on dark labels and in UI screenshots.
- Aspose.BarCode for Java supports such images via inverse image processing in `QualitySettings`.
- The main API hook is `setInverseImage(InverseImageMode.ENABLED)` on the reader’s quality settings.
- The same approach works for 1D and 2D symbologies and for a variety of image formats and bit depths.
- The accompanying example class demonstrates how to generate fixtures and verify behavior across Code 128, QR, PDF417, and Data Matrix barcodes.

For full context and runnable tests, refer to:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/ReadingColorInvertedExample.java" target="_blank" rel="noopener noreferrer">ReadingColorInvertedExample.java</a>

---

**Note – how the example generates normal and inverted fixtures**

The example class also contains code that generates **pairs of images** for each symbology used in the tests:

- positive image: normal dark bars on a light background
- inverted image: colors flipped by a helper method `ExampleAssist.invertColors(srcPath, outPath)`

This is a **technical detail of the test setup** and is not required for using inverse mode in production, but it can be useful if you want to reproduce the same fixtures locally.

Example for Code 128:

```java
private static final String FOLDER =
        ExampleAssist.getOrCreateResourceFolderPath("recognition", "color", "color_inverted");

private void generateFixtures() throws Exception {
    // Positive Code 128
    ExampleAssist.checkOrCreateImage(FOLDER, "Code128.png", out -> {
        BarcodeGenerator barcodeGenerator =
                new BarcodeGenerator(EncodeTypes.CODE_128, "INVERT IMAGE TEST");
        barcodeGenerator.save(out, BarCodeImageFormat.PNG);
    });

    // Color-inverted Code 128 (white bars on black background)
    ExampleAssist.checkOrCreateImage(FOLDER, "Code128Invert.png", out -> {
        String sourcePath = ExampleAssist.pathCombine(FOLDER, "Code128.png");
        ExampleAssist.invertColors(sourcePath, out);
    });

    // The same pattern is used for QR, PDF417 and Data Matrix
}
```

In this setup:

- The positive image is generated with `BarcodeGenerator`.
- The inverted image is created by reading the positive PNG and inverting colors pixel by pixel.
- The `checkOrCreateImage` helper ensures each image is generated only once when tests run.

You can follow the same pattern if you want controlled positive/inverted pairs for your own test suite.
