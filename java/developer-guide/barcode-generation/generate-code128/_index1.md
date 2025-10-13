title: Generate Code128
description: Learn how to generate Code128 and GS1-128 barcodes using Aspose.BarCode for Java with examples of size control, styling, and optimization techniques.
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/generate-code128/
---

# Generate Code 128

## Overview

**Code 128** is a high-density linear barcode symbology widely used in logistics, inventory management, and retail. It encodes the full ASCII character set (128 characters) and provides excellent data density through automatic subset switching. Aspose.BarCode for Java automatically optimizes subset selection (A/B/C) to produce the most compact barcode possible.

### Key Features

- **Full ASCII support**: Encodes all 128 ASCII characters (0-127)
- **High density**: Efficient encoding with automatic subset optimization
- **Three subsets**: A (uppercase + control), B (full ASCII), C (numeric pairs)
- **Variable length**: No fixed data length requirements
- **Built-in checksum**: Automatic check digit calculation
- **Wide adoption**: Industry standard for shipping and logistics

---

## Quick Start

Here's the simplest way to generate a Code 128 barcode:

```java
import com.aspose.barcode.generation.*;

public class Code128QuickStart {
    public static void main(String[] args) throws Exception {
        // Create barcode generator
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ASPOSE123");
        
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

        // Optional: Remove text completely
        // gen.getParameters().getBarcode().getCodeTextParameters()
        //     .setLocation(CodeLocation.NONE);

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

        // For colored barcodes (ensure good contrast!)
        // gen.getParameters().setBackColor(new Color(240, 240, 240));
        // gen.getParameters().getBarcode().setBarColor(new Color(0, 51, 102));

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

---

## GS1-128 (UCC/EAN-128)

GS1-128 is a variant of Code 128 that uses **Application Identifiers (AIs)** for structured data in supply chain applications:

```java
import com.aspose.barcode.generation.*;

public class GS1Code128Example {
    public static void main(String[] args) throws Exception {
        // Use parentheses format - FNC1 is automatically handled
        BarcodeGenerator gen = new BarcodeGenerator(
            EncodeTypes.GS_1_CODE_128,
            "(01)09501101530008(17)251231(10)BATCH-42"
        );

        // Configure for label printing
        gen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
        gen.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);
        gen.getParameters().setResolution(300.0f);

        gen.save("gs1_128.png", BarCodeImageFormat.PNG);
    }
}
```

### Common GS1 Application Identifiers

| AI | Description | Format | Example |
|----|-------------|--------|---------|
| `(01)` | GTIN (Global Trade Item Number) | 14 digits | `(01)09501101530008` |
| `(10)` | Batch/Lot Number | Variable | `(10)BATCH-2025` |
| `(17)` | Expiration Date | YYMMDD | `(17)251231` |
| `(21)` | Serial Number | Variable | `(21)SN12345678` |
| `(30)` | Quantity | Variable | `(30)100` |
| `(310n)` | Net Weight (kg) | Variable | `(3103)001234` |
| `(400)` | Customer Purchase Order | Variable | `(400)PO123456` |

### Advanced GS1-128 Example

```java
import com.aspose.barcode.generation.*;

public class GS1CompleteExample {
    public static void main(String[] args) throws Exception {
        // Complex GS1 data string with multiple AIs
        String gs1Data = "(01)09512345678900" +  // GTIN
                         "(17)260630" +           // Expiration: June 30, 2026
                         "(10)LOT2025A" +         // Batch number
                         "(21)SERIAL123456";      // Serial number

        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.GS_1_CODE_128, gs1Data);

        // Professional label settings
        gen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
        gen.getParameters().getBarcode().getBarHeight().setMillimeters(16.0f);
        gen.getParameters().setResolution(300.0f);

        // Add quiet zones
        gen.getParameters().getBarcode().getPadding().getLeft().setMillimeters(3.0f);
        gen.getParameters().getBarcode().getPadding().getRight().setMillimeters(3.0f);

        // Show human-readable text
        gen.getParameters().getBarcode().getCodeTextParameters()
            .setLocation(CodeLocation.BELOW);
        gen.getParameters().getBarcode().getCodeTextParameters()
            .setFont(new FontUnit("Arial", 9));

        gen.save("gs1_128_complete.png", BarCodeImageFormat.PNG);
    }
}
```

---

## Understanding Code 128 Subsets

Code 128 uses three character sets (subsets) to optimize encoding:

### Subset Characteristics

| Subset | Character Set | Best For | Encoding |
|--------|--------------|----------|----------|
| **A** | Uppercase letters, digits, control characters | Uppercase text with control codes | 1 character per symbol |
| **B** | Uppercase, lowercase, digits, punctuation | Mixed case text | 1 character per symbol |
| **C** | Digit pairs (00-99) | Numeric data | 2 digits per symbol |

### Automatic Optimization

The library automatically switches between subsets to minimize barcode length:

```java
import com.aspose.barcode.generation.*;

