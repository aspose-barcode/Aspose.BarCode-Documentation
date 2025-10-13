title: Generate Code128
description: Learn how to generate Code128 and GS1-128 barcodes using Aspose.BarCode for Java with examples of size control, styling, and optimization techniques.
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/generate-code128/
---

# Generate Code 128

## Overview

**Code 128** is a high-density linear barcode symbology widely used in logistics, inventory management, and retail. It encodes the full ASCII character set (128 characters) and provides excellent data density through automatic subset switching. Aspose.BarCode for Java automatically optimizes **subset selection (A/B/C)** to produce the most compact barcode possible.

### Key Features

- **Full ASCII support**: Encodes all 128 ASCII characters (0–127) using subsets A and B.
  Subset A covers control and uppercase characters; Subset B covers printable ASCII characters.
- **High density**: Provides compact data representation with automatic subset switching for optimal efficiency.
- **Three subsets**: A – Control codes and uppercase characters (ASCII 0–95)
B – Printable ASCII characters (ASCII 32–127)
C – Numeric pairs (00–99) for dense encoding of numeric data
- **Variable length**: No fixed data length requirements
- **Built-in checksum**: Automatic Mod-103 check character calculation ensures data integrity.
- **Wide adoption**: Commonly used across logistics, shipping, and inventory management systems.

---

## Quick Start

Here's the simplest way to generate a Code 128 barcode:

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

Control the physical dimensions of your barcode using X-Dimension (narrow bar width) and bar height:

```java
import com.aspose.barcode.generation.*;

public class Code128SizeControl {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "SIZE-DEMO-123");

        // X-Dimension: width of the narrowest element (bar or space)
        // For screen display (72-96 DPI)
        gen.getParameters().getBarcode().getXDimension().setPixels(2);
        
        // For printing (use millimeters for precision)
        // gen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);

        // Bar height: vertical height of bars
        gen.getParameters().getBarcode().getBarHeight().setPixels(60);
        // Or in millimeters for printing
        // gen.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);

        // Auto-size mode determines how the image size is calculated
        gen.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);

        gen.save("code128_sized.png", BarCodeImageFormat.PNG);
    }
}
```

**Recommended Sizes:**
- **Screen display**: X-Dimension = 2-3 pixels, Height = 50-80 pixels
- **Label printing**: X-Dimension = 0.30-0.40 mm, Height = 12-20 mm
- **Industrial printing**: X-Dimension = 0.50-1.00 mm, Height = 20-40 mm

### Code Text Display

Configure how the human-readable text appears below or above the barcode:

```java
import com.aspose.barcode.generation.*;

public class Code128WithText {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "PRODUCT-789");

        // Show code text below the bars
        gen.getParameters().getBarcode().getCodeTextParameters()
            .setLocation(CodeLocation.BELOW);

        // Customize font
        gen.getParameters().getBarcode().getCodeTextParameters()
            .setFont(new FontUnit("Arial", 12));

        // Add spacing between bars and text
        gen.getParameters().getBarcode().getCodeTextParameters()
            .getSpace().setPoint(2);

        // Text alignment
        gen.getParameters().getBarcode().getCodeTextParameters()
            .setAlignment(TextAlignment.CENTER);

        gen.save("code128_with_text.png", BarCodeImageFormat.PNG);
    }
}
```

**CodeLocation Options:**
- `BELOW` - Text below bars (most common)
- `ABOVE` - Text above bars
- `NONE` - No text (barcode only)

### Image Quality and Resolution

Set appropriate resolution for your output medium:

```java
import com.aspose.barcode.generation.*;

public class Code128PrintQuality {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "PRINT-READY-001");

        // Set resolution for the entire image
        // 300 DPI is standard for professional printing
        gen.getParameters().setResolution(300.0f);

        // For high-quality laser printing
        // gen.getParameters().setResolution(600.0f);

        // Ensure image is sized appropriately
        gen.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);

        // Image dimensions (if needed)
        gen.getParameters().getImageWidth().setPixels(400);
        gen.getParameters().getImageHeight().setPixels(150);

        gen.save("code128_300dpi.png", BarCodeImageFormat.PNG);
    }
}
```

