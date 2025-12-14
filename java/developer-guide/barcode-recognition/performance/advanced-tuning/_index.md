---
title: Advanced Tuning (SvmDetector, ScanGap)
description: "How to fine-tune the recognition engine using BarcodeSvmDetectorSettings and AllowDetectScanGap."
type: docs
weight: 90
url: /java/developer-guide/barcode-recognition/performance/advanced-tuning
---

# Advanced Tuning (SvmDetector, ScanGap)

For most cases, the standard [Performance Presets](../recognition-presets/) are sufficient.
However, if you need granular control over the detection algorithms, you can adjust `BarcodeSvmDetectorSettings` and the scan gap.

## BarcodeSvmDetectorSettings

The `BarcodeSvmDetectorSettings` controls the sensitivity of the barcode region detector.
It determines how aggressively the engine searches for potential barcode candidates in the image.

Available modes:
- `HighPerformance`: Fastest detection, but might miss barcodes in complex or noisy images.
- `NormalQuality`: Balanced approach (default).
- `HighQuality`: More thorough search.
- `MaxQuality`: Most exhaustive search, capable of finding barcodes in very cluttered images, but significantly slower.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.BarcodeSvmDetectorSettings;

String imagePath = "complex_background.png";
BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.CODE_128);

// Use MaxQuality detector for difficult images
reader.getQualitySettings().setDetectorSettings(BarcodeSvmDetectorSettings.getMaxQuality());

// Or use HighPerformance for speed on clean images
// reader.getQualitySettings().setDetectorSettings(BarcodeSvmDetectorSettings.getHighPerformance());

reader.readBarCodes();
```

## Scan Gap (AllowDetectScanGap)

For large 1D barcodes and some 2D types (like PDF417, QR), the engine can speed up detection by scanning with a gap (skipping lines), rather than checking every single pixel line.

- **Enable (`true`)**: Increases speed for large barcodes.
- **Disable (`false`)**: Required if you have very small barcodes or mixed sizes where small codes might fall into the gap.

> **Warning:** Enabling this on images with small barcodes may cause them to be missed.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;

String imagePath = "large_barcode.png";
BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.PDF_417);

// Enable scan gap to speed up reading of large barcodes
reader.getQualitySettings().setAllowDetectScanGap(true);

reader.readBarCodes();
```
