---
title: "Barcode Quality Mode"
description: "Learn how to describe expected barcode quality with BarcodeQualityMode and combine it with QualitySettings presets in Aspose.BarCode for Java."
type: docs
weight: 50
url: /java/developer-guide/barcode-recognition/performance/quality-mode
---

# Barcode Quality Mode

`BarcodeQualityMode` in Aspose.BarCode for Java describes **how good or bad you expect barcode quality to be** in a given scenario:

- `HIGH` – barcodes are expected to be **high quality** (crisp edges, good contrast, low noise).
- `NORMAL` – barcodes are expected to be of **typical / medium quality** (normal scans, slight imperfections).
- `LOW` – barcodes are expected to be **low quality** (noise, blur, poor contrast), so the engine should be more tolerant.

This enum does **not** directly specify how “powerful” or “expensive” the recognition pipeline is.  
Instead, it works as a **hint** for the recognition engine and is always used **together** with a `QualitySettings` preset.

Typical workflow:

1. Choose a `QualitySettings` preset that defines the **overall recognition strategy** (speed vs robustness).
2. Set `BarcodeQualityMode` to describe the **expected quality of barcodes** in your images.
3. Optionally, add targeted overrides such as `XDimensionMode` and `MinimalXDimension`.

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.performance.QualityModeExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/QualityModeExample.java" target="_blank" rel="noopener noreferrer">QualityModeExample.java</a>

In the snippets below, variables like `imagePath` represent paths to barcode images in your application.

---

## 1. QualitySettings presets vs BarcodeQualityMode

`QualitySettings` presets define **how strong** the recognition pipeline should be in general:

- `QualitySettings.getNormalQuality()` – default, **suitable for most barcodes**.
- `QualitySettings.getHighQuality()` – preset for **low-quality barcodes**, enables more robust processing.
- `QualitySettings.getMaxQuality()` – **maximal robustness**, tries to recognize even very difficult or partially incorrect barcodes.
- `QualitySettings.getHighPerformance()` – **speed-first** preset for clean and predictable inputs.

`BarcodeQualityMode` is applied after selecting a QualitySettings preset and refines how the reader interprets the expected barcode quality level.

- `BarcodeQualityMode.HIGH` – engine expects **high-quality symbols**, can follow the “lightest” path compatible with the preset.
- `BarcodeQualityMode.NORMAL` – engine expects **medium quality**, uses a balanced path within the chosen preset.
- `BarcodeQualityMode.LOW` – engine expects **low-quality / damaged symbols**, uses a more tolerant path within the chosen preset.

In other words:

- **Presets** answer the question: *“How strong should the overall pipeline be for this application?”*
- **BarcodeQualityMode** answers the question: *“What quality of barcodes do I expect in this image?”*

These two knobs are independent and should be tuned **together**.

---

## 2. Using BarcodeQualityMode on clean images

On clean barcodes, you can combine any preset with a suitable `BarcodeQualityMode` value.  
Below are three typical patterns for a high-quality `CODE_128` input.

### 2.1. Clean image, high-quality symbols (HIGH)

Use a **fast preset** and mark barcodes as **high quality**:

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("HIGH (clean): " + barCodeResult.getCodeText());
}
```

Here you explicitly say to the engine:

- “use a **performance** preset”, and
- “current barcodes are **high quality**”.

This pattern is appropriate when:

- barcodes are generated programmatically or printed with predictable good quality,
- scanning is done in a controlled environment,
- and you want maximum throughput.

### 2.2. Clean image, typical quality (NORMAL)

Use a **balanced preset** and mark barcodes as **normal quality**:

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getNormalQuality();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.NORMAL);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("NORMAL (clean): " + barCodeResult.getCodeText());
}
```

Typical use cases:

- back-office systems processing documents scanned under normal conditions,
- services where speed and robustness are equally important,
- systems with stable but not strictly controlled image quality.

### 2.3. Clean image, engine tuned for low-quality symbols (LOW)

