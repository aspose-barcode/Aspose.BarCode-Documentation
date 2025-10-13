---
title: Quick Generation Examples
type: docs
weight: 10
url: /java/developer-guide/quick-start/quick-generation-examples
---

# Quick Generation Examples

This guide provides quick examples to get you started with barcode generation using Aspose.BarCode for Java. These examples cover the most common scenarios and barcode types.

## Basic Setup

First, ensure you have Aspose.BarCode for Java in your project:

```java
import com.aspose.barcode.generation.*;
```

## Simple Barcode Generation

### Code 128 Barcode

```java
// Create a BarcodeGenerator instance
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "Aspose.BarCode");

// Save the barcode image
generator.save("code128.png", BarCodeImageFormat.PNG);
```

### QR Code Generation

```java
// Generate QR Code
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "https://www.aspose.com");

// Set QR Code parameters
generator.getParameters().getBarcode().getXDimension().setPixels(4);
generator.getParameters().getBarcode().getQR().setErrorLevel(QRErrorLevel.LEVEL_M);

// Save as PNG
generator.save("qrcode.png", BarCodeImageFormat.PNG);
```

## One-Minute Examples

### 1. Generate EAN-13 Barcode

```java
public class EAN13Example {
    public static void main(String[] args) {
        // Create EAN-13 barcode
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.EAN_13, "1234567890128");
        
        // Customize appearance
        generator.getParameters().getBarcode().getXDimension().setPixels(2);
        generator.getParameters().getBarcode().getBarHeight().setPixels(50);
        
        // Save the barcode
        generator.save("ean13.png", BarCodeImageFormat.PNG);
        
        System.out.println("EAN-13 barcode generated successfully!");
    }
}
```

### 2. Generate PDF417 with Custom Text

```java
public class PDF417Example {
    public static void main(String[] args) {
        // Create PDF417 barcode
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.PDF_417, 
            "Aspose.BarCode for Java makes barcode generation easy!");
        
        // Set PDF417 specific parameters
        generator.getParameters().getBarcode().getPdf417().setRows(6);
        generator.getParameters().getBarcode().getPdf417().setColumns(5);
        
        // Customize code text
        generator.getParameters().getBarcode().getCodeTextParameters().setLocation(CodeLocation.BELOW);
        generator.getParameters().getBarcode().getCodeTextParameters().getFont().setSize(12f);
        
        // Save the barcode
        generator.save("pdf417.png", BarCodeImageFormat.PNG);
        
        System.out.println("PDF417 barcode generated successfully!");
    }
}
```

### 3. Generate DataMatrix with Binary Data

```java
public class DataMatrixExample {
    public static void main(String[] args) {
        try {
            // Create DataMatrix with binary data
            String data = "Sample binary data \u0000\u0001\u0002";
            BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.DATA_MATRIX, data);
            
            // Set DataMatrix parameters
            generator.getParameters().getBarcode().getDataMatrix().setEncodeMode(DataMatrixEncodeMode.BINARY);
            generator.getParameters().getBarcode().getXDimension().setPixels(4);
            
            // Save the barcode
            generator.save("datamatrix.png", BarCodeImageFormat.PNG);
            
            System.out.println("DataMatrix barcode generated successfully!");
        } catch (Exception ex) {
            System.out.println("Error: " + ex.getMessage());
        }
    }
}
```

## Common Barcode Types

### Linear Barcodes

```java
public class LinearBarcodesExample {
    public static void generateLinearBarcodes() {
        String[] barcodeData = {
            "123456789012",  // For UPC-A
            "1234567890128", // For EAN-13
            "12345678",      // For EAN-8
            "CODE39",        // For Code 39
            "CODE93"         // For Code 93
        };
        
        BaseEncodeType[] barcodeTypes = {
            EncodeTypes.UPC_A,
            EncodeTypes.EAN_13,
            EncodeTypes.EAN_8,
            EncodeTypes.CODE_39_STANDARD,
            EncodeTypes.CODE_93_STANDARD
        };
        
        String[] fileNames = {
            "upc_a.png",
            "ean_13.png", 
            "ean_8.png",
            "code39.png",
            "code93.png"
        };
        
        for (int i = 0; i < barcodeTypes.length; i++) {
            BarcodeGenerator generator = new BarcodeGenerator(barcodeTypes[i], barcodeData[i]);
            generator.getParameters().getBarcode().getXDimension().setPixels(2);
            generator.save(fileNames[i], BarCodeImageFormat.PNG);
        }
        
        System.out.println("Linear barcodes generated successfully!");
    }
}
```

