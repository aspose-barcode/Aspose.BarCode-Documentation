---
title: "Barcode Quality Mode"
description: "Learn how to configure BarcodeQualityMode to balance recognition speed and robustness in Aspose.BarCode for Java."
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/performance/quality-mode
---

# Barcode Quality Mode

`BarcodeQualityMode` in Aspose.BarCode for Java tells the recognition engine **what image quality you expect** for a given barcode:

- **HIGH** – image is expected to be **high quality** (clean, good contrast, proper focus)
- **NORMAL** – image is expected to be of **typical, medium quality**
- **LOW** – image is expected to be **low quality** (noise, blur, low contrast, compression artifacts)

Based on this hint, the engine **chooses how much work to do**:

- for **HIGH** quality barcodes it uses **lighter processing** and fewer heavy recovery steps
- for **NORMAL** quality it enables **moderate** processing suitable for standard cases
- for **LOW** quality it enables **more complex and expensive processing** to recover difficult barcodes

In other words:

| BarcodeQualityMode | Expected input quality | Engine behavior                                      |
|--------------------|------------------------|------------------------------------------------------|
| `HIGH`             | High (clean, sharp)    | Minimal extra processing, focus on speed             |
| `NORMAL`           | Medium (typical scans) | Balanced processing for common scenarios             |
| `LOW`              | Low (noisy, blurred)   | Maximum recovery effort, highest processing cost     |

`BarcodeQualityMode` is always used together with a `QualitySettings` preset (for example, `getHighPerformance`, `getNormalQuality`, `getHighQuality`).  
You typically:

1. select a **preset** that matches your performance/robustness needs
2. set `BarcodeQualityMode` to match the **expected image quality** in your application

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.performance.QualityModeExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/QualityModeExample.java" target="_blank" rel="noopener noreferrer">QualityModeExample.java</a>

In the snippets below, variables like `imagePath` represent paths to barcode images in your application.

---

## 1. Test Data: Clean and Noisy Code 128

To demonstrate `BarcodeQualityMode`, the example class uses two fixtures for `CODE_128`:

- `code128_clean.png` – a **clean synthetic** barcode with good contrast and no artifacts
- `code128_noisy.png` – the **same symbol degraded with Gaussian noise** using `ExampleAssist.addGaussianNoise(...)`

In real projects you will not usually generate fixtures at runtime. The key idea is:

- evaluate `BarcodeQualityMode` on **clean** and **difficult** images
- pick the mode that gives you the best balance between **speed** and **recognition rate** for your real input data

---

## 2. BarcodeQualityMode on Clean Images

For clean, high-quality barcodes, all three quality modes are generally able to recognize the symbol.  
The main difference is **how aggressively** the engine tries to recover defects (which you do not really need on perfect images).

### 2.1. HIGH – fast path for high-quality images

Use `BarcodeQualityMode.HIGH` when you know that your images come from **reliable sources**:

- industrial scanners
- controlled document pipelines
- well-calibrated cameras with fixed mountings

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
// Hint: input is high quality → use cheaper processing
qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("HIGH (clean): " + barCodeResult.getCodeText());
}
```

Here:

- `getHighPerformance()` is a **performance-oriented preset**
- `BarcodeQualityMode.HIGH` tells the engine that **no heavy recovery is needed**
- for clean images this combination provides **fast and stable** recognition

### 2.2. NORMAL – balanced mode for typical scans

Use `BarcodeQualityMode.NORMAL` when images are **typical office scans**:

- medium DPI
- no strong noise or blur
- occasional small imperfections

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getNormalQuality();
// Hint: common, medium-quality scans
qualitySettings.setBarcodeQuality(BarcodeQualityMode.NORMAL);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("NORMAL (clean): " + barCodeResult.getCodeText());
}
```

This configuration is a good **starting point**:

- preset: `getNormalQuality()` – balanced speed vs robustness
- quality mode: `NORMAL` – tuned for **typical document images**

### 2.3. LOW – extra robustness even for clean images

Even if your images are clean, you can still use `BarcodeQualityMode.LOW` when:

