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
