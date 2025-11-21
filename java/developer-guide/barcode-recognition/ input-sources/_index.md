---
title: Input Sources
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/input-sources
---
# Read Barcode from Image File

## Overview

Aspose.BarCode for Java provides powerful barcode recognition capabilities that can read barcodes from various image formats. 
This guide shows you how to quickly recognize barcodes from image files.

## Basic Barcode Recognition

Here's the simplest way to read a barcode from an image:

```java
import com.aspose.barcode.barcoderecognition.*;

public class BasicRecognitionExample {
    public static void main(String[] args) {
        // Create barcode reader instance
        BarCodeReader reader = new BarCodeReader("barcode.png");
        
        // Read all barcodes
        for (BarCodeResult result : reader.readBarCodes()) {
            System.out.println("Barcode Type: " + result.getCodeTypeName());
            System.out.println("Barcode Text: " + result.getCodeText());
        }
    }
}
```

## Specifying Barcode Types

For better performance, specify which barcode types to recognize:

```java
import com.aspose.barcode.barcoderecognition.*;

public class SpecificTypeRecognition {
    public static void main(String[] args) {
        // Read only QR codes
        BarCodeReader reader = new BarCodeReader(
            "image.png", 
            DecodeType.QR
        );
        
        for (BarCodeResult result : reader.readBarCodes()) {
            System.out.println("QR Code: " + result.getCodeText());
        }
    }
}
```

### Multiple Barcode Types

```java
// Read multiple specific types
BarCodeReader reader = new BarCodeReader(
    "image.png", 
    DecodeType.CODE_128, 
    DecodeType.QR, 
    DecodeType.DATA_MATRIX
);

for (BarCodeResult result : reader.readBarCodes()) {
    System.out.println(result.getCodeTypeName() + ": " + result.getCodeText());
}
```

### All 1D Barcodes

```java
// Read all 1D barcode types
BarCodeReader reader = new BarCodeReader(
    "image.png", 
    DecodeType.ALL_SUPPORTED_TYPES.Types1D
);
```

### All 2D Barcodes

```java
// Read all 2D barcode types
BarCodeReader reader = new BarCodeReader(
    "image.png", 
    DecodeType.ALL_SUPPORTED_TYPES.Types2D
);
```

## Reading from Different Sources

### From File Path

```java
BarCodeReader reader = new BarCodeReader("/path/to/barcode.png", DecodeType.CODE_128);
```

### From Stream

```java
import java.io.FileInputStream;

try (FileInputStream stream = new FileInputStream("barcode.png")) {
    BarCodeReader reader = new BarCodeReader(stream, DecodeType.QR);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println(result.getCodeText());
    }
} catch (Exception e) {
    e.printStackTrace();
}
```

### From Byte Array

```java
import java.nio.file.Files;
import java.nio.file.Paths;

byte[] imageBytes = Files.readAllBytes(Paths.get("barcode.png"));
BarCodeReader reader = new BarCodeReader(imageBytes, DecodeType.CODE_128);
```

## Accessing Barcode Details

The `BarCodeResult` object provides detailed information about recognized barcodes:

```java
BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.QR);

for (BarCodeResult result : reader.readBarCodes()) {
    // Basic information
    System.out.println("Type: " + result.getCodeTypeName());
    System.out.println("Text: " + result.getCodeText());
    
    // Barcode region coordinates
    System.out.println("Region: " + result.getRegion().toString());
    
    // Confidence level (0-100%)
    System.out.println("Confidence: " + result.getConfidence() + "%");
    
    // Barcode angle
    System.out.println("Angle: " + result.getRegion().getAngle() + " degrees");
    
    // Raw bytes
    byte[] bytes = result.getCodeBytes();
    System.out.println("Raw bytes length: " + bytes.length);
}
```

## Setting Recognition Region (ROI)

To improve performance, you can specify a region of interest:

```java
import com.aspose.barcode.barcoderecognition.*;
import java.awt.Rectangle;

BarCodeReader reader = new BarCodeReader("image.png", DecodeType.CODE_128);

// Set recognition area (x, y, width, height)
reader.setBarCodeImage(new Rectangle(100, 100, 400, 300));

for (BarCodeResult result : reader.readBarCodes()) {
    System.out.println(result.getCodeText());
}
```

## Complete Recognition Example

