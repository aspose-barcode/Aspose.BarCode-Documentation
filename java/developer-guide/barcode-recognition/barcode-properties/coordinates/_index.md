---
title: "Coordinates"
description: "Learn how to read barcode region coordinates (Rectangle, Quadrangle, and Points) from BarCodeReader results in Aspose.BarCode for Java."
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

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/CoordinatesExample.java" target="_blank" rel="noopener noreferrer">
CoordinatesExample.java</a>

In the snippets below, variables like `imagePath` represent paths to barcode images in your application.

---

## 1. Region Geometry Basics

For each `BarCodeResult`, the method `getRegion()` returns a `BarCodeRegionParameters` instance that describes where the
barcode was found:

- `getRectangle()` — axis-aligned bounding box (`java.awt.Rectangle`).
- `getQuadrangle()` — oriented quadrilateral (`Quadrangle`) that follows rotation/skew.
- `getPoints()` — array of corner points (`java.awt.Point[]`) representing the same region.

All three describe the **same physical barcode region**, but with different levels of detail and in different data
shapes.

> Coordinate system: the origin (0,0) is at the top-left corner of the image,  
> X increases to the right, Y increases downward (standard Java 2D coordinate system).

---

## 2. Reading Coordinates for a Code 128 Barcode

The following example shows how to read region geometry for a Code 128 symbol:

```java
import java.util.stream.IntStream;

String imagePath = ExampleAssist.pathCombine(FOLDER, "coords_c128.png");

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();

if(barCodeResults.length >0){
BarCodeResult barCodeResult = barCodeResults[0];
BarCodeRegionParameters barCodeRegionParameters = barCodeResult.getRegion();

// Axis-aligned rectangle
Rectangle rectangle = barCodeRegionParameters.getRectangle();
    System.out.

println("Rect: x="+rectangle.x
            +" y="+rectangle.y
                    +" w="+rectangle.width
                    +" h="+rectangle.height);

// Oriented quadrangle (true outline with rotation/skew)
Quadrangle quadrangle = barCodeRegionParameters.getQuadrangle();
Point leftTop = quadrangle.getLeftTop();
Point rightTop = quadrangle.getRightTop();
Point rightBottom = quadrangle.getRightBottom();
Point leftBottom = quadrangle.getLeftBottom();

    System.out.

println("Quad LT="+leftTop
            +" RT="+rightTop
                    +" RB="+rightBottom
                    +" LB="+leftBottom);

// Raw corner points as an array
Point[] points = barCodeRegionParameters.getPoints();
            if(points !=null){
        IntStream.

range(0,points.length).

forEach(i ->{
Point point = points[i];
                System.out.

println("Point "+i +": x="+point.x+" y="+point.y);
            });
                    }
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
- `points` is an array of `Point` that contains the same physical corner coordinates as the quadrangle, but in a form
  convenient for iteration and generic algorithms.

Typical use cases:

- `Rectangle` is ideal for quick checks, hit-testing, or simple cropping.
- `Quadrangle` is better when precise geometry matters, for example drawing a contour around a rotated symbol or
  applying a perspective transform.
- `Point[]` is useful when you want to pass coordinates to APIs that work with arrays, serialize them, or run your own
  geometric algorithms.

---

## 3. Rectangle vs Quadrangle vs Points

All three methods describe the same region, but from different perspectives:

### `getRectangle()`

- Returns a `java.awt.Rectangle`.
- Always axis-aligned: sides are parallel to the X and Y axes.
- Represents the **minimal bounding rectangle** that fully contains the barcode.
- Useful for:
    - quick hit-testing (for example, “did the mouse click land inside the barcode?”),
    - cropping a subimage from the source image,
    - simple masks and highlight rectangles.

Limitation: it does not reflect the actual rotation angle — even if the barcode is rotated, the rectangle remains
axis-aligned.

### `getQuadrangle()`

- Returns a `Quadrangle` with four **semantically named** corners:
    - `getLeftTop()`
    - `getRightTop()`
    - `getRightBottom()`
    - `getLeftBottom()`
- The corners follow the true outline of the detected barcode, including rotation and small perspective distortions.
- Useful for:
    - drawing an accurate contour around the symbol,
    - analyzing tilt/geometry,
    - applying perspective transforms only to the barcode region.

Important: the corner methods (`getLeftTop()`, etc.) provide semantic positions; you should not assume that any
particular index in `getPoints()` is “always left top”.

### `getPoints()`

- Returns an array `java.awt.Point[]`.
- Contains the same corner points as the quadrangle, but in array form.
- The order of elements in the array is defined by the engine implementation and **must not** be used for logic like  
  “points[0] is always the top-left corner”.
- If you need **semantically named** corners, use `getQuadrangle()`.  
  If you need a generic collection of points to feed into algorithms or external libraries, use `getPoints()`.

Comparison table:

| Method            | Type         | Orientation        | Corner semantics         | Typical usage                                         |
|-------------------|--------------|--------------------|--------------------------|-------------------------------------------------------|
| `getRectangle()`  | `Rectangle`  | Axis-aligned       | None                     | Fast crop, hit-testing, simple highlighting           |
| `getQuadrangle()` | `Quadrangle` | Rotated / skewed   | LT, RT, RB, LB           | Accurate contour, angle analysis, perspective warping |
| `getPoints()`     | `Point[]`    | Same as Quadrangle | Order is engine-specific | Loops, serialization, custom geometry algorithms      |

---

## 4. Coordinates for QR and Other 2D Barcodes

The same API works uniformly for 2D symbologies such as QR.  
You can rely on `getRectangle()`, `getQuadrangle()` and `getPoints()` regardless of whether the barcode is 1D or 2D.

Example: reading region geometry for a QR code:

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "coords_qr.png");

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);
BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();

if (barCodeResults.length > 0) {
    BarCodeRegionParameters barCodeRegionParameters = barCodeResults[0].getRegion();

    Rectangle rectangle = barCodeRegionParameters.getRectangle();
    Quadrangle quadrangle = barCodeRegionParameters.getQuadrangle();
    Point[] points = barCodeRegionParameters.getPoints();

    System.out.println("QR Rect: "+rectangle);
    System.out.println("QR Quad: LT="+quadrangle.getLeftTop() +
        " RT="+quadrangle.getRightTop() + 
        " RB="+quadrangle.getRightBottom() + 
        " LB="+quadrangle.getLeftBottom());

    if(points !=null){
            IntStream.range(0, points.length).forEach(i -> {
            Point point = points[i];
            System.out.println("Point " + i + ": x=" + point.getX() + " y=" + point.getY());
        });
    }
}
```

