---
title: Damaged/Low-Resolution Barcodes
description: "How to handle noise, blur, and very small modules using QualitySettings, BarcodeQualityMode, DeconvolutionMode, and MinimalXDimension."
type: docs
weight: 70
url: /java/developer-guide/barcode-recognition/performance/damaged-low-resolution-barcodes
---

# Damaged/Low-Resolution Barcodes

Some inputs fail because barcodes are damaged (noise, blur, partial occlusion) or because they are very small (low resolution).
This page shows practical patterns to improve recognition in these cases.

> **Note:** For deep technical details on the underlying parameters, see [Using UseMinimalXDimension](../minimal-xdimension/) and [Using BarcodeQuality and DeconvolutionMode](../quality-deconvolution-mode/).

## Noisy 1D barcode (BarcodeQualityMode)

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;
import com.aspose.barcode.barcoderecognition.BarcodeQualityMode;

String imagePath = "../code128_whitespots.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighQuality();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);

barCodeReader.setQualitySettings(qualitySettings);
BarCodeResult[] results = barCodeReader.readBarCodes();
```

![Noisy Code 128 example](../code128_whitespots.png)

## Blurred barcode (DeconvolutionMode)

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;
import com.aspose.barcode.barcoderecognition.DeconvolutionMode;

String imagePath = "../pdf417_qr_corrupted.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);

QualitySettings qualitySettings = QualitySettings.getHighQuality();
qualitySettings.setDeconvolution(DeconvolutionMode.SLOW);

barCodeReader.setQualitySettings(qualitySettings);
BarCodeResult[] results = barCodeReader.readBarCodes();
```

![Degraded 2D example (QR)](../pdf417_qr_corrupted.png)

## Low-resolution barcode (MinimalXDimension)

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;
import com.aspose.barcode.barcoderecognition.BarcodeQualityMode;
import com.aspose.barcode.barcoderecognition.XDimensionMode;

String imagePath = "../code128_big_and_small.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION);
qualitySettings.setMinimalXDimension(1.0f);
qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);

barCodeReader.setQualitySettings(qualitySettings);
BarCodeResult[] results = barCodeReader.readBarCodes();
```

![Small modules example](../code128_big_and_small.png)

## A safe fallback strategy

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;

String imagePath = "../multiple_codes.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.ALL_SUPPORTED_TYPES);
reader.setQualitySettings(QualitySettings.getHighPerformance());

BarCodeResult[] results = reader.readBarCodes();
if (results.length == 0) {
    reader.setQualitySettings(QualitySettings.getHighQuality());
    results = reader.readBarCodes();
}
```
