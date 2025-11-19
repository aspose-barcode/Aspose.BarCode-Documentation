---
title: "How use X-Dimension"
description: "Learn how to configure X-Dimension for 1D and 2D barcodes in Aspose.BarCode for Java. Adjust barcode density, image size, AutoSizeMode behavior, and printing quality using precise X-Dimension and BarWidthReduction values."
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/xdimension/
---

# Configuring X-Dimension in Aspose.BarCode for Java

In *Aspose.BarCode for Java*, **X-Dimension** defines the smallest geometric unit of a barcode symbol:

- For **1D barcodes**, it is the width of the narrowest bar or space.
- For **2D barcodes**, it is the size of a single module (square cell).

This parameter directly affects:

- **Barcode density** (how compact the symbol is),
- **Overall image size**,
- **Print and scanner reliability**.

---

## What is X-Dimension and why it matters

Correct X-Dimension is critical for reliable printing and scanning:

- **Too small X-Dimension**
    - Bars or modules may blur, merge, or disappear on paper.
    - Low-cost printers and low DPI make this worse.
- **Too large X-Dimension**
    - Barcode becomes physically bigger.
    - Easier to scan, but may not fit on small labels or packaging.

### Practical starting points

From typical print workflows:

- For **1D barcodes**, start around **0.30–0.40 mm**.
- For **2D barcodes** (QR, DataMatrix), start around **0.40–0.60 mm** for modules.
- For **offset/inkjet printing**, combine X-Dimension with **BarWidthReduction** to compensate ink spreading.

---

## API overview: how to set X-Dimension

The X-Dimension is exposed through the `BarcodeParameters` API:

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ASPOSE");

// Access barcode parameters
generator.getParameters()
        .getBarcode()
        .getXDimension();
```

`getXDimension()` returns a `Unit` object that allows you to set the size in different units:

- `setPixels(int pixels)`
- `setMillimeters(float millimeters)`
- `setInches(float inches)`
- `setPoints(float points)`

Use **millimeters** for print-oriented layouts and **pixels** for on-screen/demo images.

---

## Example 1: 1D Code 128 with X-Dimension in millimeters

This example is based on the `xdim_Code128_in_millimeters` test from `XDimensionExamples`.

```java
import com.aspose.barcode.generation.BarCodeImageFormat;
import com.aspose.barcode.generation.BarcodeGenerator;
import com.aspose.barcode.generation.EncodeTypes;

public class XDimensionCode128MmExample {
    public static void main(String[] args) throws Exception {
        // Code 128 with human-friendly payload
        BarcodeGenerator generator = new BarcodeGenerator(
                EncodeTypes.CODE_128,
                "ASPOSE-12345"
        );

        // Set X-Dimension to 0.30 mm:
        // - Configures the narrowest bar width
        // - Safe starting point for thermal and laser printers
        generator.getParameters()
                 .getBarcode()
                 .getXDimension()
                 .setMillimeters(0.30f);

        // Bar height (1D only) in millimeters: affects vertical size of bars
        generator.getParameters()
                 .getBarcode()
                 .getBarHeight()
                 .setMillimeters(12.0f);

        // Save the generated barcode image
        generator.save("code128_xdim_0_30mm.png", BarCodeImageFormat.PNG);
    }
}
```

**When to use this pattern**

- Printing **Code 128** labels on thermal or laser printers.
- Logistics, warehouse, or retail barcodes where label size is known and controlled.
- When you need predictable **physical width** of the symbol.

---

## Example 2: 2D DataMatrix with X-Dimension in pixels

This example is based on the `xdim_DataMatrix_in_pixels` test.

```java
import com.aspose.barcode.generation.BarCodeImageFormat;
import com.aspose.barcode.generation.BarcodeGenerator;
import com.aspose.barcode.generation.EncodeTypes;

public class XDimensionDataMatrixPixelsExample {
    public static void main(String[] args) throws Exception {
        // 2D symbols use module (cell) size as X-Dimension
        BarcodeGenerator generator = new BarcodeGenerator(
                EncodeTypes.DATA_MATRIX,
                "ASPOSE"
        );

        // Set module size to 8 pixels.
        // For screen/demo outputs pixels are convenient;
        // for printing, prefer millimeters instead.
        generator.getParameters()
                 .getBarcode()
                 .getXDimension()
                 .setPixels(8);

        generator.save("datamatrix_xdim_8px.png", BarCodeImageFormat.PNG);
    }
}
```

**Usage notes**

- Use **pixels** when:
    - You generate barcodes for UI previews, web pages, or documentation.
    - The target is a screen, not a printer.
- For production printing, convert required mm to pixels using target DPI and use `setMillimeters`.

---

## Example 3: Comparing barcode density with small vs large X-Dimension (1D)

The test `xdim_Code128_density_comparison` shows how X-Dimension impacts overall width.

```java
import com.aspose.barcode.generation.BarCodeImageFormat;
import com.aspose.barcode.generation.BarcodeGenerator;
import com.aspose.barcode.generation.EncodeTypes;

public class XDimensionDensityComparisonExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(
                EncodeTypes.CODE_128,
                "DENSITY-CHECK-1234567890"
        );

        // Case A: compact symbol (0.25 mm)
        generator.getParameters()
                 .getBarcode()
                 .getXDimension()
                 .setMillimeters(0.25f);
        generator.getParameters()
                 .getBarcode()
                 .getBarHeight()
                 .setMillimeters(12.0f);

        generator.save("code128_xdim_0_25mm.png", BarCodeImageFormat.PNG);

        // Case B: larger symbol (0.50 mm)
        generator.getParameters()
                 .getBarcode()
                 .getXDimension()
                 .setMillimeters(0.50f);

        // Keep the same bar height for a fair visual comparison
        generator.getParameters()
                 .getBarcode()
                 .getBarHeight()
                 .setMillimeters(12.0f);

        generator.save("code128_xdim_0_50mm.png", BarCodeImageFormat.PNG);
    }
}
```

**What to look for**

- `code128_xdim_0_25mm.png`
    - Narrow bars, higher data density.
    - Symbol is significantly more compact.
    - On low-quality printing, thin bars may be harder to scan.

- `code128_xdim_0_50mm.png`
    - Wider bars, lower density, but more tolerant to printing imperfections.
    - Good choice if label space is not a constraint.

This pattern is useful when you need to visually choose a compromise between **compactness** and **scanning robustness**.

---

## AutoSizeMode vs X-Dimension

The test `xdim_AutoSizeModes_effects` demonstrates how `AutoSizeMode` interacts with X-Dimension and `ImageWidth`/`ImageHeight`.

`AutoSizeMode` defines how the engine resolves conflicts between:

- Desired **bitmap size** (`ImageWidth`, `ImageHeight`), and
- Desired **geometric parameters** (X-Dimension, paddings, etc.).

### AutoSizeMode.NONE

- `ImageWidth` and `ImageHeight` are **ignored**.
- Barcode size is fully controlled by **X-Dimension**, margins, and content length.

```java
generator.getParameters().setAutoSizeMode(AutoSizeMode.NONE);
generator.getParameters().getImageWidth().setPixels(300);   // ignored
generator.getParameters().getImageHeight().setPixels(300);  // ignored
generator.getParameters().getBarcode().getXDimension().setPixels(6);
```

Use this when you:

- Want predictable **physical size** based purely on geometry.
- Target print and do not care about exact pixel dimensions of the image.

### AutoSizeMode.INTERPOLATION

- Engine strictly fits the barcode into the requested bitmap size.
- Geometry may be interpolated (resampled), potentially distorting modules.

```java
generator.getParameters().setAutoSizeMode(AutoSizeMode.INTERPOLATION);
generator.getParameters().getImageWidth().setPixels(300);
generator.getParameters().getImageHeight().setPixels(300);

// X-Dimension is mostly overridden by interpolation
generator.getParameters().getBarcode().getXDimension().setPixels(6);
```

Use when:

- You must produce images of **exact width/height** in pixels.
- Distortion is acceptable (for example, for high-DPI images or demo thumbnails).

### AutoSizeMode.NEAREST

- Engine tries to fit the requested size with **minimal distortion**,  
  preferring valid module geometry.

```java
generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);
generator.getParameters().getImageWidth().setPixels(300);
generator.getParameters().getImageHeight().setPixels(300);
generator.getParameters().getBarcode().getXDimension().setPixels(6);
```

Use when:

- You need to respect a **target bitmap size**,
- But still care about barcode geometry and scanner tolerance.
- This is a good default when images are embedded into fixed-size UI containers or reports.

---

## Combining X-Dimension with BarWidthReduction for printing

In offset or inkjet printing, ink often **spreads**, making dark elements wider than expected.  
To compensate, Aspose.BarCode provides **BarWidthReduction (BWR)**:

- Positive BWR values **narrow** bars or modules.
- Has strong impact on ink-based printers and little to no effect on laser devices.

The test `xdim_with_BarWidthReduction_Code128_and_DataMatrix` shows both 1D and 2D scenarios.

### Example: Code 128 with and without BarWidthReduction

```java
import com.aspose.barcode.generation.BarCodeImageFormat;
import com.aspose.barcode.generation.BarcodeGenerator;
import com.aspose.barcode.generation.EncodeTypes;

