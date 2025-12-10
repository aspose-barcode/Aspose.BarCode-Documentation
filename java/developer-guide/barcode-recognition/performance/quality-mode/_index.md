---
title: "Barcode Quality Mode"
description: "Learn how to control recognition robustness and speed using BarcodeQualityMode and QualitySettings presets in Aspose.BarCode for Java."
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/performance/quality-mode
---

# Barcode Quality Mode

`BarcodeQualityMode` in Aspose.BarCode for Java tells the recognition engine how **good** you expect the input image to be.  
It does **not** directly mean how “powerful” the algorithm is, but how much effort is needed based on expected image quality:

- `HIGH` – you expect **high‑quality barcodes** → the engine uses **lighter / faster** processing
- `NORMAL` – you expect **average image quality** → the engine uses **balanced** processing
- `LOW` – you expect **low‑quality / damaged barcodes** → the engine uses **heavier / slower** processing

In other words:

> The worse the expected image quality, the lower the `BarcodeQualityMode` value you should choose.

`BarcodeQualityMode` is always used **together** with a `QualitySettings` preset (for example, `getHighPerformance`, `getNormalQuality`, `getHighQuality`).  
You start from a preset and then optionally override the quality mode to fine‑tune behavior.

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.performance.QualityModeExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/QualityModeExample.java" target="_blank" rel="noopener noreferrer">QualityModeExample.java</a>

In the snippets below, variables like `imagePath` represent paths to barcode images in your application.

---

## 1. How BarcodeQualityMode and QualitySettings presets interact

`QualitySettings` presets define **overall recognition strategy**, and `BarcodeQualityMode` further narrows the engine’s expectations about input quality.

From the API documentation:

- `QualitySettings.getNormalQuality()` – “NormalQuality recognition quality preset. Suitable for most barcodes.”
- `QualitySettings.getHighQuality()` – “HighQuality recognition quality preset. This preset is developed for **low‑quality barcodes**. Allows to detect highly damaged barcodes.”
- `QualitySettings.getMaxQuality()` – “MaxQuality recognition quality preset. This preset is developed to recognize **all possible barcodes, even incorrect barcodes**.”

So presets behave roughly like this:

- `getHighPerformance()` – fastest, for good images
- `getNormalQuality()` – default preset, good for most cases
- `getHighQuality()` – stronger, for **low‑quality / damaged** barcodes
- `getMaxQuality()` – maximum effort, even tries to recover incorrect barcodes

Now combine this with `BarcodeQualityMode`:

- `BarcodeQualityMode.HIGH` – **you promise the engine that the image is good**  
  → it can safely skip some heavy steps and treat the barcode as high‑quality.
- `BarcodeQualityMode.NORMAL` – the engine expects typical, average quality.
- `BarcodeQualityMode.LOW` – the engine expects **poor / noisy / distorted** images  
  → it enables more aggressive processing inside the chosen preset.

Put simply:

- Preset (`getHighPerformance`, `getHighQuality`, …) defines *what toolbox* is available.
- `BarcodeQualityMode` defines *how much of that toolbox is needed* for the current image.

> Note the naming difference:  
> `getHighQuality()` preset is designed for **low‑quality barcodes**,  
> while `BarcodeQualityMode.HIGH` means **high‑quality images** and thus less internal work.

---

## 2. Test data: clean and noisy Code 128

The example class prepares two fixtures:

- `code128_clean.png` – a clean synthetic `CODE_128` image with good contrast
- `code128_noisy.png` – the same symbol with Gaussian noise (`addGaussianNoise`) to simulate low signal‑to‑noise ratio

In real applications you will use your own images; here they simply help to show how different combinations of preset + `BarcodeQualityMode` behave.

---

## 3. Using BarcodeQualityMode on clean images

On a clean `CODE_128` image, all three quality modes are expected to work.  
The question is how expensive the processing should be.

### 3.1. High mode on clean image (fastest path within the preset)

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

// We expect a good image, so we combine a fast preset with HIGH quality mode.
QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("Clean, HIGH mode: " + barCodeResult.getCodeText());
}
```

Here:

- `getHighPerformance()` selects a **speed‑oriented preset**.
- `BarcodeQualityMode.HIGH` tells the engine that the image quality is **good**,  
  so it may skip some robust but expensive recovery steps.
- For a clean image, this pattern gives **fast and stable** recognition.

### 3.2. Normal mode on clean image (balanced expectation)

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getNormalQuality();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.NORMAL);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("Clean, NORMAL mode: " + barCodeResult.getCodeText());
}
```

Typical use cases:

- back‑office processing with **mostly good**, but not perfect scans
- scenarios where you prefer a **neutral default** – neither overly optimistic nor overly defensive

