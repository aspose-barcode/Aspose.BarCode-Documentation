---
title: "Recognition Presets"
description: "Learn how to use recognition presets"
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/performance/recognition-presets
---

# Recognition presets

Aspose.BarCode for Java provides several **recognition presets** through `QualitySettings`.  
These presets bundle multiple internal options (deconvolution, noise filters, search depth, etc.) to give you a convenient **speed vs robustness** trade-off:

- `QualitySettings.getHighPerformance()` – favor speed on clean, high-quality images.
- `QualitySettings.getHighQuality()` – enable additional recovery methods for degraded barcodes.
- `QualitySettings.getMaxQuality()` – use the most exhaustive, slowest analysis for the toughest cases.

This article demonstrates how to apply these presets in practice based on the example class:

`com.aspose.barcode.guide.recognition.performance.RecognitionPresets`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/RecognitionPresets.java" target="_blank" rel="noopener noreferrer">RecognitionPresets.java</a>

All snippets below assume that helper methods such as `ExampleAssist.checkOrCreateImage(...)` and `ExampleAssist.assertRecognized(...)` are available in your project.

---

## 1. Test data: clean vs degraded Code 128

The example class uses two types of barcode images:

- **Clean Code 128** – simple, high-contrast symbol generated at a comfortable size.
- **Blurred + noisy Code 128** – the same payload rendered larger and then degraded with blur and salt-and-pepper noise.

The clean image is generated as follows:

```java
private void generateCode128Clean(String fullPath) throws IOException {
    BarcodeGenerator barcodeGenerator = new BarcodeGenerator(EncodeTypes.CODE_128, "SPEED-QUALITY-DEMO");
    barcodeGenerator.getParameters().getBarcode().getXDimension().setPixels(2);
    barcodeGenerator.getParameters().getBarcode().getBarHeight().setPixels(60);
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
}
```

The degraded variant uses a custom blur + noise pipeline (simplified):

```java
private void generateCode128BlurredNoisy(String fullPath) throws IOException {
    // 1) Render a larger, high-quality Code 128
    String hi = fullPath + ".hi.png";
    BarcodeGenerator barcodeGenerator = new BarcodeGenerator(EncodeTypes.CODE_128, "ROBUSTNESS-CHECK-123");
    barcodeGenerator.getParameters().getBarcode().getXDimension().setPixels(6);   // 3 * scale
    barcodeGenerator.getParameters().getBarcode().getBarHeight().setPixels(140);  // 70 * scale
    // ... configure generous quiet zones ...
    barcodeGenerator.save(hi, BarCodeImageFormat.PNG);

    // 2) Apply a light 3×3 box blur and salt & pepper noise
    BufferedImage src = ImageIO.read(Paths.get(hi).toFile());
    BufferedImage blurred = boxBlur(src);
    addSaltPepperNoise(blurred, 0.004);

    // 3) Downscale back to target size (bilinear interpolation)
    //    and save the final degraded image
    // ...
}
```

You do not need to replicate this degradation logic in your application; it is only used to produce deterministic test fixtures for comparing presets.

---

## 2. HighPerformance on clean barcodes

Use `HighPerformance` when:

- you expect **clean, high-quality barcodes** (for example, generated labels),
- you want to prioritize **throughput** and low CPU usage,
- occasional difficult edge cases can be handled separately with more robust settings.

Example: fast recognition of a clean Code 128 symbol.

```java
String fileName = "code128_clean.png";

ExampleAssist.checkOrCreateImage(IMAGES_FOLDER, fileName, this::generateCode128Clean);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
BarCodeReader barCodeReader = new BarCodeReader(
        Paths.get(IMAGES_FOLDER, fileName).toString(),
        DecodeType.CODE_128
);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.CODE_128);
```

Key points:

- Start from `QualitySettings.getHighPerformance()`.
- Pass this instance into `barCodeReader.setQualitySettings(...)` before calling `readBarCodes()` or helper methods.
- On clean input, this preset should decode quickly while using fewer resources.

---

## 3. MaxQuality on clean images (thorough analysis)

`MaxQuality` enables the most exhaustive set of recognition procedures.  
Even though it is **not required** for clean images, running it on the same test input helps illustrate the trade-off: **higher robustness potential vs longer processing time**.

Example: using `MaxQuality` on a similar clean Code 128 image.

