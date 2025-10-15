---
title: Quick Recognition Examples
type: docs
weight: 20
url: /java/developer-guide/quick-start/quick-recognition-examples
---

# Quick Recognition Examples

This guide provides quick, ready-to-use examples for barcode recognition with Aspose.BarCode for Java. All examples use consistent APIs and include proper error handling.

## Basic Setup

Import the required packages:

```java
import com.aspose.barcode.barcoderecognition.*;
```

## Simple Barcode Recognition

### Recognize Single Barcode Type

```java
public void recognizeSingleType() throws Exception {
    // Recognize only Code 128 barcodes
    BarCodeReader reader = new BarCodeReader("code128.png", DecodeType.CODE_128);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("CodeType: " + result.getCodeTypeName());
        System.out.println("CodeText: " + result.getCodeText());
    }
}
```

### Recognize Multiple Barcode Types

```java
public void recognizeMultipleTypes() throws Exception {
    // Recognize Code 128 and QR codes
    BarCodeReader reader = new BarCodeReader(
        "mixed_barcodes.png",
        DecodeType.CODE_128,
        DecodeType.QR
    );
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Found: " + result.getCodeTypeName());
        System.out.println("Text: " + result.getCodeText());
    }
}
```

### Recognize All Supported Types

```java
public void recognizeAllTypes() throws Exception {
    // Recognize all barcode types
    BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.ALL_SUPPORTED_TYPES);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Type: " + result.getCodeTypeName());
        System.out.println("Data: " + result.getCodeText());
        System.out.println("Confidence: " + result.getConfidence());
    }
}
```

## Recognition with Quality Settings

### Fast Recognition

```java
public void fastRecognition() throws Exception {
    BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.CODE_128);
    
    // Fast recognition mode
    reader.setQualitySettings(QualitySettings.getHighPerformance());
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Code: " + result.getCodeText());
    }
}
```

### High Quality Recognition

```java
public void highQualityRecognition() throws Exception {
    BarCodeReader reader = new BarCodeReader("difficult_barcode.png", DecodeType.CODE_128);
    
    // High quality mode for difficult barcodes
    reader.setQualitySettings(QualitySettings.getHighQuality());
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Recognized: " + result.getCodeText());
    }
}
```

### Maximum Quality Recognition

```java
public void maxQualityRecognition() throws Exception {
    BarCodeReader reader = new BarCodeReader("poor_quality.png", DecodeType.ALL_SUPPORTED_TYPES);
    
    // Maximum quality for very difficult images
    reader.setQualitySettings(QualitySettings.getMaxQuality());
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Type: " + result.getCodeTypeName());
        System.out.println("Text: " + result.getCodeText());
    }
}
```

## Barcode-Specific Settings

### 1D Barcode Settings

#### Code 128 - Checksum Validation

```java
public void code128WithChecksum() throws Exception {
    BarCodeReader reader = new BarCodeReader("code128.png", DecodeType.CODE_128);
    
    // Enable checksum validation
    reader.getBarcodeSettings().setChecksumValidation(ChecksumValidation.ON);
    reader.getBarcodeSettings().setStripFNC(true); // Strip FNC characters
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Code 128: " + result.getCodeText());
    }
}
```

#### Code 39 - Extended Mode

```java
public void code39Extended() throws Exception {
    BarCodeReader reader = new BarCodeReader("code39.png", DecodeType.CODE_39_EXTENDED);
    
    // Recognize extended Code 39 (with lowercase and special characters)
    reader.getBarcodeSettings().setChecksumValidation(ChecksumValidation.ON);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Code 39 Extended: " + result.getCodeText());
    }
}
```

#### Code 93 - Extended Mode

```java
public void code93Extended() throws Exception {
    BarCodeReader reader = new BarCodeReader("code93.png", DecodeType.CODE_93_EXTENDED);
    
    // Recognize extended Code 93
    reader.getBarcodeSettings().setChecksumValidation(ChecksumValidation.ON);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Code 93 Extended: " + result.getCodeText());
    }
}
```

#### ITF - Start/Stop Pattern

```java
public void itfWithStartStop() throws Exception {
    BarCodeReader reader = new BarCodeReader("itf14.png", DecodeType.ITF_14);
    
    // ITF-14 specific settings
    reader.getBarcodeSettings().setStripFNC(false);
    reader.getBarcodeSettings().setDetectEncoding(true);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("ITF-14: " + result.getCodeText());
    }
}
```

### 2D Barcode Settings

#### QR Code - Encoding Detection

