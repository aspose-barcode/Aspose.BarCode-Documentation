---
title: Quick Generation Examples
type: docs
weight: 10
url: /java/developer-guide/quick-start/quick-generation-examples
---

# Quick Generation Examples

This guide provides quick, ready-to-use examples for barcode generation with Aspose.BarCode for Java. All examples use consistent APIs and include proper error handling.

## Basic Setup

Import the required package:

```java
import com.aspose.barcode.generation.*;
```

## Simple Barcode Generation

### Code 128 Barcode

```java
public class Code128Example {
    public static void main(String[] args) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "ABC-12345");
            
            // Basic settings
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.3f);
            gen.getParameters().getBarcode().getBarHeight().setMillimeters(10.0f);
            
            gen.save("code128.png", BarCodeImageFormat.PNG);
            System.out.println("Code 128 barcode generated successfully!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

### QR Code Generation

```java
public class QRExample {
    public static void main(String[] args) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "https://www.aspose.com");
            
            // QR-specific settings
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.5f);
            gen.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.AUTO);
            gen.getParameters().getBarcode().getQR().setQrErrorLevel(QRErrorLevel.LEVEL_M);
            
            gen.save("qrcode.png", BarCodeImageFormat.PNG);
            System.out.println("QR Code generated successfully!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

## One-Minute Examples

### 1. Generate EAN-13 Barcode

```java
public class EAN13Example {
    public static void main(String[] args) {
        try {
            // Create EAN-13 barcode (requires 13 digits with valid checksum)
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN_13, "5901234123457");
            
            // Standard EAN-13 settings
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
            gen.getParameters().getBarcode().getBarHeight().setMillimeters(25.0f);
            
            gen.save("ean13.png", BarCodeImageFormat.PNG);
            System.out.println("EAN-13 barcode generated successfully!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

### 2. Generate PDF417 with Custom Settings

```java
public class PDF417Example {
    public static void main(String[] args) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                EncodeTypes.PDF_417, 
                "Aspose.BarCode makes barcode generation easy!"
            );
            
            // PDF417-specific parameters
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.6f);
            gen.getParameters().getBarcode().getPdf417().setColumns(3);
            gen.getParameters().getBarcode().getPdf417().setRows(6);
            
            // Code text below barcode
            gen.getParameters().getBarcode().getCodeTextParameters()
                .setLocation(CodeLocation.BELOW);
            gen.getParameters().getBarcode().getCodeTextParameters()
                .setFont(new FontUnit("Arial", 9));
            
            gen.save("pdf417.png", BarCodeImageFormat.PNG);
            System.out.println("PDF417 barcode generated successfully!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

### 3. Generate DataMatrix with Custom Encoding

```java
public class DataMatrixExample {
    public static void main(String[] args) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                EncodeTypes.DATA_MATRIX, 
                "DMX-INV-000042"
            );
            
            // DataMatrix settings
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.4f);
            gen.getParameters().getBarcode().getDataMatrix()
                .setDataMatrixEncodeMode(DataMatrixEncodeMode.AUTO);
            
            // Optional: enable anti-aliasing for better quality
            gen.getParameters().setUseAntiAlias(true);
            
            gen.save("datamatrix.png", BarCodeImageFormat.PNG);
            System.out.println("DataMatrix barcode generated successfully!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

## Common Barcode Types

### Linear Barcodes

```java
import com.aspose.barcode.generation.*;

public class LinearBarcodesExample {
    public static void main(String[] args) {
        try {
            generateLinearBarcodes();
            System.out.println("All linear barcodes generated successfully!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
    
    public static void generateLinearBarcodes() throws Exception {
        // UPC-A (12 digits)
        BarcodeGenerator upcGen = new BarcodeGenerator(EncodeTypes.UPCA, "036000291452");
        upcGen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
        upcGen.save("upca.png", BarCodeImageFormat.PNG);
        
        // EAN-13 (13 digits)
        BarcodeGenerator eanGen = new BarcodeGenerator(EncodeTypes.EAN_13, "5901234123457");
        eanGen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
        eanGen.save("ean13.png", BarCodeImageFormat.PNG);
        
        // Code 39
        BarcodeGenerator code39Gen = new BarcodeGenerator(EncodeTypes.CODE_39, "ASPOSE-123");
        code39Gen.getParameters().getBarcode().getXDimension().setMillimeters(0.4f);
        code39Gen.save("code39.png", BarCodeImageFormat.PNG);
        
        // Code 128
        BarcodeGenerator code128Gen = new BarcodeGenerator(EncodeTypes.CODE_128, "ABC-12345");
        code128Gen.getParameters().getBarcode().getXDimension().setMillimeters(0.3f);
        code128Gen.save("code128.png", BarCodeImageFormat.PNG);
    }
}
```

### 2D Barcodes

```java
import com.aspose.barcode.generation.*;

public class TwoDBarcodesExample {
    public static void main(String[] args) {
        try {
            generate2DBarcodes();
            System.out.println("All 2D barcodes generated successfully!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
    
    public static void generate2DBarcodes() throws Exception {
        // QR Code
        BarcodeGenerator qrGen = new BarcodeGenerator(EncodeTypes.QR, "QR Code Data");
        qrGen.getParameters().getBarcode().getXDimension().setMillimeters(0.5f);
        qrGen.save("qr_code.png", BarCodeImageFormat.PNG);
        
        // Aztec
        BarcodeGenerator aztecGen = new BarcodeGenerator(EncodeTypes.AZTEC, "Aztec Data");
        aztecGen.getParameters().getBarcode().getXDimension().setMillimeters(0.5f);
        aztecGen.save("aztec.png", BarCodeImageFormat.PNG);
        
        // DataMatrix
        BarcodeGenerator dmGen = new BarcodeGenerator(EncodeTypes.DATA_MATRIX, "DataMatrix");
        dmGen.getParameters().getBarcode().getXDimension().setMillimeters(0.4f);
        dmGen.save("datamatrix.png", BarCodeImageFormat.PNG);
        
        // PDF417
        BarcodeGenerator pdf417Gen = new BarcodeGenerator(EncodeTypes.PDF_417, "PDF417 Data");
        pdf417Gen.getParameters().getBarcode().getXDimension().setMillimeters(0.6f);
        pdf417Gen.save("pdf417.png", BarCodeImageFormat.PNG);
    }
}
```

## Customization Examples

### Custom Colors and Styling

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

public class CustomizationExample {
    public static void main(String[] args) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "CUSTOM-STYLE");
            
            // Custom colors
            gen.getParameters().setBackColor(Color.WHITE);
            gen.getParameters().getBarcode().setBarColor(Color.BLUE);
            
            // Dimensions
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.4f);
            gen.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);
            
            // Code text styling
            gen.getParameters().getBarcode().getCodeTextParameters()
                .setLocation(CodeLocation.BELOW);
            gen.getParameters().getBarcode().getCodeTextParameters()
                .setColor(Color.RED);
            gen.getParameters().getBarcode().getCodeTextParameters()
                .setFont(new FontUnit("Arial", 12, FontStyle.BOLD));
            
            // Add padding
            gen.getParameters().getBarcode().getPadding().getLeft().setMillimeters(3.0f);
            gen.getParameters().getBarcode().getPadding().getRight().setMillimeters(3.0f);
            gen.getParameters().getBarcode().getPadding().getTop().setMillimeters(2.0f);
            gen.getParameters().getBarcode().getPadding().getBottom().setMillimeters(2.0f);
            
            gen.save("custom_style.png", BarCodeImageFormat.PNG);
            System.out.println("Custom styled barcode generated!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

### Multiple Output Formats

```java
import com.aspose.barcode.generation.*;

public class OutputFormatsExample {
    public static void main(String[] args) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "MULTI-FORMAT");
            
            // Configure once
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.3f);
            gen.getParameters().getBarcode().getBarHeight().setMillimeters(12.0f);
            gen.getParameters().setResolution(300.0f);
            
            // Save in different formats
            gen.save("barcode.png", BarCodeImageFormat.PNG);   // Recommended
            gen.save("barcode.svg", BarCodeImageFormat.SVG);   // Vector (scalable)
            gen.save("barcode.bmp", BarCodeImageFormat.BMP);   // Uncompressed
            gen.save("barcode.gif", BarCodeImageFormat.GIF);   // Simple graphics
            gen.save("barcode.tiff", BarCodeImageFormat.TIFF); // Professional printing
            
            System.out.println("Barcodes saved in multiple formats!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

**Note**: Avoid JPEG format for barcodes as compression artifacts can make them unscannable.

## Performance: Batch Generation

```java
import com.aspose.barcode.generation.*;

public class BatchGenerationExample {
    public static void main(String[] args) {
        try {
            String[] codes = {"PROD001", "PROD002", "PROD003", "PROD004", "PROD005"};
            
            // Create generator once and reuse for better performance
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, codes[0]);
            
            // Set common parameters once
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.3f);
            gen.getParameters().getBarcode().getBarHeight().setMillimeters(10.0f);
            gen.getParameters().setResolution(300.0f);
            
            // Generate batch
            for (int i = 0; i < codes.length; i++) {
                gen.setCodeText(codes[i]);  // Only change the code text
                gen.save("batch_" + codes[i] + ".png", BarCodeImageFormat.PNG);
            }
            
            System.out.println("Batch generation completed: " + codes.length + " barcodes");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

**Performance Tip**: Reusing a `BarcodeGenerator` instance is significantly faster than creating a new one for each barcode.

## GS1 Barcodes

### GS1-128 with Application Identifiers

```java
import com.aspose.barcode.generation.*;

public class GS1Example {
    public static void main(String[] args) {
        try {
            // Use parentheses format - FNC1 is handled automatically
            String gs1Data = "(01)09501101530008" +  // GTIN
                             "(17)251231" +           // Expiration date
                             "(10)BATCH-42";          // Batch number
            
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.GS_1_CODE_128, gs1Data);
            
            // Standard GS1-128 settings
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
            gen.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);
            gen.getParameters().setResolution(300.0f);
            
            gen.save("gs1_128.png", BarCodeImageFormat.PNG);
            System.out.println("GS1-128 barcode generated successfully!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

### GS1 DataMatrix and QR

```java
import com.aspose.barcode.generation.*;

public class GS1_2D_Example {
    public static void main(String[] args) {
        try {
            String gs1Data = "(01)12345678901231(21)SERIAL123";
            
            // GS1 DataMatrix
            BarcodeGenerator dmGen = new BarcodeGenerator(
                EncodeTypes.GS_1_DATA_MATRIX, 
                gs1Data
            );
            dmGen.getParameters().getBarcode().getXDimension().setMillimeters(0.4f);
            dmGen.save("gs1_datamatrix.png", BarCodeImageFormat.PNG);
            
            // GS1 QR Code
            BarcodeGenerator qrGen = new BarcodeGenerator(
                EncodeTypes.GS_1_QR, 
                gs1Data
            );
            qrGen.getParameters().getBarcode().getXDimension().setMillimeters(0.5f);
            qrGen.save("gs1_qr.png", BarCodeImageFormat.PNG);
            
            System.out.println("GS1 2D barcodes generated!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

## Postal Barcodes

```java
import com.aspose.barcode.generation.*;

public class PostalBarcodesExample {
    public static void main(String[] args) {
        try {
            // USPS Postnet (ZIP or ZIP+4)
            BarcodeGenerator postnetGen = new BarcodeGenerator(
                EncodeTypes.POSTNET, 
                "205001234"  // 9 digits for ZIP+4
            );
            postnetGen.getParameters().getBarcode().getXDimension().setMillimeters(0.5f);
            postnetGen.save("postnet.png", BarCodeImageFormat.PNG);
            
            // USPS Planet
            BarcodeGenerator planetGen = new BarcodeGenerator(
                EncodeTypes.PLANET, 
                "205001234"
            );
            planetGen.getParameters().getBarcode().getXDimension().setMillimeters(0.5f);
            planetGen.save("planet.png", BarCodeImageFormat.PNG);
            
            // USPS Intelligent Mail (OneCode)
            // Format: 20 digits (tracking) + 11 digits (routing) = 31 digits
            String intelligentMail = "01234567094987654321" + "01234567891";
            BarcodeGenerator imbGen = new BarcodeGenerator(
                EncodeTypes.ONE_CODE, 
                intelligentMail
            );
            imbGen.getParameters().getBarcode().getXDimension().setMillimeters(0.5f);
            imbGen.save("intelligent_mail.png", BarCodeImageFormat.PNG);
            
            System.out.println("Postal barcodes generated!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

## Advanced Features

### Rotation

```java
import com.aspose.barcode.generation.*;

public class RotationExample {
    public static void main(String[] args) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "ROTATED");
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.3f);
            gen.getParameters().getBarcode().getBarHeight().setMillimeters(10.0f);
            
            // Generate at different angles
            float[] angles = {0, 90, 180, 270};
            for (float angle : angles) {
                gen.getParameters().setRotationAngle(angle);
                gen.save("rotated_" + (int)angle + ".png", BarCodeImageFormat.PNG);
            }
            
            System.out.println("Rotated barcodes generated!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

### Resolution and Size Control

```java
import com.aspose.barcode.generation.*;

public class ResolutionExample {
    public static void main(String[] args) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "HIGH-RES");
            
            // Set barcode dimensions
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.3f);
            gen.getParameters().getBarcode().getBarHeight().setMillimeters(12.0f);
            
            // Set high resolution for printing
            gen.getParameters().setResolution(300.0f);
            
            // Control image size
            gen.getParameters().getImageWidth().setPixels(500);
            gen.getParameters().getImageHeight().setPixels(200);
            gen.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);
            
            gen.save("high_resolution.png", BarCodeImageFormat.PNG);
            System.out.println("High resolution barcode generated!");
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        }
    }
}
```

## Complete Example: Product Label

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

public class ProductLabelExample {
    public static void main(String[] args) {
        try {
            // Product information
            String ean13Code = "5901234123457";
            String productName = "Premium Coffee Beans";
            
            // Create EAN-13 barcode
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN_13, ean13Code);
            
            // Professional label dimensions
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
            gen.getParameters().getBarcode().getBarHeight().setMillimeters(25.0f);
            
            // Print resolution
            gen.getParameters().setResolution(300.0f);
            
            // Code text styling
            gen.getParameters().getBarcode().getCodeTextParameters()
                .setLocation(CodeLocation.BELOW);
            gen.getParameters().getBarcode().getCodeTextParameters()
                .setFont(new FontUnit("Arial", 10));
            gen.getParameters().getBarcode().getCodeTextParameters()
                .setAlignment(TextAlignment.CENTER);
            
            // Quiet zones
            gen.getParameters().getBarcode().getPadding().getLeft().setMillimeters(3.3f);
            gen.getParameters().getBarcode().getPadding().getRight().setMillimeters(3.3f);
            gen.getParameters().getBarcode().getPadding().getTop().setMillimeters(2.0f);
            gen.getParameters().getBarcode().getPadding().getBottom().setMillimeters(2.0f);
            
            // Product name caption
            gen.getParameters().getCaptionAbove().setVisible(true);
            gen.getParameters().getCaptionAbove().setText(productName);
            gen.getParameters().getCaptionAbove().setFont(new FontUnit("Arial", 12, FontStyle.BOLD));
            gen.getParameters().getCaptionAbove().setAlignment(TextAlignment.CENTER);
            gen.getParameters().getCaptionAbove().getPadding().getBottom().set
            
            // Clean appearance
            gen.getParameters().setBackColor(Color.WHITE);
            gen.getParameters().getBarcode().setBarColor(Color.BLACK);
            
            // Auto-size
            gen.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);
            
            // Save
            gen.save("product_label.png", BarCodeImageFormat.PNG);
            
            System.out.println("Product label generated successfully!");
            System.out.println("Product: " + productName);
            System.out.println("EAN-13: " + ean13Code);
            
        } catch (Exception e) {
            System.err.println("Error generating product label: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

## Best Practices Summary

### 1. **Dimensions**
- **X-Dimension**: 0.30-0.50 mm for printing, 2-4 pixels for screen
- **Height**: Minimum 15% of barcode width or ≥ 12.7 mm
- Always use consistent units (millimeters for print, pixels for screen)

### 2. **Quiet Zones**
- Minimum 10× X-Dimension on left and right
- Essential for reliable scanning

### 3. **Resolution**
- 300 DPI for standard printing
- 600 DPI for high-quality printing
- 96-150 DPI for screen display

### 4. **Testing**
Always test with actual scanner hardware before production deployment.

### 5. **Performance**
- Reuse `BarcodeGenerator` instances for batch operations
- Set parameters once, update only the code text

### 6. **Formats**
- **PNG**: Best for most applications
- **SVG**: Vector graphics, scalable
- **TIFF**: Professional printing
- **Avoid JPEG**: Compression artifacts affect scannability

## Error Handling

```java
import com.aspose.barcode.generation.*;

public class ErrorHandlingExample {
    public static void main(String[] args) {
        try {
            // Attempt to generate barcode with potentially invalid data
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN_13, "invalid");
            gen.save("test.png", BarCodeImageFormat.PNG);
            
        } catch (BarCodeException ex) {
            // Handle barcode-specific errors
            System.err.println("Barcode Error: " + ex.getMessage());
            System.err.println("Check data format and encode type compatibility");
            
        } catch (Exception ex) {
            // Handle general errors
            System.err.println("General Error: " + ex.getMessage());
            ex.printStackTrace();
        }
    }
}
```

## Next Steps

- Learn about [specific barcode types](/java/developer-guide/barcode-generation/)
- Explore [advanced customization](/java/developer-guide/barcode-generation/customization/)
- Read about [GS1 barcodes](/java/developer-guide/barcode-generation/generate-gs-128/)
- Study [barcode recognition](/java/developer-guide/barcode-recognition/)