---
title: "Deconvolution Mode"
description: "Learn how to use deconvolution mode to recognize blurred and out-of-focus barcodes in Aspose.BarCode for Java."
type: docs
weight: 20
url: /java/developer-guide/barcode-recognition/performance/deconvolution-mode
---

# Barcode Quality and Deconvolution Modes

Aspose.BarCode for Java provides flexible controls to balance **recognition speed** and **robustness**.  
These controls are exposed through:

- `QualitySettings` presets (for example, `getHighPerformance()`, `getNormalQuality()`, `getHighQuality()`)
- `BarcodeQualityMode` – selects recognition methods depending on the expected barcode quality (heavier methods for low-quality codes)
- `DeconvolutionMode` – deconvolution (image restoration) mode that defines the assumed level of image degradation and the strength of blur-reduction algorithms
- Targeted overrides such as `XDimensionMode` and `setMinimalXDimension(...)`


All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.performance.BarcodeQualityDeconvolutionModeExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/DeconvolutionModeExample.java" target="_blank" rel="noopener noreferrer">DeconvolutionModeExample.java</a>

In the snippets below, variables like `imagePath` represent paths to barcode images in your application.


## 1. DeconvolutionMode – blur and degradation handling

`DeconvolutionMode` is an image restoration mode that defines the assumed level of image degradation.  
It controls how strong deblurring and related preprocessing algorithms are, and therefore how much extra time the engine spends on image restoration.

Supported values:

| Mode                        | Description                                                                       | Typical scenario                               |
|-----------------------------|-----------------------------------------------------------------------------------|------------------------------------------------|
| `DeconvolutionMode.FAST`    | Lightweight restoration; minimal extra cost.                                     | Slight blur or almost clean images.            |
| `DeconvolutionMode.NORMAL`  | Balanced restoration level.                                                      | Typical handheld photos with some blur/noise.  |
| `DeconvolutionMode.SLOW`    | Strongest restoration pipeline; highest CPU cost, maximum robustness.           | Strong blur, motion blur, or heavy degradation.|

Again, the pattern is:

1. Pick a `QualitySettings` preset.
2. Set the desired `DeconvolutionMode`.
3. Apply `QualitySettings` to `BarCodeReader`.

Example: configuring `FAST`, `NORMAL`, and `SLOW` for QR recognition.

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "qset_qr.png");

// FAST: for clean or slightly blurred QR codes
BarCodeReader fastDeconvolutionReader = new BarCodeReader(imagePath, DecodeType.QR);
QualitySettings fastDeconvolutionSettings = QualitySettings.getHighQuality();
fastDeconvolutionSettings.setDeconvolution(DeconvolutionMode.FAST);
fastDeconvolutionReader.setQualitySettings(fastDeconvolutionSettings);

// NORMAL: default level for everyday mobile photos
BarCodeReader normalDeconvolutionReader = new BarCodeReader(imagePath, DecodeType.QR);
QualitySettings normalDeconvolutionSettings = QualitySettings.getNormalQuality();
normalDeconvolutionSettings.setDeconvolution(DeconvolutionMode.NORMAL);
normalDeconvolutionReader.setQualitySettings(normalDeconvolutionSettings);

// SLOW: strongest restoration for heavily blurred images
BarCodeReader slowDeconvolutionReader = new BarCodeReader(imagePath, DecodeType.QR);
QualitySettings slowDeconvolutionSettings = QualitySettings.getHighQuality();
slowDeconvolutionSettings.setDeconvolution(DeconvolutionMode.SLOW);
slowDeconvolutionReader.setQualitySettings(slowDeconvolutionSettings);
```

Use a higher deconvolution level only when necessary, because it increases processing time.

---

## 2. Combining presets with targeted overrides

A common pattern is to:

1. Start from a **fast preset**, such as `getHighPerformance()`.
2. Apply targeted overrides for your specific scenario.

For example, if you expect **small and low-quality 1D barcodes**:

- enable detection of small modules via `XDimensionMode.SMALL`
- set `MinimalXDimension` to the approximate minimal bar width in pixels
- use `BarcodeQualityMode.LOW` and `DeconvolutionMode.SLOW` to improve robustness

Example: tuning recognition for small, degraded Code 128 symbols.

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "qset_code128.png");

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setXDimension(XDimensionMode.SMALL);
qualitySettings.setMinimalXDimension(1.0f);
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);
qualitySettings.setDeconvolution(DeconvolutionMode.SLOW);

barCodeReader.setQualitySettings(qualitySettings);
```

