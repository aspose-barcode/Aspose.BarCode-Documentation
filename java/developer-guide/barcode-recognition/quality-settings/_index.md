---
title: Quality Settings
description: "Learn how to use QualitySettings presets and fine-tune recognition parameters in Aspose.BarCode for Java."
type: docs
weight: 70
url: /java/developer-guide/barcode-recognition/quality-settings
---

# Quality settings

`QualitySettings` in Aspose.BarCode for Java control the balance between **speed**, **robustness**, and **special processing modes** (inverse image, complex background, damaged symbols, etc.).  
This article shows how to:

- use built-in **presets** (`getNormalQuality()`, `getHighPerformance()`, `getHighQuality()`, `getMaxQuality()`)
- enable **inverse image** support for light-on-dark barcodes
- tune **X-dimension** and minimal module size for tiny barcodes
- use **barcode quality mode** for low-quality inputs
- handle **complex backgrounds**
- allow reading of **damaged or partially incorrect** barcodes
- verify and partially override preset parameters

All examples are based on the test class:

`com.aspose.barcode.guide.recognition.quality_settings.QualitySettingsExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/quality_settings/QualitySettingsExample.java" target="_blank" rel="noopener noreferrer">QualitySettingsExample.java</a>

In the snippets below, `imagesFolder` is the folder with sample images used in tests.

---

## 1. Preset overview

Aspose.BarCode for Java provides four main `QualitySettings` presets:

| Preset method                      | Profile focus                   | Typical use case                                          |
|------------------------------------|---------------------------------|-----------------------------------------------------------|
| `QualitySettings.getHighPerformance()` | Speed-first, lightweight filters | Large batches of clean barcodes, real-time scanning       |
| `QualitySettings.getNormalQuality()`    | Balanced speed / accuracy        | Default choice for most regular images                    |
| `QualitySettings.getHighQuality()`      | Robustness on degraded images    | Noisy, blurred, low-contrast or slightly damaged barcodes |
| `QualitySettings.getMaxQuality()`       | Maximum robustness, slowest      | Very hard images, complex backgrounds, QA/debug scenarios |

You always configure a reader using:

```java
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
QualitySettings qualitySettings = QualitySettings.getNormalQuality(); // choose preset
barCodeReader.setQualitySettings(qualitySettings);
```

You can then optionally fine-tune individual properties such as:

- `setBarcodeQuality(BarcodeQualityMode mode)`
- `setXDimension(XDimensionMode mode)`
- `setMinimalXDimension(float pixels)`
- `setInverseImage(InverseImageMode mode)`
- `setComplexBackground(ComplexBackgroundMode mode)`
- `setAllowIncorrectBarcodes(boolean enabled)`
- `setDeconvolution(DeconvolutionMode mode)`

The sections below show concrete examples of how these options are used.

---

## 2. Normal quality on clean Code 128

For clean, high-contrast barcodes, the **NormalQuality** preset is usually sufficient and provides a good balance between speed and accuracy.

Example: reading a standard Code 128 symbol.

```java
String imagePath = imagesFolder + "/code128.png";

QualitySettings qualitySettings = QualitySettings.getNormalQuality();

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, "code128.png", 1, DecodeType.CODE_128);
```

Use this pattern as a default baseline for most 1D and 2D barcodes if input quality is not a problem.

---

## 3. High performance preset for QR codes

`HighPerformance` is optimized for **throughput**: it uses fewer heavy filters and is ideal when you have many clean images or need real-time scanning.

Example: reading a QR code with `HighPerformance`:

```java
String imagePath = imagesFolder + "/qrcode.png";

QualitySettings qualitySettings = QualitySettings.getHighPerformance();

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, "qrcode.png", 1, DecodeType.QR);
```

This mode is well suited for:

- batch processing of generated barcodes
- scanned labels with good contrast and resolution
- server-side pipelines where latency is critical

---

## 4. High quality preset for Data Matrix

`HighQuality` enables additional noise reduction and advanced filters, making it more tolerant to moderate degradation at the cost of performance.

Example: reading a Data Matrix symbol with `HighQuality`:

```java
String imagePath = imagesFolder + "/datamatrix.png";

QualitySettings qualitySettings = QualitySettings.getHighQuality();

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.DATA_MATRIX);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, "datamatrix.png", 1, DecodeType.DATA_MATRIX);
```

Use `HighQuality` when images:

- come from low-quality cameras or fax-like sources
- have moderate noise or small distortions
- are slightly defocused

---

## 5. Max quality preset for PDF417

`MaxQuality` uses **all available** processing paths and is the slowest but most robust option. It is useful for complex or heavily degraded barcodes.

Example: reading a PDF417 symbol with `MaxQuality`:

```java
String imagePath = imagesFolder + "/pdf417.png";

