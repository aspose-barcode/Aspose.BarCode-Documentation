---
title: "Configure X-Dimension"
description: "Learn how to configure X-Dimension for 1D and 2D barcodes in Aspose.BarCode for Java, compare symbol density, use AutoSizeMode, and apply BarWidthReduction for printing."
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/xdimension/
---

# Configure X-Dimension

X-Dimension defines the smallest graphical element of a barcode:

- for a 1D barcode, it is the width of the narrowest bar or space;
- for a 2D barcode, it is the size of one module.

In Aspose.BarCode for Java, X-Dimension is configured through `BarcodeParameters.getXDimension()`. It directly affects barcode density, final image size, and scan reliability.

The complete source code for the examples in this article is available on GitHub:

[View XDimensionExamples.java](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/xdimension/XDimensionExamples.java)

You can also browse all barcode generation examples in the [Generation examples directory](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation).

## Set X-Dimension for a 1D barcode

For linear barcodes, X-Dimension controls the width of the narrowest bar. The following example generates a Code 128 barcode with an X-Dimension of `0.30 mm` and a bar height of `12 mm`.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "ASPOSE-12345"
);

generator.getParameters()
        .getBarcode()
        .getXDimension()
        .setMillimeters(0.30f);

generator.getParameters()
        .getBarcode()
        .getBarHeight()
        .setMillimeters(12.0f);

generator.save("code128_xdim_0_30mm.png", BarCodeImageFormat.PNG);
```

Using millimeters is convenient for print layouts because the requested dimensions describe a physical size rather than only a bitmap size.

## Set module size for a 2D barcode

For matrix symbologies such as Data Matrix and QR Code, X-Dimension controls module size.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.DATA_MATRIX,
        "ASPOSE"
);

generator.getParameters()
        .getBarcode()
        .getXDimension()
        .setPixels(8);

generator.save("datamatrix_xdim_8px.png", BarCodeImageFormat.PNG);
```

Pixels are useful for screen images and test fixtures. For printing, use physical units together with the target image resolution.

## Compare barcode density

A smaller X-Dimension produces a more compact symbol. A larger X-Dimension increases the symbol width but usually improves tolerance to print and capture imperfections.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "DENSITY-CHECK-1234567890"
);

// Compact barcode
generator.getParameters().getBarcode().getXDimension().setMillimeters(0.25f);
generator.getParameters().getBarcode().getBarHeight().setMillimeters(12.0f);
generator.save("code128_xdim_0_25mm.png", BarCodeImageFormat.PNG);

// Larger barcode
generator.getParameters().getBarcode().getXDimension().setMillimeters(0.50f);
generator.save("code128_xdim_0_50mm.png", BarCodeImageFormat.PNG);
```

When selecting a value, balance the available label space against the expected print and scanning conditions.

## Use X-Dimension with AutoSizeMode

`AutoSizeMode` determines how the generator combines barcode geometry with the requested image width and height.

### AutoSizeMode.NONE

With `AutoSizeMode.NONE`, the resulting image size is calculated from X-Dimension, barcode content, padding, captions, and other layout parameters. Explicit image width and height do not determine the output dimensions.

```java
generator.getParameters().setAutoSizeMode(AutoSizeMode.NONE);
generator.getParameters().getImageWidth().setPixels(300);
generator.getParameters().getImageHeight().setPixels(300);
generator.getParameters().getBarcode().getXDimension().setPixels(6);
```

### AutoSizeMode.INTERPOLATION

With `AutoSizeMode.INTERPOLATION`, the generated barcode is fitted to the specified image dimensions through interpolation.

```java
generator.getParameters().setAutoSizeMode(AutoSizeMode.INTERPOLATION);
generator.getParameters().getImageWidth().setPixels(300);
generator.getParameters().getImageHeight().setPixels(300);
generator.getParameters().getBarcode().getXDimension().setPixels(6);
```

This mode is useful when the bitmap must have exact dimensions, but interpolation can alter the originally requested module geometry.

### AutoSizeMode.NEAREST

With `AutoSizeMode.NEAREST`, the generator adjusts the layout to the nearest valid barcode size while trying to preserve module proportions.

```java
generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);
generator.getParameters().getImageWidth().setPixels(300);
generator.getParameters().getImageHeight().setPixels(300);
generator.getParameters().getBarcode().getXDimension().setPixels(6);
```

This mode is useful when a barcode should fit a target image box without arbitrary resampling.

## Apply BarWidthReduction

`BarWidthReduction` reduces the width of dark bars or modules. It can be used to compensate for ink spread in printing workflows.

The following Code 128 example compares output with and without bar width reduction:

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "ASPOSE"
);

generator.getParameters().getBarcode().getXDimension().setMillimeters(0.30f);
generator.getParameters().getBarcode().getBarHeight().setMillimeters(12.0f);

// No reduction
generator.getParameters().getBarcode().getBarWidthReduction().setPixels(0);
generator.save("code128_bwr_0.png", BarCodeImageFormat.PNG);

// Reduce bar width
generator.getParameters().getBarcode().getBarWidthReduction().setPixels(4);
generator.save("code128_bwr_4.png", BarCodeImageFormat.PNG);
```

The same property can also be applied to 2D symbols:

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.DATA_MATRIX,
        "ASPOSE"
);

generator.getParameters().getBarcode().getXDimension().setPixels(10);
generator.getParameters().getBarcode().getBarWidthReduction().setPixels(4);
generator.save("datamatrix_bwr_4.png", BarCodeImageFormat.PNG);
```

Select the reduction value according to the actual printer, media, and print process. Excessive reduction can damage barcode geometry.

## Recommendations

- Use pixels for screen-oriented images and reproducible test fixtures.
- Use millimeters for labels and other print-oriented layouts.
- Test small X-Dimension values with the actual printer and scanner.
- Prefer `AutoSizeMode.NONE` when geometric dimensions must control the output.
- Prefer `AutoSizeMode.NEAREST` when the symbol must fit a target image box.
- Use `BarWidthReduction` only after evaluating the real print process.