This configuration:

- keeps the **overall preset** tuned for performance,
- but adds **extra robustness** for tiny and degraded bars through explicit overrides.

---

## 3. QualitySettings presets overview

`QualitySettings` provides ready-made presets that enable appropriate internal algorithms for typical scenarios:

| Preset method                      | Typical use case                                        | Trade-off                             |
|-----------------------------------|---------------------------------------------------------|---------------------------------------|
| `QualitySettings.getHighPerformance()` | Fast processing of clean, high-contrast images           | Maximum speed, reduced robustness     |
| `QualitySettings.getNormalQuality()`   | General-purpose recognition for normal image quality     | Balanced speed and robustness         |
| `QualitySettings.getHighQuality()`     | Difficult images: noise, blur, low contrast, tiny codes  | Maximum robustness, lower performance |

You can use these presets as a **starting point** and then adjust details with `BarcodeQualityMode`, `DeconvolutionMode`, and other properties.

---

## 4. BarcodeQualityMode – quality analysis profile

`BarcodeQualityMode` selects and enables recognition methods depending on the expected barcode quality.  
For lower-quality barcodes it turns on heavier, more tolerant algorithms, which improves robustness but slows recognition.


Supported values:

| Mode                      | Description                                                                                              | Typical scenario                         |
|---------------------------|----------------------------------------------------------------------------------------------------------|------------------------------------------|
| `BarcodeQualityMode.HIGH`   | Lightweight checks assuming good print quality and clear edges.                                         | High-quality printed labels, synthetic test data. |
| `BarcodeQualityMode.NORMAL` | Standard analysis for regular-quality images.                                                            | Most business documents and mobile photos.        |
| `BarcodeQualityMode.LOW`    | Enables heavy and tolerant algorithms for damaged, low-contrast, or distorted barcodes.                 | Poor printing, fax/scans, degraded images.       |

The general pattern:

1. Choose a `QualitySettings` preset.
2. Set the desired `BarcodeQualityMode`.
3. Apply the configured `QualitySettings` to `BarCodeReader`.

Example: switching between `HIGH`, `NORMAL`, and `LOW` for Code 128.

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "qset_code128.png");

// HIGH: fastest on clean images
BarCodeReader highQualityReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
QualitySettings highPerformanceSettings = QualitySettings.getHighPerformance();
highPerformanceSettings.setBarcodeQuality(BarcodeQualityMode.HIGH);
highQualityReader.setQualitySettings(highPerformanceSettings);

// NORMAL: balanced default
BarCodeReader normalQualityReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
QualitySettings normalQualitySettings = QualitySettings.getNormalQuality();
normalQualitySettings.setBarcodeQuality(BarcodeQualityMode.NORMAL);
normalQualityReader.setQualitySettings(normalQualitySettings);

// LOW: most tolerant, slowest
BarCodeReader lowQualityReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
QualitySettings highQualitySettings = QualitySettings.getHighQuality();
highQualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);
lowQualityReader.setQualitySettings(highQualitySettings);
```

Use this pattern when you need to tune performance:

- Start with `BarcodeQualityMode.HIGH` if you expect consistently clean barcodes.
- Use `BarcodeQualityMode.NORMAL` as a general default.
- Switch to `BarcodeQualityMode.LOW` only for problematic inputs where robustness is more important than speed.

---


## 5. Practical guidelines

When configuring quality and deconvolution parameters:

- Start with presets:
    - `getHighPerformance()` for synthetic data or controlled environments.
    - `getNormalQuality()` for most real-world applications.
    - `getHighQuality()` for known difficult inputs.
- Use `BarcodeQualityMode` to match expected print quality:
    - **HIGH** – clean barcodes, best speed.
    - **NORMAL** – default choice if you are not sure.
    - **LOW** – damaged or low-contrast barcodes.
- Use `DeconvolutionMode` for blur and focus issues:
    - **FAST** – light restoration.
    - **NORMAL** – typical mobile snapshots.
    - **SLOW** – strong blur or motion artifacts.
- Combine presets with overrides (`XDimensionMode`, `MinimalXDimension`, etc.) when you know specific constraints of your data (for example, very small modules).

All patterns in this article are demonstrated in:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/DeconvolutionModeExample.java" target="_blank" rel="noopener noreferrer">DeconvolutionModeExample.java</a>

Use it as a reference when tuning recognition performance in your Java applications.
