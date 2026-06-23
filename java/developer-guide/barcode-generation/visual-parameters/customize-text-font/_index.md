---
title: "Customize Human-Readable Text and Font"
description: "Learn how to configure human-readable barcode text position, font size, color, alignment, visibility, and spacing in Aspose.BarCode for Java."
type: docs
weight: 60
url: /java/developer-guide/barcode-generation/visual-parameters/customize-human-readable-text-font/
---

# Customize Human-Readable Text and Font

Human-readable text displays the encoded barcode value as text near the barcode symbol.

In Aspose.BarCode for Java, it is configured through `CodetextParameters`:

```java
CodetextParameters codeTextParameters =
        generator.getParameters()
                .getBarcode()
                .getCodeTextParameters();
```

Changes to human-readable text affect only the visual representation. They do not change the encoded payload.

The complete source code for the examples in this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/TextAndFontExample.java" target="_blank">View TextAndFontExample.java</a>

You can also browse the <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation" target="_blank">Generation examples directory</a>.

## Place human-readable text below the barcode

Use `CodeLocation.BELOW` to display the encoded value below the bars.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "HRI-BELOW"
);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setLocation(CodeLocation.BELOW);

generator.save(
        "c128_hri_below_default.png",
        BarCodeImageFormat.PNG
);
```

This is a common layout for linear barcodes.

## Place human-readable text above the barcode

Use `CodeLocation.ABOVE` to display the text above the barcode.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "ABOVE-14PT-BLUE"
);

CodetextParameters codeText =
        generator.getParameters()
                .getBarcode()
                .getCodeTextParameters();

codeText.setLocation(CodeLocation.ABOVE);
codeText.getFont().getSize().setPoint(14);
codeText.setColor(Color.BLUE);

generator.save(
        "c128_hri_above_14pt_blue.png",
        BarCodeImageFormat.PNG
);
```

The barcode payload remains unchanged and can still be decoded as `ABOVE-14PT-BLUE`.

## Hide human-readable text

Use `CodeLocation.NONE` when the barcode value should not be rendered as text.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.UPCA,
        "042100005264"
);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setLocation(CodeLocation.NONE);

generator.save(
        "upca_hri_none.png",
        BarCodeImageFormat.PNG
);
```

This setting hides only the visible text. It does not remove the encoded data.

This layout is useful when:

- text is rendered separately by the application;
- independent captions are used;
- the barcode must fit into a compact image area.

## Configure font size

The font size is configured through the code-text font unit.

```java
CodetextParameters codeText =
        generator.getParameters()
                .getBarcode()
                .getCodeTextParameters();

codeText.getFont().getSize().setPoint(12);
```

The example project compares 8-point and 16-point human-readable text using the same Code 128 payload.

```java
BarcodeGenerator generatorSmall = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "FONT-COMPARE"
);

generatorSmall.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .getFont()
        .getSize()
        .setPoint(8);

BarcodeGenerator generatorLarge = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "FONT-COMPARE"
);

generatorLarge.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .getFont()
        .getSize()
        .setPoint(16);
```

Choose the font size according to the final image dimensions and print resolution.

## Configure text color

Use `setColor` to change the color of the human-readable text.

```java
CodetextParameters codeText =
        generator.getParameters()
                .getBarcode()
                .getCodeTextParameters();

codeText.setColor(Color.BLUE);
```

The text color is independent from the barcode bar or module color.

Maintain enough contrast between the text and the background.

## Configure text alignment

Use `TextAlignment` to control horizontal placement.

```java
CodetextParameters codeText =
        generator.getParameters()
                .getBarcode()
                .getCodeTextParameters();

codeText.setLocation(CodeLocation.BELOW);
codeText.setAlignment(TextAlignment.RIGHT);
```

Available values include:

```java
TextAlignment.LEFT
TextAlignment.CENTER
TextAlignment.RIGHT
```

Alignment is most visible when the generated image is wider than the rendered text.

## Configure spacing between the barcode and text

Use `CodetextParameters.getSpace()` to control the gap between the symbol and the human-readable text.

```java
CodetextParameters codeText =
        generator.getParameters()
                .getBarcode()
                .getCodeTextParameters();

codeText.setLocation(CodeLocation.BELOW);

Unit textGap = codeText.getSpace();
textGap.setPoint(10.0f);
```

Spacing can be configured in different units, including pixels, points, millimeters, and inches.

Point-based spacing is converted to pixels according to the unit resolution.

## Configure human-readable text for EAN-13

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.EAN_13,
        "5901234123457"
);

CodetextParameters codeText =
        generator.getParameters()
                .getBarcode()
                .getCodeTextParameters();

codeText.setLocation(CodeLocation.BELOW);
codeText.getSpace().setPoint(10.0f);

generator.save(
        "ean13_hri_below_space_pt.png",
        BarCodeImageFormat.PNG
);
```

EAN and UPC symbologies have standardized text layouts. Always verify that visual customization remains suitable for the target application and scanning environment.

## Configure human-readable text for QR Code

Two-dimensional barcodes can also display human-readable text.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "QR-UTF8"
);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setECIEncoding(ECIEncodings.UTF8);

CodetextParameters codeText =
        generator.getParameters()
                .getBarcode()
                .getCodeTextParameters();

codeText.setLocation(CodeLocation.ABOVE);
codeText.getFont().getSize().setPoint(12);

generator.save(
        "qr_hri_above_utf8_12pt.png",
        BarCodeImageFormat.PNG
);
```

The ECI setting controls the QR payload encoding. The human-readable text settings control only how the payload is displayed near the symbol.

## Configure image size for text layouts

Human-readable text requires additional vertical space.

```java
generator.getParameters()
        .getImageWidth()
        .setPixels(360);

generator.getParameters()
        .getImageHeight()
        .setPixels(180);
```

If the output image is too small, text can become compressed, clipped, or difficult to read.

When increasing the font size or spacing, increase the image height as needed.

## Human-readable text and captions

Human-readable text always represents the encoded payload.

Captions are independent labels and can contain arbitrary text.

Use human-readable text when the visible value must match the barcode payload. Use captions for titles, instructions, product descriptions, or other supporting information.

## Recommendations

- Keep the visible text consistent with the encoded payload.
- Use `CodeLocation.NONE` only when hiding the text is intentional.
- Select a font size suitable for the final output dimensions.
- Provide enough vertical space for the font and text gap.
- Maintain strong text-to-background contrast.
- Verify alignment and spacing in the generated image.
- Test EAN and UPC layouts with the intended application requirements.
- Confirm that the output remains readable after printing or image scaling.