### 3.3. Low mode on clean image (overkill, but still valid)

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

// Start from a robust preset designed for low-quality barcodes…
QualitySettings qualitySettings = QualitySettings.getHighQuality();
// …but tell the engine that the current image is actually low-quality:
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("Clean, LOW mode (overkill): " + barCodeResult.getCodeText());
}
```

Even though the image is clean:

- we use `getHighQuality()` — a preset **designed for low‑quality barcodes**
- and `BarcodeQualityMode.LOW` — an expectation of **poor input**

This combination is effectively **over‑provisioned** for a clean image: it should still decode correctly, but at a higher CPU cost than necessary.

---

## 4. Quality mode on noisy images

With noisy or degraded images, `BarcodeQualityMode` and presets become much more important.

### 4.1. Noisy image with HIGH mode (optimistic expectation)

```java
String imagePath = "code128_noisy.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);
barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
System.out.println("Noisy, HIGH mode: results=" + barCodeResults.length);
```

In the example test data, this configuration can still recognize the barcode, but conceptually it is **optimistic**:

- we use a fast preset (`getHighPerformance()`)
- and we tell the engine that the image quality is **high**

This is appropriate when:

- the noise level is moderate
- you want to keep latency low and are ready to tolerate some failures on very bad images

### 4.2. Noisy image with LOW mode (defensive expectation)

```java
String imagePath = "code128_noisy.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

// A more robust preset for low-quality images
QualitySettings qualitySettings = QualitySettings.getHighQuality();
// Tell the engine that this particular image is low-quality
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);

barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
System.out.println("Noisy, LOW mode: results=" + barCodeResults.length);
```

This combination is what you typically use for **difficult** barcodes:

- `getHighQuality()` preset is built specifically for **low‑quality / damaged** barcodes.
- `BarcodeQualityMode.LOW` confirms that the engine should **expect trouble** and use heavier processing.

In the sample tests, both HIGH and LOW modes recognize the noisy image, but LOW is the **safer choice** when you know that your inputs can be heavily degraded.

---

## 5. Combining presets with targeted overrides

The example also shows how to combine a fast preset with additional hints for geometric properties such as X‑dimension.

Example: clean `CODE_128` with small modules and low quality mode.

```java
String imagePath = "code128_clean.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

// Start from a performance-oriented preset
QualitySettings qualitySettings = QualitySettings.getHighPerformance();

// Hint that modules can be small and thin
qualitySettings.setXDimension(XDimensionMode.SMALL);
qualitySettings.setMinimalXDimension(1.0f);

// At the same time, we keep BarcodeQualityMode.LOW to be conservative on robustness
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);

barCodeReader.setQualitySettings(qualitySettings);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];
    System.out.println("Preset + overrides: " + barCodeResult.getCodeText());
}
```

Here:

- `getHighPerformance()` still keeps the base configuration fast.
- `XDimensionMode.SMALL` + `MinimalXDimension(1.0f)` tell the engine to expect **small bar widths**.
- `BarcodeQualityMode.LOW` says the barcode may be **hard to read**, so more work is allowed inside that preset.

This pattern is useful when you:

- know that barcodes are **physically small** (for example, on labels or parts)
- expect **low resolution** or **noise**, but still want a performance‑oriented base configuration

---

## 6. Practical recommendations

When configuring `BarcodeQualityMode` and `QualitySettings` together:

1. **Choose a preset based on the general quality of your dataset:**

    - mostly good images → start with `QualitySettings.getHighPerformance()` or `getNormalQuality()`
    - many low‑quality / damaged barcodes → start with `QualitySettings.getHighQuality()`
    - extremely difficult cases where you must recover everything, even incorrect symbols → try `QualitySettings.getMaxQuality()`

2. **Then set `BarcodeQualityMode` according to the expected quality of the current image batch:**

    - `BarcodeQualityMode.HIGH` – use when images are **clean and high‑quality**
    - `BarcodeQualityMode.NORMAL` – use for **typical mixed** quality
    - `BarcodeQualityMode.LOW` – use when images are **noisy, blurred, low‑contrast or damaged**

3. **Measure on real data.**  
   Use your own images (both clean and problematic) to find the sweet spot between robustness and speed.

4. **Add targeted overrides only when needed.**  
   Use hints like `setXDimension(...)` and `setMinimalXDimension(...)` when you know the approximate bar width or symbol size in pixels.

All patterns in this article are demonstrated in the sample test class:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/QualityModeExample.java" target="_blank" rel="noopener noreferrer">QualityModeExample.java</a>

Use it as a reference when tuning recognition quality and performance in your own Java applications.
