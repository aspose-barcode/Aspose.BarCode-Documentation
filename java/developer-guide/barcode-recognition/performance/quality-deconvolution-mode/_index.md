---
title: Using BarcodeQuality and DeconvolutionMode
description: "How to tune recognition for noisy and blurred images using BarcodeQualityMode and DeconvolutionMode."
type: docs
weight: 50
url: /java/developer-guide/barcode-recognition/performance/quality-deconvolution-mode
---

# Using BarcodeQuality and DeconvolutionMode

When input images are noisy or blurred, presets alone may not be enough.
You can tune recognition using:

- `BarcodeQualityMode` to describe expected barcode quality.
- `DeconvolutionMode` to control blur compensation strength.

Both options are set on a `QualitySettings` instance and then applied to `BarCodeReader`.

## When to use BarcodeQualityMode

Use `BarcodeQualityMode` when the barcode itself is degraded, for example when modules are damaged, noisy, or partially missing.
This setting tells the engine what quality level it should expect from the barcode image.

Start with your preset (`HighPerformance` or `HighQuality`), then set `BarcodeQualityMode` only when you see unstable results on similar inputs.

## When to use DeconvolutionMode

Use `DeconvolutionMode` when the image is blurred, for example due to camera motion, out-of-focus capture, or aggressive resizing.
Deconvolution tries to compensate blur, which may improve detection and decoding.

## Trade-offs

These options usually increase CPU cost compared to a preset alone.
Deconvolution can also make clean images slower without improving results.

If you process mixed inputs, it is often better to use a fallback strategy: start fast and apply these options only when the first pass returns no results.

## Example: noisy barcode with BarcodeQualityMode

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;
import com.aspose.barcode.barcoderecognition.BarcodeQualityMode;

String imagePath = "code128_noisy.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighQuality();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);

barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] results = barCodeReader.readBarCodes();
```

## Example: blurred barcode with DeconvolutionMode

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;
import com.aspose.barcode.barcoderecognition.DeconvolutionMode;

String imagePath = "qr_blurred_mild.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);

QualitySettings qualitySettings = QualitySettings.getHighQuality();
qualitySettings.setDeconvolution(DeconvolutionMode.SLOW);

barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] results = barCodeReader.readBarCodes();
```

## Example: fast first pass, then enable deconvolution

This pattern keeps the average latency low while still supporting blurred images.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;
import com.aspose.barcode.barcoderecognition.DeconvolutionMode;

String imagePath = "qr_blurred_mild.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.QR);
reader.setQualitySettings(QualitySettings.getHighPerformance());

BarCodeResult[] results = reader.readBarCodes();
if (results.length == 0) {
    QualitySettings retry = QualitySettings.getHighQuality();
    retry.setDeconvolution(DeconvolutionMode.SLOW);
    reader.setQualitySettings(retry);
    results = reader.readBarCodes();
}
```

## Related topics

- If you need an overview of presets: see [Recognition presets](../recognition-presets).
- If you need robust recognition as a baseline: see [High quality mode](../high-quality-mode).
- If images are damaged or very small: see [Damaged or low resolution barcodes](../damaged-low-resolution-barcodes) and [Using UseMinimalXDimension](../minimal-xdimension).
- If barcodes have inverted colors: see [Reading color inverted barcodes](../reading-color-inverted).
- If you need targeted overrides beyond presets: see [Advanced tuning](../advanced-tuning).