```java
String fileName = "code128_max_quality.png";

ExampleAssist.checkOrCreateImage(IMAGES_FOLDER, fileName, this::generateCode128Clean);

QualitySettings qualitySettings = QualitySettings.getMaxQuality();
BarCodeReader barCodeReader = new BarCodeReader(
        Paths.get(IMAGES_FOLDER, fileName).toString(),
        DecodeType.CODE_128
);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.CODE_128);
```

Recommendations:

- Reserve `MaxQuality` for **challenging inputs** (poor lighting, severe distortions, difficult backgrounds).
- For normal production flow, prefer `NormalQuality` or `HighQuality` and use `MaxQuality` in a fallback path or for re-processing.

---

## 4. HighQuality on blurred and noisy barcodes

`HighQuality` presets are targeted at **degraded images**: slight blur, noise, or poor contrast.  
In the example, a Code 128 image is blurred, sprinkled with salt-and-pepper noise, and then downscaled. The `HighQuality` preset is used to recover it.

```java
String fileName = "code128_blur_noise.png";

ExampleAssist.checkOrCreateImage(IMAGES_FOLDER, fileName, this::generateCode128BlurredNoisy);

QualitySettings qualitySettings = QualitySettings.getHighQuality();
BarCodeReader barCodeReader = new BarCodeReader(
        Paths.get(IMAGES_FOLDER, fileName).toString(),
        DecodeType.CODE_128
);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.CODE_128);
```

Why `HighQuality` helps on damaged inputs:

- it may enable more aggressive **deconvolution** and noise suppression,
- it increases the search space for potential barcode candidates,
- it can apply additional robustness filters that would be too expensive for realtime-only scenarios.

Use this preset when you cannot fully control input quality (for example, mobile cameras or scanned documents).

---

## 5. Measuring speed vs quality trade-off

The example class also contains a method that compares elapsed time for `HighPerformance` vs `MaxQuality` on the **same image**.  
This test does not enforce any strict timing; it only prints measured values so you can estimate the relative cost.

```java
String fileName = "compare_timing_high_quality.png";

ExampleAssist.checkOrCreateImage(IMAGES_FOLDER, fileName, this::generateCode128Clean);

// HighPerformance timing
BarCodeReader fastReader = new BarCodeReader(path(fileName), DecodeType.CODE_128);
fastReader.setQualitySettings(QualitySettings.getHighPerformance());
long t1 = System.nanoTime();
ExampleAssist.assertRecognized(fastReader, "HighPerformance timing", 1, DecodeType.CODE_128);
long fastMs = (System.nanoTime() - t1) / 1_000_000L;

// MaxQuality timing
BarCodeReader thoroughReader = new BarCodeReader(path(fileName), DecodeType.CODE_128);
thoroughReader.setQualitySettings(QualitySettings.getMaxQuality());
long t2 = System.nanoTime();
ExampleAssist.assertRecognized(thoroughReader, "MaxQuality timing", 1, DecodeType.CODE_128);
long thoroughMs = (System.nanoTime() - t2) / 1_000_000L;

System.out.println(
        "[Speed vs Quality] HighPerformance: " + fastMs + " ms; MaxQuality: " + thoroughMs + " ms"
);
```

How to use such measurements in your project:

- Run similar tests on **your own sample set** (typical resolutions, camera devices, printers).
- Log both recognition time and success rate (how many barcodes fail to decode).
- Choose a preset (or combination of presets) that satisfies your **latency budget** while keeping failure rate acceptable.

---

## 6. Practical recommendations

When configuring recognition in a real application, a common strategy is:

1. **Start fast**  
   Use `HighPerformance` or `NormalQuality` for the first pass on incoming frames or images.

2. **Fallback on failure**  
   If no barcodes are recognized (or confidence is too low), re-run recognition on the same image with a more robust preset such as `HighQuality` or `MaxQuality`.

3. **Tune per scenario**
    - For **scanned documents** or images captured in controlled conditions, `NormalQuality` or `HighPerformance` is often enough.
    - For **mobile camera input** (low light, perspective distortions, motion blur), consider `HighQuality` or a dedicated slow path for re-processing.

4. **Measure and iterate**  
   Use tests similar to `compareTimingHighPerformanceVsMaxQuality()` to collect timing statistics and make data-driven decisions about presets.

All examples in this article are based on:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/RecognitionPresets.java" target="_blank" rel="noopener noreferrer">RecognitionPresets.java</a>

Use them as a template for integrating recognition presets into your own Java applications.
