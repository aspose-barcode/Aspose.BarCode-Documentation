---
title: "Customize Barcode Size"
description: "Configure X-dimension, bar height, physical units, auto-size modes, image bounds, quiet zones, and symbology-specific dimensions."
type: docs
weight: 20
url: /java/developer-guide/barcode-generation/visual-parameters-and-layout/customize-barcode-size/
---

# Customize Barcode Size

Barcode size is determined by the encoded data, X-dimension, vertical dimensions, padding, captions, and optional fixed image bounds.

The complete source code for the examples in this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/CustomizeBarcodeSize.java" target="_blank">View CustomizeBarcodeSize.java</a>

## Set X-dimension and bar height

X-dimension is the width of the smallest module or narrow bar. For one-dimensional barcodes, bar height controls the vertical size of the bars.

Use `AutoSizeMode.NONE` when the explicitly configured dimensions must remain in effect.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "XDIM-PX"
);

generator.getParameters()
        .setAutoSizeMode(AutoSizeMode.NONE);

generator.getParameters()
        .getBarcode()
        .getXDimension()
        .setPixels(3.0f);

generator.getParameters()
        .getBarcode()
        .getBarHeight()
        .setPixels(100);
```

See the <a href="https://docs.aspose.com/barcode/info-cards/x-dimension/" target="_blank">X-dimension overview</a>.

## Use physical units and resolution

Barcode dimensions can be specified in physical units such as millimeters. Update the resolution of the relevant `Unit` before assigning the physical value.

```java
Unit barHeight = generator.getParameters()
        .getBarcode()
        .getBarHeight();

Unit xDimension = generator.getParameters()
        .getBarcode()
        .getXDimension();

barHeight.updateResolution(300f);
xDimension.updateResolution(300f);

barHeight.setMillimeters(12.0f);
xDimension.setMillimeters(0.5f);
```

The resolution controls how the physical value is converted to pixels. In this example, 12 mm at 300 DPI is approximately 142 pixels, and 0.5 mm is approximately 6 pixels.

## Use auto-size modes

`AutoSizeMode.NONE` preserves explicitly configured dimensions.

`AutoSizeMode.NEAREST` selects the nearest suitable barcode size for the requested image bounds.

`AutoSizeMode.INTERPOLATION` scales the generated image to the requested bounds and may introduce resampling.

```java
generator.getParameters()
        .setAutoSizeMode(AutoSizeMode.NEAREST);

generator.getParameters()
        .getImageWidth()
        .setPixels(240);

generator.getParameters()
        .getImageHeight()
        .setPixels(240);
```

When `NEAREST` or `INTERPOLATION` is used, the requested image bounds can become the controlling dimensions.

## Configure image bounds and padding

Set image width and height when the barcode must fit within a known raster area.

```java
generator.getParameters()
        .getImageWidth()
        .setPixels(500);

generator.getParameters()
        .getImageHeight()
        .setPixels(180);
```

Padding defines the empty area around the barcode.

```java
generator.getParameters()
        .getBarcode()
        .getPadding()
        .getLeft()
        .setPixels(12);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getRight()
        .setPixels(12);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getTop()
        .setPixels(8);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getBottom()
        .setPixels(8);
```

Sufficient padding helps prevent clipping and preserves the required quiet zones.

## Configure quiet zones in physical units

For EAN-13, left and right padding can be specified in millimeters at the target printer resolution.

```java
Unit leftPadding = generator.getParameters()
        .getBarcode()
        .getPadding()
        .getLeft();

Unit rightPadding = generator.getParameters()
        .getBarcode()
        .getPadding()
        .getRight();

leftPadding.updateResolution(300f);
rightPadding.updateResolution(300f);

leftPadding.setMillimeters(3.7f);
rightPadding.setMillimeters(3.7f);
```

For QR Code, padding can also be specified in typographic points.

```java
generator.getParameters()
        .getBarcode()
        .getPadding()
        .getLeft()
        .setPoint(12f);
```

## Configure Australia Post short-bar height

Australia Post exposes a dedicated short-bar-height parameter.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.AUSTRALIA_POST,
        "5912345678"
);

Unit shortBarHeight = generator.getParameters()
        .getBarcode()
        .getAustralianPost()
        .getAustralianPostShortBarHeight();

shortBarHeight.updateResolution(300f);
shortBarHeight.setMillimeters(3.0f);
```

The first two digits form the Format Control Code, and the following eight digits form the Delivery Point Identifier used in this example.

Recognition can append generated machine data to the original value, so tests should compare the recognized value by prefix rather than require exact text equality.

## Configure ITF-14 bearer bars

ITF-14 supports bearer-bar type, thickness, and quiet-zone coefficient settings.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.ITF_14,
        "10012345000017"
);

ITFParameters itfParameters = generator.getParameters()
        .getBarcode()
        .getITF();

itfParameters.setItfBorderType(
        ITF14BorderType.FRAME
);

Unit borderThickness =
        itfParameters.getItfBorderThickness();

borderThickness.updateResolution(300f);
borderThickness.setMillimeters(2.5f);

itfParameters.setQuietZoneCoef(12);
```

Ensure that the image bounds are large enough for the barcode, quiet zones, and surrounding frame.

## Configure QR dimensions

QR module size can be controlled through X-dimension.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "QR-203DPI"
);

Unit xDimension = generator.getParameters()
        .getBarcode()
        .getXDimension();

xDimension.updateResolution(203f);
xDimension.setMillimeters(0.50f);
```

A fixed QR version controls the module matrix size.

```java
generator.getParameters()
        .getBarcode()
        .getQR()
        .setVersion(QRVersion.VERSION_02);
```

See the <a href="https://docs.aspose.com/barcode/info-cards/qr-code/" target="_blank">QR Code standard overview</a>.

## Configure Data Matrix size

Data Matrix can use a fixed ECC 200 symbol version together with an explicit X-dimension.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.DATA_MATRIX,
        "DM-SIZE"
);

generator.getParameters()
        .getBarcode()
        .getDataMatrix()
        .setDataMatrixEcc(
                DataMatrixEccType.ECC_200
        );

generator.getParameters()
        .getBarcode()
        .getDataMatrix()
        .setDataMatrixVersion(
                DataMatrixVersion.ECC200_24x24
        );

generator.getParameters()
        .getBarcode()
        .getXDimension()
        .setPixels(3.0f);
```

See the <a href="https://docs.aspose.com/barcode/info-cards/data-matrix/" target="_blank">Data Matrix standard overview</a>.

## Configure PDF417 rows and columns

PDF417 exposes row and column settings that control the symbol grid.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.PDF_417,
        "PDF417-SIZE"
);

generator.getParameters()
        .getBarcode()
        .getPdf417()
        .setRows(8);

generator.getParameters()
        .getBarcode()
        .getPdf417()
        .setColumns(5);
```

See the <a href="https://docs.aspose.com/barcode/info-cards/pdf417-family/" target="_blank">PDF417 standard overview</a>.

## Recommendations

- Use `AutoSizeMode.NONE` when X-dimension and bar height must remain exact.
- Use `NEAREST` when the barcode must fit the requested image bounds without interpolation.
- Use `INTERPOLATION` only when scaled raster output is acceptable.
- Update a `Unit` resolution before assigning millimeters or inches.
- Provide sufficient image bounds and padding to prevent clipping.
- Verify physical dimensions against the printer resolution and barcode specification.
- Test the generated image with the expected scanner and print process.
