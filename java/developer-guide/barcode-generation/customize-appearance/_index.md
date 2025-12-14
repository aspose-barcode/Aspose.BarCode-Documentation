---
title: "Customize Appearance"
type: docs
weight: 30
url: /java/developer-guide/customize-appearance/
---

# **Customizing Barcode Appearance**

## **Overview**

Aspose.BarCode for Java provides extensive customization options to control the visual appearance of generated barcodes.  
This guide covers barcode sizing, colors, resolution, margins, and rotation settings.

---

## **Barcode Size and Dimensions**

### **X-Dimension (Bar Width)**

The X-dimension controls the width of the narrowest bar (for 1D) or module (for 2D) in the barcode.

```java
import com.aspose.barcode.generation.*;

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ABC123");

// Set X-dimension in pixels
generator.getParameters().getBarcode().getXDimension().setPixels(3);

// Or set in millimeters
generator.getParameters().getBarcode().getXDimension().setMillimeters(0.5f);

generator.save("barcode_xdim.png", BarCodeImageFormat.PNG);
```

---

### **Barcode Height**

```java
import com.aspose.barcode.generation.*;

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "12345");

// Set bar height in pixels
generator.getParameters().getBarcode().getBarHeight().setPixels(80);

// Or in millimeters
generator.getParameters().getBarcode().getBarHeight().setMillimeters(20.0f);

generator.save("barcode_height.png", BarCodeImageFormat.PNG);
```

---

### **Auto-Sizing**

Let the barcode automatically scale to fit specific dimensions using the `AutoSizeMode` property.

```java
import com.aspose.barcode.generation.*;

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "AutoSize Example");

// Target bitmap dimensions
generator.getParameters().getImageHeight().setPixels(200);
generator.getParameters().getImageWidth().setPixels(200);

// Enable auto-sizing (fit while preserving geometry as much as possible)
generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);

generator.save("barcode_autosize.png", BarCodeImageFormat.PNG);
```

---

## **Color Customization**

### **Basic Colors**

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "COLOR");

// Background color
generator.getParameters().setBackColor(Color.WHITE);

// Bar (foreground) color
generator.getParameters().getBarcode().setBarColor(Color.BLACK);

generator.save("barcode_colors.png", BarCodeImageFormat.PNG);
```

---

### **Custom RGB Colors**

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "Custom Colors");

// Custom background color
generator.getParameters().setBackColor(new Color(240, 248, 255)); // AliceBlue

// Custom bar color
generator.getParameters().getBarcode().setBarColor(new Color(25, 25, 112)); // MidnightBlue

generator.save("barcode_custom_rgb.png", BarCodeImageFormat.PNG);
```

---

### **Border Color**

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "BORDER");

// Enable border and set thickness
generator.getParameters().getBorder().setVisible(true);
generator.getParameters().getBorder().getWidth().setPixels(2);

// Set border color
generator.getParameters().getBorder().setColor(Color.RED);

generator.save("barcode_border.png", BarCodeImageFormat.PNG);
```

---

## **Resolution and Quality**

### **Setting Resolution (DPI)**

```java
import com.aspose.barcode.generation.*;

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "HIGH-RES");

// Set resolution in DPI (dots per inch)
generator.getParameters().setResolution(300.0f); // 300 dpi for print

// Optionally control bitmap size
generator.getParameters().getImageWidth().setPixels(400);
generator.getParameters().getImageHeight().setPixels(200);

generator.save("barcode_300dpi.png", BarCodeImageFormat.PNG);
```

Common resolution settings:
- **72 DPI**: Screen display
- **150 DPI**: Draft printing
- **300 DPI**: Standard printing quality
- **600 DPI**: High-quality printing

> If your build does not contain `setResolution()`, manage print density through `ImageWidth` and `ImageHeight` parameters.

---

## **Margins and Padding**

### **Barcode Padding (Quiet Zone)**

```java
import com.aspose.barcode.generation.*;

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "PADDING");

// Quiet zone (padding) on all sides
generator.getParameters().getBarcode().getPadding().getLeft().setPixels(20);
generator.getParameters().getBarcode().getPadding().getRight().setPixels(20);
generator.getParameters().getBarcode().getPadding().getTop().setPixels(10);
generator.getParameters().getBarcode().getPadding().getBottom().setPixels(10);

generator.save("barcode_padding.png", BarCodeImageFormat.PNG);
```

> Padding defines the clear space around the barcode image (quiet zone) to ensure reliable scanning.

---

## **Rotation**

Rotate barcode images at any required angle by setting the `RotationAngle` property.

```java
import com.aspose.barcode.generation.*;

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ROTATE");

// Rotate barcode (clockwise), degrees: 0, 90, 180, -90, etc.
generator.getParameters().setRotationAngle(90.0f);
generator.save("barcode_rotate_90.png", BarCodeImageFormat.PNG);

generator.getParameters().setRotationAngle(-90.0f);
generator.save("barcode_rotate_-90.png", BarCodeImageFormat.PNG);

generator.getParameters().setRotationAngle(180.0f);
generator.save("barcode_rotate_180.png", BarCodeImageFormat.PNG);
```

---

{{% alert color="info" %}}
💡 **Related Example**  
See the full runnable TestNG example for X-Dimension and appearance customization here:  
👉 <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/design_usage_examples/src/test/java/com/aspose/barcode/guide/generation/XDimensionExamples.java" target="_blank" rel="noopener noreferrer">XDimensionExamples.java on GitHub</a>
{{% /alert %}}