QualitySettings qualitySettings = QualitySettings.getMaxQuality();

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.PDF_417);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, "pdf417.png", 1, DecodeType.PDF_417);
```

Typical use cases:

- QA scenarios where recognition success matters more than speed
- images with strong distortions, skew, or non-uniform lighting
- low-resolution scans with visible artifacts

---

## 6. Working with 1D and 2D type groups

Instead of specifying a single symbology, you can use grouped decode types:

- `DecodeType.TYPES_1D` — any supported 1D symbology
- `DecodeType.TYPES_2D` — any supported 2D symbology

### 6.1. 1D group with EAN-13

```java
String imagePath = imagesFolder + "/ean13.png";

QualitySettings qualitySettings = QualitySettings.getNormalQuality();

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.TYPES_1D);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, "ean13.png", 1, DecodeType.EAN_13);
```

The reader automatically searches all 1D symbologies and you still validate that the detected type is `EAN_13`.

### 6.2. 2D group with Aztec

```java
String imagePath = imagesFolder + "/aztec.png";

QualitySettings qualitySettings = QualitySettings.getNormalQuality();

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.TYPES_2D);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, "aztec.png", 1, DecodeType.AZTEC);
```

This pattern is useful when the input may contain different 2D formats and you do not want to configure each type individually.

---

## 7. Inverse image mode for light-on-dark barcodes

Some barcodes are printed **inverted** (light modules on a dark background), or the image is inverted during scanning.  
In such cases you must explicitly enable inverse processing via `InverseImageMode`.

Example: recognizing an inverted QR code:

```java
String imagePath = imagesFolder + "/qrcode_inverted.png";

QualitySettings qualitySettings = QualitySettings.getNormalQuality();
qualitySettings.setInverseImage(InverseImageMode.ENABLED);

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, "qrcode_inverted.png", 1, DecodeType.QR);
```

Key points:

- Default presets may have inverse processing disabled or enabled depending on profile.
- If you expect **light-on-dark** codes (reversed contrast), always check and set `setInverseImage(InverseImageMode.ENABLED)` explicitly.

---

## 8. Tiny barcodes and minimal X-dimension

For very small barcodes, the physical bar width (module size) in pixels is close to 1–2 px.  
To make the detector more robust in such scenarios, you can:

- hint that bars are small: `setXDimension(XDimensionMode.SMALL)`
- specify minimal expected module width in pixels: `setMinimalXDimension(float value)`

Example: reading a very small Code 128 symbol:

```java
String imagePath = imagesFolder + "/code128_small.png";

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setXDimension(XDimensionMode.SMALL);
qualitySettings.setMinimalXDimension(1.0f);

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, "code128_small.png", 1, DecodeType.CODE_128);
```

Recommendations:

- `MinimalXDimension` should roughly match the smallest bar width in your images.
- For dense barcodes on screens or small labels, use `XDimensionMode.SMALL` together with a realistic minimal value.

---

## 9. Forcing low quality mode for hard images

`BarcodeQualityMode` controls the **internal recognition strategy**.  
Setting `BarcodeQualityMode.LOW` instructs the engine to use more intensive correction and recovery steps, which are helpful for low-quality images.

Example: enabling low quality mode on a degraded Code 128 image:

```java
String imagePath = imagesFolder + "/code128_blurred.png";

QualitySettings qualitySettings = QualitySettings.getHighPerformance();
qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, "code128_blurred.png", 1, DecodeType.CODE_128);
```

Trade-off:

- **Pros:** better tolerance to blur, noise, low contrast
- **Cons:** higher CPU cost and longer recognition time

---

## 10. Complex background mode

When barcodes are printed on **textured, colored, or noisy backgrounds**, segmentation becomes harder.  
`ComplexBackgroundMode.ENABLED` enables additional processing stages to handle such cases.

Example: reading a QR code on a complex background:

```java
String imagePath = imagesFolder + "/qrcode_colored.png";

QualitySettings qualitySettings = QualitySettings.getMaxQuality();
qualitySettings.setComplexBackground(ComplexBackgroundMode.ENABLED);

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, "qrcode_colored.png", 1, DecodeType.QR);
```

Use this mode when:

- barcodes are printed directly on product photos or patterned packaging
- there is no clean white background around the code
- you see mis-detections due to background elements

---

## 11. Allowing incorrect or partially damaged barcodes

If you work with **damaged** or **partially corrupted** barcodes, you may want to relax strict internal validation rules and allow potentially incorrect results for further manual or domain-specific validation.

This is controlled by `setAllowIncorrectBarcodes(true)`.

Example: enabling incorrect barcode recognition for a damaged Code 128 image:

```java
String imagePath = imagesFolder + "/code128_damaged.png";