```java
public void qrWithEncoding() throws Exception {
    BarCodeReader reader = new BarCodeReader("qrcode.png", DecodeType.QR);
    
    // Enable automatic encoding detection
    reader.getBarcodeSettings().setDetectEncoding(true);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("QR Code: " + result.getCodeText());
        System.out.println("Encoding: " + result.getCodeType());
    }
}
```

#### QR Code - Unicode Data

```java
public void qrUnicode() throws Exception {
    BarCodeReader reader = new BarCodeReader("qr_unicode.png", DecodeType.QR);
    
    // Detect encoding for Unicode data
    reader.getBarcodeSettings().setDetectEncoding(true);
    reader.setQualitySettings(QualitySettings.getHighQuality());
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("QR Unicode: " + result.getCodeText());
    }
}
```

#### DataMatrix - Encoding Modes

```java
public void dataMatrixEncoding() throws Exception {
    BarCodeReader reader = new BarCodeReader("datamatrix.png", DecodeType.DATA_MATRIX);
    
    // Enable encoding detection for DataMatrix
    reader.getBarcodeSettings().setDetectEncoding(true);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("DataMatrix: " + result.getCodeText());
    }
}
```

#### PDF417 - Macro Characters

```java
public void pdf417Macro() throws Exception {
    BarCodeReader reader = new BarCodeReader("pdf417.png", DecodeType.PDF_417);
    
    // Enable detection of PDF417 macro characters
    reader.getBarcodeSettings().setDetectEncoding(true);
    reader.getBarcodeSettings().setStripFNC(false);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("PDF417: " + result.getCodeText());
        
        // Check for macro mode
        if (result.getExtended() != null && result.getExtended().getPDF417() != null) {
            System.out.println("Macro File ID: " + result.getExtended().getPDF417().getMacroPdf417FileID());
            System.out.println("Macro Segment ID: " + result.getExtended().getPDF417().getMacroPdf417SegmentID());
        }
    }
}
```

#### Aztec - Structured Append

```java
public void aztecStructuredAppend() throws Exception {
    BarCodeReader reader = new BarCodeReader("aztec.png", DecodeType.AZTEC);
    
    // Read Aztec with structured append support
    reader.setQualitySettings(QualitySettings.getHighQuality());
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Aztec: " + result.getCodeText());
    }
}
```

### GS1 Barcode Specific Settings

#### GS1-128 - AI Parsing

```java
public void gs1_128WithAIParsing() throws Exception {
    BarCodeReader reader = new BarCodeReader("gs1_128.png", DecodeType.GS_1_CODE_128);
    
    // Enable FNC character stripping for clean AI parsing
    reader.getBarcodeSettings().setStripFNC(true);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        String codeText = result.getCodeText();
        System.out.println("GS1-128: " + codeText);
        
        // Parse AIs
        if (codeText.contains("(01)")) {
            int gtinStart = codeText.indexOf("(01)") + 4;
            int gtinEnd = codeText.indexOf("(", gtinStart);
            if (gtinEnd == -1) gtinEnd = codeText.length();
            String gtin = codeText.substring(gtinStart, gtinEnd);
            System.out.println("GTIN: " + gtin);
        }
        
        if (codeText.contains("(10)")) {
            int lotStart = codeText.indexOf("(10)") + 4;
            int lotEnd = codeText.indexOf("(", lotStart);
            if (lotEnd == -1) lotEnd = codeText.length();
            String lot = codeText.substring(lotStart, lotEnd);
            System.out.println("Lot: " + lot);
        }
    }
}
```

#### GS1 DataMatrix - FNC1 Handling

```java
public void gs1DataMatrixFNC1() throws Exception {
    BarCodeReader reader = new BarCodeReader("gs1_datamatrix.png", DecodeType.GS_1_DATA_MATRIX);
    
    // GS1 DataMatrix settings
    reader.getBarcodeSettings().setStripFNC(true);
    reader.getBarcodeSettings().setDetectEncoding(true);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("GS1 DataMatrix: " + result.getCodeText());
    }
}
```

### Postal Barcode Settings

#### Postnet/Planet - Checksum

```java
public void postnetWithChecksum() throws Exception {
    BarCodeReader reader = new BarCodeReader("postnet.png", DecodeType.POSTNET);
    
    // Enable checksum validation for postal barcodes
    reader.getBarcodeSettings().setChecksumValidation(ChecksumValidation.ON);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Postnet: " + result.getCodeText());
    }
}
```

#### Australian Post - Encoding Table

