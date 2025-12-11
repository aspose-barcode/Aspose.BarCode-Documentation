---
title: "Reading Low-Resolution Barcode"
description: "Learn how to read low-resolution barcodes in Aspose.BarCode for Java using QualitySettings and X-dimension hints."
type: docs
weight: 70
url: /java/developer-guide/barcode-recognition/performance/reading-low-resolution-barcode
---

# Reading Low-Resolution Barcode

When barcodes are rendered **directly at a small pixel width** (for example, icons, thumbnails, or compressed UI widgets), the modules (bars) can be just 1–2 pixels wide.  
Such low-resolution images are not “damaged” in the classic sense (no blur, no noise), but they are **close to the resolution limit** and require careful tuning of recognition settings.

This article explains how to read low-resolution Code 128 barcodes in Aspose.BarCode for Java using:

- `QualitySettings` presets (HighPerformance, NormalQuality, HighQuality)
- `BarcodeQualityMode` (HIGH / NORMAL / LOW)
- `XDimensionMode.USE_MINIMAL_X_DIMENSION` and `setMinimalXDimension(float)`
- proper barcode generation (crisp rendering, explicit width, quiet zones)

> Important: The `MinimalXDimension` value is taken into account **only when** `XDimensionMode` is set to `USE_MINIMAL_X_DIMENSION`.  
> For all other XDimension modes (such as `SMALL`, `NORMAL`, or `LARGE`), the engine ignores `MinimalXDimension` and uses the built-in preset module width.

All code samples are based on the test class:

