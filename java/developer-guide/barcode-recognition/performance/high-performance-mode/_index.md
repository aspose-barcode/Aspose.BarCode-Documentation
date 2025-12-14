---
title: High Performance Mode
description: "How to maximize recognition throughput using QualitySettings.getHighPerformance()."
type: docs
weight: 20
url: /java/developer-guide/barcode-recognition/performance/high-performance-mode
---

# High Performance Mode

High performance mode is based on `QualitySettings.getHighPerformance()`.
Use it when inputs are clean and you want the fastest recognition.

## Enable High Performance mode

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;

BarCodeReader barCodeReader = new BarCodeReader("qr_hp.png", DecodeType.QR);
barCodeReader.setQualitySettings(QualitySettings.getHighPerformance());
```

## Combine with type filtering for extra speed

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;

String imagePath = "limited_types_hp.png";

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.ALL_SUPPORTED_TYPES);

barCodeReader.setQualitySettings(QualitySettings.getHighPerformance());

barCodeReader.setBarCodeReadType(
        DecodeType.CODE_128,
        DecodeType.QR,
        DecodeType.DATA_MATRIX
);
```

## Use 1D or 2D groups when you do not know the exact type

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;

String imagePath = "types_1d_hp.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.TYPES_1D);
barCodeReader.setQualitySettings(QualitySettings.getHighPerformance());
```
