---
title: Performance & Quality
description: "How to balance speed and recognition robustness using QualitySettings and related options."
type: docs
weight: 30
url: /java/developer-guide/barcode-recognition/performance
---

# Performance & Quality

Barcode recognition always has a trade-off between speed and robustness.
In Aspose.BarCode for Java, most tuning is done through `QualitySettings` and a small set of related parameters.

## Practical tuning order

1. Limit recognition symbologies with `DecodeType`.
2. Use ROI when the barcode location is known.
3. Choose a recognition preset (`HighPerformance`, `NormalQuality`, `HighQuality`, `MaxQuality`).
4. Add targeted overrides only for specific problems, such as blur, low resolution, or inverted colors.

## Example: start fast, then fallback to higher quality

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;

String imagePath = "difficult_barcode.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.CODE_128);
reader.setQualitySettings(QualitySettings.getHighPerformance());

BarCodeResult[] results = reader.readBarCodes();
if (results.length == 0) {
    reader.setQualitySettings(QualitySettings.getHighQuality());
    results = reader.readBarCodes();
}
```