```java
public void australianPost() throws Exception {
    BarCodeReader reader = new BarCodeReader("australian_post.png", DecodeType.AUSTRALIA_POST);
    
    // Australian Post specific settings
    reader.getBarcodeSettings().setAustralianPostEncodingTable(
        CustomerInformationInterpretingType.C_TABLE
    );
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Australian Post: " + result.getCodeText());
        
        // Get extended info
        if (result.getExtended() != null && result.getExtended().getAustralianPost() != null) {
            System.out.println("Encoding Table: " + 
                result.getExtended().getAustralianPost().getAustralianPostEncodingTable());
        }
    }
}
```

### Special Recognition Scenarios

#### Inverted Barcodes (White on Black)

```java
public void recognizeInvertedBarcode() throws Exception {
    BarCodeReader reader = new BarCodeReader("inverted_barcode.png", DecodeType.CODE_128);
    
    // Enable inverted image detection
    QualitySettings settings = QualitySettings.getHighQuality();
    settings.setAllowInvertImage(true);
    reader.setQualitySettings(settings);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Inverted barcode: " + result.getCodeText());
    }
}
```

#### Low Contrast Barcodes

```java
public void recognizeLowContrast() throws Exception {
    BarCodeReader reader = new BarCodeReader("low_contrast.png", DecodeType.CODE_128);
    
    // Settings for low contrast images
    QualitySettings settings = QualitySettings.getMaxQuality();
    settings.setAllowComplexBackground(true);
    settings.setAllowMedianSmoothing(true);
    settings.setAllowRegularWiping(true);
    settings.setAllowWhiteSpotsRemoving(true);
    
    reader.setQualitySettings(settings);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Low contrast: " + result.getCodeText());
    }
}
```

#### Damaged or Dirty Barcodes

```java
public void recognizeDamagedBarcode() throws Exception {
    BarCodeReader reader = new BarCodeReader("damaged_barcode.png", DecodeType.CODE_128);
    
    // Maximum quality with all filters enabled
    QualitySettings settings = QualitySettings.getMaxQuality();
    settings.setAllowSaltAndPaperFiltering(true);
    settings.setAllowWhiteSpotsRemoving(true);
    settings.setAllowMedianSmoothing(true);
    settings.setAllowDecreasedImage(true);
    
    reader.setQualitySettings(settings);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Damaged barcode: " + result.getCodeText());
        System.out.println("Confidence: " + result.getConfidence() + "%");
    }
}
```

#### Rotated Barcodes

```java
public void recognizeRotatedBarcode() throws Exception {
    BarCodeReader reader = new BarCodeReader("rotated_barcode.png", DecodeType.CODE_128);
    
    // Enable detection of rotated barcodes
    QualitySettings settings = QualitySettings.getHighQuality();
    settings.setAllowQRMicroQrRestoration(true);
    
    reader.setQualitySettings(settings);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Rotated barcode: " + result.getCodeText());
        
        // Get rotation angle
        Rectangle rect = result.getRegion().getRectangle();
        System.out.println("Region: " + rect);
    }
}
```

#### Small or Dense Barcodes

```java
public void recognizeSmallBarcode() throws Exception {
    BarCodeReader reader = new BarCodeReader("small_barcode.png", DecodeType.CODE_128);
    
    // Settings for small or dense barcodes
    QualitySettings settings = QualitySettings.getHighQuality();
    settings.setAllowDecreasedImage(false); // Don't decrease small images
    settings.setAllowOneDFastBarcodesDetector(true);
    
    reader.setQualitySettings(settings);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Small barcode: " + result.getCodeText());
    }
}
```

### Multiple Barcode Types in One Image

#### Mixed 1D and 2D Barcodes

```java
public void recognizeMixed1DAnd2D() throws Exception {
    BarCodeReader reader = new BarCodeReader(
        "mixed_barcodes.png",
        DecodeType.CODE_128,
        DecodeType.QR,
        DecodeType.DATA_MATRIX,
        DecodeType.EAN_13
    );
    
    // Optimize for mixed barcode types
    reader.setQualitySettings(QualitySettings.getHighQuality());
    
    BarCodeResult[] results = reader.readBarCodes();
    System.out.println("Found " + results.length + " barcodes");
    
    for (BarCodeResult result : results) {
        System.out.println(result.getCodeTypeName() + ": " + result.getCodeText());
        
        Rectangle rect = result.getRegion().getRectangle();
        System.out.println("  Position: (" + rect.x + ", " + rect.y + ")");
    }
}
```

#### Separate 1D and 2D Recognition

