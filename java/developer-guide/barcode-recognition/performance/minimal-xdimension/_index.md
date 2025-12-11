---
title: "Minimal XDimension"
description: "Learn how to use MinimalXDimension together with XDimension mode to control recognition of very small barcode modules."
type: docs
weight: 40
url: /java/developer-guide/barcode-recognition/performance/minimal-xdimension
---

# Minimal XDimension in Recognition

When you work with very small barcodes (thin bars or tiny modules), it is useful to give the recognition engine an explicit hint about the **minimal module size** it should expect.

Aspose.BarCode for Java exposes this through:

- `QualitySettings.setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION)`
- `QualitySettings.setMinimalXDimension(float minimalXDimension)`

> Important: The `MinimalXDimension` value is taken into account **only when** `XDimensionMode` is set to `USE_MINIMAL_X_DIMENSION`.  
> For all other XDimension modes (such as `SMALL`, `NORMAL`, or `LARGE`), the engine ignores `MinimalXDimension` and uses the built-in preset module width.

Together these parameters tell the engine:

> Treat modules thinner than `minimalXDimension` pixels as unlikely candidates  
> and prioritize detection around this scale and above.


This article explains how to use these properties based on the sample test class:

`com.aspose.barcode.guide.recognition.performance.MinimalXDimensionExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/MinimalXDimensionExample.java" target="_blank" rel="noopener noreferrer">MinimalXDimensionExample.java</a>

All snippets below use `Code 128` barcodes generated with different X-dimensions.

---

## 1. Test Data: Code 128 with X = 1 px and X = 2 px

The example class generates two synthetic Code 128 images:

- **`code128_x1.png`** – very thin bars (`XDimension = 1 px`)
- **`code128_x2.png`** – more practical minimal bars (`XDimension = 2 px`)

Generation for the 1‑pixel version (edge case):

```java
private void generate_Code128_X1(String fullPath) throws IOException {
    BarcodeGenerator barcodeGenerator = new BarcodeGenerator(EncodeTypes.CODE_128, "MIN-XD-128-X1");
    barcodeGenerator.getParameters().getBarcode().getXDimension().setPixels(1);
    barcodeGenerator.getParameters().getBarcode().getBarHeight().setPixels(60);

    // Quiet zones help tiny modules
    barcodeGenerator.getParameters().getBarcode().getPadding().getLeft().setPixels(16);
    barcodeGenerator.getParameters().getBarcode().getPadding().getRight().setPixels(16);
    barcodeGenerator.getParameters().getBarcode().getPadding().getTop().setPixels(8);
    barcodeGenerator.getParameters().getBarcode().getPadding().getBottom().setPixels(8);

    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
}
```

Generation for the 2‑pixel version:

```java
private void generate_Code128_X2(String fullPath) throws IOException {
    BarcodeGenerator barcodeGenerator = new BarcodeGenerator(EncodeTypes.CODE_128, "MIN-XD-128-X2");
    barcodeGenerator.getParameters().getBarcode().getXDimension().setPixels(2);
    barcodeGenerator.getParameters().getBarcode().getBarHeight().setPixels(60);

    barcodeGenerator.getParameters().getBarcode().getPadding().getLeft().setPixels(20);
    barcodeGenerator.getParameters().getBarcode().getPadding().getRight().setPixels(20);
    barcodeGenerator.getParameters().getBarcode().getPadding().getTop().setPixels(10);
    barcodeGenerator.getParameters().getBarcode().getPadding().getBottom().setPixels(10);

    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
}
```

Quiet zones are slightly larger for tiny modules to keep the symbol stable under downsampling and compression.

---

## 2. Reading X = 1 px with `MinimalXDimension = 1.0f`

In the first test the engine is explicitly allowed to look for modules as small as 1 pixel:

```java
@Test
public void read_Code128_X1_with_MinimalX_1px() throws Exception {
    String fileName = "code128_x1.png";
    checkOrCreateImage(FOLDER, fileName, this::generate_Code128_X1);

    String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);

    BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

    QualitySettings qualitySettings = QualitySettings.getHighQuality();
    qualitySettings.setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION); // respect minimal X
    qualitySettings.setMinimalXDimension(1.0f);                            // accept 1 px modules
    barCodeReader.setQualitySettings(qualitySettings);

    ExampleAssist.assertRecognized(barCodeReader, currentMethodName(), 1, DecodeType.CODE_128);
}
```

**What this does:**

- `XDimensionMode.USE_MINIMAL_X_DIMENSION` switches the detector into a mode where `MinimalXDimension` is taken into account.
- `MinimalXDimension = 1.0f` tells the engine that 1‑pixel bars are acceptable and should be considered during detection.
- A high quality preset is used as a base to keep recognition robust on this edge case.

Use this pattern when you know that barcodes can be extremely small and you still want them to be detected.

---

## 3. Using a Stricter Threshold on the Same Image

In the second test, the same `code128_x1.png` (X = 1 px) is read with a **stricter** minimal X dimension:

```java
@Test
public void read_Code128_X1_with_MinimalX_2px_should_be_stricter() throws Exception {
    String fileName = "code128_x1.png";
    checkOrCreateImage(FOLDER, fileName, this::generate_Code128_X1);

    String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);

    BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

    QualitySettings qualitySettings = QualitySettings.getHighQuality();
    qualitySettings.setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION);
    qualitySettings.setMinimalXDimension(2.0f); // prefer bars at least 2 px wide
    barCodeReader.setQualitySettings(qualitySettings);

    ExampleAssist.assertRecognized(barCodeReader, currentMethodName(), 1, DecodeType.CODE_128);
}
```

Key observations:

- `MinimalXDimension = 2.0f` is now **larger** than the actual bar width in the image.
- In theory this is a stricter hint and may cause very thin symbols to be skipped.
- In this particular synthetic test the engine still manages to decode the barcode, which illustrates that:
    - `MinimalXDimension` is a **heuristic**, not a hard physical limit.
    - The recognizer may still succeed if there is enough contrast and signal quality.

In real projects you can use this pattern to filter out extremely small symbols that should not be considered valid for your workflow (for example, to avoid false positives on noisy screenshots).

---

## 4. Matching XDimension and MinimalXDimension (X = 2 px)

The third test uses a more practical symbol with `XDimension = 2 px` and sets `MinimalXDimension` to the same value:

```java
@Test
public void read_Code128_X2_with_MinimalX_2px() throws Exception {
    String fileName = "code128_x2.png";
    checkOrCreateImage(FOLDER, fileName, this::generate_Code128_X2);

    String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);

    BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

    QualitySettings qualitySettings = QualitySettings.getHighQuality();
    qualitySettings.setXDimension(XDimensionMode.USE_MINIMAL_X_DIMENSION);
    qualitySettings.setMinimalXDimension(2.0f);
    barCodeReader.setQualitySettings(qualitySettings);

    ExampleAssist.assertRecognized(barCodeReader, currentMethodName(), 1, DecodeType.CODE_128);
}
```

Here the hints perfectly match the generated barcode:

- Bars are ~2 pixels wide.
- `MinimalXDimension` is set to 2.0f, so the engine is tuned for that scale.
- This configuration is close to a realistic “small but safe” printing resolution.

Use this approach when you know your production barcodes will not be thinner than a specific bar width and you want to optimize detection for that range.

---

## 5. When to Use `MinimalXDimension`

Use `MinimalXDimension` together with `XDimensionMode.USE_MINIMAL_X_DIMENSION` when:

- Your images contain **very small barcodes** (for example, screenshots, tiny labels, dense layouts).
- You want to **narrow the search space** and reduce false positives from noise that looks like sub‑pixel bars.
- You have a known **minimal print size** (for example, at 300 DPI your minimal bar is 4 mils), and you can convert it to pixels in your capture pipeline.

General recommendations:

- For unknown sources and mixed image quality, start with a **conservative** value (for example, 1–2 pixels) and adjust based on tests.
- For controlled environments (industrial scanners, fixed camera setups), set `MinimalXDimension` to the **smallest bar you expect** in production to improve stability and performance.
- Always combine this with an appropriate preset: `QualitySettings.getHighQuality()` gives the engine more tools to recover tiny modules.

---

## Summary

`MinimalXDimension` is a powerful tuning parameter for recognition in Aspose.BarCode for Java:

- It acts as a **lower bound** for module size in pixels.
- It is **only applied** when `XDimensionMode.USE_MINIMAL_X_DIMENSION` is set in `QualitySettings`. For all other modes the hint is ignored.
- It can help:
    - detect **very small** symbols when set to a low value (for example, `1.0f`),
    - or **filter out** unrealistic thin patterns when set higher (for example, `2.0f` or more).

The examples in

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/MinimalXDimensionExample.java" target="_blank" rel="noopener noreferrer">MinimalXDimensionExample.java</a>

demonstrate typical usage patterns with Code 128 and can be used as a template when configuring recognition for your own applications.

