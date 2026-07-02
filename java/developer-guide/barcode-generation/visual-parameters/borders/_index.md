---
title: "Customize Barcode Borders"
description: "Learn how to configure barcode image borders, colors, widths, padding, and ITF-14 bearer bars in Aspose.BarCode for Java."
type: docs
weight: 30
url: /java/developer-guide/barcode-generation/visual-parameters/borders/
---

# Customize Barcode Borders

Aspose.BarCode for Java can draw a decorative border around the generated barcode image. You can configure border visibility, color, and width.

For ITF-14, separate bearer-bar settings are available because bearer bars are part of the symbology-specific layout rather than a decorative image border.

The complete source code for the examples in this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/BordersExample.java" target="_blank">View BordersExample.java</a>

## Enable an image border

Use `BorderParameters` to enable a border around the complete generated image.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "BORDER-RED-2PT"
);

BorderParameters border =
        generator.getParameters().getBorder();

border.setVisible(true);
border.getWidth().setPoint(2.0f);
border.setColor(new Color(0xE5, 0x2B, 0x2B));
```

The border width can be specified through the `Unit` returned by `getWidth()`.

## Keep the border outside the barcode area

A decorative border should remain visually separate from the barcode bars or modules. Add enough padding so that the border does not intrude into the required blank margins.

```java
generator.getParameters()
        .getBarcode()
        .getPadding()
        .getLeft()
        .setPixels(14);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getRight()
        .setPixels(14);

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
```

Then save the image:

```java
generator.save(
        "c128_border_red_2pt_on_white.png",
        BarCodeImageFormat.PNG
);
```

## Add a white border on a dark background

A barcode image can use a dark background, light modules, and a contrasting border.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "QR-WHITE-BORDER"
);

generator.getParameters()
        .setBackColor(Color.BLACK);

generator.getParameters()
        .getBarcode()
        .setBarColor(Color.WHITE);

BorderParameters border =
        generator.getParameters().getBorder();

border.setVisible(true);
border.getWidth().setPoint(2.0f);
border.setColor(Color.WHITE);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getLeft()
        .setPixels(16);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getRight()
        .setPixels(16);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getTop()
        .setPixels(16);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getBottom()
        .setPixels(16);

generator.getParameters()
        .getImageWidth()
        .setPixels(260);

generator.getParameters()
        .getImageHeight()
        .setPixels(260);

generator.save(
        "qr_white_border_on_black.png",
        BarCodeImageFormat.PNG
);
```

This example creates a white QR Code and a white solid border on a black background.

Inverted barcodes are not supported equally by all scanners. A generated image can be visually correct even when a particular reader does not recognize it. Therefore, the related test verifies that the image is created but does not require successful barcode recognition.

For maximum interoperability, use dark modules on a light background.

## Set border width in physical units

Border width can also be specified in millimeters for a target resolution.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.EAN_13,
        "5901234123457"
);

BorderParameters border =
        generator.getParameters().getBorder();

border.setVisible(true);
border.setColor(new Color(0x0B, 0x57, 0xD0));

Unit borderWidth = border.getWidth();

borderWidth.updateResolution(300f);
borderWidth.setMillimeters(1.0f);
```

In this example, the border width is configured as 1 mm at 300 DPI.

## Configure ITF-14 bearer bars

ITF-14 uses bearer bars that are specific to the symbology.

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

Unit bearerThickness =
        itfParameters.getItfBorderThickness();

bearerThickness.updateResolution(300f);
bearerThickness.setMillimeters(2.5f);

itfParameters.setQuietZoneCoef(12);
```

The `FRAME` option creates a rectangular bearer around the barcode.

## Use an alternative ITF-14 bearer layout

ITF-14 also supports alternative bearer layouts such as `BAR_OUT`.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.ITF_14,
        "10012345000017"
);

ITFParameters itfParameters = generator.getParameters()
        .getBarcode()
        .getITF();

itfParameters.setItfBorderType(
        ITF14BorderType.BAR_OUT
);

Unit bearerThickness =
        itfParameters.getItfBorderThickness();

bearerThickness.updateResolution(300f);
bearerThickness.setMillimeters(2.0f);

itfParameters.setQuietZoneCoef(12);
```

The exact bearer type, thickness, and quiet-zone dimensions should be validated against the applicable barcode specification and printing process.

## Decorative borders and bearer bars

A decorative image border and an ITF-14 bearer bar serve different purposes:

- a decorative border surrounds the complete generated image;
- an ITF-14 bearer bar is part of the barcode-specific layout;
- padding separates a decorative border from the barcode;
- `QuietZoneCoef` controls the ITF-14 quiet zone in multiples of X-dimension.

Do not replace required ITF-14 bearer bars with a decorative image border.

## Recommendations

- Keep decorative borders outside the required quiet zones.
- Use sufficient padding between the barcode and the border.
- Avoid thick borders close to linear barcode bars.
- Prefer dark bars or modules on a light background for reliable recognition.
- Do not assume that inverted barcodes are supported by every scanner.
- Treat ITF-14 bearer bars as symbology-specific elements.
- Validate physical dimensions against the target resolution and printing process.
- Test the final image with the intended scanner.
