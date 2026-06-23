---
title: "Visual Parameters & Layout"
description: "Configure common barcode dimensions, padding, image bounds, text placement, and layout."
type: docs
weight: 20
url: /java/developer-guide/barcode-generation/visual-parameters-and-layout/
---

# Visual Parameters & Layout

Visual parameters control how barcode data is rendered. Common settings are available from `generator.getParameters()` and `generator.getParameters().getBarcode()`.

## Configure common layout parameters

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "LAYOUT-EXAMPLE"
);

generator.getParameters().getBarcode().getXDimension().setPixels(2.0f);
generator.getParameters().getBarcode().getBarHeight().setPixels(90);
generator.getParameters().getBarcode().getPadding().getLeft().setPixels(24);
generator.getParameters().getBarcode().getPadding().getRight().setPixels(24);
generator.getParameters().getBarcode().getCodeTextParameters()
        .setLocation(CodeLocation.BELOW);
generator.getParameters().getImageWidth().setPixels(520);
generator.getParameters().getImageHeight().setPixels(180);
```

The most important layout groups are:

- `Unit` values for pixels and physical measurements;
- X-dimension and bar height;
- image width and height;
- padding around the barcode;
- captions and human-readable text;
- colors, borders, backgrounds, and rotation;
- symbology-specific dimensions.

A large image canvas does not automatically make barcode modules larger. Module size is controlled by X-dimension unless an auto-size mode recalculates it.

## Complete example


<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/ImageAndLayoutParametersExample.java" target="_blank">View ImageAndLayoutParametersExample.java</a>

You can also browse the <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation" target="_blank">Generation examples directory</a>.