public class XDimensionBwrCode128Example {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(
                EncodeTypes.CODE_128,
                "ASPOSE"
        );

        // Base geometry
        generator.getParameters()
                 .getBarcode()
                 .getXDimension()
                 .setMillimeters(0.30f);
        generator.getParameters()
                 .getBarcode()
                 .getBarHeight()
                 .setMillimeters(12.0f);

        // No reduction
        generator.getParameters()
                 .getBarcode()
                 .getBarWidthReduction()
                 .setPixels(0);
        generator.save("code128_bwr_0.png", BarCodeImageFormat.PNG);

        // Reduce bars by 4 pixels (visible on low-DPI demo images)
        // For real printers, use values recommended by the printer vendor.
        generator.getParameters()
                 .getBarcode()
                 .getBarWidthReduction()
                 .setPixels(4);
        generator.save("code128_bwr_4.png", BarCodeImageFormat.PNG);
    }
}
```

### Example: DataMatrix with BarWidthReduction

```java
import com.aspose.barcode.generation.BarCodeImageFormat;
import com.aspose.barcode.generation.BarcodeGenerator;
import com.aspose.barcode.generation.EncodeTypes;

public class XDimensionBwrDataMatrixExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(
                EncodeTypes.DATA_MATRIX,
                "ASPOSE"
        );

        // Module size in pixels
        generator.getParameters()
                 .getBarcode()
                 .getXDimension()
                 .setPixels(10);

        // No reduction
        generator.getParameters()
                 .getBarcode()
                 .getBarWidthReduction()
                 .setPixels(0);
        generator.save("datamatrix_bwr_0.png", BarCodeImageFormat.PNG);

        // Reduce modules by 4 pixels: shrinks black modules slightly
        generator.getParameters()
                 .getBarcode()
                 .getBarWidthReduction()
                 .setPixels(4);
        generator.save("datamatrix_bwr_4.png", BarCodeImageFormat.PNG);
    }
}
```

**When to tune BWR**

- Offset printing on porous paper.
- Inkjet labels where black elements tend to “grow”.
- Regulatory barcodes requiring strict bar width tolerances.

---

## Recommended X-Dimension ranges

| Scenario                      | Typical X-Dimension | Unit | Notes                                                      |
|------------------------------|---------------------|------|-----------------------------------------------------------|
| Office laser printing        | 0.25–0.35           | mm   | High resolution (≥300 dpi), minimal ink spread           |
| Thermal label printer        | 0.30–0.40           | mm   | Common for logistics and retail labels                   |
| Inkjet / offset printing     | 0.35–0.45           | mm   | Combine with positive BarWidthReduction                  |
| High-density 2D codes        | 0.40–0.60           | mm   | QR / DataMatrix; very small modules may blur            |
| On-screen UI / demo images   | 4–10                | px   | Choose visually; not directly tied to print requirements |

Treat these values as **starting points**; always verify with your target printers and scanners.

---

## Complete test example on GitHub

> Full TestNG Example  
> A complete, runnable TestNG class that demonstrates X-Dimension usage for 1D and 2D barcodes, AutoSizeMode interaction, and BarWidthReduction is available in the Aspose.BarCode for Java examples repository.  
> Look for `XDimensionExamples.java` in package `com.aspose.barcode.guide.generation.xdimension`.

---

## Summary

| Property              | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| **X-Dimension**       | Size of the narrowest bar (1D) or module (2D).                             |
| **Units**             | Can be set in pixels, millimeters, inches, or points.                      |
| **Effect on layout**  | Controls barcode density, image size, and scanner readability.             |
| **AutoSizeMode.NONE** | Size is driven by X-Dimension and geometry; ImageWidth/Height are ignored. |
| **AutoSizeMode.INTERPOLATION** | Fits exact bitmap size, may distort modules.                     |
| **AutoSizeMode.NEAREST**       | Balances requested size with valid module geometry.              |
| **BarWidthReduction** | Narrows bars/modules to compensate ink spread during printing.             |

By carefully tuning **X-Dimension**, **AutoSizeMode**, and **BarWidthReduction**, you can achieve an optimal balance between barcode compactness, print quality, and scanner reliability across different printers and media types.