```java
public void recognizeSeparate1DAnd2D() throws Exception {
    String imagePath = "mixed_barcodes.png";
    
    // First pass: recognize 1D barcodes (faster)
    BarCodeReader reader1D = new BarCodeReader(
        imagePath,
        DecodeType.CODE_128,
        DecodeType.CODE_39,
        DecodeType.EAN_13
    );
    reader1D.setQualitySettings(QualitySettings.getHighPerformance());
    
    System.out.println("1D Barcodes:");
    for (BarCodeResult result : reader1D.readBarCodes()) {
        System.out.println("  " + result.getCodeTypeName() + ": " + result.getCodeText());
    }
    
    // Second pass: recognize 2D barcodes
    BarCodeReader reader2D = new BarCodeReader(
        imagePath,
        DecodeType.QR,
        DecodeType.DATA_MATRIX,
        DecodeType.PDF_417
    );
    reader2D.setQualitySettings(QualitySettings.getHighQuality());
    
    System.out.println("2D Barcodes:");
    for (BarCodeResult result : reader2D.readBarCodes()) {
        System.out.println("  " + result.getCodeTypeName() + ": " + result.getCodeText());
    }
}
```

## Linear Barcode Recognition

### Recognize EAN-13

```java
public void recognizeEAN13() throws Exception {
    BarCodeReader reader = new BarCodeReader("ean13.png", DecodeType.EAN_13);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("EAN-13: " + result.getCodeText());
    }
}
```

### Recognize UPC-A

```java
public void recognizeUPCA() throws Exception {
    BarCodeReader reader = new BarCodeReader("upca.png", DecodeType.UPCA);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("UPC-A: " + result.getCodeText());
    }
}
```

### Recognize Code 39

```java
public void recognizeCode39() throws Exception {
    BarCodeReader reader = new BarCodeReader("code39.png", DecodeType.CODE_39);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Code 39: " + result.getCodeText());
    }
}
```

### Recognize Code 128

```java
public void recognizeCode128() throws Exception {
    BarCodeReader reader = new BarCodeReader("code128.png", DecodeType.CODE_128);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Code 128: " + result.getCodeText());
    }
}
```

### Recognize ITF-14

```java
public void recognizeITF14() throws Exception {
    BarCodeReader reader = new BarCodeReader("itf14.png", DecodeType.ITF_14);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("ITF-14: " + result.getCodeText());
    }
}
```

## 2D Barcode Recognition

### Recognize QR Code

```java
public void recognizeQR() throws Exception {
    BarCodeReader reader = new BarCodeReader("qrcode.png", DecodeType.QR);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("QR Code: " + result.getCodeText());
    }
}
```

### Recognize DataMatrix

```java
public void recognizeDataMatrix() throws Exception {
    BarCodeReader reader = new BarCodeReader("datamatrix.png", DecodeType.DATA_MATRIX);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("DataMatrix: " + result.getCodeText());
    }
}
```

### Recognize PDF417

```java
public void recognizePDF417() throws Exception {
    BarCodeReader reader = new BarCodeReader("pdf417.png", DecodeType.PDF_417);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("PDF417: " + result.getCodeText());
    }
}
```

### Recognize Aztec

```java
public void recognizeAztec() throws Exception {
    BarCodeReader reader = new BarCodeReader("aztec.png", DecodeType.AZTEC);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Aztec: " + result.getCodeText());
    }
}
```

## Postal Barcode Recognition

### Recognize Postnet

```java
public void recognizePostnet() throws Exception {
    BarCodeReader reader = new BarCodeReader("postnet.png", DecodeType.POSTNET);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Postnet: " + result.getCodeText());
    }
}
```

### Recognize Planet

```java
public void recognizePlanet() throws Exception {
    BarCodeReader reader = new BarCodeReader("planet.png", DecodeType.PLANET);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Planet: " + result.getCodeText());
    }
}
```

### Recognize Intelligent Mail

```java
public void recognizeIntelligentMail() throws Exception {
    BarCodeReader reader = new BarCodeReader("intelligent_mail.png", DecodeType.ONE_CODE);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Intelligent Mail: " + result.getCodeText());
    }
}
```

## GS1 Barcode Recognition

### Recognize GS1-128

```java
public void recognizeGS1_128() throws Exception {
    BarCodeReader reader = new BarCodeReader("gs1_128.png", DecodeType.GS_1_CODE_128);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("GS1-128: " + result.getCodeText());
        
        // Parse GS1 data if needed
        String codeText = result.getCodeText();
        if (codeText.contains("(01)")) {
            System.out.println("Contains GTIN");
        }
    }
}
```

