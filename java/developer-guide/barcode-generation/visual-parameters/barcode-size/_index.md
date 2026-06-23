---
title: "Customize Barcode Size"
description: "Configure X-dimension, bar height, auto-size modes, image bounds, and symbology-specific dimensions."
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/visual-parameters-and-layout/customize-barcode-size/
---

# Customize Barcode Size

Barcode size is determined by the encoded data, X-dimension, vertical dimensions, padding, captions, and optional fixed image bounds.

## Set X-dimension and bar height

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "SIZE-1D"
);

generator.getParameters().setAutoSizeMode(AutoSizeMode.NONE);
generator.getParameters().getBarcode().getXDimension().setPixels(3.0f);
generator.getParameters().getBarcode().getBarHeight().setPixels(100);
```

X-dimension is the width of the smallest module or narrow bar. See the <a href="https://docs.aspose.com/barcode/info-cards/x-dimension/" target="_blank">X-dimension overview</a>.

## Use auto-size modes

`AutoSizeMode.NONE` preserves explicitly configured dimensions. `AutoSizeMode.NEAREST` calculates a suitable barcode size for the image box. `AutoSizeMode.INTERPOLATION` scales the generated image to the requested bounds and may introduce resampling.

```java
generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);
generator.getParameters().getImageWidth().setPixels(240);
generator.getParameters().getImageHeight().setPixels(240);
```

When `NEAREST` is enabled, explicit X-dimension and bar-height values are not the controlling dimensions.

## Symbology-specific dimensions

Some barcode types expose additional size parameters:

- `AustralianPostShortBarHeight` controls short bars in Australian Post symbols;
- ITF-14 bearer-bar thickness and border type control the surrounding frame;
- QR version determines the module matrix size;
- Data Matrix version selects a fixed matrix configuration;
- PDF417 columns, rows, and aspect ratio influence the rectangular layout.

See the <a href="https://docs.aspose.com/barcode/info-cards/qr-code/" target="_blank">QR Code standard overview</a>, <a href="https://docs.aspose.com/barcode/info-cards/data-matrix/" target="_blank">Data Matrix standard overview</a>, and <a href="https://docs.aspose.com/barcode/info-cards/pdf417-family/" target="_blank">PDF417 standard overview</a> for structural details.

Always verify the final dimensions against the applicable barcode specification, printer process, label material, and scanner environment.

## Complete example


<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/CustomizingSizeExample.java" target="_blank">View CustomizingSizeExample.java</a>

set