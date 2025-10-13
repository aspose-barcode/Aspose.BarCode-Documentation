---
title: Generate Code128
description: Learn how to generate Code128 barcodes using Aspose.BarCode for Java with examples of size control, styling, and optimization techniques.
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/generate-code128/
---

# Generate Code 128

## Overview

**Code 128** is a high-density linear barcode symbology widely used in logistics, inventory management, and retail.  
It encodes the full ASCII character set (128 characters) and provides excellent data density through automatic subset switching.  
Aspose.BarCode for Java automatically optimizes **subset selection (A/B/C)** to produce the most compact barcode possible.

### Key Features

- **Full ASCII support** – encodes all 128 ASCII characters (0–127) using subsets A, B, and C
    - Subset A: control and uppercase characters (ASCII 0–95)
    - Subset B: printable ASCII characters (ASCII 32–127)
    - Subset C: numeric pairs (00–99) for dense encoding of numeric data
- **High density** – automatic subset switching ensures compact encoding
- **Variable length** – supports arbitrary data lengths
- **Built-in checksum** – automatic Mod-103 check character for integrity
- **Wide adoption** – standard for logistics, shipping, and warehouse labeling

---

## Quick Start

The simplest way to generate a Code 128 barcode:

```java
import com.aspose.barcode.generation.*;

public class Code128QuickStart {
    public static void main(String[] args) throws Exception {
        // Create barcode generator
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ASPOSE COMPANY");

        // Save with default settings
        generator.save("code128_quick.png", BarCodeImageFormat.PNG);
    }
}
```

---

## Key Parameters

### Setting Barcode Size

Control the physical dimensions of your barcode using **X-Dimension** (narrow bar width) and **Bar Height**:

```java
import com.aspose.barcode.generation.*;

public class Code128SizeControl {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "SIZE-DEMO-123");

        // X-Dimension: width of the narrowest bar or space
        // For screen display (72–96 DPI)
        gen.getParameters().getBarcode().getXDimension().setPixels(2);

        // For printing (use millimeters for precision)
        // gen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);

        // Bar height
        gen.getParameters().getBarcode().getBarHeight().setPixels(60);
        // Or for printing:
        // gen.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);

        // Auto-size mode determines how the final image is adjusted
        gen.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);

        gen.save("code128_sized.png", BarCodeImageFormat.PNG);
    }
}
```

**Recommended Sizes:**

| Purpose             | X-Dimension  | Height   |
|---------------------|--------------|----------|
| Screen display      | 2–3 px       | 50–80 px |
| Label printing      | 0.30–0.40 mm | 12–20 mm |
| Industrial printing | 0.50–1.00 mm | 20–40 mm |

---

### Code Text Display

Control how human-readable text appears below or above the barcode:

```java
import com.aspose.barcode.generation.*;

public class Code128WithText {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "PRODUCT-789");

        // Show code text below the bars
        gen.getParameters().getBarcode().getCodeTextParameters().setLocation(CodeLocation.BELOW);

        // Customize font (safe way – modify existing FontUnit)
        gen.getParameters().getBarcode().getCodeTextParameters().getFont().setFamilyName("Arial");
        gen.getParameters().getBarcode().getCodeTextParameters().getFont().setStyle(java.awt.Font.PLAIN);
        gen.getParameters().getBarcode().getCodeTextParameters().getFont().getSize().setPoint(12);

        // Add spacing between bars and text
        gen.getParameters().getBarcode().getCodeTextParameters().getSpace().setPoint(2);

        gen.save("code128_with_text.png", BarCodeImageFormat.PNG);
    }
}
```

**CodeLocation Options:**

- `BELOW` – Text below bars (default)
- `ABOVE` – Text above bars
- `NONE` – No text (bars only)

---

### Image Quality and Resolution

Adjust resolution to match your output medium:

```java
import com.aspose.barcode.generation.*;

public class Code128PrintQuality {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "PRINT-READY-001");

        // 300 DPI is standard for label printing
        gen.getParameters().setResolution(300.0f);

        // 600 DPI for high-precision laser printing
        // gen.getParameters().setResolution(600.0f);

        // Optional: adjust total image size
        gen.getParameters().getImageWidth().setPixels(400);
        gen.getParameters().getImageHeight().setPixels(150);

        gen.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);
        gen.save("code128_300dpi.png", BarCodeImageFormat.PNG);
    }
}
```

**Resolution Guidelines:**

| Medium             | DPI   | Notes           |
|--------------------|-------|-----------------|
| Screen / web       | 72–96 | Low precision   |
| Office printer     | 200   | Basic documents |
| Label printer      | 300   | Recommended     |
| Laser / industrial | 600   | Fine detail     |

---

## Appearance Customization

### Colors and Styling

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

