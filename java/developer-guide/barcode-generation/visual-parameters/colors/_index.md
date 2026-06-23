---
title: "Customize Barcode Colors"
description: "Learn how to configure bar, module, caption, and human-readable text colors in Aspose.BarCode for Java."
type: docs
weight: 50
url: /java/developer-guide/barcode-generation/visual-parameters/colors/
---

# Customize Barcode Colors

Aspose.BarCode for Java allows you to customize the colors of barcode bars, two-dimensional modules, captions, and human-readable code text.

The complete source code for the examples in this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/ColorsExample.java" target="_blank">View ColorsExample.java</a>

You can also browse the <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation" target="_blank">Generation examples directory</a>.

## Set the bar or module color

Use `setBarColor` to configure the foreground color of a barcode.

For linear symbologies, this setting changes the bar color. For two-dimensional symbologies, it changes the module color.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "COLOR-EXAMPLE"
);

generator.getParameters()
        .getBarcode()
        .setBarColor(Color.DARK_GRAY);

generator.save(
        "code128_dark_gray.png",
        BarCodeImageFormat.PNG
);
```

## Use a custom RGB color

```java
Color darkBlue = new Color(20, 45, 90);

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "CUSTOM-RGB"
);

generator.getParameters()
        .getBarcode()
        .setBarColor(darkBlue);

generator.save(
        "qr_dark_blue.png",
        BarCodeImageFormat.PNG
);
```

## Set human-readable text color

Human-readable code text is configured through `CodetextParameters`.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "TEXT-COLOR"
);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setColor(Color.BLUE);

generator.save(
        "code128_text_color.png",
        BarCodeImageFormat.PNG
);
```

## Set caption colors

Caption colors are configured independently for the upper and lower captions.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "CAPTION-COLOR"
);

generator.getParameters()
        .getCaptionAbove()
        .setVisible(true);

generator.getParameters()
        .getCaptionAbove()
        .setText("Inventory");

generator.getParameters()
        .getCaptionAbove()
        .setTextColor(Color.RED);

generator.getParameters()
        .getCaptionBelow()
        .setVisible(true);

generator.getParameters()
        .getCaptionBelow()
        .setText("Warehouse A");

generator.getParameters()
        .getCaptionBelow()
        .setTextColor(Color.BLUE);

generator.save(
        "code128_caption_colors.png",
        BarCodeImageFormat.PNG
);
```

## Use light modules on a dark background

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "LIGHT-ON-DARK"
);

generator.getParameters().setBackColor(Color.BLACK);

generator.getParameters()
        .getBarcode()
        .setBarColor(Color.WHITE);

generator.save(
        "qr_light_on_dark.png",
        BarCodeImageFormat.PNG
);
```

Not all scanners process inverted barcodes equally well. Dark bars or modules on a light background remain the safest choice for broad interoperability.

## Recommendations

- Maintain strong contrast between the barcode and the background.
- Avoid combinations with similar luminance.
- Test custom colors with the target scanner and printer.
- Verify caption and code-text readability separately.
- Prefer dark foreground colors on a light background for critical applications.