`com.aspose.barcode.guide.recognition.performance.ReadingLowResolutionBarcodeExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/ReadingLowResolutionBarcodeExample.java" target="_blank" rel="noopener noreferrer">ReadingLowResolutionBarcodeExample.java</a>

---

## 1. Test data: clean and low-resolution images

The example class operates on one **clean** Code 128 image and three **low-resolution** variants that are rendered directly at fixed widths.

- **Clean baseline**
    - `code128_clean_width_600px.png` — large, high-quality Code 128 symbol (comfortable X-dimension, wide quiet zones).

- **Low-resolution variants**
    - `code128_low_resolution_width_150px.png` — moderately small barcode, still detailed.
    - `code128_low_resolution_width_80px.png` — small barcode with modules ≈1–2 pixels wide.
    - `code128_low_resolution_width_40px.png` — extremely small barcode, close to the practical resolution limit.

All images encode the same payload text, so you can directly compare recognition behavior under different `QualitySettings` configurations.

---

## 2. Baseline: clean barcode with normal quality

Before dealing with low-resolution cases, the example validates that a clean, large barcode is recognized with **balanced** settings.

```java
@Test
public void read_Code128_Clean_NormalQuality() throws Exception {
    BarCodeReader barCodeReader = new BarCodeReader(
            ExampleAssist.pathCombine(FOLDER, FILE_CODE128_CLEAN_BASE), DecodeType.CODE_128);

    QualitySettings qualitySettings = QualitySettings.getNormalQuality();
    qualitySettings.setBarcodeQuality(BarcodeQualityMode.NORMAL);
    barCodeReader.setQualitySettings(qualitySettings);

    ExampleAssist.assertRecognized(barCodeReader, FILE_CODE128_CLEAN_BASE, 1, DecodeType.CODE_128);
}
```

Conceptually:

- `QualitySettings.getNormalQuality()` is a **balanced preset** (speed vs robustness).
- `BarcodeQualityMode.NORMAL` keeps the standard quality profile.
- On high-quality input, **no special hints** are needed.

Use this pattern as a sanity check: if recognition fails here, the issue is not related to low resolution.

---

## 3. Low resolution, width ≈ 150 px

At **150 px width**, the barcode is smaller but still reasonably detailed.

### 3.1 HighPerformance preset + HIGH quality mode

```java
@Test
public void read_Code128_Width150_PerformancePreset_HighQualityMode() throws Exception {
    BarCodeReader barCodeReader = new BarCodeReader(
            ExampleAssist.pathCombine(FOLDER, FILE_CODE128_LOWRES_WIDTH_150), DecodeType.CODE_128);

    QualitySettings qualitySettings = QualitySettings.getHighPerformance();
    qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);
    barCodeReader.setQualitySettings(qualitySettings);

    ExampleAssist.assertRecognized(barCodeReader, FILE_CODE128_LOWRES_WIDTH_150, 1, DecodeType.CODE_128);
}
```

How this configuration behaves:

- `getHighPerformance()` starts from a **speed-oriented preset**.
- `BarcodeQualityMode.HIGH` upgrades the quality profile, enabling stronger methods.
- The result is a preset suitable for **small but not tiny** barcodes when performance matters.

Recommended usage:

- Mobile or desktop scanning where barcodes are moderately small but still captured in good conditions.

### 3.2 NormalQuality preset + NORMAL quality mode

```java
@Test
public void read_Code128_Width150_NormalPreset_NormalQualityMode() throws Exception {
    BarCodeReader barCodeReader = new BarCodeReader(
            ExampleAssist.pathCombine(FOLDER, FILE_CODE128_LOWRES_WIDTH_150), DecodeType.CODE_128);

    QualitySettings qualitySettings = QualitySettings.getNormalQuality();
    qualitySettings.setBarcodeQuality(BarcodeQualityMode.NORMAL);
    barCodeReader.setQualitySettings(qualitySettings);

    ExampleAssist.assertRecognized(barCodeReader, FILE_CODE128_LOWRES_WIDTH_150, 1, DecodeType.CODE_128);
}
```

Here:

- Only the **preset** changes; there are no X-dimension hints.
- When the low-resolution image is crisp and well padded, **balanced settings are still sufficient**.

---

## 4. Low resolution, width ≈ 80 px

At **80 px width**, module width approaches 1–2 pixels and correctly detecting bars becomes harder.  
This is where **X-dimension hints** and **quality mode** start to matter.

### 4.1 HighPerformance + USE_MINIMAL_X_DIMENSION + MinimalXDimension

```java
@Test
public void read_Code128_Width80_PerformancePreset_MinimalXDim_HighQualityMode() throws Exception {
    BarCodeReader barCodeReader = new BarCodeReader(
            ExampleAssist.pathCombine(FOLDER, FILE_CODE128_LOWRES_WIDTH_80), DecodeType.CODE_128);

    QualitySettings qualitySettings = QualitySettings.getHighPerformance();
    qualitySettings.setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION); // enable MinimalXDimension hint
    qualitySettings.setMinimalXDimension(1.0f);                            // expected minimal module width in pixels
    qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);
    barCodeReader.setQualitySettings(qualitySettings);

    ExampleAssist.assertRecognized(barCodeReader, FILE_CODE128_LOWRES_WIDTH_80, 1, DecodeType.CODE_128);
}
```

Important parameters:

- `setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION)`  
  Switches the detector into a mode where `MinimalXDimension` is taken into account.

- `setMinimalXDimension(1.0f)`  
  Provides a **heuristic lower bound** (in pixels) for expected module size. The engine treats modules thinner than `MinimalXDimension` as unlikely candidates and prioritizes detection around this scale and above.

- `BarcodeQualityMode.HIGH`  
  Enables more robust preprocessing, which helps when bars are only 1–2 pixels wide.

This combination is a good template for **tiny but still crisp** barcodes.

### 4.2 NormalQuality, no XDimension hints

```java
@Test
public void read_Code128_Width80_NormalPreset_NoHints_NormalQualityMode() throws Exception {
    BarCodeReader barCodeReader = new BarCodeReader(
            ExampleAssist.pathCombine(FOLDER, FILE_CODE128_LOWRES_WIDTH_80), DecodeType.CODE_128);

    QualitySettings qualitySettings = QualitySettings.getNormalQuality();
    qualitySettings.setBarcodeQuality(BarcodeQualityMode.NORMAL);
    barCodeReader.setQualitySettings(qualitySettings);

    ExampleAssist.assertRecognized(barCodeReader, FILE_CODE128_LOWRES_WIDTH_80, 1, DecodeType.CODE_128);
}
```

Here:

- The engine relies on **internal heuristics** to infer X-dimension.
- It can still succeed on a crisp image, but is more sensitive to module quantization and quiet zones.

Use this configuration if:

- you prefer simpler setup and testing shows that images are consistently readable, or
- you do not want to tune XDimension hints yet.

---

## 5. Very low resolution, width ≈ 40 px

At **40 px width**, the barcode is near the practical resolution limit.  
Modules are roughly 1 pixel wide, and even slight blur or interpolation can break recognition.

The example demonstrates two **edge-case positive** scenarios — they show what is possible, not what is universally guaranteed.

### 5.1 HighQuality preset + USE_MINIMAL_X_DIMENSION + HIGH quality mode

```java
@Test
public void read_Code128_Width40_Negative_TooSmallEvenWhenCrisp() throws Exception {
    BarCodeReader barCodeReader = new BarCodeReader(
            ExampleAssist.pathCombine(FOLDER, FILE_CODE128_LOWRES_WIDTH_40), DecodeType.CODE_128);

    QualitySettings qualitySettings = QualitySettings.getHighQuality();
    qualitySettings.setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION);
    qualitySettings.setMinimalXDimension(1.0f);
    qualitySettings.setBarcodeQuality(BarcodeQualityMode.HIGH);
    barCodeReader.setQualitySettings(qualitySettings);

    ExampleAssist.assertRecognized(barCodeReader, currentMethodName(), 1, DecodeType.CODE_128);
}
```

Behavior:

- `getHighQuality()` enables a **heavier** recognition pipeline.
- `XDimensionMode.USE_MINIMAL_X_DIMENSION` together with `MinimalXDimension` strongly bias detection towards very small modules of around 1 px.
- `BarcodeQualityMode.HIGH` makes the engine more tolerant to borderline cases.

This is the **most tolerant** configuration in this example and shows that even extremely small symbols can be decoded **if**:

- they are rendered crisply,
- quiet zones are respected,
- and the capturing device does not add blur or resampling artifacts.

### 5.2 HighPerformance preset + LOW quality mode

```java
@Test
public void read_Code128_Width40_Negative_PerformancePreset_LowQualityMode() throws Exception {
    BarCodeReader barCodeReader = new BarCodeReader(
            ExampleAssist.pathCombine(FOLDER, FILE_CODE128_LOWRES_WIDTH_40), DecodeType.CODE_128);

    QualitySettings qualitySettings = QualitySettings.getHighPerformance();
    qualitySettings.setBarcodeQuality(BarcodeQualityMode.LOW);
    barCodeReader.setQualitySettings(qualitySettings);

    ExampleAssist.assertRecognized(barCodeReader, currentMethodName(), 1, DecodeType.CODE_128);
}
```

This test is intentionally **aggressive**:

- Performance-oriented preset (`getHighPerformance()`),
- `BarcodeQualityMode.LOW` relaxes quality to favor speed even more.

On the synthetic, crisp sample in the test, recognition still succeeds, but in real-world conditions this configuration is likely to be fragile for such a tiny barcode.

Treat it as:

- a **limit-case demonstration** of the engine’s capability, not a general recommendation.

---

## 6. Practical recommendations

Based on the patterns in `ReadingLowResolutionBarcodeExample`:

1. **Generate crisp low-resolution barcodes**
    - Prefer rendering directly at the target pixel size over resampling larger images.
    - Use enough bar height and quiet zones so that the symbol occupies most of the useful area.

2. **Start with balanced settings for moderate sizes (≥ 150 px)**
    - Use `QualitySettings.getNormalQuality()` with `BarcodeQualityMode.NORMAL`, or
    - `QualitySettings.getHighPerformance()` with `BarcodeQualityMode.HIGH` if you need more speed.

3. **For small symbols (≈ 80 px)**
    - Enable X-dimension hints:
        - `setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION);`
        - `setMinimalXDimension(1.0f);`
    - Use at least `BarcodeQualityMode.HIGH` on a suitable preset.

4. **For extremely small symbols (≈ 40 px)**
    - Use **HighQuality** preset plus:
        - `XDimensionMode.USE_MINIMAL_X_DIMENSION`,
        - `MinimalXDimension` around 1.0 px,
        - `BarcodeQualityMode.HIGH`.
    - Understand that this is near the physical resolution limit; any blur or scaling can make such barcodes unreadable.

5. **Always validate on your own images**
    - The examples use synthetic, crisp test data.
    - For production, run similar experiments on real screenshots or camera captures and adjust:
        - target width,
        - X-dimension hints,
        - quality mode,
        - and presets accordingly.

---

All code samples in this article are derived from:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/ReadingLowResolutionBarcodeExample.java" target="_blank" rel="noopener noreferrer">ReadingLowResolutionBarcodeExample.java</a>

Use this class as a reference when tuning Aspose.BarCode for Java to work reliably with low-resolution barcodes.

---

**Note – how the example generates low-resolution fixtures**

In the sample project, the test data is generated programmatically so that all images share the same payload and differ only by size and rendering parameters.

Typical setup in `ReadingLowResolutionBarcodeExample` looks like this:

```java
private static final String FOLDER =
        ExampleAssist.getOrCreateResourceFolderPath("recognition", "quality", "reading_low_resolution");

