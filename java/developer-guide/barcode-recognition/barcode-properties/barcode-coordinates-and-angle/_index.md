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
