---
title: "Result Validation"
description: "Learn how to validate barcode recognition results with checksum metadata, confidence values, incorrect-result settings, and quality presets in Aspose.BarCode for Java."
type: docs
weight: 60
url: /java/developer-guide/barcode-recognition/barcode-properties/result-validation/
---

# Result Validation in Barcode Recognition

Barcode recognition should not rely only on whether a result was returned. A production workflow may also need to evaluate checksum information, confidence, recognition settings, and application-specific acceptance rules.

Aspose.BarCode for Java provides several mechanisms that can help validate recognition results:

- checksum-related metadata for one-dimensional barcodes;
- the confidence value exposed by `BarCodeResult`;
- `QualitySettings.setAllowIncorrectBarcodes(...)`;
- quality presets such as `HighPerformance` and `HighQuality`.

The complete source code for the examples in this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/ResultValidationExample.java" target="_blank">View ResultValidationExample.java</a>

## Validate checksum-related metadata

For supported one-dimensional symbologies, recognition results can expose checksum-related information through extended parameters.

The following example reads an EAN-13 barcode, disables incorrect barcode results, and inspects the one-dimensional checksum metadata.

```java
String imagePath = "rv_ean13_valid.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.EAN_13);
reader.getQualitySettings().setAllowIncorrectBarcodes(false);

BarCodeResult[] results = reader.readBarCodes();

if (results.length == 0) {
        throw new IllegalStateException("Expected a valid EAN-13 barcode.");
}

BarCodeResult result = results[0];
BarCodeExtendedParameters extended = result.getExtended();

if (extended == null || extended.getOneD() == null) {
        throw new IllegalStateException("One-dimensional extended parameters are not available.");
}

        System.out.println("Recognized text: " + result.getCodeText());
        System.out.println("Confidence: " + result.getConfidence());
        System.out.println("Checksum: " + extended.getOneD().getCheckSum());
```

`setAllowIncorrectBarcodes(false)` requests stricter filtering of incorrect recognition candidates. If the barcode is severely damaged, the reader may return no result rather than expose an unreliable candidate.

Checksum metadata should be combined with validation of the recognized type, text or bytes, and application rules.

## Compare strict and lenient recognition

For damaged input, you can compare recognition with incorrect barcode results disabled and enabled.

```java
String imagePath = "rv_code39_damaged.png";

BarCodeReader strictReader = new BarCodeReader(imagePath, DecodeType.CODE_39);
strictReader.getQualitySettings().setAllowIncorrectBarcodes(false);
BarCodeResult[] strictResults = strictReader.readBarCodes();

BarCodeReader lenientReader = new BarCodeReader(imagePath, DecodeType.CODE_39);
lenientReader.getQualitySettings().setAllowIncorrectBarcodes(true);
BarCodeResult[] lenientResults = lenientReader.readBarCodes();

System.out.println("Strict count: " + strictResults.length);
System.out.println("Lenient count: " + lenientResults.length);
```

Allowing incorrect results can expose additional candidates for diagnostics. It does not mean that every returned candidate should be accepted.

When lenient recognition is used, validate each candidate carefully:

- confirm the recognized symbology;
- compare the decoded text or bytes with the expected format;
- inspect confidence and checksum metadata where available;
- apply application-specific validation rules.

A common workflow is to use strict recognition for normal processing and lenient recognition only as a diagnostic or fallback step.

## Compare confidence values

Each `BarCodeResult` exposes a confidence value. It can be useful when comparing results produced from the same barcode under different image conditions.

The following example compares a clean QR image with a noisy version of the same barcode.