- you want **maximum safety margin**
- you are not sure about future input quality
- small degradations may appear after format conversions or additional processing

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighQuality(); // quality-oriented preset
// Hint: be ready for low-quality data → enable full recovery pipeline
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("LOW (clean): " + barCodeResult.getCodeText());
}
```

For really clean images, this is usually **more processing than needed**, but it shows that:

- you can keep a **high-quality preset**
- and still tell the engine to prepare for **worst-case input**

---

## 3. BarcodeQualityMode on Noisy Images

On noisy or degraded images, `BarcodeQualityMode` becomes a **critical tuning knob**.  
Here the engine must decide **how much extra work** to perform to try to recover the barcode.

### 3.1. Noisy image with HIGH (fast hint for good quality)

Using `BarcodeQualityMode.HIGH` on noisy images tells the engine:

> “I still expect reasonably good quality; do not over-spend resources.”

```java
String imagePath = "code128_noisy.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
System.out.println("Noisy, HIGH: results=" + barCodeResults.length);
```

This configuration is useful when:

- your images are **sometimes noisy**, but you still prefer **speed over maximum robustness**
- you know that most images are OK, and only occasional ones are strongly degraded

If such noisy samples start to fail, it is a signal that you should switch to `NORMAL` or `LOW` for that scenario.

### 3.2. Noisy image with LOW (robust hint for poor quality)

On heavily degraded data, `BarcodeQualityMode.LOW` is the recommended choice:

```java
String imagePath = "code128_noisy.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighQuality();
// Hint: data may be low quality → enable additional recovery methods
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("Noisy, LOW: " + barCodeResult.getCodeText());
} else {
    System.out.println("Noisy, LOW: nothing recognized");
}
```

Typical use cases:

- mobile camera photos under poor lighting
- barcodes printed on rough or reflective surfaces
- low-resolution screenshots or compressed images

In many scenarios:

- `HIGH` and `NORMAL` may still work, but
- `LOW` gives you **more safety** when quality is unpredictable

---

## 4. Combining Presets with Targeted Overrides

The example class also shows that you can **combine**:

- a preset (`HighPerformance`, `NormalQuality`, `HighQuality`)
- `BarcodeQualityMode`
- additional hints like `XDimensionMode` and `MinimalXDimension`

to precisely tune behavior.

Example from `QualityModeExample`: clean `CODE_128` with small modules and a low quality hint.

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();

// Geometric hints: expect small modules
qualitySettings.setXDimension(XDimensionMode.SMALL);
qualitySettings.setMinimalXDimension(1.0f);

// Quality hint: LOW → be ready for lower-quality input (more processing)
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);

barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("Preset + overrides: " + barCodeResult.getCodeText());
}
```

This pattern is useful when:

- barcodes are physically **small** (printed on labels, small packaging, etc.)
- you know the **approximate module size** (X-dimension)
- you can afford **extra processing** to reliably read such barcodes

---

## 5. Practical Recommendations

When configuring `BarcodeQualityMode` in your application, treat it as a **hint about expected image quality**, not just an abstract “quality level”.

Recommended workflow:

1. **Start simple**
    - Use `QualitySettings.getNormalQuality()`
    - Set `BarcodeQualityMode.NORMAL`

2. **Measure on your real images**
    - include both **clean** and **problematic** samples
    - track recognition rate and performance

3. **If you mostly have high-quality images**
    - try `BarcodeQualityMode.HIGH` with `getHighPerformance()`
    - if all barcodes are recognized reliably, you gain **speed**

4. **If you often have low-quality images**
    - switch to `BarcodeQualityMode.LOW`
    - consider using `getHighQuality()` as base preset
    - optionally add `XDimension` hints if you know typical module size

5. **Use overrides when you know the geometry**
    - `setXDimension(XDimensionMode.SMALL)` and `setMinimalXDimension(...)`
    - help the engine focus on realistic module sizes and avoid unnecessary search

6. **Document your choices**
    - for each processing pipeline (scanner, camera, screenshot source)
    - clearly specify which `QualitySettings` preset and `BarcodeQualityMode` are used
    - keep a small regression set to re-check behavior after library upgrades

All configuration patterns shown in this article are implemented in:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/QualityModeExample.java" target="_blank" rel="noopener noreferrer">QualityModeExample.java</a>

Use this class as a reference when tuning recognition speed and robustness with `BarcodeQualityMode` in Aspose.BarCode for Java.
