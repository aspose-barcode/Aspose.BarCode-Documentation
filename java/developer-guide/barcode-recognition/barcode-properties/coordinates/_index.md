---
title: "Coordinates"
description: "Learn how to read barcode region coordinates (Rectangle and Quadrangle) from BarCodeReader results in Aspose.BarCode for Java."
type: docs
weight: 20
url: /java/developer-guide/barcode-recognition/barcode-properties/coordinates
---

# Reading Barcode Coordinates

When Aspose.BarCode for Java recognizes a barcode, it not only returns the decoded text and type,  
but also the **coordinates of the detected region** inside the image.

This region geometry is exposed through `BarCodeRegionParameters` and lets you:

- locate the barcode on the image,
- draw overlays for debugging or UI highlighting,
- perform cropping, perspective correction, or further image processing.

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.barcode_properties.CoordinatesExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/CoordinatesExample.java" target="_blank" rel="noopener noreferrer">CoordinatesExample.java</a>

In the snippets below, variables like `imagePath` represent paths to barcode images in your application.

---

## 1. Region Geometry Basics

For each `BarCodeResult`, the method `getRegion()` returns a `BarCodeRegionParameters` instance that describes where the barcode was found:

- `getRectangle()` — axis-aligned bounding box (`java.awt.Rectangle`).
- `getQuadrangle()` — oriented quadrilateral (`Quadrangle`) that follows rotation/skew.

Both shapes refer to the **same physical barcode region**, but with different levels of detail.

> Coordinate system: the origin (0,0) is at the top-left corner of the image,  
> X increases to the right, Y increases downward (standard Java 2D coordinates).

---

## 2. Reading Coordinates for a Code 128 Barcode

The following example shows how to read region geometry for a Code 128 symbol:

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "coords_c128.png");

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();

if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    BarCodeRegionParameters barCodeRegionParameters = barCodeResult.getRegion();

    // Axis-aligned rectangle
    Rectangle rectangle = barCodeRegionParameters.getRectangle();
    System.out.println("Rect: x=" + rectangle.x
            + " y=" + rectangle.y
            + " w=" + rectangle.width
            + " h=" + rectangle.height);

    // Oriented quadrangle (true outline with rotation/skew)
    Quadrangle quadrangle = barCodeRegionParameters.getQuadrangle();
    Point leftTop = quadrangle.getLeftTop();
    Point rightTop = quadrangle.getRightTop();
    Point rightBottom = quadrangle.getRightBottom();
    Point leftBottom = quadrangle.getLeftBottom();

    System.out.println("LT=" + leftTop
            + " RT=" + rightTop
            + " RB=" + rightBottom
            + " LB=" + leftBottom);
}
```

What this snippet shows:

- `rectangle` is the **bounding box** that encloses the entire barcode region. It is always axis-aligned.
- `quadrangle` has four named corners:
    - `leftTop`
    - `rightTop`
    - `rightBottom`
    - `leftBottom`  
      These points follow the **actual shape** of the barcode region, including rotation or slight skew.

Use cases:

- `Rectangle` is ideal for quick checks, hit-testing, or simple cropping.
- `Quadrangle` is better when precise geometry matters, e.g., drawing a contour around a rotated symbol or applying a perspective transform.

---

## 3. Coordinates for QR and Other 2D Barcodes

The same API works uniformly for 2D symbologies such as QR.  
You can rely on `getRectangle()` and `getQuadrangle()` regardless of whether the barcode is 1D or 2D.

Example: reading region geometry for a QR code:

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "coords_qr.png");

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);
BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();

if (barCodeResults.length > 0) {
    BarCodeRegionParameters barCodeRegionParameters = barCodeResults[0].getRegion();

    Rectangle rectangle = barCodeRegionParameters.getRectangle();
    Quadrangle quadrangle = barCodeRegionParameters.getQuadrangle();

    System.out.println("QR Rect: " + rectangle);
    System.out.println("QR Quad: LT=" + quadrangle.getLeftTop()
            + " RT=" + quadrangle.getRightTop()
            + " RB=" + quadrangle.getRightBottom()
            + " LB=" + quadrangle.getLeftBottom());
}
```

Key points:

- The geometry model is **consistent** between 1D and 2D barcode types.
- `Quadrangle` always exposes the four corner points in a semantic order (left-top, right-top, right-bottom, left-bottom).
- You can overlay these coordinates on screen, store them for later processing, or use them to extract the region from the image.

---

## 4. Drawing a Debug Overlay

A common practical scenario is to **visualize** detected barcodes on top of the original image:  
for example, in a debugging tool or an admin UI.

The helper method below shows how to draw both the rectangle and the quadrangle onto a copy of the source image and save it as a PNG:

```java
private static void drawOverlay(String srcPath,
                                String outPath,
                                Rectangle rectangle,
                                Quadrangle quadrangle) throws Exception {
    BufferedImage image = ImageIO.read(new File(srcPath));
    Graphics2D graphics = image.createGraphics();
    try {
        graphics.setRenderingHint(RenderingHints.KEY_ANTIALIASING,
                                  RenderingHints.VALUE_ANTIALIAS_ON);
        graphics.setColor(new Color(0, 180, 0));
        graphics.setStroke(new BasicStroke(2f));

        // Rectangle (axis-aligned bounding box)
        if (rectangle != null) {
            graphics.drawRect(rectangle.x, rectangle.y,
                              rectangle.width, rectangle.height);
        }

        // Quadrangle polygon: LT -> RT -> RB -> LB -> LT
        if (quadrangle != null) {
            Point leftTop = quadrangle.getLeftTop();
            Point rightTop = quadrangle.getRightTop();
            Point rightBottom = quadrangle.getRightBottom();
            Point leftBottom = quadrangle.getLeftBottom();

            graphics.drawLine(leftTop.x, leftTop.y, rightTop.x, rightTop.y);
            graphics.drawLine(rightTop.x, rightTop.y, rightBottom.x, rightBottom.y);
            graphics.drawLine(rightBottom.x, rightBottom.y, leftBottom.x, leftBottom.y);
            graphics.drawLine(leftBottom.x, leftBottom.y, leftTop.x, leftTop.y);
        }
    } finally {
        graphics.dispose();
    }

    ImageIO.write(image, "PNG", new File(outPath));
    System.out.println("[INFO] Overlay saved: " + outPath);
}
```

How to use this helper in your code:

1. Recognize the barcode and obtain `rectangle` and `quadrangle` from `BarCodeRegionParameters`.
2. Call `drawOverlay(sourceImagePath, debugOutputPath, rectangle, quadrangle)`.
3. Open the generated debug image to visually verify that the coordinates match the actual barcode position.

This is extremely useful when:

- tuning recognition parameters,
- debugging ROI logic,
- or validating that cropping and post-processing use the correct coordinates.

---

## Summary

In Aspose.BarCode for Java, the **coordinates** of a recognized barcode are exposed through `BarCodeRegionParameters`:

- `getRectangle()` — axis-aligned bounding box for quick operations.
- `getQuadrangle()` — oriented quadrilateral that follows rotation and skew.

Using these shapes you can:

- highlight barcodes in your UI,
- crop or pre-process only the relevant regions,
- validate detection results visually with debug overlays.

All examples in this article are based on:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/CoordinatesExample.java" target="_blank" rel="noopener noreferrer">CoordinatesExample.java</a>

Use this class as a reference when integrating coordinate-based processing into your barcode recognition workflows.