```java
String cleanImagePath = "rv_qr_clean.png";
String noisyImagePath = "rv_qr_noisy.png";

BarCodeReader cleanReader = new BarCodeReader(cleanImagePath, DecodeType.QR);
cleanReader.setQualitySettings(QualitySettings.getHighQuality());
BarCodeResult[] cleanResults = cleanReader.readBarCodes();

BarCodeReader noisyReader = new BarCodeReader(noisyImagePath, DecodeType.QR);
noisyReader.setQualitySettings(QualitySettings.getHighQuality());
BarCodeResult[] noisyResults = noisyReader.readBarCodes();

if (cleanResults.length == 0 || noisyResults.length == 0) {
    throw new IllegalStateException("Both QR images must be recognized for confidence comparison.");
}

double cleanConfidence = cleanResults[0].getConfidence();
double noisyConfidence = noisyResults[0].getConfidence();

System.out.println("Clean confidence: " + cleanConfidence);
System.out.println("Noisy confidence: " + noisyConfidence);
```

Confidence is a heuristic value, not a calibrated probability that the result is correct.

Use it to compare similar recognition cases, such as:

- clean and degraded versions of the same barcode;
- different quality presets on the same image;
- different capture conditions for the same barcode type.

Do not rely on confidence alone. Combine it with the recognized type, decoded content, checksum information, and business rules.

## Use quality presets for difficult input

Aspose.BarCode provides quality presets that apply different recognition strategies.

Two common presets are:

- `QualitySettings.getHighPerformance()` for faster recognition;
- `QualitySettings.getHighQuality()` for more thorough processing.

The following example compares both presets on a small Code 128 image.

```java
String imagePath = "rv_c128_small.png";

BarCodeReader highPerformanceReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
highPerformanceReader.setQualitySettings(QualitySettings.getHighPerformance());
BarCodeResult[] highPerformanceResults = highPerformanceReader.readBarCodes();

BarCodeReader highQualityReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
highQualityReader.setQualitySettings(QualitySettings.getHighQuality());
BarCodeResult[] highQualityResults = highQualityReader.readBarCodes();

System.out.println("HighPerformance count: " + highPerformanceResults.length);
System.out.println("HighQuality count: " + highQualityResults.length);
```

Different presets can return different candidate counts for the same image. For example, `HighPerformance` may return no result while `HighQuality` detects a candidate.

A detected candidate still requires validation. Check:

- `getCodeType()` for the recognized symbology;
- `getCodeText()` or `getCodeBytes()` for the decoded content;
- `getConfidence()` for diagnostic comparison;
- checksum metadata where supported;
- the expected format and business constraints.

A practical fallback strategy is:

1. Run `HighPerformance` as the initial pass.
2. If no acceptable result is found, run `HighQuality`.
3. Validate the returned candidate before accepting it.

Quality presets influence recognition behavior, but they do not guarantee that every returned candidate is correct.

## Validate the recognized type and content

A result should normally be accepted only after its type and decoded value have been checked.

```java
BarCodeResult result = results[0];

if (!result.getCodeType().equals(DecodeType.CODE_128)) {
        throw new IllegalStateException("Unexpected barcode type: " + result.getCodeType());
        }

        if (!result.getCodeText().matches("[A-Z0-9-]+")) {
        throw new IllegalStateException("Recognized text does not match the expected format.");
}
```

For binary data, validate `getCodeBytes()` instead of converting arbitrary bytes to text.

Validation rules should reflect the actual application. Examples include:

- expected symbology;
- fixed or maximum length;
- numeric-only content;
- required prefixes;
- identifier check digits;
- membership in an application database.

## Recommendations

- Do not accept a result only because the reader returned one candidate.
- Validate the recognized symbology and decoded content.
- Use `setAllowIncorrectBarcodes(false)` for strict recognition workflows.
- Use lenient recognition only when additional diagnostic candidates are useful.
- Treat confidence as a comparative heuristic rather than a probability.
- Use `HighQuality` as a fallback for difficult images when appropriate.
- Validate every candidate returned by a fallback pass.
- Combine engine metadata with application-specific rules.
- Test validation logic on representative clean, noisy, damaged, and low-resolution images.
