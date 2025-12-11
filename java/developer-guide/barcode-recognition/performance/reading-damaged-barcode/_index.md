---
title: "Reading Damaged Barcode"
description: "Learn how to read damaged barcode"
type: docs
weight: 60
url: /java/developer-guide/barcode-recognition/performance/reading-damaged-barcode
---

# Reading damaged barcodes

Real-world barcodes are rarely perfect. Photos from mobile devices, low-quality printers, scanners with dust or scratches — all of this can introduce **noise**, **blur**, and other distortions that make recognition harder.

Aspose.BarCode for Java provides several tuning knobs under `QualitySettings` that help you keep recognition robust even when the image is degraded:

- `BarcodeQualityMode` — how aggressive the recognition pipeline should be
- `DeconvolutionMode` — how strong blur compensation should be
- `XDimensionMode` and `setMinimalXDimension` — hints about expected bar/module size

This article is based on the sample class:

`com.aspose.barcode.guide.recognition.performance.ReadingDamagedBarcodeExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/ReadingDamagedBarcodeExample.java" target="_blank" rel="noopener noreferrer">ReadingDamagedBarcodeExample.java</a>

In the snippets below, helper methods like `ExampleAssist.checkOrCreateImage` are used only to generate test images in the sample project. In your application you can replace them with your own file I/O.

---

## 1. Clean vs damaged test images

The example class operates on a small set of baseline (clean) images and corresponding damaged variants:

- **Clean images**
    - `code128_clean.png` — clean Code 128 barcode
    - `qr_clean.png` — clean QR code with slightly thicker modules

- **Damaged images**
    - `code128_noisy.png` — Code 128 with added noise (simulates low SNR)
    - `qr_blurred_mild.png` — mildly blurred QR (recoverable with stronger settings)
    - `qr_blurred_heavy.png` — heavily blurred + slightly noisy QR (too degraded for FAST mode)

These fixtures allow you to **compare recognition behavior** under different `QualitySettings` configurations for the same logical barcode data.

---

## 2. Handling noise on Code 128 with `BarcodeQualityMode`

### 2.1 Noisy Code 128 with `BarcodeQualityMode.LOW`

The method `read_Code128_Noisy_WithBarcodeQuality_LOW` demonstrates how to recognize a noisy Code 128 barcode by switching to a more robust quality profile.

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "code128_noisy.png");

// Reader is restricted to Code 128
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

// Start from a robust preset
QualitySettings qualitySettings = QualitySettings.getHighQuality();

// Enable heavy methods for low-quality / noisy bars
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);

// Apply settings to the reader
barCodeReader.setQualitySettings(qualitySettings);

// Validate that Code 128 is recognized
ExampleAssist.assertRecognized(
        barCodeReader,
        "code128_noisy.png",
        1,
        DecodeType.CODE_128
);
```

Key ideas:

- `QualitySettings.getHighQuality()` enables a more thorough recognition pipeline.
- `BarcodeQualityMode.LOW` turns on additional heavy methods for **very noisy / low-contrast** barcodes.
- This combination is appropriate when latency is less important than robustness.

### 2.2 Tuning for tiny or weak modules with `XDimensionMode`

The method `read_Code128_Noisy_TinyModules_Tuned` shows how to hint that bars may be very small by using `XDimensionMode` and `setMinimalXDimension`.

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "code128_noisy.png");

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

// Start from a performance-oriented preset
QualitySettings qualitySettings = QualitySettings.getHighPerformance();

// Hint that bars can be very small
qualitySettings.setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION);
qualitySettings.setMinimalXDimension(1.0f);

// Still use LOW quality for noisy / weak bars
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);

barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(
        barCodeReader,
        "code128_noisy.png",
        1,
        DecodeType.CODE_128
);
```

What this configuration does:

- `setMinimalXDimension(1.0f)` expresses that you expect bar width to be as small as **1 pixel**.
- `BarcodeQualityMode.LOW` again enables heavier processing to help with noise.

This combination is useful for:

- **Low-resolution images** (for example, thumbnails, webcam captures)
- **Screenshots** where barcodes are very small
- Any scenario where bars are thin and signal-to-noise ratio is low

---

## 3. Recovering blurred QR codes with `DeconvolutionMode`

Blur (motion or out-of-focus) is a common failure mode for mobile captures. Aspose.BarCode exposes a blur compensation pipeline through `DeconvolutionMode`:

- `FAST` — light, speed-first restoration
- `NORMAL` — balanced
- `SLOW` — strongest blur compensation, but also the slowest

### 3.1 Mild blur + `DeconvolutionMode.SLOW` (positive case)

The method `read_QR_BlurredMild_WithDeconvolution_SLOW` demonstrates how to restore a mildly blurred QR code.

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "qr_blurred_mild.png");

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);

// Start from HighQuality preset
QualitySettings qualitySettings = QualitySettings.getHighQuality();

// Enable strongest deconvolution for blur
qualitySettings.setDeconvolution(DeconvolutionMode.SLOW);

// Hint that modules can be small if needed
qualitySettings.setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION);
qualitySettings.setMinimalXDimension(1.0f);

barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(
        barCodeReader,
        "qr_blurred_mild.png",
        1,
        DecodeType.QR
);
```