### Recognize GS1 DataMatrix

```java
public void recognizeGS1_DataMatrix() throws Exception {
    BarCodeReader reader = new BarCodeReader("gs1_datamatrix.png", DecodeType.GS_1_DATA_MATRIX);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("GS1 DataMatrix: " + result.getCodeText());
    }
}
```

### Recognize GS1 QR Code

```java
public void recognizeGS1_QR() throws Exception {
    BarCodeReader reader = new BarCodeReader("gs1_qr.png", DecodeType.GS_1_QR);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("GS1 QR: " + result.getCodeText());
    }
}
```

## Advanced Recognition Features

### Get Barcode Region Information

```java
public void getBarcodeRegion() throws Exception {
    BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.CODE_128);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Code: " + result.getCodeText());
        
        // Get barcode region
        Point[] points = result.getRegion().getPoints();
        System.out.println("Barcode found at:");
        for (int i = 0; i < points.length; i++) {
            System.out.println("  Point " + i + ": (" + points[i].x + ", " + points[i].y + ")");
        }
        
        // Get bounding rectangle
        Rectangle rect = result.getRegion().getRectangle();
        System.out.println("Rectangle: X=" + rect.x + ", Y=" + rect.y + 
                         ", Width=" + rect.width + ", Height=" + rect.height);
    }
}
```

### Get Recognition Confidence

```java
public void getConfidence() throws Exception {
    BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.ALL_SUPPORTED_TYPES);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Type: " + result.getCodeTypeName());
        System.out.println("Text: " + result.getCodeText());
        System.out.println("Confidence: " + result.getConfidence() + "%");
        
        // Check if confidence is high enough
        if (result.getConfidence() >= 80) {
            System.out.println("High confidence recognition");
        }
    }
}
```

### Recognize from Stream

```java
public void recognizeFromStream() throws Exception {
    // Read image from file into stream
    java.io.FileInputStream stream = new java.io.FileInputStream("barcode.png");
    
    BarCodeReader reader = new BarCodeReader(stream, DecodeType.CODE_128);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Code: " + result.getCodeText());
    }
    
    stream.close();
}
```

### Recognize from Byte Array

```java
public void recognizeFromByteArray() throws Exception {
    // Read image into byte array
    java.nio.file.Path path = java.nio.file.Paths.get("barcode.png");
    byte[] imageBytes = java.nio.file.Files.readAllBytes(path);
    
    // Create input stream from byte array
    java.io.ByteArrayInputStream stream = new java.io.ByteArrayInputStream(imageBytes);
    
    BarCodeReader reader = new BarCodeReader(stream, DecodeType.CODE_128);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Code: " + result.getCodeText());
    }
    
    stream.close();
}
```

## Region of Interest (ROI) Recognition

### Recognize Specific Area

```java
public void recognizeROI() throws Exception {
    BarCodeReader reader = new BarCodeReader("large_image.png", DecodeType.CODE_128);
    
    // Set region of interest (x, y, width, height)
    reader.setArea(new Rectangle(100, 100, 300, 200));
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Found in ROI: " + result.getCodeText());
    }
}
```

### Recognize Multiple Regions

```java
public void recognizeMultipleROIs() throws Exception {
    String imagePath = "document_with_barcodes.png";
    
    // Define multiple regions
    Rectangle[] regions = {
        new Rectangle(50, 50, 200, 100),
        new Rectangle(50, 200, 200, 100),
        new Rectangle(50, 350, 200, 100)
    };
    
    for (int i = 0; i < regions.length; i++) {
        BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.ALL_SUPPORTED_TYPES);
        reader.setArea(regions[i]);
        
        System.out.println("Region " + (i + 1) + ":");
        for (BarCodeResult result : reader.readBarCodes()) {
            System.out.println("  " + result.getCodeTypeName() + ": " + result.getCodeText());
        }
    }
}
```

## Batch Recognition

### Recognize Multiple Barcodes in Single Image

```java
public void recognizeMultipleBarcodes() throws Exception {
    BarCodeReader reader = new BarCodeReader(
        "multiple_barcodes.png",
        DecodeType.CODE_128,
        DecodeType.QR,
        DecodeType.EAN_13
    );
    
    BarCodeResult[] results = reader.readBarCodes();
    System.out.println("Found " + results.length + " barcodes:");
    
    for (int i = 0; i < results.length; i++) {
        System.out.println("Barcode " + (i + 1) + ":");
        System.out.println("  Type: " + results[i].getCodeTypeName());
        System.out.println("  Text: " + results[i].getCodeText());
    }
}
```

