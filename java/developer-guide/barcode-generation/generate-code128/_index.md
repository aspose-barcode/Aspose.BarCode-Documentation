---
title: Generate Code128
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/Generate-Code128
---
# Generate Code128 - Quick Example

## Overview

Code 128 is a high-density linear barcode symbology widely used in logistics, inventory management, and retail. 
It can encode the full ASCII character set and is known for its excellent data density.

## Basic Code128 Generation

Here's the simplest way to generate a Code128 barcode:

```java
import com.aspose.barcode.generation.*;

public class Code128Example {
    public static void main(String[] args) {
        // Create barcode generator instance
        BarcodeGenerator generator = new BarcodeGenerator(
            EncodeTypes.CODE_128, 
            "ASPOSE123"
        );
        
        // Save barcode image
        generator.save("code128.png");
    }
}
```

## Code128 Subsets

Code 128 has three subsets (A, B, C) that are automatically selected based on your data:

- **Subset A**: Uppercase letters, control characters, special symbols
- **Subset B**: Uppercase and lowercase letters, numbers, special symbols
- **Subset C**: Double-digit numbers (most compact for numeric data)

The library automatically optimizes subset selection for best encoding efficiency.

## Key Configuration Options

### 1. Setting Barcode Height and Width

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ABC123");

// Set bar width (X-dimension) in pixels
generator.getParameters().getBarcode().getXDimension().setPixels(2);

// Set barcode height in pixels
generator.getParameters().getBarcode().getBarHeight().setPixels(80);

generator.save("code128_sized.png");
```

### 2. Adding Human-Readable Text

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "PRODUCT-789");

// Configure code text (human-readable text below barcode)
generator.getParameters().getBarcode().getCodeTextParameters()
    .setLocation(CodeLocation.BELOW);
generator.getParameters().getBarcode().getCodeTextParameters()
    .setFont(new com.aspose.barcode.generation.FontUnit("Arial", 12));
generator.getParameters().getBarcode().getCodeTextParameters()
    .setSpace(new com.aspose.barcode.generation.Unit(2, UnitType.POINT));

generator.save("code128_with_text.png");
```

### 3. Setting Image Resolution

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "12345678");

// Set resolution for high-quality printing
generator.getParameters().setResolution(300); // 300 DPI

generator.save("code128_high_res.png");
```

## GS1-128 (EAN-128)

GS1-128 is a variant of Code 128 used in supply chain applications. It uses Application Identifiers (AI) for data formatting:

```java
BarcodeGenerator generator = new BarcodeGenerator(
    EncodeTypes.GS_1_CODE_128, 
    "(01)12345678901231(21)SERIAL123"
);

// GS1-128 automatically handles FNC1 characters
generator.save("gs1_128.png");
```

Common Application Identifiers:
- `(01)` - GTIN (Global Trade Item Number)
- `(10)` - Batch/Lot number
- `(21)` - Serial number
- `(17)` - Expiration date

## Complete Example with All Settings

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

public class CompleteCode128Example {
    public static void main(String[] args) {
        try {
            // Initialize barcode generator
            BarcodeGenerator generator = new BarcodeGenerator(
                EncodeTypes.CODE_128, 
                "INVENTORY-2024-001"
            );
            
            // Configure barcode dimensions
            generator.getParameters().getBarcode().getXDimension().setPixels(2);
            generator.getParameters().getBarcode().getBarHeight().setPixels(60);
            
            // Set resolution
            generator.getParameters().setResolution(300);
            
            // Configure code text
            generator.getParameters().getBarcode().getCodeTextParameters()
                .setLocation(CodeLocation.BELOW);
            generator.getParameters().getBarcode().getCodeTextParameters()
                .setFont(new FontUnit("Arial", 10));
            generator.getParameters().getBarcode().getCodeTextParameters()
                .getSpace().setPoint(2);
            
            // Set colors
            generator.getParameters().setBackColor(Color.WHITE);
            generator.getParameters().getBarcode().setBarColor(Color.BLACK);
            
            // Add margins
            generator.getParameters().getBarcode().getPadding().getLeft().setPixels(10);
            generator.getParameters().getBarcode().getPadding().getRight().setPixels(10);
            generator.getParameters().getBarcode().getPadding().getTop().setPixels(10);
            generator.getParameters().getBarcode().getPadding().getBottom().setPixels(10);
            
            // Save to file
            generator.save("code128_complete.png");
            
            System.out.println("Code 128 barcode generated successfully!");
            
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Common Use Cases

### Inventory Management
```java
BarcodeGenerator generator = new BarcodeGenerator(
    EncodeTypes.CODE_128, 
    "SKU-" + System.currentTimeMillis()
);
generator.save("inventory_barcode.png");
```

### Shipping Labels
```java
String trackingNumber = "1Z999AA10123456784";
BarcodeGenerator generator = new BarcodeGenerator(
    EncodeTypes.CODE_128, 
    trackingNumber
);
generator.getParameters().getBarcode().getBarHeight().setPixels(100);
generator.save("shipping_label.png");
```

### Serial Numbers
```java
BarcodeGenerator generator = new BarcodeGenerator(
    EncodeTypes.CODE_128, 
    "SN:" + "ABC123XYZ789"
);
generator.save("serial_number.png");
```

## Optimization Tips

### For Numeric Data
When encoding only numbers, Code 128 automatically uses Subset C for optimal density:

```java
// This will be encoded efficiently using Subset C
BarcodeGenerator generator = new BarcodeGenerator(
    EncodeTypes.CODE_128, 
    "123456789012"
);
```

### For Mixed Data
Mixed alphanumeric data uses the optimal combination of subsets:

```java
// Automatically switches between subsets for best encoding
BarcodeGenerator generator = new BarcodeGenerator(
    EncodeTypes.CODE_128, 
    "ABC123def456"
);
```

## Checksum

Code 128 always includes a mandatory checksum character that is automatically calculated. You don't need to add it manually.

## Best Practices

1. **Use appropriate X-dimension**: Typically 1-3 pixels for screen display, 2-4 pixels for printing
2. **Set adequate height**: Minimum height should be 15% of barcode width, or at least 0.25 inches
3. **Include quiet zones**: Add margins (at least 10x of X-dimension) on both sides
4. **Test readability**: Verify barcodes scan correctly with your target hardware
5. **Use high resolution**: Set at least 300 DPI for printed barcodes
6. **Keep data reasonable**: While Code 128 can encode long strings, shorter is generally better

## Error Handling

```java
try {
    BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128, 
        "YOUR-DATA"
    );
    generator.save("output.png");
} catch (Exception e) {
    System.err.println("Error generating barcode: " + e.getMessage());
    e.printStackTrace();
}
```

## Next Steps

- Learn about [GS1-128 in Detail](./gs1-128-guide.md)
- Explore [Code 128 Advanced Settings](./code128-advanced.md)
- Read about [1D Barcode Recognition](./1d-barcode-recognition.md)



