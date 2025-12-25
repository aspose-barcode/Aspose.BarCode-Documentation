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

## When to use it

High performance mode is a good default for:

- server-side batch processing with consistent image quality
- scanned documents where barcodes are sharp and have enough resolution
- real-time pipelines where latency matters and inputs are controlled

If recognition becomes unstable on blurred, low-resolution, or damaged images, switch to a higher quality preset or enable targeted options. See [High quality mode](../high-quality-mode) and [Damaged or low resolution barcodes](../damaged-low-resolution-barcodes).

## What it changes

This preset prioritizes speed over robustness.
It can reduce the chance of recognizing barcodes in difficult conditions.
To keep results stable, combine it with type filtering and ROI when possible.

## Enable High Performance mode

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;

BarCodeReader barCodeReader = new BarCodeReader("qr_hp.png", DecodeType.QR);
barCodeReader.setQualitySettings(QualitySettings.getHighPerformance());
```

## Combine with type filtering for extra speed

Restricting the possible symbologies is often the biggest performance improvement.

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

## Related topics

- If you need an overview of presets: see [Recognition presets](../recognition-presets).
- If you need higher robustness: see [High quality mode](../high-quality-mode).
- If you need throughput across many images: see [Multithread barcode reading](../multithread-barcode-reading).
- If you can limit the scan area: see [Use ROI](../../basic-recognition-setup/use-roi).
- If presets are not enough: see [Advanced tuning](../advanced-tuning).
