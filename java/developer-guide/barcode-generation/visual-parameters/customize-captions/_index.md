---
title: "Customize Barcode Captions"
description: "Learn how to add and customize independent captions above and below barcode images in Aspose.BarCode for Java."
type: docs
weight: 50
url: /java/developer-guide/barcode-generation/visual-parameters/customize-captions/
---

# Customize Barcode Captions

Aspose.BarCode for Java supports two independent caption areas:

- `CaptionAbove` renders text above the barcode;
- `CaptionBelow` renders text below the barcode.

Captions are independent from the encoded payload. They can contain titles, product names, instructions, warehouse locations, batch information, or any other descriptive text.

The complete source code for the examples in this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/CustomizingCaptionsExample.java" target="_blank">View CustomizingCaptionsExample.java</a>

You can also browse the <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation" target="_blank">Generation examples directory</a>.

## Captions and human-readable code text

Captions and human-readable code text serve different purposes.

Human-readable code text represents the encoded barcode value and is configured through `CodetextParameters`.

Captions are independent labels configured through `CaptionParameters`.

To use a caption as the only visible text, hide the built-in human-readable code text:

```java
generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setLocation(CodeLocation.NONE);
```

Hiding the human-readable text does not change the encoded barcode payload.

## Add a caption above a barcode

The following example adds a centered title above a QR Code.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "QR-TITLE"
);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setLocation(CodeLocation.NONE);

CaptionParameters captionAbove =
        generator.getParameters().getCaptionAbove();

captionAbove.setVisible(true);
captionAbove.setText("SCAN ME");
captionAbove.getFont().getSize().setPoint(14);
captionAbove.setAlignment(TextAlignment.CENTER);
captionAbove.getPadding().getBottom().setPoint(8);

generator.save(
        "qr_title_only.png",
        BarCodeImageFormat.PNG
);
```

`CaptionAbove.getPadding().getBottom()` controls the space between the upper caption and the barcode.

## Add captions above and below

Upper and lower captions can be displayed at the same time.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "ABOVE-BELOW"
);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setLocation(CodeLocation.NONE);

CaptionParameters captionAbove =
        generator.getParameters().getCaptionAbove();

captionAbove.setVisible(true);
captionAbove.setText("INVENTORY LABEL");
captionAbove.getFont().getSize().setPoint(12);
captionAbove.setAlignment(TextAlignment.CENTER);
captionAbove.getPadding().getBottom().setPoint(6);

CaptionParameters captionBelow =
        generator.getParameters().getCaptionBelow();

captionBelow.setVisible(true);
captionBelow.setText("SKU-001-RED");
captionBelow.getFont().getSize().setPoint(10);
captionBelow.setAlignment(TextAlignment.CENTER);
captionBelow.getPadding().getTop().setPoint(8);

generator.save(
        "code128_above_and_below.png",
        BarCodeImageFormat.PNG
);
```

The upper and lower captions have separate text, font, color, alignment, and padding settings.

## Configure caption alignment

Use `TextAlignment` to align caption text horizontally.

```java
CaptionParameters caption =
        generator.getParameters().getCaptionBelow();

caption.setVisible(true);
caption.setText("WAREHOUSE A");
caption.setAlignment(TextAlignment.CENTER);
```

Available alignment values include:

```java
TextAlignment.LEFT
TextAlignment.CENTER
TextAlignment.RIGHT
```

The visual effect is easiest to see when the output image is wider than the caption text.

## Configure caption font size

Caption font size is configured through the caption font unit.

```java
CaptionParameters caption =
        generator.getParameters().getCaptionBelow();

caption.setVisible(true);
caption.setText("CAPTION 14pt");
caption.getFont().getSize().setPoint(14);
```

Point units are convenient when the output is intended for print because they represent typographic size rather than a fixed number of pixels.

The requested font must be available in the runtime environment. Otherwise, Java can substitute another installed font.

## Configure caption color

Use `setTextColor` to set the caption text color.

```java
CaptionParameters caption =
        generator.getParameters().getCaptionBelow();

caption.setVisible(true);
caption.setText("BRAND CAPTION");
caption.setTextColor(new Color(0, 128, 128));
```

The caption color can be matched to the barcode bar color for a consistent visual style.

```java
Color brandColor = new Color(30, 30, 30);

generator.getParameters()
        .getBarcode()
        .setBarColor(brandColor);

generator.getParameters()
        .getCaptionBelow()
        .setTextColor(brandColor);
```

Maintain sufficient contrast between caption text and the image background.

## Configure caption padding

Each caption has independent padding on all sides.

```java
CaptionParameters caption =
        generator.getParameters().getCaptionBelow();

caption.getPadding().getTop().setPoint(6);
caption.getPadding().getLeft().setMillimeters(2.0f);
caption.getPadding().getRight().setPixels(10);
```

Padding can be specified in different units:

- pixels for exact raster spacing;
- points for typographic layouts;
- millimeters or inches for print-oriented layouts.

For a caption above the barcode, bottom padding controls the gap toward the symbol.

For a caption below the barcode, top padding controls the gap toward the symbol.

## Use DPI-aware caption spacing

A `Unit` value can be associated with a specific resolution before converting physical or typographic units to pixels.

```java
CaptionParameters captionAbove =
        generator.getParameters().getCaptionAbove();

Unit bottomPadding =
        captionAbove.getPadding().getBottom();

bottomPadding.updateResolution(203.0f);
bottomPadding.setPoint(10.0f);
```

This is useful for thermal-printer layouts where the same physical spacing must be converted for a known printer resolution.

## Create multiline captions

Captions can contain explicit line breaks.

```java
CaptionParameters caption =
        generator.getParameters().getCaptionBelow();

caption.setVisible(true);
caption.setText("PICK FACE\nAISLE 12");
caption.setNoWrap(false);
caption.getFont().getSize().setPoint(11);
caption.setAlignment(TextAlignment.CENTER);
```

`setNoWrap(false)` allows the caption text to wrap when the available image width is limited.

Provide enough image height for all caption lines and the barcode symbol.

## Combine a title with human-readable code text

A caption can be used as a title while the barcode value remains visible below the symbol.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.EAN_13,
        "5901234123457"
);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setLocation(CodeLocation.BELOW);

CaptionParameters captionAbove =
        generator.getParameters().getCaptionAbove();

captionAbove.setVisible(true);
captionAbove.setText("PRODUCT LABEL");
captionAbove.getFont().getSize().setPoint(12);
captionAbove.setAlignment(TextAlignment.CENTER);
captionAbove.getPadding().getBottom().setPoint(6);
```

The caption text does not replace or modify the EAN-13 payload.

## Configure compact caption layouts

For compact labels, use a small font and exact pixel spacing.

```java
CaptionParameters caption =
        generator.getParameters().getCaptionBelow();

caption.setVisible(true);
caption.setText("LOT 24");
caption.getFont().getSize().setPoint(8);
caption.getPadding().getTop().setPixels(4);
caption.setAlignment(TextAlignment.CENTER);
```

Test compact layouts at the final print resolution. A caption that looks readable on screen may become too small after printing.

## Recommendations

- Use captions for descriptive text that is not part of the encoded payload.
- Hide human-readable code text only when the layout requires it.
- Keep caption text visually separate from barcode bars and modules.
- Provide enough image width and height for the selected font and padding.
- Use point, millimeter, or inch units for print-oriented layouts.
- Verify that the required fonts are installed in the runtime environment.
- Test multiline and compact captions with the final renderer and printer.