public class Code128Styling {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "STYLE-2025");

        gen.getParameters().setBackColor(Color.WHITE);
        gen.getParameters().getBarcode().setBarColor(Color.BLACK);

        // Quiet zone (blank margins for reliable scanning)
        gen.getParameters().getBarcode().getPadding().getLeft().setPixels(12);
        gen.getParameters().getBarcode().getPadding().getRight().setPixels(12);
        gen.getParameters().getBarcode().getPadding().getTop().setPixels(6);
        gen.getParameters().getBarcode().getPadding().getBottom().setPixels(6);

        // Optional: visible border
        gen.getParameters().getBorder().setVisible(true);
        gen.getParameters().getBorder().setColor(Color.GRAY);
        gen.getParameters().getBorder().getWidth().setPixels(2);

        gen.save("code128_styled.png", BarCodeImageFormat.PNG);
    }
}
```

---

### Rotation and Orientation

```java
import com.aspose.barcode.generation.*;

public class Code128Rotation {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "ROTATE-ME");

        // Rotate 90° clockwise
        gen.getParameters().setRotationAngle(90.0f);

        // Supported: 0, 90, 180, 270
        gen.save("code128_rotate_90.png", BarCodeImageFormat.PNG);
    }
}
```

---

### Caption Text

*(Available only if your build supports CaptionAbove / CaptionBelow)*

```java
import com.aspose.barcode.generation.*;

public class Code128WithCaption {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "ITEM-12345");

        // Caption above
        gen.getParameters().getCaptionAbove().setVisible(true);
        gen.getParameters().getCaptionAbove().setText("Product Label");
        gen.getParameters().getCaptionAbove().getFont().setFamilyName("Arial");
        gen.getParameters().getCaptionAbove().getFont().getSize().setPoint(14);
        gen.getParameters().getCaptionAbove().getPadding().getBottom().setPixels(4);

        // Caption below
        gen.getParameters().getCaptionBelow().setVisible(true);
        gen.getParameters().getCaptionBelow().setText("Batch: A-2025-01");
        gen.getParameters().getCaptionBelow().getFont().setFamilyName("Arial");
        gen.getParameters().getCaptionBelow().getFont().getSize().setPoint(10);
        gen.getParameters().getCaptionBelow().getPadding().getTop().setPixels(4);

        gen.save("code128_with_caption.png", BarCodeImageFormat.PNG);
    }
}
```

---

## Understanding Code 128 Subsets

Code 128 uses three subsets (A, B, C) to balance density and compatibility.

| Subset  | Character Set         | Best For                    | Encoding            |
|---------|-----------------------|-----------------------------|---------------------|
| **A**   | Uppercase + control   | Control codes and uppercase | 1 char per symbol   |
| **B**   | Printable ASCII       | Mixed-case text             | 1 char per symbol   |
| **C**   | Numeric pairs (00–99) | Pure numeric data           | 2 digits per symbol |

Aspose.BarCode automatically switches between subsets for optimal encoding:

```java
import com.aspose.barcode.generation.*;

public class SubsetOptimization {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator numeric = new BarcodeGenerator(EncodeTypes.CODE_128, "123456789012");  // Uses subset C
        numeric.save("code128_numeric.png", BarCodeImageFormat.PNG);

        BarcodeGenerator mixed = new BarcodeGenerator(EncodeTypes.CODE_128, "ABC123def456");    // Auto-switching
        mixed.save("code128_mixed.png", BarCodeImageFormat.PNG);

        BarcodeGenerator lowercase = new BarcodeGenerator(EncodeTypes.CODE_128, "product-code"); // Subset B
        lowercase.save("code128_lowercase.png", BarCodeImageFormat.PNG);
    }
}
```

**Tips:**
- Use numeric data when possible for smaller symbols (Subset C)
- Avoid unnecessary character mixing
- Group similar data types to help auto-optimization

---

## Best Practices

1. **X-Dimension** – 0.30–0.40 mm for label printers; 2–3 px for on-screen use
2. **Quiet Zone** – at least 10× X-Dimension on left/right, 2× on top/bottom
3. **Height** – ≥ 15 % of barcode width or ≥ 0.25 in for printed labels
4. **Resolution** – ≥ 300 DPI for printing
5. **Testing** – verify readability on all intended scanners and substrates
6. **Data Efficiency** – shorter data → faster scan, smaller symbol

---

{{% alert color="info" %}}
💡 **Full Example on GitHub**  
You can find the complete, runnable TestNG example demonstrating Code 128 generation, size control, and text configuration here:  
👉 [GenerateCode128ExamplesTest.java on GitHub](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/design_usage_examples/src/test/java/com/aspose/barcode/guide/generation/GenerateCode128ExamplesTest.java)
{{% /alert %}}