public class SubsetOptimization {
    public static void main(String[] args) throws Exception {
        // Pure numeric → Subset C (most compact)
        BarcodeGenerator gen1 = new BarcodeGenerator(EncodeTypes.CODE_128, "123456789012");
        gen1.save("code128_numeric.png");

        // Mixed content → Automatic switching between A/B/C
        BarcodeGenerator gen2 = new BarcodeGenerator(EncodeTypes.CODE_128, "ABC123def456");
        gen2.save("code128_mixed.png");

        // Lowercase → Subset B
        BarcodeGenerator gen3 = new BarcodeGenerator(EncodeTypes.CODE_128, "product-code");
        gen3.save("code128_lowercase.png");

        // You don't need to specify subsets - optimization is automatic!
    }
}
```

**Performance Tips:**
- Use **all numeric** data when possible for maximum density
- Avoid mixing character types unnecessarily
- Group similar characters together for better optimization

---

## Output Formats

Save barcodes in various image formats:

```java
import com.aspose.barcode.generation.*;

public class Code128Formats {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "FORMAT-TEST");

        // PNG - Best for web and general use (lossless)
        gen.save("code128.png", BarCodeImageFormat.PNG);

        // JPEG - Smaller files (lossy compression)
        // Note: Not recommended for barcodes due to compression artifacts
        gen.save("code128.jpg", BarCodeImageFormat.JPEG);

        // BMP - Uncompressed (large files)
        gen.save("code128.bmp", BarCodeImageFormat.BMP);

        // GIF - Good for simple graphics
        gen.save("code128.gif", BarCodeImageFormat.GIF);

        // TIFF - Professional printing (supports high resolution)
        gen.save("code128.tiff", BarCodeImageFormat.TIFF);

        // SVG - Vector format (scalable)
        gen.save("code128.svg", BarCodeImageFormat.SVG);

        // To stream
        java.io.ByteArrayOutputStream stream = new java.io.ByteArrayOutputStream();
        gen.save(stream, BarCodeImageFormat.PNG);
        byte[] imageBytes = stream.toByteArray();
    }
}
```

**Format Recommendations:**
- **PNG**: Default choice for most applications
- **SVG**: When scalability is needed (logos, print materials)
- **TIFF**: Professional printing workflows
- **Avoid JPEG**: Compression artifacts can make barcodes unscannable

---

## Best Practices

### 1. Size and Dimensions

```java
// For label printers (thermal transfer)
gen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
gen.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);

// For screen display
gen.getParameters().getBarcode().getXDimension().setPixels(2);
gen.getParameters().getBarcode().getBarHeight().setPixels(60);
```

**Guidelines:**
- **X-Dimension**: 0.30-0.50 mm (printing), 2-3 px (screen)
- **Height**: Minimum 15% of barcode width or ≥ 12.7 mm (0.5 inch)
- **Aspect Ratio**: Height should be 5-10x the X-Dimension for reliable scanning

### 2. Quiet Zones (Essential!)

```java
// Minimum quiet zone: 10x X-Dimension on each side
float xDim = gen.getParameters().getBarcode().getXDimension().getPixels();
gen.getParameters().getBarcode().getPadding().getLeft().setPixels(xDim * 10);
gen.getParameters().getBarcode().getPadding().getRight().setPixels(xDim * 10);

// Vertical quiet zones: smaller but still important
gen.getParameters().getBarcode().getPadding().getTop().setPixels(xDim * 2);
gen.getParameters().getBarcode().getPadding().getBottom().setPixels(xDim * 2);
```

### 3. Print Resolution

```java
// Always set appropriate resolution for printing
gen.getParameters().setResolution(300.0f);  // Standard
// gen.getParameters().setResolution(600.0f);  // High quality
```

### 4. Testing

Always test your barcodes with actual scanning devices:

```java
// Generate test barcode
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "TEST-SCAN-001");
gen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
gen.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);
gen.getParameters().setResolution(300.0f);

// Add quiet zones
float quietZone = gen.getParameters().getBarcode().getXDimension().getMillimeters() * 10;
gen.getParameters().getBarcode().getPadding().getLeft().setMillimeters(quietZone);
gen.getParameters().getBarcode().getPadding().getRight().setMillimeters(quietZone);

gen.save("test_barcode.png", BarCodeImageFormat.PNG);