QualitySettings qualitySettings = QualitySettings.getMaxQuality();
qualitySettings.setAllowIncorrectBarcodes(true);

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
barCodeReader.setQualitySettings(qualitySettings);

ExampleAssist.assertRecognized(barCodeReader, "code128_damaged.png", 1, DecodeType.CODE_128);
```

Important:

- When this mode is enabled, you may receive results that do not fully conform to specification.
- Apply your own business rules or checksum logic to decide whether to accept or reject them.

---

## 12. Inspecting and partially overriding presets

You can inspect built-in preset parameters and then create a **custom profile** by overriding only a subset of them.

Example: verifying preset defaults and applying partial overrides:

```java
// Inspect NormalQuality defaults
QualitySettings normal = QualitySettings.getNormalQuality();
Assert.assertEquals(normal.getXDimension(), XDimensionMode.NORMAL);
Assert.assertEquals(normal.getMinimalXDimension(), 1.0f);
Assert.assertEquals(normal.getBarcodeQuality(), BarcodeQualityMode.NORMAL);
Assert.assertEquals(normal.getDeconvolution(), DeconvolutionMode.NORMAL);
Assert.assertEquals(normal.getInverseImage(), InverseImageMode.DISABLED);
Assert.assertEquals(normal.getComplexBackground(), ComplexBackgroundMode.DISABLED);
Assert.assertFalse(normal.getAllowIncorrectBarcodes());

// Inspect other presets
QualitySettings highPerformance = QualitySettings.getHighPerformance();
Assert.assertEquals(highPerformance.getDeconvolution(), DeconvolutionMode.FAST);
Assert.assertEquals(highPerformance.getBarcodeQuality(), BarcodeQualityMode.HIGH);

QualitySettings highQuality = QualitySettings.getHighQuality();
Assert.assertEquals(highQuality.getInverseImage(), InverseImageMode.ENABLED);
Assert.assertEquals(highQuality.getDeconvolution(), DeconvolutionMode.SLOW);

QualitySettings maxQuality = QualitySettings.getMaxQuality();
Assert.assertEquals(maxQuality.getComplexBackground(), ComplexBackgroundMode.ENABLED);
```

Then build a custom profile based on a preset:

```java
QualitySettings custom = QualitySettings.getHighPerformance();

// Partial overrides for a specific scenario
custom.setInverseImage(InverseImageMode.ENABLED);   // support inverse images
custom.setAllowIncorrectBarcodes(true);             // allow partially damaged codes
custom.setMinimalXDimension(2.5f);                  // adjust minimal bar width

String imagePath = imagesFolder + "/code128_custom.png";
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
barCodeReader.setQualitySettings(custom);

ExampleAssist.assertRecognized(barCodeReader, "code128_custom.png", 1, DecodeType.CODE_128);

// You can also verify that the applied settings were retained:
QualitySettings applied = barCodeReader.getQualitySettings();
Assert.assertEquals(applied.getInverseImage(), InverseImageMode.ENABLED);
Assert.assertTrue(applied.getAllowIncorrectBarcodes());
Assert.assertEquals(applied.getMinimalXDimension(), 2.5f);
```

This pattern is recommended when you need a **stable base profile** (preset) with only a few adjustments for your environment.

---

## Summary

`QualitySettings` are the central mechanism for tuning recognition behavior in Aspose.BarCode for Java. In practice:

- Start from a preset that matches your scenario:
    - `getHighPerformance()` for speed on clean images
    - `getNormalQuality()` as a default for most cases
    - `getHighQuality()` for noisy or slightly degraded images
    - `getMaxQuality()` for the hardest inputs and complex backgrounds
- Use fine-tuning options to adapt recognition to your data:
    - `setInverseImage(...)` for light-on-dark or inverted images
    - `setXDimension(...)` and `setMinimalXDimension(...)` for tiny modules
    - `setBarcodeQuality(...)` for low-quality inputs
    - `setComplexBackground(...)` for non-uniform backgrounds
    - `setAllowIncorrectBarcodes(true)` when you want to capture partially damaged symbols

All examples in this article are based on:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/quality_settings/QualitySettingsExample.java" target="_blank" rel="noopener noreferrer">QualitySettingsExample.java</a>

Use these patterns as a reference when configuring `QualitySettings` in your own Java applications.
