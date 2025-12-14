---
title: High Quality Mode
description: "How to improve recognition robustness using QualitySettings.getHighQuality() and getMaxQuality()."
type: docs
weight: 30
url: /java/developer-guide/barcode-recognition/performance/high-quality-mode
---

# High Quality Mode

High quality mode focuses on recognition robustness for noisy, blurred, low-contrast, or otherwise degraded images.
In Aspose.BarCode for Java, this is typically done via:

- `QualitySettings.getHighQuality()`
- `QualitySettings.getMaxQuality()`

## Enable High Quality mode

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;

BarCodeReader reader = new BarCodeReader("difficult_barcode.png", DecodeType.CODE_128);
reader.setQualitySettings(QualitySettings.getHighQuality());

BarCodeResult[] results = reader.readBarCodes();
```

## Use MaxQuality as a fallback

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;

BarCodeReader reader = new BarCodeReader("poor_quality.png", DecodeType.ALL_SUPPORTED_TYPES);
reader.setQualitySettings(QualitySettings.getMaxQuality());

for (BarCodeResult result : reader.readBarCodes()) {
    System.out.println("Type: " + result.getCodeTypeName());
    System.out.println("Text: " + result.getCodeText());
}
```
