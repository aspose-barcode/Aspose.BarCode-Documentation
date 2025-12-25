---
title: Use ROI (Region of Interest)
description: "How to limit recognition to a known rectangle to improve speed and stability."
type: docs
weight: 20
url: /java/developer-guide/barcode-recognition/basic-recognition-setup/use-roi
---

# Use ROI (Region of Interest)

ROI lets you restrict recognition to a rectangle or to several rectangles.
This reduces work on large images and helps ignore unrelated content outside the target area.

## Limit recognition to a single region

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;
import java.awt.Rectangle;

Rectangle roi = new Rectangle(20, 20, 440, 140);
BarCodeReader reader = new BarCodeReader("roi_canvas.png", roi, DecodeType.CODE_128);
```

## Use ROI with type groups

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;
import java.awt.Rectangle;

Rectangle roi = new Rectangle(470, 10, 250, 250);
BarCodeReader reader = new BarCodeReader("roi_canvas.png", roi, DecodeType.TYPES_2D);
```

## Scan multiple ROIs in one pass

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import java.awt.Rectangle;

Rectangle[] areas = new Rectangle[] {
        new Rectangle(20, 20, 440, 140),
        new Rectangle(470, 240, 450, 160)
};

BarCodeReader reader = new BarCodeReader("roi_canvas.png", areas, DecodeType.TYPES_1D);
BarCodeResult[] results = reader.readBarCodes();
```
