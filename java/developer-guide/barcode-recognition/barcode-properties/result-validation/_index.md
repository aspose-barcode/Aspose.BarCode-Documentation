---
title: "Result Validation"
description: "Learn how to validate recognition results and use checksums, confidence, and quality settings in Aspose.BarCode for Java."
type: docs
weight: 60
url: /java/developer-guide/barcode-recognition/barcode-properties/result-validation
---

# Result validation in barcode recognition

When you integrate barcode recognition into a real system (logistics, retail, tickets, access control), you need more than just “a result was found”.  
You also want to answer questions like:

- Is this barcode **checksum-correct**?
- How **confident** is the engine in this read?
- Should I accept a **damaged** or **low-quality** symbol?
- Which **quality preset** should I use for difficult images?

Aspose.BarCode for Java provides several mechanisms to validate and qualify recognition results:

- checksum handling and 1D metadata (`OneDExtendedParameters`)
- the `confidence` score on `BarCodeResult`
- `QualitySettings`, including `setAllowIncorrectBarcodes(...)` and preset profiles

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.barcode_properties.ResultValidationExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/ResultValidationExample.java" target="_blank" rel="noopener noreferrer">ResultValidationExample.java</a>

In the snippets below, variables like `imagePath` represent paths to barcode images in your application.

---

## 1. Validating checksums for 1D barcodes (EAN‑13)

Most linear (1D) symbologies, such as EAN‑13, UPC, Code 128, and others, include a **checksum digit**.  
Aspose.BarCode validates this checksum internally and also exposes it via extended parameters.

A common pattern is:

1. Disable incorrect barcodes via `QualitySettings.setAllowIncorrectBarcodes(false)`.
2. Read the barcode.
3. Inspect the OneD checksum metadata if needed.

Example: validating an EAN‑13 symbol and reading its checksum value.

```java
String imagePath = "rv_ean13_valid.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.EAN_13);
barCodeReader.getQualitySettings().setAllowIncorrectBarcodes(false);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeResult barCodeResult = barCodeResults[0];

    System.out.println("EAN-13 text      = " + barCodeResult.getCodeText());
    System.out.println("EAN-13 confidence= " + barCodeResult.getConfidence());

    BarCodeExtendedParameters barCodeExtendedParameters = barCodeResult.getExtended();
    if (barCodeExtendedParameters != null && barCodeExtendedParameters.getOneD() != null) {
        OneDExtendedParameters oneDExtendedParameters = barCodeExtendedParameters.getOneD();
        System.out.println("OneD checksum    = " + oneDExtendedParameters.getCheckSum());
    }
}
```

Key points:

- With `setAllowIncorrectBarcodes(false)`, the engine **filters out** reads with invalid checksums where it can detect them.
- `barCodeResult.getExtended().getOneD().getCheckSum()` exposes the checksum that was calculated from the bars.
- This checksum can be logged or compared against expectations (for example, when implementing custom validation rules).

If the image is severely damaged, the engine may return no results at all instead of a low-confidence, checksum-invalid candidate. This is usually desirable in production systems.

---

## 2. Allowing vs. disallowing incorrect barcodes on damaged input

For heavily degraded barcodes, you may want to **inspect borderline candidates** even if the checksum fails.  
Aspose.BarCode lets you choose between strict and lenient behavior using `setAllowIncorrectBarcodes(...)`.

Example: comparing results on a damaged Code 39 barcode.

```java
String imagePath = "rv_code39_damaged.png";

// Strict mode: incorrect barcodes are filtered out
BarCodeReader barCodeReaderStrict = new BarCodeReader(imagePath, DecodeType.CODE_39);
barCodeReaderStrict.getQualitySettings().setAllowIncorrectBarcodes(false);
BarCodeResult[] strictResults = barCodeReaderStrict.readBarCodes();
int strictCount = strictResults.length;

// Lenient mode: allow potentially incorrect barcodes
BarCodeReader barCodeReaderLenient = new BarCodeReader(imagePath, DecodeType.CODE_39);
barCodeReaderLenient.getQualitySettings().setAllowIncorrectBarcodes(true);
BarCodeResult[] lenientResults = barCodeReaderLenient.readBarCodes();
int lenientCount = lenientResults.length;

System.out.println("[Code39 damaged] strict=" + strictCount + " | lenient=" + lenientCount);
if (lenientCount > 0) {
    BarCodeResult firstLenient = lenientResults[0];
    System.out.println("  lenient first: text=" + firstLenient.getCodeText()
            + " conf=" + firstLenient.getConfidence());
}
```

How to interpret this:

- In **strict mode**, you usually get **fewer results** but they are checksum-correct where checksums exist.
- In **lenient mode**, you may see **more candidates**, including reads that fail checksum validation or look suspicious.
- Lenient mode can be useful when you want to implement your own custom validation or diagnostics pipeline, while strict mode is more appropriate for production acceptance.

