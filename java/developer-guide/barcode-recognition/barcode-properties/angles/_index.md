---
title: "Angles"
description: "Learn how to work with barcode rotation angles using BarCodeReader in Aspose.BarCode for Java."
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/barcode-properties/angles
---

# Barcode Rotation Angles

When a barcode is rotated in an image, Aspose.BarCode for Java can report its orientation.  
This information is exposed through `BarCodeRegionParameters` for each recognized barcode and can be used for:

- Understanding how a symbol is oriented on labels or documents
- Validating layout constraints (for example, barcodes must not be tilted beyond a threshold)
- Building visual overlays (debug images) with the correct geometry
- Further image processing that depends on rotation

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.barcode_properties.AnglesExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/AnglesExample.java" target="_blank" rel="noopener noreferrer">AnglesExample.java</a>

In the snippets below, variables like `imagePath` represent paths to sample images that contain rotated barcodes.

---

## 1. Reading the Rotation Angle

Each `BarCodeResult` contains a `BarCodeRegionParameters` object that describes where the barcode was found.  
The method `getAngle()` returns the approximate rotation angle of the detected barcode in degrees.

```java
String imagePath = "path/to/rotated_code128.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.CODE_128);
BarCodeResult[] results = reader.readBarCodes();

if (results.length > 0) {
    BarCodeRegionParameters region = results[0].getRegion();
    double angle = region.getAngle();
    System.out.println("Detected angle: " + angle + " degrees");
}
```

Key points:

- `getAngle()` returns a `double` value in degrees.
- The angle is estimated by the recognition engine and may differ slightly from the exact rotation.
- You should compare angles using a tolerance rather than expecting exact equality.

For example, to check if a barcode is approximately 30 degrees rotated:

```java
double angle = region.getAngle();
double expected = 30.0;
double tolerance = 7.5;

boolean isCloseTo30 = Math.abs(angle - expected) <= tolerance;
```

---

## 2. Angles for 2D Barcodes (QR Example)

Angle detection works in the same way for 2D barcodes such as QR codes.  
You can combine rotation reading with higher quality settings for more complex images.

```java
String imagePath = "path/to/rotated_qr.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.QR);
reader.setQualitySettings(QualitySettings.getHighQuality());

BarCodeResult[] results = reader.readBarCodes();

if (results.length > 0) {
    BarCodeRegionParameters region = results[0].getRegion();
    double angle = region.getAngle();
    System.out.println("Detected QR angle: " + angle + " degrees");
}
```

Key points:

- The same `getAngle()` method is used for both 1D and 2D symbologies.
- `QualitySettings.getHighQuality()` can improve detection robustness for rotated or small symbols.
- The reported angle for a QR rotated by about 45 degrees should be close to 45, within a reasonable tolerance.

---

## 3. Rectangle vs. Quadrangle for Rotated Barcodes

For each detected barcode, the engine provides two geometric representations of its location:

- `Rectangle` – an axis-aligned bounding box.
- `Quadrangle` – a four-point shape that follows the actual rotated outline.

You can access both via `BarCodeRegionParameters`.

```java
String imagePath = "path/to/rotated_code128.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.CODE_128);
BarCodeResult[] results = reader.readBarCodes();

if (results.length > 0) {
    BarCodeRegionParameters region = results[0].getRegion();

    Rectangle rect = region.getRectangle();
    Quadrangle quad = region.getQuadrangle();

    System.out.println("Rectangle: " + rect);
    System.out.println("Quad LT=" + quad.getLeftTop()
            + " RT=" + quad.getRightTop()
            + " RB=" + quad.getRightBottom()
            + " LB=" + quad.getLeftBottom());

    Rectangle quadBounds = quad.getBoundingRectangle();
    System.out.println("Quadrangle bounds: " + quadBounds);
}
```

Key points:

- The `Rectangle` is always axis-aligned and grows to fully enclose the rotated barcode.
- The `Quadrangle` tracks the true corners of the symbol and preserves its rotation and skew.
- `quad.getBoundingRectangle()` gives the same axis-aligned bounds as `region.getRectangle()`.

Use the quadrangle when you need precise geometry (for example, drawing the rotated shape),  
and use the rectangle when you only need a simple bounding box.

---

## 4. Reading Raw Corner Points with `getPoints()`

If you prefer to work directly with corner points, you can use `getPoints()` from `BarCodeRegionParameters`.  
It exposes an array of four `java.awt.Point` objects that correspond to the quadrangle corners.

```java
String imagePath = "path/to/rotated_qr.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.QR);
reader.setQualitySettings(QualitySettings.getHighQuality());

BarCodeResult[] results = reader.readBarCodes();

if (results.length > 0) {
    BarCodeRegionParameters region = results[0].getRegion();

    Point[] points = region.getPoints();
    if (points != null && points.length == 4) {
        for (int i = 0; i < points.length; i++) {
            System.out.println("Corner " + i + ": " + points[i]);
        }
    }
}
```

Key points:

- `getPoints()` returns four points that describe the corners of the detected region.
- The order of points is consistent and corresponds to the quadrangle corners.
- Corner points are useful for custom visualizations and geometry calculations.

---

## 5. Drawing a Visual Overlay with Angle and Geometry

You can combine the rotation angle, rectangle, and quadrangle to build a debug overlay image.  
This helps to visually confirm how the engine sees the barcode and its orientation.

```java
String srcPath = "path/to/rotated_code128.png";
String outPath = "path/to/angles_overlay.png";

BarCodeReader reader = new BarCodeReader(srcPath, DecodeType.CODE_128);
BarCodeResult[] results = reader.readBarCodes();

if (results.length > 0) {
    BarCodeRegionParameters region = results[0].getRegion();

    BufferedImage img = ImageIO.read(new File(srcPath));
    Graphics2D g = img.createGraphics();

    Rectangle rect = region.getRectangle();
    Quadrangle quad = region.getQuadrangle();
    double angle = region.getAngle();

    g.setColor(new Color(0, 160, 0));
    g.setStroke(new BasicStroke(2f));
    g.drawRect(rect.x, rect.y, rect.width, rect.height);

    Point lt = quad.getLeftTop();
    Point rt = quad.getRightTop();
    Point rb = quad.getRightBottom();
    Point lb = quad.getLeftBottom();

    g.setColor(new Color(0, 90, 220));
    g.drawLine(lt.x, lt.y, rt.x, rt.y);
    g.drawLine(rt.x, rt.y, rb.x, rb.y);
    g.drawLine(rb.x, rb.y, lb.x, lb.y);
    g.drawLine(lb.x, lb.y, lt.x, lt.y);

    String text = String.format("angle: %.1f°", angle);
    g.setColor(Color.BLACK);
    g.drawString(text, Math.max(0, rect.x), Math.max(12, rect.y - 6));

    g.dispose();
    ImageIO.write(img, "PNG", new File(outPath));
}
```

Key points:

- The rectangle is drawn in one color to show the axis-aligned bounds.
- The quadrangle is drawn in another color to show the actual rotated shape.
- The detected angle is rendered as a label near the barcode.
- This pattern is useful for debugging recognition results and tuning tolerance thresholds.

---

## Summary

Aspose.BarCode for Java provides detailed rotation information for each recognized barcode:

- `BarCodeRegionParameters.getAngle()` returns the approximate angle in degrees.
- `getRectangle()` gives an axis-aligned bounding box.
- `getQuadrangle()` and `getPoints()` provide precise corner geometry for rotated symbols.
- You can combine these APIs to validate orientation, enforce layout rules, or draw visual overlays.

All examples shown here are based on:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/AnglesExample.java" target="_blank" rel="noopener noreferrer">AnglesExample.java</a>

Use these patterns as a reference when working with barcode rotation angles in your own Java applications.
