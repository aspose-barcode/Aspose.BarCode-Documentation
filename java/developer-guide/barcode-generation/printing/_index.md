---
title: Printing
type: docs
weight: 60
url: /java/developer-guide/barcode-generation2/printing/
---

# Printing

## Overview

When you generate barcodes for printing, you typically need to control resolution (DPI), geometry (X-Dimension and bar height), and symbology-specific parameters such as wide-to-narrow ratio.

## Printing Checklist

For reliable printed barcodes, verify these key parameters:

1.  **Resolution**: Ensure at least **300 DPI** for thermal/label printers and **600 DPI** for laser printers.
2.  **X-Dimension**: Set explicitly (e.g., 0.33mm). Do not rely on default pixel sizes.
3.  **Quiet Zones**: Ensure mandatory white space (padding) around the barcode.
4.  **Contrast**: Use high contrast (black on white) and avoid glossy materials that reflect scanner light.
5.  **Bar Width Reduction**: If using inkjet or wet ink, apply reduction to compensate for ink spread.

## Resolution (DPI)

Use `setResolution` to control output DPI.

```java
import com.aspose.barcode.generation.*;

public class DpiExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "HIGH-RES");

        generator.getParameters().setResolution(300.0f);
        generator.getParameters().getImageWidth().setPixels(400);
        generator.getParameters().getImageHeight().setPixels(200);

        generator.save("barcode_300dpi.png", BarCodeImageFormat.PNG);
    }
}
```

### Resolution guidelines

| Medium | DPI | Notes |
|---|---|---|
| Screen / web | 72–96 | Low precision |
| Office printer | 200 | Basic documents |
| Label printer | 300 | Recommended |
| Laser / industrial | 600 | Fine detail |

> If your build does not contain `setResolution()`, manage print density through `ImageWidth` and `ImageHeight` parameters.

## Anti-aliasing

Some workflows enable anti-aliasing for smoother rendering.

Anti-aliasing can improve visual appearance, but for some printing and scanning pipelines it can make edges less crisp. If you enable it, validate the printed result with your scanners.

```java
import com.aspose.barcode.generation.*;

public class AntiAliasExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DATA_MATRIX, "DMX-INV-000042");

        gen.getParameters().getBarcode().getXDimension().setMillimeters(0.4f);
        gen.getParameters().setUseAntiAlias(true);

        gen.save("datamatrix_antialias.png", BarCodeImageFormat.PNG);
    }
}
```

## Wide-to-narrow ratio

Some 1D symbologies such as Code 39, Interleaved 2 of 5, and Standard 2 of 5 allow you to set the ratio of wide to narrow elements (bars or spaces). Decoders use this ratio to distinguish wide and narrow elements.

If you change this value, verify the result against the symbology standard and the target scanners.

Set the ratio using `setWideNarrowRatio`.

```java
import com.aspose.barcode.generation.*;

public class WideNarrowRatioExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_39_STANDARD, "123456");

        gen.getParameters().getBarcode().setWideNarrowRatio(3.0f);
        gen.save("code39_ratio_3.png", BarCodeImageFormat.PNG);
    }
}
```
