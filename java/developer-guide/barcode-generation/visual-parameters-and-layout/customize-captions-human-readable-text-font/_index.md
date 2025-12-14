---
title: Customize Captions, Human-Readable Text, Font
type: docs
weight: 30
url: /java/developer-guide/barcode-generation2/visual-parameters-and-layout/customize-captions-human-readable-text-font/
---

# Customize Captions, Human-Readable Text, Font

## Overview

A barcode image can include human-readable text (code text) and additional captions above or below the symbol. This page shows how to control location, font, and spacing for these text elements.

## Human-readable code text

`CodeTextParameters` controls how the code text is rendered.

```java
import com.aspose.barcode.generation.*;

public class Code128WithText {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "PRODUCT-789");

        gen.getParameters().getBarcode().getCodeTextParameters().setLocation(CodeLocation.BELOW);

        gen.getParameters().getBarcode().getCodeTextParameters().getFont().setFamilyName("Arial");
        gen.getParameters().getBarcode().getCodeTextParameters().getFont().setStyle(java.awt.Font.PLAIN);
        gen.getParameters().getBarcode().getCodeTextParameters().getFont().getSize().setPoint(12);

        gen.getParameters().getBarcode().getCodeTextParameters().getSpace().setPoint(2);

        gen.save("code128_with_text.png", BarCodeImageFormat.PNG);
    }
}
```

Use code text for readability and manual checks. For automatic scanning, the barcode symbol and its quiet zone are the primary inputs.

## Alignment and color

You can control alignment and text color through `CodeTextParameters`.

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

public class CodeTextAlignmentAndColor {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "TEXT");

        gen.getParameters().getBarcode().getCodeTextParameters().setLocation(CodeLocation.BELOW);
        gen.getParameters().getBarcode().getCodeTextParameters().setAlignment(TextAlignment.CENTER);
        gen.getParameters().getBarcode().getCodeTextParameters().setColor(Color.RED);

        gen.getParameters().getBarcode().getCodeTextParameters().getFont().setFamilyName("Arial");
        gen.getParameters().getBarcode().getCodeTextParameters().getFont().getSize().setPoint(12);

        gen.save("codetext_alignment_color.png", BarCodeImageFormat.PNG);
    }
}
```

### CodeLocation options

- `BELOW` places text below the bars.
- `ABOVE` places text above the bars.
- `NONE` disables the code text.

## Captions above and below

Some builds support `CaptionAbove` and `CaptionBelow`. If available, you can render extra text blocks.

Keep captions outside the quiet zone. If the caption overlaps the symbol area or reduces padding, scanning reliability can drop.

```java
import com.aspose.barcode.generation.*;

public class Code128WithCaption {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "ITEM-12345");

        gen.getParameters().getCaptionAbove().setVisible(true);
        gen.getParameters().getCaptionAbove().setText("Product Label");
        gen.getParameters().getCaptionAbove().getFont().setFamilyName("Arial");
        gen.getParameters().getCaptionAbove().getFont().getSize().setPoint(14);
        gen.getParameters().getCaptionAbove().getPadding().getBottom().setPixels(4);

        gen.getParameters().getCaptionBelow().setVisible(true);
        gen.getParameters().getCaptionBelow().setText("Batch: A-2025-01");
        gen.getParameters().getCaptionBelow().getFont().setFamilyName("Arial");
        gen.getParameters().getCaptionBelow().getFont().getSize().setPoint(10);
        gen.getParameters().getCaptionBelow().getPadding().getTop().setPixels(4);

        gen.save("code128_with_caption.png", BarCodeImageFormat.PNG);
    }
}
```
