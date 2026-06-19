---
title: "Generate Code 128 Barcodes"
description: "Learn how to generate Code 128 barcodes in Aspose.BarCode for Java, configure human-readable text, print resolution, colors, padding, borders, rotation, and compact layouts."
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/generate-code128/
---

# Generate Code 128 Barcodes

Code 128 is a high-density linear symbology that can encode numeric data, uppercase and lowercase letters, punctuation, and control characters. Aspose.BarCode for Java automatically selects and switches between Code 128 subsets when generating a symbol.

The complete source code for the examples in this article is available on GitHub:

[View GenerateCode128.java](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/GenerateCode128.java)

You can also browse all barcode generation examples in the [Generation examples directory](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation).

## Generate a basic Code 128 barcode

Create a `BarcodeGenerator` with `EncodeTypes.CODE_128`, provide the code text, and save the generated image.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "ASPOSE COMPANY"
);

generator.save("code128_quick.png", BarCodeImageFormat.PNG);
```

The generator selects the appropriate Code 128 subsets automatically.

## Configure human-readable text

The human-readable code text can be positioned below the bars and formatted through `CodeTextParameters`.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "PRODUCT-789"
);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setLocation(CodeLocation.BELOW);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .getFont()
        .setFamilyName("Arial");

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .getFont()
        .setStyle(Font.PLAIN);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .getFont()
        .getSize()
        .setPoint(12);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .getSpace()
        .setPoint(2);

generator.save("code128_with_text.png", BarCodeImageFormat.PNG);
```

The `Space` property defines the distance between the bars and the text.

## Prepare a barcode for 300 DPI output

Use `setResolution` to define the output resolution. The following example also specifies an image box and uses `AutoSizeMode.NEAREST` to fit the barcode while preserving valid geometry.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "PRINT-READY-001"
);

generator.getParameters().setResolution(300.0f);
generator.getParameters().getImageWidth().setPixels(400);
generator.getParameters().getImageHeight().setPixels(150);
generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);

generator.save("code128_300dpi.png", BarCodeImageFormat.PNG);
```

The resolution value is especially important when barcode dimensions are specified in physical units.

## Configure colors, padding, and border

Barcode appearance can be customized through common generation parameters.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "STYLE-2025"
);

// Colors
generator.getParameters().setBackColor(Color.WHITE);
generator.getParameters().getBarcode().setBarColor(Color.BLACK);

// Padding and quiet zones
generator.getParameters().getBarcode().getPadding().getLeft().setPixels(12);
generator.getParameters().getBarcode().getPadding().getRight().setPixels(12);
generator.getParameters().getBarcode().getPadding().getTop().setPixels(6);
generator.getParameters().getBarcode().getPadding().getBottom().setPixels(6);

// Border
generator.getParameters().getBorder().setVisible(true);
generator.getParameters().getBorder().setColor(Color.GRAY);
generator.getParameters().getBorder().getWidth().setPixels(2);

generator.save("code128_styled.png", BarCodeImageFormat.PNG);
```

Left and right padding provide the blank area required around the barcode. Avoid reducing these areas excessively.

## Rotate a Code 128 barcode

Set `RotationAngle` to rotate the generated barcode image.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "ROTATE-ME"
);

generator.getParameters().setRotationAngle(90.0f);
generator.save("code128_rotate_90.png", BarCodeImageFormat.PNG);
```

Rotation is applied to the complete generated image, including code text and padding.

## Encode numeric, mixed, and lowercase content

Aspose.BarCode selects Code 128 subsets automatically according to the supplied data.

### Numeric content

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "123456789012"
);

generator.save("code128_numeric.png", BarCodeImageFormat.PNG);
```

Numeric pairs can be encoded efficiently with subset C.

### Mixed content

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "ABC123def456"
);

generator.save("code128_mixed.png", BarCodeImageFormat.PNG);
```

The generator can switch between subsets within one symbol.

### Lowercase text

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "product-code"
);

generator.save("code128_lowercase.png", BarCodeImageFormat.PNG);
```

Lowercase letters and punctuation are typically encoded with subset B.

## Create a compact Code 128 image

For a small barcode image, configure X-Dimension and bar height, disable human-readable text, reduce vertical padding, and fit the barcode to a target image box.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "SIZE-DEMO-123"
);

generator.getParameters().getBarcode().getXDimension().setPixels(2);
generator.getParameters().getBarcode().getBarHeight().setPixels(16);
generator.getParameters().getBarcode().getCodeTextParameters().setLocation(CodeLocation.NONE);
generator.getParameters().getBarcode().getPadding().getTop().setPixels(1);
generator.getParameters().getBarcode().getPadding().getBottom().setPixels(1);

generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);
generator.getParameters().getImageWidth().setPixels(300);
generator.getParameters().getImageHeight().setPixels(60);

generator.save("code128_tiny_no_text.png", BarCodeImageFormat.PNG);
```

Compact layouts should still be tested with the intended recognition device and output medium.
