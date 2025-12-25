---
title: Barcode Coordinates & Angle
description: "How to read barcode region geometry and rotation angle from BarCodeRegionParameters."
type: docs
weight: 30
url: /java/developer-guide/barcode-recognition/barcode-properties/barcode-coordinates-and-angle
---

# Barcode Coordinates & Angle

For each recognized barcode, `BarCodeResult.getRegion()` returns geometry information.
You can use it to locate the barcode on the image and to understand its rotation.

## Rectangle vs quadrangle

`BarCodeRegionParameters` exposes the barcode region in several forms.
The two most common are:

- `Rectangle`: an axis-aligned bounding box. It is always aligned with the image axes (X and Y).
  Use it when you need a simple crop, a quick overlay, or a rough location.
- `Quadrangle`: four corner points of the detected barcode region (`leftTop`, `rightTop`, `rightBottom`, `leftBottom`).
  Use it when the barcode is rotated, skewed, or affected by perspective.

If the barcode is rotated, the rectangle will usually include extra background because it cannot rotate with the barcode.
The quadrangle follows the barcode shape more closely.

Coordinates are in image pixels. The origin is the top-left corner of the image.

## Read rectangle, quadrangle, points

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.BarCodeRegionParameters;
import com.aspose.barcode.barcoderecognition.Quadrangle;
import java.awt.Point;
import java.awt.Rectangle;

String imagePath = "coords_c128.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();

if (barCodeResults.length > 0) {
    BarCodeRegionParameters region = barCodeResults[0].getRegion();

    Rectangle rectangle = region.getRectangle();
    Quadrangle quadrangle = region.getQuadrangle();
    Point[] points = region.getPoints();

    System.out.println("Rect: " + rectangle);
    System.out.println("Quad LT=" + quadrangle.getLeftTop()
            + " RT=" + quadrangle.getRightTop()
            + " RB=" + quadrangle.getRightBottom()
            + " LB=" + quadrangle.getLeftBottom());
    System.out.println("Points count: " + (points != null ? points.length : 0));
}
```

## Read rotation angle

The angle is reported in degrees and represents the detected barcode orientation.
Use it when you need to rotate an overlay or to decide whether you should pre-rotate images before recognition.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

String imagePath = "rotated_code128.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.CODE_128);
BarCodeResult[] results = reader.readBarCodes();

if (results.length > 0) {
    double angle = results[0].getRegion().getAngle();
    System.out.println("Detected angle: " + angle + " degrees");
}
```

## Related topics

- If you need to validate results before using them: see [Result validation](../result-validation).