// Descriptive file names
private static final String FILE_CODE128_CLEAN_BASE = "code128_clean_width_600px.png";
private static final String FILE_CODE128_LOWRES_WIDTH_150 = "code128_low_resolution_width_150px.png";
private static final String FILE_CODE128_LOWRES_WIDTH_80  = "code128_low_resolution_width_80px.png";
private static final String FILE_CODE128_LOWRES_WIDTH_40  = "code128_low_resolution_width_40px.png";

private static final String PAYLOAD_TEXT = "LowRes:CODE128";

@BeforeClass
public void setUp() throws Exception {
    LicenseAssist.setupLicense();
    generateCode128Base();
    generateLowResVariants();
}
```

The clean baseline is created once with comfortable X-dimension and quiet zones:

```java
private void generateCode128Base() throws Exception {
    ExampleAssist.checkOrCreateImage(FOLDER, FILE_CODE128_CLEAN_BASE, path -> {
        BarcodeGenerator barcodeGenerator = new BarcodeGenerator(EncodeTypes.CODE_128, PAYLOAD_TEXT);
        barcodeGenerator.getParameters().getBarcode().getXDimension().setPixels(3.0f);
        barcodeGenerator.getParameters().getBarcode().getPadding().getLeft().setPixels(40f);
        barcodeGenerator.getParameters().getBarcode().getPadding().getRight().setPixels(40f);
        barcodeGenerator.getParameters().getBarcode().getPadding().getTop().setPixels(20f);
        barcodeGenerator.getParameters().getBarcode().getPadding().getBottom().setPixels(20f);
        barcodeGenerator.save(path, BarCodeImageFormat.PNG);
    });
}
```

Low-resolution variants are rendered directly at the target pixel width:

```java
private void generateLowResVariants() throws Exception {
    final int heightPx = 140;
    final int quietPx  = 12;

    ExampleAssist.checkOrCreateImage(FOLDER, FILE_CODE128_LOWRES_WIDTH_150,
            out -> ExampleAssist.renderBarcodeFixedSizePNG(
                    EncodeTypes.CODE_128, PAYLOAD_TEXT,
                    /*widthPx*/150, /*heightPx*/heightPx,
                    /*xDimPx*/2.0f, /*quietPx*/quietPx, out));

    ExampleAssist.checkOrCreateImage(FOLDER, FILE_CODE128_LOWRES_WIDTH_80,
            out -> ExampleAssist.renderBarcodeFixedSizePNG(
                    EncodeTypes.CODE_128, PAYLOAD_TEXT,
                    /*widthPx*/80, /*heightPx*/heightPx,
                    /*xDimPx*/1.2f, /*quietPx*/quietPx, out));

    ExampleAssist.checkOrCreateImage(FOLDER, FILE_CODE128_LOWRES_WIDTH_40,
            out -> ExampleAssist.renderBarcodeFixedSizePNG(
                    EncodeTypes.CODE_128, PAYLOAD_TEXT,
                    /*widthPx*/40, /*heightPx*/heightPx,
                    /*xDimPx*/1.0f, /*quietPx*/quietPx, out));
}
```

The helper `renderBarcodeFixedSizePNG(...)` is responsible for:

- drawing a crisp, binarized barcode,
- fitting it into a fixed canvas (width × height),
- aligning modules to the pixel grid as much as possible.

This avoids post-resampling artifacts (no blur, no scaling in external tools) and provides **clean but tiny** barcodes.

You can use a similar approach in your own test suite to generate controlled low-resolution fixtures and experiment with different recognition settings.