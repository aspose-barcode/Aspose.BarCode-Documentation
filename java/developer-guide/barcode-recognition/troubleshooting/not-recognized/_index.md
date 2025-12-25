---
title: My Barcode is Not Found
description: "Steps to take when BarCodeReader returns no results."
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/troubleshooting/not-recognized
---

# My Barcode is Not Found

If `readBarCodes()` returns an empty array, it means the engine could not detect or decode the barcode with the current settings.
Follow this checklist to fix the issue.

## 1. Verify the input image
- Is the barcode visible to the human eye?
- Is the image resolution sufficient? (Aim for at least 200 DPI).
- Is the barcode too close to the edge? (Add a whitespace margin if possible).

## 2. Switch to a more robust preset
The default settings balance speed and quality, but may fail on difficult images.
Try `HighQuality` or `MaxQuality` to enable more expensive recognition algorithms.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;

BarCodeReader reader = new BarCodeReader("input.png", DecodeType.CODE_128);
reader.setQualitySettings(QualitySettings.getHighQuality());

BarCodeResult[] results = reader.readBarCodes();
```

## 3. Check for color inversion (White on Black)
If your barcode is light on a dark background, you must enable `InverseImageMode`.

```java
import com.aspose.barcode.barcoderecognition.InverseImageMode;

// ...
reader.getQualitySettings().setInverseImage(InverseImageMode.ENABLED);
```

## 4. Narrow the symbology set
Searching for `ALL_SUPPORTED_TYPES` on a noisy image can be problematic.
Always specify the exact type if you know it (e.g. `DecodeType.CODE_128`).

## 5. Use ROI (Region of Interest)
If the image is very large (e.g. A4 document at 600 DPI), the barcode might be relatively small.
Restricting the search area helps the engine focus.

```java
import java.awt.Rectangle;

Rectangle roi = new Rectangle(100, 100, 300, 200);
BarCodeReader reader = new BarCodeReader("large_image.png", roi, DecodeType.CODE_128);
```