Key points:

- The geometry model is **consistent** between 1D and 2D barcode types.
- `Quadrangle` always exposes four corners with clear semantics (left-top, right-top, right-bottom, left-bottom).
- `Point[]` can be used for any generic coordinate-based processing.

---

## 5. Test: Creating a Debug Overlay Image

The example class also contains a dedicated test that shows how to **create a debug overlay image** with the detected
region drawn on top of the original barcode image.

A simplified version of this pattern looks like this:

```java
String sourceImagePath = ExampleAssist.pathCombine(FOLDER, "coords_c128.png");
String debugImagePath = ExampleAssist.pathCombine(FOLDER, "coords_overlay.png");

// Recognize barcode
BarCodeReader barCodeReader = new BarCodeReader(sourceImagePath, DecodeType.CODE_128);
BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();

if(barCodeResults.length >0){
    BarCodeRegionParameters barCodeRegionParameters = barCodeResults[0].getRegion();
    Rectangle rectangle = barCodeRegionParameters.getRectangle();
    Quadrangle quadrangle = barCodeRegionParameters.getQuadrangle();

    // Draw overlay and save result
    drawOverlay(sourceImagePath, debugImagePath, rectangle, quadrangle);

    File debugFile = new File(debugImagePath);
    System.out.println("Overlay image exists: " + debugFile.exists());
}
```

This pattern corresponds to a test method in `CoordinatesExample` that:

1. Recognizes a Code 128 barcode.
2. Extracts `Rectangle` and `Quadrangle` from `BarCodeRegionParameters`.
3. Calls a helper method to draw both shapes on top of the source image.
4. Verifies that the output overlay file has been created.

### Helper: `drawOverlay`

The helper method below draws both the rectangle and the quadrangle onto a copy of the source image and saves it as a
PNG:

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

How to use this helper in your own code:

1. Recognize the barcode and obtain `Rectangle` and `Quadrangle` from `BarCodeRegionParameters`.
2. Call `drawOverlay(sourceImagePath, debugImagePath, rectangle, quadrangle)`.
3. Open the generated debug image to visually verify that the coordinates match the actual barcode position.

This is extremely useful when:

- tuning recognition parameters,
- debugging ROI logic,
- validating that cropping and post-processing use the correct coordinates.

---

## Summary

In Aspose.BarCode for Java, the **coordinates** of a recognized barcode are exposed through `BarCodeRegionParameters`:

- `getRectangle()` — axis-aligned bounding box for quick operations.
- `getQuadrangle()` — oriented quadrilateral that follows rotation and skew.
- `getPoints()` — the same corners as a `Point[]` array for generic processing.

Using these shapes you can:

- highlight barcodes in your UI,
- crop or pre-process only the relevant regions,
- validate detection results visually with debug overlays,
- integrate barcode geometry into your own analysis and post-processing algorithms.

All examples in this article are based on:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/CoordinatesExample.java" target="_blank" rel="noopener noreferrer">
CoordinatesExample.java</a>

Use this class as a reference when integrating coordinate-based processing into your barcode recognition workflows.