### Recognize Multiple Files

```java
public void recognizeMultipleFiles() throws Exception {
    String[] files = {
        "barcode1.png",
        "barcode2.png",
        "barcode3.png",
        "barcode4.png",
        "barcode5.png"
    };
    
    for (String file : files) {
        System.out.println("Processing: " + file);
        
        BarCodeReader reader = new BarCodeReader(file, DecodeType.ALL_SUPPORTED_TYPES);
        
        for (BarCodeResult result : reader.readBarCodes()) {
            System.out.println("  " + result.getCodeTypeName() + ": " + result.getCodeText());
        }
    }
}
```

## Custom Quality Settings

### Configure Detection Settings

```java
public void customQualitySettings() throws Exception {
    BarCodeReader reader = new BarCodeReader("difficult_barcode.png", DecodeType.CODE_128);
    
    // Create custom quality settings
    QualitySettings settings = new QualitySettings();
    settings.setHighPerformance();
    
    // Enable specific detectors
    settings.setAllowInvertImage(true);
    settings.setAllowComplexBackground(true);
    settings.setAllowMedianSmoothing(true);
    settings.setAllowRegularWiping(true);
    
    reader.setQualitySettings(settings);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Code: " + result.getCodeText());
    }
}
```

### Fine-Tune Detection

```java
public void fineTuneDetection() throws Exception {
    BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.CODE_128);
    
    QualitySettings settings = QualitySettings.getNormalQuality();
    
    // Enable advanced features for difficult images
    settings.setAllowDecreasedImage(true);
    settings.setAllowWhiteSpotsRemoving(true);
    settings.setAllowOneDFastBarcodesDetector(true);
    settings.setFastScanOnly(false);
    
    reader.setQualitySettings(settings);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println("Recognized: " + result.getCodeText());
    }
}
```

## Error Handling

### Handle Recognition Errors

```java
public void handleRecognitionErrors() throws Exception {
    try {
        BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.CODE_128);
        
        boolean found = false;
        for (BarCodeResult result : reader.readBarCodes()) {
            System.out.println("Found: " + result.getCodeText());
            found = true;
        }
        
        if (!found) {
            System.out.println("No barcodes found in the image");
        }
        
    } catch (Exception ex) {
        System.err.println("Recognition error: " + ex.getMessage());
    }
}
```

### Validate Recognition Results

```java
public void validateResults() throws Exception {
    BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.EAN_13);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        String codeText = result.getCodeText();
        
        // Validate EAN-13 (should be 13 digits)
        if (codeText != null && codeText.length() == 13 && codeText.matches("\\d+")) {
            System.out.println("Valid EAN-13: " + codeText);
        } else {
            System.out.println("Invalid EAN-13 format: " + codeText);
        }
        
        // Check confidence
        if (result.getConfidence() < 70) {
            System.out.println("Warning: Low confidence (" + result.getConfidence() + "%)");
        }
    }
}
```

## Best Practices Summary

### 1. **Choose Appropriate Decode Types**
```java
// Specific type for better performance
BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.CODE_128);

// Multiple specific types if you know what to expect
BarCodeReader reader2 = new BarCodeReader("barcode.png", 
    DecodeType.CODE_128, DecodeType.EAN_13, DecodeType.QR);

// ALL_SUPPORTED_TYPES only when necessary (slower)
BarCodeReader reader3 = new BarCodeReader("barcode.png", DecodeType.ALL_SUPPORTED_TYPES);
```

### 2. **Use Quality Settings Wisely**
- **HighPerformance**: Fast recognition for good quality images
- **NormalQuality**: Balanced approach (default)
- **HighQuality**: For difficult barcodes
- **MaxQuality**: Last resort for very poor quality images

### 3. **Barcode-Specific Settings**

#### For 1D Barcodes (Code 128, Code 39, EAN, UPC):
```java
reader.getBarcodeSettings().setChecksumValidation(ChecksumValidation.ON);
reader.getBarcodeSettings().setStripFNC(true);
```

#### For 2D Barcodes (QR, DataMatrix):
```java
reader.getBarcodeSettings().setDetectEncoding(true);
reader.setQualitySettings(QualitySettings.getHighQuality());
```

#### For GS1 Barcodes:
```java
reader.getBarcodeSettings().setStripFNC(true); // Clean AI parsing
reader.getBarcodeSettings().setDetectEncoding(true);
```

#### For Postal Barcodes:
```java
reader.getBarcodeSettings().setChecksumValidation(ChecksumValidation.ON);
```

