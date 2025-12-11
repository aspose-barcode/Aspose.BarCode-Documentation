---
title: "High Performance Mode"
description: "Learn how to use the High Performance quality preset in Aspose.BarCode for Java recognition."
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/performance/high-performance-mode
---

# High Performance Mode

`QualitySettings.getHighPerformance()` is a preset that configures the recognition engine for **maximum speed** on **clean, well‑printed barcodes**.

Compared to `getNormalQuality()` or `getHighQuality()`, the High Performance preset:

- prefers **fast detection paths** and simplified preprocessing
- assumes **good image quality** (sharp edges, sufficient resolution, good contrast)
- is ideal for **production scanners**, **back‑office batch jobs**, and other scenarios where input is controlled

This article shows how to:

- enable High Performance mode for 1D and 2D barcodes
- combine it with **type filters** (`DecodeType`) for extra speed
- use **1D/2D groups** when you only know the category of symbology

All examples are based on the sample class:

`com.aspose.barcode.guide.recognition.performance.HighPerformanceModeExample`

Source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/HighPerformanceModeExample.java" target="_blank" rel="noopener noreferrer">HighPerformanceModeExample.java</a>

Paths like `imagePath` in the snippets below refer to your own image locations.

---

## 1. Reading a QR code with High Performance

The simplest pattern: generate a clean QR code, enable High Performance, and verify that it is recognized.

```java
String fileName = "qr_hp.png";
String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);

// Generate fixture if needed
ExampleAssist.checkOrCreateImage(FOLDER, fileName, path -> {
    BarcodeGenerator barcodeGenerator = new BarcodeGenerator(EncodeTypes.QR, "HP-QR");
    // Slightly larger modules for robust detection with HighPerformance
    barcodeGenerator.getParameters().getBarcode().getXDimension().setPixels(4);
    barcodeGenerator.save(path, BarCodeImageFormat.PNG);
});

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);

// Enable High Performance preset
barCodeReader.setQualitySettings(QualitySettings.getHighPerformance());

// Expect a single QR result
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.QR);
```

Key points:

- Use `QualitySettings.getHighPerformance()` when you **control how codes are printed** and captured (for example, your own labels, office scanners).
- Make sure modules/bars are not too small; increasing `XDimension` on generation side makes life easier for a speed‑oriented preset.

---

## 2. Fast Code 128 recognition

High Performance mode is especially suitable for **1D symbologies** used in logistics, inventory, and POS systems.

```java
String fileName = "code128_hp.png";
String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);

// Generate Code 128 sample
ExampleAssist.checkOrCreateImage(FOLDER, fileName, path -> {
    BarcodeGenerator barcodeGenerator = new BarcodeGenerator(EncodeTypes.CODE_128, "FAST-128");
    barcodeGenerator.save(path, BarCodeImageFormat.PNG);
});

// Recognize using High Performance
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
barCodeReader.setQualitySettings(QualitySettings.getHighPerformance());

ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.CODE_128);
```

Use this pattern when you want **low latency** and you know that:

- the symbol type is fixed (`DecodeType.CODE_128` in this example)
- the print quality and capture conditions are under your control

---

## 3. Limiting the symbology set for extra speed

Even with High Performance, you can still waste time if the engine has to consider many symbologies.  
A common optimization is to:

1. Construct the reader with `DecodeType.ALL_SUPPORTED_TYPES`.
2. Limit the set of **actual candidates** using `setBarCodeReadType(...)`.

Example: image contains a **Data Matrix**, but you know that only Code 128, QR, or Data Matrix are possible.

```java
String fileName = "limited_types_hp.png";
String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);

// Generate Data Matrix sample
ExampleAssist.checkOrCreateImage(FOLDER, fileName, path -> {
    BarcodeGenerator barcodeGenerator = new BarcodeGenerator(EncodeTypes.DATA_MATRIX, "HP-DM");
    barcodeGenerator.save(path, BarCodeImageFormat.PNG);
});

// Reader scans all supported types, but we will narrow the set
BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.ALL_SUPPORTED_TYPES);

// Speed‑oriented preset
barCodeReader.setQualitySettings(QualitySettings.getHighPerformance());

// Limit recognition to a small subset of types
barCodeReader.setBarCodeReadType(
        DecodeType.CODE_128,
        DecodeType.QR,
        DecodeType.DATA_MATRIX
);

// Expect one Data Matrix result
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.DATA_MATRIX);
```

Benefits:

- **Fewer detector branches** → less work per frame.
- Easier to debug: if something unexpected is recognized, you know it is one of the allowed types.

---

## 4. Scanning any 1D barcode with `TYPES_1D`

Sometimes you do not know the exact 1D symbology, but you know it will be **linear** (EAN, UPC, Code 39, Code 128, etc.).  
In that case you can use `DecodeType.TYPES_1D` together with High Performance.

Example: recognize any 1D barcode, here using EAN‑13 as a fixture.

```java
String fileName = "types_1d_hp.png";
String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);

// Generate EAN-13 sample (scanner-grade)
ExampleAssist.checkOrCreateImage(FOLDER, fileName, path -> {
    BarcodeGenerator barcodeGenerator = new BarcodeGenerator(EncodeTypes.EAN_13, "5901234123457");
    barcodeGenerator.save(path, BarCodeImageFormat.PNG);
});

// Reader restricted to the 1D group
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.TYPES_1D);
barCodeReader.setQualitySettings(QualitySettings.getHighPerformance());

// Expect EAN-13 among 1D types
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.EAN_13);
```

Notes:

- `DecodeType.TYPES_1D` is a **group flag** that covers many linear symbologies.
- Combining a **group** with **High Performance** is a good default for fast handheld scanners where:
    - the physical labels are well‑printed,
    - the application does not care which exact 1D symbology is used.

---

## 5. High Performance mode: practical recommendations

When to use `QualitySettings.getHighPerformance()`:

- Inputs are **clean and predictable**:
    - printed on high‑quality labels,
    - captured by stationary scanners or well‑lit cameras,
    - little to no blur, skew, or heavy noise.
- You need **throughput**:
    - scanning many items per second,
    - minimizing CPU usage on the server or mobile device.
- You are ready to **tune type filters** (`DecodeType`).

When you might prefer `getNormalQuality()` or `getHighQuality()`:

- users scan codes from **paper receipts**, **screens**, or **user‑generated content**
- there is noticeable **blur**, **motion**, or **low resolution**
- you do not fully control **lighting conditions** or **camera focus**

A common pattern is to:

1. Try `HighPerformance` first for fast UX.
2. If recognition fails or confidence is low, fall back to a **slower preset** on the same frame.

---

## Summary

High Performance mode in Aspose.BarCode for Java is a preset that prioritizes **speed over aggressive error recovery**.  
Using it effectively involves three main ideas:

- Enable it via `barCodeReader.setQualitySettings(QualitySettings.getHighPerformance())`.
- Keep barcodes **clean and sufficiently large** (adjust `XDimension` during generation).
- Narrow down the recognition space with **type filters**:
    - single type, like `DecodeType.QR` or `DecodeType.CODE_128`
    - groups, such as `DecodeType.TYPES_1D`
    - custom subsets via `setBarCodeReadType(...)`.

All code snippets in this article are derived from:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/performance/HighPerformanceModeExample.java" target="_blank" rel="noopener noreferrer">HighPerformanceModeExample.java</a>

Use this sample as a template when wiring High Performance mode into your own Java applications.
