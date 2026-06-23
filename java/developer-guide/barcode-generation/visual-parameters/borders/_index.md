---
title: "Customize Barcode Borders"
description: "Learn how to configure barcode image borders, colors, widths, line styles, and ITF-14 bearer bars in Aspose.BarCode for Java."
type: docs
weight: 30
url: /java/developer-guide/barcode-generation/visual-parameters/borders/
---

# Customize Barcode Borders

Aspose.BarCode for Java can draw a border around the generated barcode image. You can configure border visibility, color, width, and line style.

For ITF-14, separate bearer-bar settings are available because bearer bars are part of the symbology-specific layout rather than a decorative image border.

The complete source code for the examples in this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/BordersExample.java" target="_blank">View BordersExample.java</a>

You can also browse the <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation" target="_blank">Generation examples directory</a>.

## Enable an image border

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "BORDER-EXAMPLE"
);

generator.getParameters()
        .getBorder()
        .setVisible(true);

generator.save(
        "code128_border.png",
        BarCodeImageFormat.PNG
);
```

## Set border color and width

```java
generator.getParameters()
        .getBorder()
        .setColor(Color.GRAY);

generator.getParameters()
        .getBorder()
        .getWidth()
        .setPixels(2);
```

## Set the border line style

```java
generator.getParameters()
        .getBorder()
        .setDashStyle(BorderDashStyle.SOLID);
```

Depending on the library version, additional dash styles can be available.

A decorative border should remain visually separate from the barcode bars or modules. Provide enough padding so that the border does not intrude into the required blank margins.

## Use a border with a custom background

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "BORDER-STYLE"
);

generator.getParameters().setBackColor(
        new Color(245, 248, 252)
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
        .getBorder()
        .setVisible(true);

generator.getParameters()
        .getBorder()
        .setColor(Color.DARK_GRAY);

generator.getParameters()
        .getBorder()
        .getWidth()
        .setPixels(2);

generator.save(
        "code128_border_complete.png",
        BarCodeImageFormat.PNG
);
```

## Configure ITF-14 bearer bars

ITF-14 uses bearer bars that are specific to the symbology.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.ITF_14,
        "12345678901231"
);

generator.getParameters()
        .getBarcode()
        .getITF()
        .setItfBorderType(ITF14BorderType.FRAME);

generator.getParameters()
        .getBarcode()
        .getITF()
        .getItfBorderThickness()
        .setPixels(4);

generator.save(
        "itf14_frame.png",
        BarCodeImageFormat.PNG
);
```

Available bearer-bar layouts can include frame and bar variants. The exact physical dimensions should be validated against the applicable barcode specification and printing process.

## Recommendations

- Keep decorative borders outside the required quiet zones.
- Use sufficient padding between the barcode and the border.
- Avoid thick borders near linear barcode bars.
- Treat ITF-14 bearer bars as symbology-specific elements.
- Validate the result with the intended printer and scanner.