```java
import com.aspose.barcode.barcoderecognition.*;
import java.io.File;

public class CompleteRecognitionExample {
    public static void main(String[] args) {
        try {
            String imagePath = "barcode_image.png";
            
            // Check if file exists
            if (!new File(imagePath).exists()) {
                System.err.println("Image file not found!");
                return;
            }
            
            // Create reader for multiple barcode types
            BarCodeReader reader = new BarCodeReader(
                imagePath,
                DecodeType.CODE_128,
                DecodeType.QR,
                DecodeType.DATA_MATRIX,
                DecodeType.PDF_417
            );
            
            // Configure recognition quality
            reader.setQualitySettings(QualitySettings.getHighPerformance());
            
            // Read all barcodes
            BarCodeResult[] results = reader.readBarCodes();
            
            if (results.length == 0) {
                System.out.println("No barcodes found in the image.");
                return;
            }
            
            System.out.println("Found " + results.length + " barcode(s):");
            System.out.println("-----------------------------------");
            
            for (int i = 0; i < results.length; i++) {
                BarCodeResult result = results[i];
                
                System.out.println("\nBarcode #" + (i + 1));
                System.out.println("Type: " + result.getCodeTypeName());
                System.out.println("Text: " + result.getCodeText());
                System.out.println("Confidence: " + result.getConfidence() + "%");
                
                // Get coordinates
                java.awt.Point[] points = result.getRegion().getPoints();
                System.out.println("Position: (" + 
                    points[0].x + ", " + points[0].y + ")");
                
                // Rotation angle
                System.out.println("Angle: " + 
                    result.getRegion().getAngle() + "°");
            }
            
            System.out.println("\nRecognition completed successfully!");
            
        } catch (Exception e) {
            System.err.println("Error during recognition: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

## Performance Optimization

### High Performance Mode

For fast recognition when image quality is good:

```java
BarCodeReader reader = new BarCodeReader("image.png", DecodeType.CODE_128);
reader.setQualitySettings(QualitySettings.getHighPerformance());
```

### High Quality Mode

For difficult images or damaged barcodes:

```java
BarCodeReader reader = new BarCodeReader("image.png", DecodeType.QR);
reader.setQualitySettings(QualitySettings.getHighQuality());
```

### Maximum Barcodes

Set expected number of barcodes for optimization:

```java
BarCodeReader reader = new BarCodeReader("image.png", DecodeType.CODE_128);
reader.setQualitySettings(QualitySettings.getHighPerformance());

// Expect exactly 1 barcode
reader.getQualitySettings().setExpectSingleBarcode(true);
```

## Handling Multiple Barcodes

```java
BarCodeReader reader = new BarCodeReader("multiple_barcodes.png");

int barcodeCount = 0;
for (BarCodeResult result : reader.readBarCodes()) {
    barcodeCount++;
    System.out.println("Barcode " + barcodeCount + ": " + result.getCodeText());
}

System.out.println("Total barcodes found: " + barcodeCount);
```

## Supported Image Formats

Aspose.BarCode supports reading barcodes from:
- **Raster formats**: PNG, JPEG, BMP, GIF, TIFF, EXIF
- **Multi-page formats**: Multi-page TIFF
- **Other formats**: EMF, WMF

```java
// Example with different formats
BarCodeReader pngReader = new BarCodeReader("barcode.png", DecodeType.QR);
BarCodeReader jpgReader = new BarCodeReader("barcode.jpg", DecodeType.CODE_128);
BarCodeReader tiffReader = new BarCodeReader("barcode.tiff", DecodeType.DATA_MATRIX);
```

## Error Handling

Always handle potential exceptions:

```java
try {
    BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.CODE_128);
    BarCodeResult[] results = reader.readBarCodes();
    
    if (results.length == 0) {
        System.out.println("No barcodes detected");
    } else {
        for (BarCodeResult result : results) {
            System.out.println(result.getCodeText());
        }
    }
    
} catch (java.io.FileNotFoundException e) {
    System.err.println("Image file not found: " + e.getMessage());
} catch (Exception e) {
    System.err.println("Recognition error: " + e.getMessage());
    e.printStackTrace();
}
```

## Best Practices

1. **Specify barcode types**: Always specify expected types for better performance
2. **Use appropriate quality settings**: Balance speed vs accuracy based on your needs
3. **Handle no results**: Always check if any barcodes were found
4. **Set recognition region**: Use ROI when you know where barcodes are located
5. **Check confidence levels**: Validate results with low confidence scores
6. **Optimize image quality**: Use high-resolution, clear images for best results

## Next Steps

- Learn about [Advanced Recognition Settings](./advanced-recognition-settings.md)
- Explore [Image Preprocessing](./image-preprocessing.md)
- Read about [Recognition Quality Optimization](./recognition-quality.md)
- See [Multi-Page TIFF Recognition](./multipage-tiff-recognition.md)



