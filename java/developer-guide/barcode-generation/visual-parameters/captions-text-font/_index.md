---
title: "Customize Captions and Font"
description: "Configure captions, human-readable text position, fonts, colors, alignment, and spacing."
type: docs
weight: 40
url: /java/developer-guide/barcode-generation/visual-parameters-and-layout/customize-captions-human-readable-text-font/
---

# Customize Captions, Human-Readable Text, and Font

Aspose.BarCode distinguishes between human-readable code text and independent captions.

- Human-readable text represents the encoded payload and is configured through `CodetextParameters`.
- `CaptionAbove` and `CaptionBelow` are independent labels and can contain arbitrary text.

## Configure human-readable text

```java
CodetextParameters codeTextParameters = generator.getParameters()
        .getBarcode()
        .getCodeTextParameters();

codeTextParameters.setLocation(CodeLocation.BELOW);
codeTextParameters.setFontMode(FontMode.MANUAL);
codeTextParameters.getFont().setFamilyName("Arial");
codeTextParameters.getFont().setStyle(FontStyle.BOLD);
codeTextParameters.getFont().getSize().setPoint(11);
codeTextParameters.setAlignment(TextAlignment.CENTER);
codeTextParameters.getSpace().setPoint(2);
```

`FontMode.MANUAL` is required when a configured font size must be used. In automatic mode, the library calculates the font size from the available layout.

The requested font must be installed in the runtime environment. Otherwise, Java may substitute another font.

## Add captions

```java
generator.getParameters().getBarcode().getCodeTextParameters()
        .setLocation(CodeLocation.NONE);

CaptionParameters captionAbove = generator.getParameters().getCaptionAbove();
captionAbove.setVisible(true);
captionAbove.setText("INVENTORY LABEL");
captionAbove.setAlignment(TextAlignment.CENTER);
captionAbove.getFont().getSize().setPoint(12);
```

Captions have their own visibility, text, font, color, alignment, and padding. They do not change the encoded barcode payload.

## Complete example


<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/CustomizingCaptionsExample.java" target="_blank">View CustomizingCaptionsExample.java</a>

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/TextAndFontExample.java" target="_blank">View TextAndFontExample.java</a>

You can also browse the <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation" target="_blank">Generation examples directory</a>.