### 2D Barcodes

```java
public class TwoDBarcodesExample {
    public static void generate2DBarcodes() {
        // QR Code
        BarcodeGenerator qrGenerator = new BarcodeGenerator(EncodeTypes.QR, "QR Code Text");
        qrGenerator.save("qr_code.png", BarCodeImageFormat.PNG);
        
        // Aztec
        BarcodeGenerator aztecGenerator = new BarcodeGenerator(EncodeTypes.AZTEC, "Aztec Text");
        aztecGenerator.save("aztec.png", BarCodeImageFormat.PNG);
        
        // DataMatrix
        BarcodeGenerator dmGenerator = new BarcodeGenerator(EncodeTypes.DATA_MATRIX, "DataMatrix");
        dmGenerator.save("datamatrix.png", BarCodeImageFormat.PNG);
        
        System.out.println("2D barcodes generated successfully!");
    }
}
```

## Customization Examples

### Custom Colors and Fonts

```java
public class CustomizationExample {
    public static void main(String[] args) {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "Custom Style");
        
        // Set custom colors
        generator.getParameters().getBarcode().setBarColor(Color.BLUE);
        generator.getParameters().setBackColor(Color.YELLOW);
        
        // Customize code text
        CodetextParameters codetext = generator.getParameters().getBarcode().getCodeTextParameters();
        codetext.setColor(Color.RED);
        codetext.getFont().setSize(14f);
        codetext.getFont().setStyle(FontStyle.BOLD);
        
        // Set dimensions
        generator.getParameters().getBarcode().getXDimension().setPixels(3);
        generator.getParameters().getBarcode().getBarHeight().setPixels(80);
        
        // Add margins
        generator.getParameters().getBarcode().getPadding().getLeft().setPixels(10);
        generator.getParameters().getBarcode().getPadding().getRight().setPixels(10);
        
        generator.save("custom_style.png", BarCodeImageFormat.PNG);
        
        System.out.println("Custom styled barcode generated!");
    }
}
```

### Different Output Formats

```java
public class OutputFormatsExample {
    public static void main(String[] args) {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "Multiple Formats");
        
        // Save in different formats
        generator.save("barcode.png", BarCodeImageFormat.PNG);
        generator.save("barcode.jpg", BarCodeImageFormat.JPEG);
        generator.save("barcode.gif", BarCodeImageFormat.GIF);
        generator.save("barcode.bmp", BarCodeImageFormat.BMP);
        generator.save("barcode.svg", BarCodeImageFormat.SVG);
        
        System.out.println("Barcodes saved in multiple formats!");
    }
}
```

## Performance Tips

### Batch Generation

```java
public class BatchGenerationExample {
    public static void generateBatch() {
        String[] codes = {"CODE001", "CODE002", "CODE003", "CODE004", "CODE005"};
        
        // Reuse generator instance for better performance
        BarcodeGenerator generator = new BarcodeGenerator();
        generator.setEncodeType(EncodeTypes.CODE_128);
        
        // Set common parameters once
        generator.getParameters().getBarcode().getXDimension().setPixels(2);
        generator.getParameters().getBarcode().getBarHeight().setPixels(50);
        
        for (int i = 0; i < codes.length; i++) {
            // Only change the code text
            generator.setCodeText(codes[i]);
            generator.save("batch_" + (i + 1) + ".png", BarCodeImageFormat.PNG);
        }
        
        System.out.println("Batch generation completed!");
    }
}
```

## Error Handling

```java
public class ErrorHandlingExample {
    public static void main(String[] args) {
        try {
            BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.EAN_13, "invalid_data");
            generator.save("error_test.png", BarCodeImageFormat.PNG);
        } catch (BarCodeException ex) {
            System.err.println("BarCode Error: " + ex.getMessage());
        } catch (Exception ex) {
            System.err.println("General Error: " + ex.getMessage());
        }
    }
}
```

## Complete Example: Product Label Generator