// Test with:
// - Your target scanner hardware
// - Different lighting conditions
// - Different printing substrates
// - Various scanning angles
```

### 5. Data Optimization

```java
// Keep data concise for better scanning
String optimal = "PROD123";           // Good
String verbose = "PRODUCT-123-LONG"; // Less optimal

// Use numeric data when possible (Subset C)
String numeric = "123456789012";     // Very efficient

// Avoid unnecessary special characters
String simple = "ABC123";            // Better
String complex = "A#B$C%123";        // Less efficient
```

---

## Complete Production Example

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

public class ProductionCode128 {
    public static void main(String[] args) {
        try {
            // Product data
            String productCode = "INVENTORY-2025-001";
            
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, productCode);

            // Physical dimensions for label printer (0.33mm x-dimension)
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
            gen.getParameters().getBarcode().getBarHeight().setMillimeters(16.0f);

            // Professional printing resolution
            gen.getParameters().setResolution(300.0f);

            // Quiet zones (10x x-dimension = 3.3mm on each side)
            gen.getParameters().getBarcode().getPadding().getLeft().setMillimeters(3.3f);
            gen.getParameters().getBarcode().getPadding().getRight().setMillimeters(3.3f);
            gen.getParameters().getBarcode().getPadding().getTop().setMillimeters(1.0f);
            gen.getParameters().getBarcode().getPadding().getBottom().setMillimeters(1.0f);

            // Code text configuration
            gen.getParameters().getBarcode().getCodeTextParameters()
                .setLocation(CodeLocation.BELOW);
            gen.getParameters().getBarcode().getCodeTextParameters()
                .setFont(new FontUnit("Arial", 10));
            gen.getParameters().getBarcode().getCodeTextParameters()
                .setAlignment(TextAlignment.CENTER);
            gen.getParameters().getBarcode().getCodeTextParameters()
                .getSpace().setPoint(2);

            // Professional appearance
            gen.getParameters().setBackColor(Color.WHITE);
            gen.getParameters().getBarcode().setBarColor(Color.BLACK);

            // Optional border for label separation
            gen.getParameters().getBorder().setVisible(true);
            gen.getParameters().getBorder().setColor(Color.LIGHT_GRAY);
            gen.getParameters().getBorder().getWidth().setPixels(1);
            gen.getParameters().getBorder().setDashStyle(BorderDashStyle.SOLID);

            // Caption for product description
            gen.getParameters().getCaptionAbove().setVisible(true);
            gen.getParameters().getCaptionAbove().setText("Product Label");
            gen.getParameters().getCaptionAbove().setFont(new FontUnit("Arial", 12));
            gen.getParameters().getCaptionAbove().setAlignment(TextAlignment.CENTER);

            // Auto-size to fit content
            gen.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);

            // Save in multiple formats for different uses
            gen.save("code128_production.png", BarCodeImageFormat.PNG);
            gen.save("code128_production.svg", BarCodeImageFormat.SVG);  // For print
            
            System.out.println("Production-ready barcode generated successfully!");
            System.out.println("Product Code: " + productCode);
            System.out.println("X-Dimension: 0.33 mm");
            System.out.println("Resolution: 300 DPI");
            
        } catch (Exception e) {
            System.err.println("Error generating barcode: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

---

## Troubleshooting

### Common Issues and Solutions

**Problem: Barcode won't scan**
- ✅ Check quiet zones (minimum 10x X-Dimension)
- ✅ Verify adequate bar height (minimum 12.7 mm)
- ✅ Ensure sufficient contrast (black bars on white background)
- ✅ Check print resolution (minimum 200 DPI)
- ✅ Test with multiple scanners

**Problem: Barcode too large/small**
- ✅ Adjust X-Dimension for your medium
- ✅ Use millimeters for printing, pixels for screen
- ✅ Consider the scanning distance

**Problem: Poor print quality**
- ✅ Increase resolution to 300+ DPI
- ✅ Use PNG or TIFF format (avoid JPEG)
- ✅ Check printer settings and media quality

**Problem: Text doesn't appear**
- ✅ Set `CodeLocation.BELOW` or `CodeLocation.ABOVE`
- ✅ Ensure font size is appropriate for the barcode size
- ✅ Check that code text is not disabled

---

## Next Steps

- [Generate QR Code](/barcode/java/developer-guide/barcode-generation/generate-qr-code/)
- [Generate DataMatrix](/barcode/java/developer-guide/barcode-generation/generate-datamatrix/)
- [Customizing Barcode Appearance](/barcode/java/developer-guide/barcode-generation/customize-appearance/)
- [Barcode Recognition](/barcode/java/developer-guide/barcode-recognition/basic-barcode-recognition/)
