---
title: False Positives
description: "How to reduce incorrect matches by restricting types and validating results."
type: docs
weight: 20
url: /java/developer-guide/barcode-recognition/troubleshooting/false-positives
---

# False Positives

False positives happen when the engine interprets image patterns as a barcode.
The most effective way to reduce false positives is to limit the search space and validate results.

## Restrict symbologies

Searching for "all supported types" increases the chance of misinterpreting noise as a simple barcode (like Code 39 or Interleaved 2 of 5). Always specify exact types if known.

```java
BarCodeReader reader = new BarCodeReader(
        "input.png",
        DecodeType.CODE_128,
        DecodeType.QR
);
```

## Use ROI to ignore unrelated content

If the barcode is always in a specific area, tell the reader where to look. This excludes noise from the rest of the image.

```java
Rectangle roi = new Rectangle(20, 20, 440, 140);
BarCodeReader reader = new BarCodeReader("input.png", roi, DecodeType.CODE_128);
```

## Apply confidence threshold

Each result has a confidence score from **0 to 100**. Real barcodes usually have high confidence (often 100). False positives typically have lower scores.

```java
BarCodeReader reader = new BarCodeReader("input.png", DecodeType.ALL_SUPPORTED_TYPES);

for (BarCodeResult result : reader.readBarCodes()) {
    // Only accept results with high confidence
    if (result.getConfidence() >= 90) {
        System.out.println("Accepted: " + result.getCodeText());
    }
}
```