### 4. **Optimize Image Quality**
- Resolution: 200-300 DPI for printed barcodes
- Contrast: Ensure good contrast between bars and background
- Focus: Image should be sharp and in focus
- Lighting: Avoid shadows and glare

### 5. **Use ROI for Large Images**
When working with large images, use Region of Interest to improve performance:
```java
reader.setArea(new Rectangle(x, y, width, height));
```

### 6. **Handle Multiple Barcodes**
Always iterate through all results:
```java
BarCodeResult[] results = reader.readBarCodes();
for (BarCodeResult result : results) {
    // Process each barcode
}
```

### 7. **Validate Results**
Always validate recognition results:
- Check confidence level
- Validate format (length, characters)
- Verify checksum if applicable

### 8. **Performance Optimization**
```java
// Reuse reader instance
BarCodeReader reader = new BarCodeReader();
reader.setBarCodeDecodeType(DecodeType.CODE_128);

for (String file : files) {
    reader.setBarCodeImage(file);
    for (BarCodeResult result : reader.readBarCodes()) {
        // Process
    }
}
```

## Quality Settings Reference

### Quality Level Comparison

| Setting | Speed | Accuracy | Use Case |
|---------|-------|----------|----------|
| **HighPerformance** | ⚡⚡⚡ | ⭐⭐ | Good quality images, real-time scanning |
| **NormalQuality** | ⚡⚡ | ⭐⭐⭐ | Balanced (default), most cases |
| **HighQuality** | ⚡ | ⭐⭐⭐⭐ | Difficult barcodes, poor lighting |
| **MaxQuality** | 🐢 | ⭐⭐⭐⭐⭐ | Very poor quality, last resort |

### Specific Filters

| Filter | Purpose | When to Use |
|--------|---------|-------------|
| `AllowInvertImage` | Detects white-on-black barcodes | Inverted colors |
| `AllowComplexBackground` | Handles noisy backgrounds | Complex patterns behind barcode |
| `AllowMedianSmoothing` | Smooths image noise | Grainy images |
| `AllowRegularWiping` | Removes regular noise patterns | Printed on textured surface |
| `AllowWhiteSpotsRemoving` | Removes white spots | Damaged or dirty barcodes |
| `AllowSaltAndPaperFiltering` | Removes salt-and-pepper noise | Old or weathered barcodes |
| `AllowDecreasedImage` | Resizes large images | High-resolution scans |
| `AllowOneDFastBarcodesDetector` | Fast 1D detection | Performance-critical 1D barcodes |

## Troubleshooting Guide

### Problem: Barcode Not Recognized

**Solution 1: Try Higher Quality Settings**
```java
reader.setQualitySettings(QualitySettings.getHighQuality());
// If still not working:
reader.setQualitySettings(QualitySettings.getMaxQuality());
```

**Solution 2: Enable Specific Filters**
```java
QualitySettings settings = QualitySettings.getHighQuality();
settings.setAllowInvertImage(true);
settings.setAllowComplexBackground(true);
settings.setAllowMedianSmoothing(true);
reader.setQualitySettings(settings);
```

**Solution 3: Check Image Quality**
- Ensure resolution is at least 200 DPI
- Check for proper focus
- Verify sufficient contrast

### Problem: Low Confidence Recognition

**Solution: Improve Image Quality or Settings**
```java
reader.setQualitySettings(QualitySettings.getMaxQuality());

for (BarCodeResult result : reader.readBarCodes()) {
    if (result.getConfidence() < 80) {
        System.out.println("Low confidence: " + result.getConfidence());
        // Consider rejecting or requesting rescan
    }
}
```

### Problem: Wrong Barcode Type Detected

**Solution: Specify Exact Decode Types**
```java
// Instead of ALL_SUPPORTED_TYPES, use specific types
BarCodeReader reader = new BarCodeReader(
    "barcode.png",
    DecodeType.CODE_128,  // Only the expected types
    DecodeType.EAN_13
);
```

### Problem: Slow Recognition

**Solution 1: Use Specific Decode Types**
```java
// Specific types are much faster than ALL_SUPPORTED_TYPES
BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.CODE_128);
```

**Solution 2: Use ROI**
```java
// Only scan relevant area
reader.setArea(new Rectangle(x, y, width, height));
```

**Solution 3: Use HighPerformance Settings**
```java
reader.setQualitySettings(QualitySettings.getHighPerformance());
```

### Problem: Multiple False Positives

