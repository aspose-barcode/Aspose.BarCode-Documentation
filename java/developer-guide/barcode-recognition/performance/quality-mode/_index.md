---
title: "Barcode Quality Mode"
description: "Learn how to control recognition robustness and performance using BarcodeQualityMode together with QualitySettings presets in Aspose.BarCode for Java."
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/performance/quality-mode
---

# Barcode Quality Mode

`BarcodeQualityMode` in Aspose.BarCode for Java tells the recognition engine **how good you expect the input image to be** and, based on that expectation, how much processing it should perform:

- `HIGH` – the barcode image is expected to be **high quality** (clean, high contrast, minimal noise);  
  the engine can use **lighter** processing and run faster.
- `NORMAL` – the barcode image is expected to be of **typical / medium quality**;  
  the engine uses a **balanced** amount of processing.
- `LOW` – the barcode image is expected to be **low quality** (noise, blur, low contrast);  
  the engine enables **heavier and more robust** processing.

The preset defines a baseline recognition pipeline, and `BarcodeQualityMode` refines this pipeline based on the *expected* image quality.

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.performance.QualityModeExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/QualityModeExample.java" target="_blank" rel="noopener noreferrer">QualityModeExample.java</a>

---

## 1. How BarcodeQualityMode works

The `BarcodeQualityMode` enum is defined as:

```java
public enum BarcodeQualityMode
{
    /**
     * Enables recognition methods for High quality barcodes.
     */
    HIGH(0),

    /**
     * Enables recognition methods for Common (Normal) quality barcodes.
     */
    NORMAL(1),

    /**
     * Enables recognition methods for Low quality barcodes.
     */
    LOW(2);
}
```

The key idea:

- `HIGH` – **input is high quality**, so the engine can skip some heavy recovery steps.
- `NORMAL` – **input is average quality**, use a balanced configuration.
- `LOW` – **input is low quality**, enable additional robust methods even if this is slower.

> Important: this is **different** from `QualitySettings.getHighQuality()` / `getMaxQuality()`, which are *presets* oriented toward **difficult** barcodes.  
> `BarcodeQualityMode` does **not** describe how “strong” the preset is in general; it only hints what level of image degradation the engine should expect for the current image.

In practice, you:

1. Choose a base preset (`getHighPerformance`, `getNormalQuality`, `getHighQuality`, or `getMaxQuality`).
2. Adjust `BarcodeQualityMode` to match the **quality of the specific input image** you are processing.

---

## 2. Using BarcodeQualityMode on clean images

On clean, synthetic, or well-scanned barcodes, all three modes usually recognize the code successfully.  
The primary difference is how many robustness features are enabled and, consequently, how much time recognition takes.

In all code snippets below, `imagePath` represents a path to a `CODE_128` image in your application.

### 2.1. HIGH quality mode – for high quality input

Use `BarcodeQualityMode.HIGH` when you know that barcodes come from a **reliable scanning process** (for example, industrial scanners or high‑resolution document scanners).

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
// Input is expected to be high quality → less heavy processing is needed
qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);

barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("HIGH (clean input): " + barCodeResult.getCodeText());
}
```

Typical use cases:

- clearly printed labels on conveyor lines
- barcodes printed with good contrast, scanned in controlled lighting
- bulk batch processing where you want minimal CPU usage per barcode

### 2.2. NORMAL quality mode – default for typical images

Use `BarcodeQualityMode.NORMAL` when you expect **typical, mixed quality** input:

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getNormalQuality();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.NORMAL);

barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("NORMAL (clean input): " + barCodeResult.getCodeText());
}
```

Recommended for:

- back‑office processing of scanned documents (invoices, shipping labels)
- typical desktop scanners with reasonable but not perfect quality
- applications where you want a good balance between throughput and robustness

### 2.3. LOW quality mode – extra robustness for difficult cases

Use `BarcodeQualityMode.LOW` when you expect **problematic images**: noise, faded print, partial occlusions, or low contrast.

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighQuality(); // robust preset
// Tell the engine to expect low‑quality input and enable heavier methods
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);

barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("LOW (clean input, extra robust): " + barCodeResult.getCodeText());
}
```

Even on a clean image, `LOW` mode may still work, but it will usually be **slower** than `HIGH` or `NORMAL`.  
This mode is intended for barcodes that are close to the readability limit.

---

## 3. Quality mode on noisy images

On noisy or degraded images, `BarcodeQualityMode` becomes more important.  
By raising the mode from `HIGH` to `LOW`, you tell the engine to **spend more effort** trying to recover a valid result.

### 3.1. Noisy image with HIGH mode – faster, less robust

```java
String imagePath = "code128_noisy.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
// Expect reasonably good quality, even if some noise is present
qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);

barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
System.out.println("Noisy, HIGH mode: results = " + barCodeResults.length);
```

Use this configuration if:

- your noisy images are still largely readable
- throughput is critical and an occasional failure is acceptable
- you want to keep processing close to the “fast path”

### 3.2. Noisy image with LOW mode – slower, more robust

```java
String imagePath = "code128_noisy.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighQuality();
// Explicitly inform the engine that the image is low quality
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);

barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
System.out.println("Noisy, LOW mode: results = " + barCodeResults.length);
```

Compared to the previous example:

- if `LOW` returns a result and `HIGH` does not, it means the image is near the quality threshold
- you can decide whether it is acceptable to pay extra CPU time to rescue such inputs

---

## 4. Combining presets with targeted overrides

The strongest configuration is achieved by **combining**:

- a `QualitySettings` preset – describing the *general* robustness profile, and
- `BarcodeQualityMode` – describing the *expected quality* of the current image, plus
- additional hints such as `XDimensionMode` and `MinimalXDimension`.

Example: clean `CODE_128` with small modules and a performance‑oriented preset.

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

// 1. Start from a fast preset
QualitySettings qualitySettings = QualitySettings.getHighPerformance();

// 2. Hint the engine that modules are small
qualitySettings.setXDimension(XDimensionMode.SMALL);
qualitySettings.setMinimalXDimension(1.0f);

// 3. Expected quality: average, not heavily degraded
qualitySettings.setBarcodeQuality(BarcodeQualityMode.NORMAL);

barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("Preset + overrides: " + barCodeResult.getCodeText());
}
```

This pattern is useful when:

- you know something about your barcodes (for example, small X‑dimension)
- you want to keep base settings fast (`getHighPerformance`)
- but still provide the engine with enough hints to decode reliably

---

## 5. Interaction with QualitySettings presets

`BarcodeQualityMode` works **together with** the main presets of `QualitySettings`:

```java
public static QualitySettings getNormalQuality() { return new QualitySettings(PresetType.NormalQuality); }
public static QualitySettings getHighQuality()   { return new QualitySettings(PresetType.HighQuality); }
public static QualitySettings getMaxQuality()    { return new QualitySettings(PresetType.MaxQuality); }
```

Conceptually:

- `QualitySettings.getNormalQuality()` – baseline preset for **most barcodes**, balanced speed vs quality.
- `QualitySettings.getHighQuality()` – preset designed for **low‑quality barcodes**, more robust algorithms, slower.
- `QualitySettings.getMaxQuality()` – preset designed to recognize **all possible barcodes, including heavily damaged ones**, with maximum effort.

Compared to that, `BarcodeQualityMode`:

- does **not** define a full preset;
- tells the engine how much additional robustness to enable **for the currently selected preset**, based on your **expectation about input quality**.

This means:

- you can use `getHighPerformance()` with `BarcodeQualityMode.HIGH` for **very fast processing** of clean barcodes;
- or use `getHighQuality()` with `BarcodeQualityMode.LOW` for **maximum robustness** on extremely low‑quality images;
- or stay at `getNormalQuality()` with `BarcodeQualityMode.NORMAL` for **typical scenarios**.

Think of the relationship as:

- **preset** = “how strong is the general recognition pipeline?”
- **BarcodeQualityMode** = “what is the expected quality of *this* image, and how much extra work should we do for it?”

---

## 6. Practical recommendations

When configuring `BarcodeQualityMode` in real applications:

- Start with:
    - `QualitySettings.getNormalQuality()`, and
    - `BarcodeQualityMode.NORMAL`.
- Measure recognition speed and success rate on your **actual images** (both clean and degraded).
- If some images fail due to noise or blur:
    - try switching to `BarcodeQualityMode.LOW`, or
    - move from `getHighPerformance()` to `getHighQuality()` / `getMaxQuality()` as presets.
- If everything is recognized reliably and CPU usage is high:
    - try using `BarcodeQualityMode.HIGH` on clean inputs, or
    - replace `getHighQuality()` with `getNormalQuality()` or `getHighPerformance()`.
- Use `XDimensionMode`, `MinimalXDimension`, and other hints when:
    - barcodes are consistently small, or
    - you work with a fixed camera or print resolution.

All patterns demonstrated here come from the test class:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/QualityModeExample.java" target="_blank" rel="noopener noreferrer">QualityModeExample.java</a>

This class also contains helper code for generating **clean** and **noisy** `CODE_128` test images (for example, by adding Gaussian noise).  
These fixtures are only used to emulate different input quality levels in automated tests and are **not required** in production code. In your own projects you will typically work with real images coming from scanners or cameras, while using `BarcodeQualityMode` and `QualitySettings` to tune recognition behavior.
