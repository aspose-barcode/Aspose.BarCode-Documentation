---
title: "Barcode Quality Mode"
description: "Learn how to control recognition robustness and speed using BarcodeQualityMode in Aspose.BarCode for Java."
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/performance/quality-mode
---

# Barcode Quality Mode

`BarcodeQualityMode` in Aspose.BarCode for Java controls how much effort the recognition engine spends on analyzing barcode quality:

- higher modes enable more advanced processing and are more tolerant to noise and distortions
- lower modes favor speed and are best suited for clean, high-contrast images

`BarcodeQualityMode` is always used together with a `QualitySettings` preset (for example, `getHighPerformance`, `getNormalQuality`, `getHighQuality`).  
You can start from a preset and then override the quality mode to fine-tune behavior.

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.performance.BarcodeQualityModeExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/BarcodeQualityModeExample.java" target="_blank" rel="noopener noreferrer">BarcodeQualityModeExample.java</a>

In the snippets below, variables like `imagePath` represent paths to barcode images in your application.

---

## 1. Test Data: Clean and Noisy Code 128

To demonstrate `BarcodeQualityMode`, the example class uses two fixtures:

- `code128_clean.png` – a clean synthetic `CODE_128` image with good contrast
- `code128_noisy.png` – the same symbol degraded with Gaussian noise to simulate low signal-to-noise ratio

In production, you do not need to generate fixtures manually. The important idea is that you should evaluate quality modes both on **clean** and **difficult** images to find the right balance between speed and robustness for your scenario.

---

## 2. Using BarcodeQualityMode on Clean Images

On clean barcodes, all three quality modes are expected to read the symbol reliably.  
The main difference is the internal amount of processing and, as a result, performance.

### 2.1. High quality mode (more robust, more work)

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("HIGH: " + barCodeResult.getCodeText());
}
```

Here:

- `QualitySettings.getHighPerformance()` is used as a fast preset.
- `setBarcodeQuality(BarcodeQualityMode.HIGH)` tells the engine to apply a more robust quality profile on top of that preset.
- For a clean image, this will still be fast and reliably recognize the barcode.

### 2.2. Normal quality mode (balanced default)

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getNormalQuality();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.NORMAL);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("NORMAL: " + barCodeResult.getCodeText());
}
```

Typical use cases:

- back-office systems processing documents scanned with predictable quality
- services where performance and robustness are equally important

### 2.3. Low quality mode (minimal processing, fastest)

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighQuality();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("LOW: " + barCodeResult.getCodeText());
}
```

Even with `BarcodeQualityMode.LOW`, a clean `CODE_128` image is usually recognized without problems.  
This mode is helpful when:

- input quality is controlled and consistently good
- you want to reduce processing overhead as much as possible

---

## 3. Quality Mode on Noisy Images

With noisy or degraded images, the choice of quality mode matters much more.  
Higher modes typically enable stronger denoising and more advanced checks, which can rescue barcodes that would fail under lower modes.

### 3.1. Noisy image with HIGH quality mode

```java
String imagePath = "code128_noisy.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("Noisy, HIGH quality: " + barCodeResult.getCodeText());
}
```

Use this pattern when:

- your application receives images from mobile cameras or low-quality scanners
- you expect motion blur, noise, or compression artifacts
- you want to maximize the chance of successful recognition on difficult inputs

### 3.2. Noisy image with LOW quality mode

```java
String imagePath = "code128_noisy.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighQuality();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
System.out.println("Noisy, LOW quality: results=" + barCodeResults.length);
```

This configuration illustrates that lowering the quality mode on degraded images may reduce robustness.  
It is useful as a contrast case when tuning your pipeline:

- if `HIGH` reads the noisy barcode but `LOW` does not, you know that the image is close to the quality limit
- this helps you decide whether you can afford to stay at a lower quality mode or should raise it in production

---

## 4. Combining Presets with Targeted Overrides

The real power of `QualitySettings` comes from **combining** a preset with **targeted overrides**.  
For example, you can bias the detector towards small bar widths while still using a performance-oriented preset and a lower quality mode.

Example: clean `CODE_128` with small modules and low quality mode.

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setXDimension(XDimensionMode.SMALL);
qualitySettings.setMinimalXDimension(1.0f);
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("Preset + overrides: " + barCodeResult.getCodeText());
}
```

Here:

- `getHighPerformance()` provides a fast base configuration
- `setXDimension(XDimensionMode.SMALL)` and `setMinimalXDimension(1.0f)` tell the engine to expect small bar widths
- `setBarcodeQuality(BarcodeQualityMode.LOW)` keeps the quality mode low to reduce cost, but the geometric hints ensure the detector still performs well on this particular class of images

This pattern is useful when you:

- know something about the typical module size or print resolution in advance
- need to support specific devices (for example, a fixed-resolution camera or scanner)
- want to stay close to performance presets while still being precise about barcode geometry

---

## 5. Practical Recommendations

When configuring `BarcodeQualityMode` for your application:

- Start with `QualitySettings.getNormalQuality()` and `BarcodeQualityMode.NORMAL` as a baseline.
- Measure recognition speed and success rate on **your** real images (clean and noisy).
- If recognition fails on noisy inputs, try:
    - raising the quality mode (`NORMAL` → `HIGH`)
    - or switching from `getHighPerformance()` to `getHighQuality()` as a base preset
- If recognition is stable and fast enough on clean inputs, experiment with:
    - lowering the quality mode (`HIGH` → `NORMAL` → `LOW`)
    - or switching to a performance preset to reduce CPU usage
- Use targeted overrides like `setXDimension(...)` and `setMinimalXDimension(...)` when you know the expected bar width or symbol size.

All patterns demonstrated here come from:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/BarcodeQualityModeExample.java" target="_blank" rel="noopener noreferrer">BarcodeQualityModeExample.java</a>

Use this class as a reference when tuning recognition quality and performance in your own Java applications.
