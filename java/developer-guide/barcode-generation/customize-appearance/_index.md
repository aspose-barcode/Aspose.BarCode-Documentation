---
title: Customize Appearance
type: docs
weight: 30
url: /java/developer-guide/Customize-Appearance
---
# Customizing Barcode Appearance

## Overview

Aspose.BarCode for Java provides extensive customization options to control the visual appearance of generated barcodes. 
This guide covers barcode sizing, colors, resolution, and visual styling.

## Barcode Size and Dimensions

### X-Dimension (Bar Width)

The X-dimension controls the width of the narrowest bar in the barcode:

```java
import com.aspose.barcode.generation.*;

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ABC123");

// Set X-dimension in pixels
generator.getParameters().getBarcode().getXDimension().setPixels(3);

// Or set in millimeters
generator.getParameters().getBarcode().getXDimension().setMillimeters(0.5f);

generator.save("barcode_xdim.png");
```

### Barcode Height

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "12345");

// Set bar height in pixels
generator.getParameters().getBarcode().getBarHeight().setPixels(80);

// Or in millimeters
generator.getParameters().getBarcode().getBarHeight().setMillimeters(20);

generator.save("barcode_height.png");
```

### Auto-Sizing

Let the barcode automatically size to fit specific dimensions:

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "AutoSize Example");

// Set image dimensions
generator.getParameters().getImageHeight().setPixels(200);
generator.getParameters().getImageWidth().setPixels(200);

// Enable auto-sizing
generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);

generator.save("barcode_autosize.png");
```

## Color Customization

### Basic Colors

```java
import java.awt.Color;

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "COLOR");

// Set background color
generator.getParameters().setBackColor(Color.WHITE);

// Set bar color
generator.getParameters().getBarcode().setBarColor(Color.BLACK);

generator.save("barcode_colors.png");
```

### Custom RGB Colors

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "Custom Colors");

// Custom background color
generator.getParameters().setBackColor(new Color(240, 248, 255)); // AliceBlue

// Custom bar color  
generator.getParameters().getBarcode().setBarColor(new Color(25, 25, 112)); // MidnightBlue

generator.save("barcode_custom_rgb.png");
```

### Border Color

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "BORDER");

// Enable border
generator.getParameters().getBorder().setVisible(true);
generator.getParameters().getBorder().getWidth().setPixels(2);

// Set border color
generator.getParameters().getBorder().setColor(Color.RED);

generator.save("barcode_border.png");
```

## Resolution and Quality

### Setting Resolution (DPI)

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "HIGH-RES");

// Set resolution in DPI (dots per inch)
generator.getParameters().setResolution(300); // High quality for printing

// Or set horizontal and vertical separately
generator.getParameters().getImageWidth().setPixels(400);
generator.getParameters().getImageHeight().setPixels(200);

generator.save("barcode_300dpi.png");
```

Common resolution settings:
- **72 DPI**: Screen display
- **150 DPI**: Draft printing
- **300 DPI**: Standard printing quality
- **600 DPI**: High-quality printing

## Margins and Padding

### Barcode Padding

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "PADDING");

// Set padding for all sides (quiet zone)
generator.getParameters().getBarcode().getPadding().getLeft().setPixels(20);
generator.getParameters().getBarcode().getPadding().getRight().setPixels(20);
generator.getParameters().getBarcode().getPadding().getTop().setPixels(10);
generator.getParameters().getBarcode().getPadding().getBottom().setPixels(10);

generator.save("barcode_padding.png");
```

### Image Margins

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "MARGINS");

// Set image margins
generator.getParameters().getImageHeight().setPixels(300);
generator.getParameters().getImageWidth().setPixels(300);

// Add margins around the image
generator.getParameters().getCaptionAbove().setVisible(true);
generator.getParameters().getCaptionAbove().setText("Product QR Code");
generator.getParameters().getCaptionAbove().getFont().setSize(new com.aspose.barcode.generation.FontUnit(14));

generator.save("barcode_margins.png");
```

## Rotation

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ROTATE");

// Rotate barcode (0, 90, 180