Why this works:

- `DeconvolutionMode.SLOW` enables the strongest blur-compensation pipeline, suitable for **mild to moderate blur**.
- The X-dimension hints help when blur slightly reduces contrast and apparent module size.
- This configuration trades **performance** for **maximum robustness**.

Use it when:

- You receive images with clear blur from camera motion or focus issues.
- Missing a barcode is worse than spending extra CPU time per frame.

### 3.2 Heavy blur + `DeconvolutionMode.FAST` (negative case)

The method `read_QR_BlurredHeavy_WithDeconvolution_FAST_Negative` is intentionally a **negative test**.  
It shows that using a lightweight deconvolution profile on a heavily blurred image can result in zero recognized barcodes.

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "qr_blurred_heavy.png");

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);

// Use performance preset with light deconvolution
QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setDeconvolution(DeconvolutionMode.FAST);
barCodeReader.setQualitySettings(qualitySettings);

// Expectation: image is too blurred for FAST profile → no results
ExampleAssist.assertNotRecognized(
        barCodeReader,
        "qr_blurred_heavy.png"
);
```

Takeaways:

- `DeconvolutionMode.FAST` is ideal for **slightly blurred or sharp images** where performance is critical.
- For **heavily blurred** barcodes, FAST may not be sufficient — you should switch to `NORMAL` or `SLOW`.
---

## 4. Practical guidelines

When working with damaged barcodes (noise, blur, small modules), consider the following patterns:

1. **Start from a preset that matches your typical quality**
    - `QualitySettings.getHighPerformance()` for speed-first scenarios with mostly clean images.
    - `QualitySettings.getNormalQuality()` when you want balanced speed and robustness.
    - `QualitySettings.getHighQuality()` when you expect many difficult images.

2. **Use `BarcodeQualityMode` for noise and contrast issues**
    - Use `BarcodeQualityMode.LOW` when bars are noisy, low-contrast or partially degraded.
    - Use `BarcodeQualityMode.NORMAL` for regular images.
    - Use `BarcodeQualityMode.HIGH` when you care about speed and inputs are high-quality.

3. **Use `DeconvolutionMode` for blur**
    - `DeconvolutionMode.FAST` — high-quality or slightly blurred images.
    - `DeconvolutionMode.NORMAL` — mild blur from typical camera motion.
    - `DeconvolutionMode.SLOW` — heavily blurred or difficult captures.

4. **Hint expected bar/module size with X-dimension settings**
    - `setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION)` and `setMinimalXDimension(...)` help for **tiny barcodes**.
    - Do not set `MinimalXDimension` too small if your images are not tiny — it may slow recognition.
---

## Summary

The `ReadingDamagedBarcodeExample` class shows how to combine `QualitySettings` options to handle various kinds of degradation:

- **Noise** on 1D Code 128:
    - Use `BarcodeQualityMode.LOW` with a robust preset.
    - Combine with X-dimension hints for tiny or weak bars.

- **Blur** on QR codes:
    - Use `DeconvolutionMode.SLOW` together with `QualitySettings.getHighQuality()` and X-dimension hints for mildly blurred images.
    - Understand that `DeconvolutionMode.FAST` is not sufficient for heavily blurred images — expect failures and fall back to SLOW when needed.

All examples in this article are based on:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/ReadingDamagedBarcodeExample.java" target="_blank" rel="noopener noreferrer">ReadingDamagedBarcodeExample.java</a>

Use these patterns as a starting point when tuning Aspose.BarCode for Java to your own damaged or low-quality barcode images.

---

**Note – how the example generates damaged fixtures**

In the sample project, damaged images are generated from clean barcodes by applying synthetic degradations.  
This helps to demonstrate how `QualitySettings` behave on the same logical data under different distortion levels.

Typical helper methods used in the example class include:

- `ExampleAssist.addGaussianNoise(inputPath, outputPath, stdDev)` — adds noise to simulate low signal-to-noise ratio.
- `ExampleAssist.blur(inputPath, outputPath, sigma)` — applies blur to simulate motion or out-of-focus captures.

You can use a similar approach in your own test suite:

1. Generate a clean barcode with `BarcodeGenerator`.
2. Save it as an image.
3. Produce noisy or blurred copies using your own image-processing pipeline.
4. Run the same recognition configuration on clean vs damaged variants and compare the results.

This is purely a **test fixture technique** and is not required to use `BarcodeQualityMode`, `DeconvolutionMode`, or X-dimension settings in production.