A typical production setup:

- use **strict mode** (`allowIncorrectBarcodes = false`) for live validation,
- optionally run **lenient mode** in a secondary diagnostic pass if you need to investigate why a given image is hard to read.

---

## 3. Comparing confidence for clean vs. noisy images

Every `BarCodeResult` includes a **confidence score** (0–100).  
Although this is not a formal probability, it is a useful heuristic for comparing reads of the **same barcode** under different conditions.

Example: comparing recognition confidence between a clean QR code and a noisy QR code.

```java
String cleanImagePath = "rv_qr_clean.png";
String noisyImagePath = "rv_qr_noisy.png";

BarCodeReader cleanReader = new BarCodeReader(cleanImagePath, DecodeType.QR);
cleanReader.setQualitySettings(QualitySettings.getHighQuality());
BarCodeResult[] cleanResults = cleanReader.readBarCodes();

BarCodeReader noisyReader = new BarCodeReader(noisyImagePath, DecodeType.QR);
noisyReader.setQualitySettings(QualitySettings.getHighQuality());
BarCodeResult[] noisyResults = noisyReader.readBarCodes();

if (cleanResults.length > 0 && noisyResults.length > 0) {
    double cleanConfidence = cleanResults[0].getConfidence();
    double noisyConfidence = noisyResults[0].getConfidence();

    System.out.println("[QR] clean confidence = " + cleanConfidence
            + " vs noisy = " + noisyConfidence);
}
```

Typical expectations:

- Clean, well-printed codes tend to produce **higher confidence** than heavily degraded ones.
- You can log these values to understand how different imaging conditions affect recognition quality.
- In some workflows, you can enforce a **minimum confidence threshold** before accepting a result (for example, only accept confidence ≥ 60), while still combining this with checksum and business rules.

Use the confidence value only to compare results on the same barcode or image (for example, clean vs. noisy input or different presets), and do not treat it as a calibrated probability that the result is correct.

---

## 4. Using quality presets for difficult barcodes

Aspose.BarCode provides several `QualitySettings` presets, such as:

- `QualitySettings.getHighPerformance()` — optimized for speed.
- `QualitySettings.getHighQuality()` — optimized for robustness on difficult inputs.

A common validation pattern is to try more than one preset when dealing with **tiny**, **noisy**, or **distorted** barcodes.

Example: reading a very small Code 128 symbol with both presets.

```java
String imagePath = "rv_c128_tiny.png";

BarCodeReader barCodeReaderHighPerformance = new BarCodeReader(imagePath, DecodeType.CODE_128);
barCodeReaderHighPerformance.setQualitySettings(QualitySettings.getHighPerformance());
BarCodeResult[] highPerformanceResults = barCodeReaderHighPerformance.readBarCodes();

BarCodeReader barCodeReaderHighQuality = new BarCodeReader(imagePath, DecodeType.CODE_128);
barCodeReaderHighQuality.setQualitySettings(QualitySettings.getHighQuality());
BarCodeResult[] highQualityResults = barCodeReaderHighQuality.readBarCodes();

System.out.println("[Tiny Code 128] HighPerformance count=" + highPerformanceResults.length
        + (highPerformanceResults.length > 0
            ? (" conf=" + highPerformanceResults[0].getConfidence()) : "")
        + " | HighQuality count=" + highQualityResults.length
        + (highQualityResults.length > 0
            ? (" conf=" + highQualityResults[0].getConfidence()) : ""));
```

How to use this pattern:

- Start with a **default preset** that balances speed and quality for your use case.
- For difficult inputs (tiny, low-resolution, compressed images), try `HighQuality` on a subset of images or as a fallback.
- Compare both **result count** and **confidence** to decide which preset works better for a particular input type.

In many real systems, you might:

1. Run a fast pass (for example, `HighPerformance`) for all frames or pages.
2. If nothing is found or confidence is too low, re-run a **second pass** with `HighQuality` on the same image.

---

## Summary

Result validation in Aspose.BarCode for Java combines several independent signals:

- **Checksum validation**
    - Use `QualitySettings.setAllowIncorrectBarcodes(false)` to filter out invalid 1D reads where possible.
    - Inspect `OneDExtendedParameters.getCheckSum()` when you need explicit checksum information.
- **Confidence score**
    - `BarCodeResult.getConfidence()` (0–100) is useful for comparing reads on the same barcode under different conditions.
    - You can log confidence or enforce minimum thresholds in your own business logic.
- **Quality presets**
    - `QualitySettings.getHighPerformance()` vs `QualitySettings.getHighQuality()` let you balance speed and robustness.
    - Running multiple presets on difficult images can significantly improve overall reliability.

All examples shown here are based on:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/ResultValidationExample.java" target="_blank" rel="noopener noreferrer">ResultValidationExample.java</a>

Use these patterns as a reference when designing result validation logic and acceptance criteria in your barcode-based Java applications.

