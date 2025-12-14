---
title: Customize barcode size
type: docs
weight: 20
url: /java/developer-guide/barcode-generation2/visual-parameters-and-layout/customize-barcode-size/
---

# Customize barcode size

## Overview

Barcode size is controlled by geometry parameters such as X-Dimension (module width), bar height (for 1D), padding (quiet zone), and auto-sizing.

This page focuses on the parameters that define the final barcode geometry.

## X-Dimension

X-Dimension is the smallest geometric unit of a barcode symbol.

For 1D barcodes, it is the width of the narrowest bar or space. For 2D barcodes, it is the size of a single module (cell).

### Practical starting points

- For 1D barcodes, a common starting point is 0.30–0.40 mm.
- For 2D barcodes (QR, DataMatrix), a common starting point is 0.40–0.60 mm.

### Example: 1D Code 128 with X-Dimension in millimeters

```java
import com.aspose.barcode.generation.BarCodeImageFormat;
import com.aspose.barcode.generation.BarcodeGenerator;
import com.aspose.barcode.generation.EncodeTypes;

public class XDimensionCode128MmExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(
                EncodeTypes.CODE_128,
                "ASPOSE-12345"
        );

        generator.getParameters()
                 .getBarcode()
                 .getXDimension()
                 .setMillimeters(0.30f);

        generator.getParameters()
                 .getBarcode()
                 .getBarHeight()
                 .setMillimeters(12.0f);

        generator.save("code128_xdim_0_30mm.png", BarCodeImageFormat.PNG);
    }
}
```

### Example: 2D DataMatrix with X-Dimension in pixels

```java
import com.aspose.barcode.generation.BarCodeImageFormat;
import com.aspose.barcode.generation.BarcodeGenerator;
import com.aspose.barcode.generation.EncodeTypes;

public class XDimensionDataMatrixPixelsExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(
                EncodeTypes.DATA_MATRIX,
                "ASPOSE"
        );

        generator.getParameters()
                 .getBarcode()
                 .getXDimension()
                 .setPixels(8);

        generator.save("datamatrix_xdim_8px.png", BarCodeImageFormat.PNG);
    }
}
```

## AutoSizeMode vs X-Dimension

`AutoSizeMode` defines how the engine resolves conflicts between a target bitmap size (`ImageWidth`, `ImageHeight`) and geometric parameters (X-Dimension, padding, and other sizes).

The code snippets below assume that you have already created a `BarcodeGenerator` instance named `generator`.

### AutoSizeMode.NONE

- `ImageWidth` and `ImageHeight` are ignored.
- Barcode size is controlled by X-Dimension and geometry.

```java
generator.getParameters().setAutoSizeMode(AutoSizeMode.NONE);
generator.getParameters().getImageWidth().setPixels(300);   // ignored
generator.getParameters().getImageHeight().setPixels(300);  // ignored
generator.getParameters().getBarcode().getXDimension().setPixels(6);
```

### AutoSizeMode.INTERPOLATION

- The engine fits the barcode into the requested bitmap size.
- Geometry may be resampled.

```java
generator.getParameters().setAutoSizeMode(AutoSizeMode.INTERPOLATION);
generator.getParameters().getImageWidth().setPixels(300);
generator.getParameters().getImageHeight().setPixels(300);
generator.getParameters().getBarcode().getXDimension().setPixels(6);
```

### AutoSizeMode.NEAREST

- The engine fits the barcode into the requested size and prefers valid module geometry.

```java
generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);
generator.getParameters().getImageWidth().setPixels(300);
generator.getParameters().getImageHeight().setPixels(300);
generator.getParameters().getBarcode().getXDimension().setPixels(6);
```

## BarWidthReduction (printing compensation)

In offset or inkjet printing, ink can spread and make dark elements wider than expected. `BarWidthReduction` narrows bars or modules to compensate.

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

        generator.getParameters()
                 .getBarcode()
                 .getXDimension()
                 .setMillimeters(0.30f);
        generator.getParameters()
                 .getBarcode()
                 .getBarHeight()
                 .setMillimeters(12.0f);

        generator.getParameters()
                 .getBarcode()
                 .getBarWidthReduction()
                 .setPixels(0);
        generator.save("code128_bwr_0.png", BarCodeImageFormat.PNG);

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

        generator.getParameters()
                 .getBarcode()
                 .getXDimension()
                 .setPixels(10);

        generator.getParameters()
                 .getBarcode()
                 .getBarWidthReduction()
                 .setPixels(0);
        generator.save("datamatrix_bwr_0.png", BarCodeImageFormat.PNG);

        generator.getParameters()
                 .getBarcode()
                 .getBarWidthReduction()
                 .setPixels(4);
        generator.save("datamatrix_bwr_4.png", BarCodeImageFormat.PNG);
    }
}
```

## Recommended X-Dimension ranges

| Scenario | Typical X-Dimension | Unit | Notes |
|---|---|---|---|
| Office laser printing | 0.25–0.35 | mm | High resolution (≥300 dpi), minimal ink spread |
| Thermal label printer | 0.30–0.40 | mm | Common for logistics and retail labels |
| Inkjet / offset printing | 0.35–0.45 | mm | Combine with positive BarWidthReduction |
| High-density 2D codes | 0.40–0.60 | mm | QR / DataMatrix; very small modules may blur |
| On-screen UI / demo images | 4–10 | px | Choose visually; not directly tied to print requirements |

## Symbology-specific size parameters

Some symbologies have additional size parameters that are not covered by X-Dimension and bar height.

These parameters are available under symbology-specific parameter groups. Use them only when required by the barcode standard for the selected symbology.

## Bar height (1D barcodes)

For 1D barcodes, bar height controls the vertical size of the bars.

```java
import com.aspose.barcode.generation.*;

public class BarHeightExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "12345");

        generator.getParameters().getBarcode().getBarHeight().setPixels(80);
        generator.getParameters().getBarcode().getBarHeight().setMillimeters(20.0f);

        generator.save("barcode_height.png", BarCodeImageFormat.PNG);
    }
}
```

## Padding (quiet zone)

Padding defines the clear space around the barcode image (quiet zone). It is required for reliable scanning.

{{% alert color="tip" %}}
**Best Practice:**  
For most 1D barcodes (like Code 128), the standard requires a quiet zone of at least **10x the X-Dimension** on the left and right sides.  
For 2D barcodes (like QR Code), typically **4 modules (4x X-Dimension)** is required around the entire symbol.  
Always include sufficient padding to prevent nearby text or graphics from interfering with the scanner.
{{% /alert %}}

```java
import com.aspose.barcode.generation.*;

public class PaddingExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "PADDING");

        // Example: If X-Dimension is 2 pixels, Left/Right padding should be at least 20 pixels
        generator.getParameters().getBarcode().getXDimension().setPixels(2);
        
        generator.getParameters().getBarcode().getPadding().getLeft().setPixels(20);
        generator.getParameters().getBarcode().getPadding().getRight().setPixels(20);
        
        // Top/Bottom padding is less critical for 1D scanning but good for aesthetics
        generator.getParameters().getBarcode().getPadding().getTop().setPixels(10);
        generator.getParameters().getBarcode().getPadding().getBottom().setPixels(10);

        generator.save("barcode_padding.png", BarCodeImageFormat.PNG);
    }
}
```
