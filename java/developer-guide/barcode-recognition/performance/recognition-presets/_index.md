---
title: "Recognition Presets (Speed vs Quality)"
description: "How to use QualitySettings presets to trade speed for robustness."
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/performance/recognition-presets
---

# Recognition Presets (Speed vs Quality)

Aspose.BarCode for Java provides recognition presets through `QualitySettings`.
Each preset bundles internal options and is designed for a typical speed versus robustness profile.

## Presets overview

- `QualitySettings.getHighPerformance()` for clean, predictable images.
- `QualitySettings.getNormalQuality()` for balanced behavior.
- `QualitySettings.getHighQuality()` for noisy or degraded images.
- `QualitySettings.getMaxQuality()` for the hardest cases, with higher CPU cost.

## Example: apply a preset

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;

BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.CODE_128);
reader.setQualitySettings(QualitySettings.getHighPerformance());

BarCodeResult[] results = reader.readBarCodes();
```

## Example: compare presets on the same input

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;

String imagePath = "barcode.png";

BarCodeReader fastReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
fastReader.setQualitySettings(QualitySettings.getHighPerformance());
BarCodeResult[] fastResults = fastReader.readBarCodes();

BarCodeReader thoroughReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
thoroughReader.setQualitySettings(QualitySettings.getMaxQuality());
BarCodeResult[] thoroughResults = thoroughReader.readBarCodes();
```
