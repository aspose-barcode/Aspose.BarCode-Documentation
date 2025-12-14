---
title: Using UseMinimalXDimension
description: "How to use XDimensionMode.USE_MINIMAL_X_DIMENSION and MinimalXDimension for very small modules."
type: docs
weight: 40
url: /java/developer-guide/barcode-recognition/performance/minimal-xdimension
---

# Using UseMinimalXDimension

When barcodes are very small, bars or modules can be 1–2 pixels wide.
In such cases you can provide a hint about the minimal expected module size using:

- `QualitySettings.setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION)`
- `QualitySettings.setMinimalXDimension(float minimalXDimension)`

`MinimalXDimension` is taken into account only when `XDimensionMode` is `USE_MINIMAL_X_DIMENSION`.

## Example

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;
import com.aspose.barcode.barcoderecognition.XDimensionMode;

String imagePath = "code128_small.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighQuality();
qualitySettings.setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION);
qualitySettings.setMinimalXDimension(1.0f);

barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] results = barCodeReader.readBarCodes();
```
