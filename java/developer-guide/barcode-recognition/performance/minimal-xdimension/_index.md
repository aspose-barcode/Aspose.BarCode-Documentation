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

## What problem it solves

During detection, the engine tries to separate real barcode modules from noise and texture.
If your images contain a lot of small details, the reader may spend CPU time checking tiny candidates that cannot be a real barcode in your scenario.

`MinimalXDimension` is a lower bound for the expected module width (in pixels).
When you set it, the engine can skip searching for barcode patterns that are smaller than this value, which usually reduces CPU cost.

## Trade-offs and risks

This setting is a performance hint. It does not automatically improve recognition quality.

- If you set `MinimalXDimension` too low, you will not gain much performance because the engine still needs to evaluate small noise.
- If you set `MinimalXDimension` too high, real barcodes with smaller modules may not be detected at all.

## When to use it

Use `USE_MINIMAL_X_DIMENSION` when you have a predictable camera or scanner setup and you know that barcodes are never smaller than a certain module size.
If barcode size varies a lot, prefer ROI and type filtering first, and keep `MinimalXDimension` conservative.

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

## Related topics

- If you need a faster baseline: see [High performance mode](../high-performance-mode).
- If you need tuning for hard inputs: see [Damaged or low resolution barcodes](../damaged-low-resolution-barcodes).
- If presets are not enough: see [Advanced tuning](../advanced-tuning).
