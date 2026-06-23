---
title: "Image and Layout Parameters"
description: "Learn how to configure barcode image dimensions, automatic sizing, resolution, and layout behavior in Aspose.BarCode for Java."
type: docs
weight: 90
url: /java/developer-guide/barcode-generation/visual-parameters/image-and-layout-parameters/
---

# Image and Layout Parameters

Aspose.BarCode for Java provides image-level and layout-level parameters that control the generated canvas, barcode placement, automatic sizing, and conversion between physical units and pixels.

These settings are useful when a barcode must fit a predefined image area or match a target print resolution.

The complete source code for the examples in this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/ImageAndLayoutParametersExample.java" target="_blank">View ImageAndLayoutParametersExample.java</a>

## Image parameters and barcode parameters

Generation settings are organized into several parameter groups.

Image-level settings are available directly from `BaseGenerationParameters`:

```java
generator.getParameters().getImageWidth();
generator.getParameters().getImageHeight();
generator.getParameters().setResolution(300.0f);
generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);
```

Barcode-level settings are available through `getBarcode()`:

```java
generator.getParameters().getBarcode().getXDimension();
generator.getParameters().getBarcode().getBarHeight();
generator.getParameters().getBarcode().getPadding();
```

Image dimensions define the output canvas. Barcode dimensions define the geometry of the symbol inside that canvas.

## Set the output image size

Use `ImageWidth` and `ImageHeight` to specify the generated bitmap dimensions.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "IMAGE-SIZE"
);

generator.getParameters()
        .getImageWidth()
        .setPixels(400);

generator.getParameters()
        .getImageHeight()
        .setPixels(160);

generator.save(
        "code128_image_size.png",
        BarCodeImageFormat.PNG
);
```

The image size includes the barcode, human-readable text, captions, padding, and border.

A canvas that is too small can force the barcode into an unsuitable layout or leave insufficient room for text and margins.

## Configure automatic sizing

Use `AutoSizeMode` when the barcode must fit a predefined image box.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "AUTO-SIZE"
);

generator.getParameters()
        .getImageWidth()
        .setPixels(240);

generator.getParameters()
        .getImageHeight()
        .setPixels(240);

generator.getParameters()
        .setAutoSizeMode(AutoSizeMode.NEAREST);

generator.save(
        "qr_auto_size.png",
        BarCodeImageFormat.PNG
);
```

`AutoSizeMode.NEAREST` selects barcode dimensions that fit the specified image size while preserving valid symbol geometry as closely as possible.

This mode is useful for:

- thumbnails;
- fixed-size labels;
- predefined UI placeholders;
- generated reports;
- bitmap templates.

## Manual sizing and automatic sizing

Manual sizing and automatic sizing represent different layout strategies.

With manual sizing, you control barcode geometry directly:

```java
generator.getParameters()
        .getBarcode()
        .getXDimension()
        .setPixels(3);

generator.getParameters()
        .getBarcode()
        .getBarHeight()
        .setPixels(80);
```

With automatic sizing, the library calculates effective dimensions to fit the requested image box:

```java
generator.getParameters()
        .setAutoSizeMode(AutoSizeMode.NEAREST);

generator.getParameters()
        .getImageWidth()
        .setPixels(300);

generator.getParameters()
        .getImageHeight()
        .setPixels(100);
```

When automatic sizing is enabled, explicit X-dimension and bar-height values may no longer determine the final symbol size.

Use manual sizing when exact module width or bar height is required. Use automatic sizing when fitting the barcode into a target canvas is the primary requirement.

## Configure output resolution

Use `setResolution` to define the output resolution in dots per inch.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "PRINT-READY"
);

generator.getParameters()
        .setResolution(300.0f);

generator.save(
        "code128_300dpi.png",
        BarCodeImageFormat.PNG
);
```

Resolution is especially important when dimensions are specified in physical units such as:

- millimeters;
- inches;
- points.

For example:

```java
generator.getParameters()
        .getBarcode()
        .getXDimension()
        .setMillimeters(0.33f);

generator.getParameters()
        .getBarcode()
        .getBarHeight()
        .setMillimeters(15.0f);

generator.getParameters()
        .setResolution(300.0f);
```

The resolution value determines how physical measurements are converted to pixels.

When image dimensions are already specified directly in pixels, increasing the resolution value does not by itself increase the bitmap width or height.

## Create a fixed-size print-oriented image

The following example combines a target image box with a print resolution.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "PRINT-BOX"
);

generator.getParameters()
        .setResolution(300.0f);

generator.getParameters()
        .getImageWidth()
        .setPixels(500);

generator.getParameters()
        .getImageHeight()
        .setPixels(180);

generator.getParameters()
        .setAutoSizeMode(AutoSizeMode.NEAREST);

generator.save(
        "code128_print_box.png",
        BarCodeImageFormat.PNG
);
```

A fixed pixel box does not guarantee a specific physical barcode size unless the image is rendered or printed at the intended resolution.

Validate the final X-dimension, quiet zones, and print dimensions for the target application.

## Configure padding within the image

Padding adds blank space around the barcode symbol inside the generated image.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "IMAGE-PADDING"
);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getLeft()
        .setPixels(20);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getRight()
        .setPixels(20);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getTop()
        .setPixels(10);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getBottom()
        .setPixels(10);

generator.save(
        "code128_image_padding.png",
        BarCodeImageFormat.PNG
);
```

Padding affects the available layout area. Large padding values leave less space for the symbol when a fixed image size is used.

Padding can reserve space for quiet zones, but the required quiet-zone dimensions depend on the symbology and application specification.

## Account for human-readable text

Human-readable text requires additional vertical space.

```java
generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setLocation(CodeLocation.BELOW);

generator.getParameters()
        .getImageHeight()
        .setPixels(180);
```

If the image height is too small, the barcode or text can become compressed.

When using large fonts, captions, or increased text spacing, increase the image height accordingly.

## Create a compact barcode image

To create a compact image:

1. hide human-readable text if it is not required;
2. reduce top and bottom padding;
3. set the target image dimensions;
4. enable automatic sizing.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "COMPACT-LAYOUT"
);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setLocation(CodeLocation.NONE);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getTop()
        .setPixels(1);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getBottom()
        .setPixels(1);

generator.getParameters()
        .getImageWidth()
        .setPixels(300);

generator.getParameters()
        .getImageHeight()
        .setPixels(60);

generator.getParameters()
        .setAutoSizeMode(AutoSizeMode.NEAREST);

generator.save(
        "code128_compact.png",
        BarCodeImageFormat.PNG
);
```

Compact barcodes should always be tested with the intended scanner and output medium.

## Choose between pixels and physical units

Use pixels when:

- the final output is a screen image;
- exact bitmap dimensions are required;
- the rendering environment is fully controlled.

Use millimeters or inches when:

- the barcode is intended for printing;
- physical dimensions must remain consistent;
- the printer resolution is known.

Use points primarily for typographic values such as font size and text spacing.

## Recommendations

- Decide whether exact barcode geometry or exact image size is more important.
- Use manual sizing for controlled X-dimension and bar height.
- Use `AutoSizeMode.NEAREST` for fixed image boxes.
- Set the intended resolution before using physical units.
- Provide enough image space for text, captions, padding, and borders.
- Do not assume that a fixed pixel image has a fixed physical size.
- Validate compact and print-oriented layouts with the final scanner and printer.