**Resolution Guidelines:**
- **72-96 DPI**: Screen display, web pages
- **200 DPI**: Desktop printing, documents
- **300 DPI**: Professional label printing (recommended)
- **600 DPI**: High-quality laser printing, small labels

---

## Appearance Customization

### Colors and Styling

Customize barcode appearance for branding or visibility requirements:

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

public class Code128Styling {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "STYLE-2025");

        // Background and bar colors
        gen.getParameters().setBackColor(Color.WHITE);
        gen.getParameters().getBarcode().setBarColor(Color.BLACK);

        // Quiet zone (mandatory blank space for reliable scanning)
        // Recommended: at least 10x X-Dimension on each side
        gen.getParameters().getBarcode().getPadding().getLeft().setPixels(12);
        gen.getParameters().getBarcode().getPadding().getRight().setPixels(12);
        gen.getParameters().getBarcode().getPadding().getTop().setPixels(6);
        gen.getParameters().getBarcode().getPadding().getBottom().setPixels(6);

        // Optional: Add visible border
        gen.getParameters().getBorder().setVisible(true);
        gen.getParameters().getBorder().setColor(Color.GRAY);
        gen.getParameters().getBorder().getWidth().setPixels(2);
        gen.getParameters().getBorder().setDashStyle(BorderDashStyle.SOLID);

        gen.save("code128_styled.png", BarCodeImageFormat.PNG);
    }
}
```

### Rotation and Orientation

Rotate barcodes for different label orientations:

```java
import com.aspose.barcode.generation.*;

public class Code128Rotation {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "ROTATE-ME");

        // Rotate 90 degrees clockwise
        gen.getParameters().setRotationAngle(90.0f);

        // Supported angles: 0, 90, 180, 270
        // gen.getParameters().setRotationAngle(180.0f);
        // gen.getParameters().setRotationAngle(270.0f);

        gen.save("code128_rotate_90.png", BarCodeImageFormat.PNG);
    }
}
```

### Caption Text

Add custom captions above or below the barcode:

```java
import com.aspose.barcode.generation.*;

public class Code128WithCaption {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "ITEM-12345");

        // Caption above barcode
        gen.getParameters().getCaptionAbove().setVisible(true);
        gen.getParameters().getCaptionAbove().setText("Product Label");
        gen.getParameters().getCaptionAbove().setFont(new FontUnit("Arial", 14));
        gen.getParameters().getCaptionAbove().setAlignment(TextAlignment.CENTER);
        gen.getParameters().getCaptionAbove().getPadding().getBottom().setPixels(4);

        // Caption below barcode
        gen.getParameters().getCaptionBelow().setVisible(true);
        gen.getParameters().getCaptionBelow().setText("Batch: A-2025-01");
        gen.getParameters().getCaptionBelow().setFont(new FontUnit("Arial", 10));
        gen.getParameters().getCaptionBelow().setAlignment(TextAlignment.CENTER);
        gen.getParameters().getCaptionBelow().getPadding().getTop().setPixels(4);

        gen.save("code128_with_caption.png", BarCodeImageFormat.PNG);
    }
}
```
## Best Practices

1. **X‑Dimension**: 0.30–0.40 mm for label printers; 2–3 px for on‑screen.
2. **Quiet Zone**: ≥ 10× X‑Dimension on left/right; a few modules on top/bottom.
3. **Height**: ≥ 15% of barcode width or ≥ 0.25 in for printed labels.
4. **Resolution**: ≥ 300 DPI for print.
5. **Test Scanning** with your target devices and media.
6. **Keep Data Reasonable**: shorter strings scan faster and produce smaller symbols.