```java
public class ProductLabelGenerator {
    public static void main(String[] args) {
        try {
            // Product information
            String productCode = "1234567890128";
            String productName = "Sample Product";
            
            // Create EAN-13 barcode for product
            BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.EAN_13, productCode);
            
            // Customize appearance for product label
            generator.getParameters().getBarcode().getXDimension().setPixels(2);
            generator.getParameters().getBarcode().getBarHeight().setPixels(60);
            
            // Set code text parameters
            CodetextParameters codetext = generator.getParameters().getBarcode().getCodeTextParameters();
            codetext.setLocation(CodeLocation.BELOW);
            codetext.getFont().setSize(12f);
            codetext.setColor(Color.BLACK);
            
            // Add padding for label
            Padding padding = generator.getParameters().getBarcode().getPadding();
            padding.getLeft().setPixels(10);
            padding.getRight().setPixels(10);
            padding.getTop().setPixels(10);
            padding.getBottom().setPixels(10);
            
            // Set resolution for printing
            generator.getParameters().setResolution(300f);
            
            // Save the product label
            generator.save("product_label.png", BarCodeImageFormat.PNG);
            
            System.out.println("Product label generated successfully!");
            System.out.println("Product: " + productName);
            System.out.println("Code: " + productCode);
            
        } catch (Exception ex) {
            System.err.println("Error generating product label: " + ex.getMessage());
            ex.printStackTrace();
        }
    }
}
```

## Working with Different Symbologies

### Postal Barcodes

```java
public class PostalBarcodesExample {
    public static void main(String[] args) {
        // Australia Post
        BarcodeGenerator ausPostGen = new BarcodeGenerator(
            EncodeTypes.AUSTRALIA_POST, 
            "1234567890"
        );
        ausPostGen.save("australia_post.png", BarCodeImageFormat.PNG);
        
        // Deutsche Post Identcode
        BarcodeGenerator deutscheGen = new BarcodeGenerator(
            EncodeTypes.DEUTSCHE_POST_IDENTCODE, 
            "12345678901"
        );
        deutscheGen.save("deutsche_post.png", BarCodeImageFormat.PNG);
        
        // Royal Mail
        BarcodeGenerator royalGen = new BarcodeGenerator(
            EncodeTypes.RM4SCC, 
            "RM4SCC"
        );
        royalGen.save("royal_mail.png", BarCodeImageFormat.PNG);
        
        System.out.println("Postal barcodes generated!");
    }
}
```

### GS1 Barcodes

```java
public class GS1BarcodesExample {
    public static void main(String[] args) {
        // GS1 Code 128
        BarcodeGenerator gs1Gen = new BarcodeGenerator(
            EncodeTypes.GS_1_CODE_128, 
            "(01)12345678901231(21)SERIAL123"
        );
        gs1Gen.save("gs1_code128.png", BarCodeImageFormat.PNG);
        
        // GS1 DataMatrix
        BarcodeGenerator gs1DmGen = new BarcodeGenerator(
            EncodeTypes.GS_1_DATA_MATRIX, 
            "(01)12345678901231"
        );
        gs1DmGen.save("gs1_datamatrix.png", BarCodeImageFormat.PNG);
        
        // GS1 QR Code
        BarcodeGenerator gs1QrGen = new BarcodeGenerator(
            EncodeTypes.GS_1_QR, 
            "(01)12345678901231(10)ABC123"
        );
        gs1QrGen.save("gs1_qr.png", BarCodeImageFormat.PNG);
        
        System.out.println("GS1 barcodes generated!");
    }
}
```

## Advanced Customization

### Rotation and Orientation

```java
public class RotationExample {
    public static void main(String[] args) {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "Rotated");
        
        // Rotate 90 degrees
        generator.getParameters().setRotationAngle(90);
        generator.save("rotated_90.png", BarCodeImageFormat.PNG);
        
        // Rotate 180 degrees
        generator.getParameters().setRotationAngle(180);
        generator.save("rotated_180.png", BarCodeImageFormat.PNG);
        
        // Rotate 270 degrees
        generator.getParameters().setRotationAngle(270);
        generator.save("rotated_270.png", BarCodeImageFormat.PNG);
        
        System.out.println("Rotated barcodes generated!");
    }
}
```

### Resolution and Size Control

```java
public class ResolutionExample {
    public static void main(String[] args) {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "High Resolution");
        
        // Set high resolution for printing
        generator.getParameters().setResolution(300f);
        
        // Set specific image size
        generator.getParameters().getImageWidth().setPixels(400);
        generator.getParameters().getImageHeight().setPixels(200);
        
        // Auto-size mode
        generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);
        
        generator.save("high_resolution.png", BarCodeImageFormat.PNG);
        
        System.out.println("High resolution barcode generated!");
    }
}
```