**Solution: Validate Results and Use Confidence Threshold**
```java
for (BarCodeResult result : reader.readBarCodes()) {
    if (result.getConfidence() >= 90) {  // Higher threshold
        // Validate format
        if (isValidFormat(result.getCodeText())) {
            System.out.println("Valid: " + result.getCodeText());
        }
    }
}
```

## Common Recognition Patterns

### Pattern 1: Simple Recognition

```java
public void simplePattern() throws Exception {
    BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.CODE_128);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println(result.getCodeText());
    }
}
```

### Pattern 2: Recognition with Validation

```java
public void validationPattern() throws Exception {
    BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.EAN_13);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        if (result.getConfidence() >= 80 && result.getCodeText().length() == 13) {
            System.out.println("Valid: " + result.getCodeText());
        }
    }
}
```

### Pattern 3: Robust Recognition

```java
public void robustPattern() throws Exception {
    BarCodeReader reader = new BarCodeReader("difficult_barcode.png", DecodeType.CODE_128);
    reader.setQualitySettings(QualitySettings.getHighQuality());
    
    BarCodeResult[] results = reader.readBarCodes();
    
    if (results.length == 0) {
        // Try with max quality
        reader.setQualitySettings(QualitySettings.getMaxQuality());
        results = reader.readBarCodes();
    }
    
    for (BarCodeResult result : results) {
        System.out.println("Found: " + result.getCodeText());
    }
}
```

### Pattern 4: Production Recognition with Logging

```java
public void productionPattern() throws Exception {
    BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.CODE_128);
    reader.setQualitySettings(QualitySettings.getHighQuality());
    
    long startTime = System.currentTimeMillis();
    
    BarCodeResult[] results = reader.readBarCodes();
    
    long elapsed = System.currentTimeMillis() - startTime;
    
    if (results.length == 0) {
        System.err.println("No barcodes found after " + elapsed + " ms");
        return;
    }
    
    for (BarCodeResult result : results) {
        System.out.println("Recognized: " + result.getCodeTypeName());
        System.out.println("  Text: " + result.getCodeText());
        System.out.println("  Confidence: " + result.getConfidence() + "%");
        System.out.println("  Time: " + elapsed + " ms");
        
        // Validate confidence
        if (result.getConfidence() < 70) {
            System.err.println("  WARNING: Low confidence!");
        }
    }
}
```

## Common Recognition Patterns

### Pattern 1: Simple Recognition

```java
public void simplePattern() throws Exception {
    BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.CODE_128);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println(result.getCodeText());
    }
}
```

### Pattern 2: Recognition with Validation

```java
public void validationPattern() throws Exception {
    BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.EAN_13);
    
    for (BarCodeResult result : reader.readBarCodes()) {
        if (result.getConfidence() >= 80 && result.getCodeText().length() == 13) {
            System.out.println("Valid: " + result.getCodeText());
        }
    }
}
```

### Pattern 3: Robust Recognition

```java
public void robustPattern() throws Exception {
    BarCodeReader reader = new BarCodeReader("difficult_barcode.png", DecodeType.CODE_128);
    reader.setQualitySettings(QualitySettings.getHighQuality());
    
    BarCodeResult[] results = reader.readBarCodes();
    
    if (results.length == 0) {
        // Try with max quality
        reader.setQualitySettings(QualitySettings.getMaxQuality());
        results = reader.readBarCodes();
    }
    
    for (BarCodeResult result : results) {
        System.out.println("Found: " + result.getCodeText());
    }
}
```

## Performance Tips

### 1. **Reuse Reader Instance**
```java
// Create once
BarCodeReader reader = new BarCodeReader();
reader.setBarCodeDecodeType(DecodeType.CODE_128);

// Reuse for multiple images
String[] files = {"img1.png", "img2.png", "img3.png"};
for (String file : files) {
    reader.setBarCodeImage(file);
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println(result.getCodeText());
    }
}
```

### 2. **Use Specific Decode Types**
Specifying exact barcode types is faster than using ALL_SUPPORTED_TYPES.

### 3. **Use ROI for Large Images**
Limit recognition area to speed up processing.

### 4. **Choose Appropriate Quality Settings**
Start with HighPerformance, increase only if needed.

## Next Steps

- Learn about [barcode generation](/java/developer-guide/barcode-generation/)
- Explore [advanced recognition features](/java/developer-guide/barcode-recognition/advanced/)
- Read about [quality settings](/java/developer-guide/barcode-recognition/quality-settings/)
- Study [specific barcode types](/java/developer-guide/barcode-recognition/symbologies/)