You can still use a “robust” preset and explicitly say that barcodes might be **low quality**:

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighQuality(); // preset for low-quality barcodes
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);          // tell engine that barcodes may be low quality
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("LOW (clean): " + barCodeResult.getCodeText());
}
```

This combination is useful when:

- your input pipeline usually contains difficult images (noise, blur, weak contrast),
- a particular subset of images is clean, but you still want the engine tuned for low-quality barcodes,
- you prefer to keep the same configuration across different input sources.

---

## 3. Working with noisy images

With noisy or degraded images, `BarcodeQualityMode` becomes more important.  
Higher presets (`HighQuality`, `MaxQuality`) already target difficult barcodes.  
`BarcodeQualityMode` tells the engine **how bad the current data is expected to be**.

### 3.1. Noisy image with a speed-first preset (HIGH)

In some cases you may still treat a noisy image as “high-quality” if the noise level is controlled and barcodes remain legible:

```java
String imagePath = "code128_noisy.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
System.out.println("Noisy + HighPerformance + HIGH mode: results = " + barCodeResults.length);
```

Use this configuration when:

- noise is moderate and barcodes are still close to high quality,
- you prefer to keep latency as low as possible,
- and some read failures are acceptable.

### 3.2. Noisy image with a robust preset (LOW)

If the image is clearly degraded (strong noise, weak contrast), it is better to use a robust preset and explicitly mark symbols as low quality:

```java
String imagePath = "code128_noisy.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighQuality(); // preset for low-quality barcodes
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);          // engine expects low-quality symbols
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
System.out.println("Noisy + HighQuality + LOW mode: results = " + barCodeResults.length);
```

This pattern is appropriate when:

- images come from mobile cameras or cheap scanners,
- you often see motion blur, compression artifacts, or strong noise,
- and throughput is less important than maximum recognition probability.

---

## 4. Combining presets, BarcodeQualityMode, and X-dimension hints

The real power of `QualitySettings` comes from **combining**:

- a preset (`HighPerformance`, `NormalQuality`, `HighQuality`, `MaxQuality`),
- a `BarcodeQualityMode` value (`HIGH`, `NORMAL`, `LOW`),
- additional overrides such as `XDimensionMode` and `MinimalXDimension`.

Example: clean `CODE_128` with very small modules and a speed-first preset.

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION);
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

- `getHighPerformance()` provides a fast baseline,
- `setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION)` and `setMinimalXDimension(1.0f)` tell the engine that bar widths may be very small,
- `BarcodeQualityMode.LOW` says that barcodes may be low quality (weak / noisy), so the recognition path should be tolerant even though the preset is speed-oriented.

Use this approach when:

- you know something about expected module size (print resolution, target device, etc.),
- you need to support tiny barcodes rendered at the edge of resolution,
- you want to stay close to performance presets but still help the engine with geometry hints.

---

## 5. Practical recommendations

When configuring `BarcodeQualityMode` and `QualitySettings` in a real system:

- Start from a preset that matches your scenario:
    - `getNormalQuality()` for general-purpose applications.
    - `getHighPerformance()` for clean, predictable barcodes and maximum throughput.
    - `getHighQuality()` when barcodes are often low quality or damaged.
    - `getMaxQuality()` when you need the most robust behavior, even for difficult or partially incorrect symbols.
- Set `BarcodeQualityMode` according to expected quality of **current inputs**:
    - `HIGH` – clean synthetic data, good printers, controlled environment.
    - `NORMAL` – ordinary scans, moderate imperfections.
    - `LOW` – noisy/blurred barcodes, poor lighting, low-contrast prints.
- For noisy or degraded images, prefer combinations like:
    - `HighQuality + LOW`,
    - `MaxQuality + LOW`.
- For clean high-throughput scenarios, start from:
    - `HighPerformance + HIGH`,
    - or `NormalQuality + NORMAL` for a balanced profile.
- Combine presets with targeted overrides (`XDimensionMode`, `MinimalXDimension`, etc.) when you know details about symbol geometry or device resolution.

---

## Notes about the example class

The example class `QualityModeExample` generates its own test images:

- `code128_clean.png` – a clean synthetic `CODE_128` image,
- `code128_noisy.png` – the same image with Gaussian noise added by `ExampleAssist.addGaussianNoise(...)`.

These fixtures help demonstrate how different combinations of presets and `BarcodeQualityMode` behave on clean vs noisy data.  
In your own projects you can reuse the patterns but work with your real images instead of generated ones.

Full class source:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/QualityModeExample.java" target="_blank" rel="noopener noreferrer">QualityModeExample.java</a>
