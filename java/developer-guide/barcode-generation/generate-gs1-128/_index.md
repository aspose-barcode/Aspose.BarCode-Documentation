title: Generate GS1-128
description: Learn how to generate GS1-128 barcodes using Aspose.BarCode for Java with examples of size control, styling, and optimization techniques.
type: docs
weight: 30
url: /java/developer-guide/barcode-generation/generate-gs-128/
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

| AI       | Description                     | Format    | Example              |
|----------|---------------------------------|-----------|----------------------|
| `(01)`   | GTIN (Global Trade Item Number) | 14 digits | `(01)09501101530008` |
| `(10)`   | Batch/Lot Number                | Variable  | `(10)BATCH-2025`     |
| `(17)`   | Expiration Date                 | YYMMDD    | `(17)251231`         |
| `(21)`   | Serial Number                   | Variable  | `(21)SN12345678`     |
| `(30)`   | Quantity                        | Variable  | `(30)100`            |
| `(310n)` | Net Weight (kg)                 | Variable  | `(3103)001234`       |
| `(400)`  | Customer Purchase Order         | Variable  | `(400)PO123456`      |

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

| Subset   | Character Set                                   | Best For                          | Encoding               |
|----------|-------------------------------------------------|-----------------------------------|------------------------|
| **A**    | Uppercase letters, digits, control characters   | Uppercase text with control codes | 1 character per symbol |
| **B**    | Uppercase, lowercase, digits, punctuation       | Mixed case text                   | 1 character per symbol |
| **C**    | Digit pairs (00-99)                             | Numeric data                      | 2 digits per symbol    |

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