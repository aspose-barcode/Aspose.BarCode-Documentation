---
title: "Checksum validation"
description: "Learn how checksum validation modes influence barcode recognition results in Aspose.BarCode for Java."
type: docs
weight: 30
url: /java/developer-guide/barcode-recognition/checksum-validation
---

# Checksum validation

Many linear symbologies include a check digit that protects the payload from typical reading errors.  
Aspose.BarCode for Java exposes this logic via the `ChecksumValidation` setting in `BarcodeSettings`.  
By changing this mode you can decide whether symbols with **invalid** or **untrusted** checksums:

- are rejected completely, or
- are still returned to your application for further inspection.

This article shows how `ChecksumValidation` behaves on EAN‑13 barcodes using the sample test class:

`com.aspose.barcode.guide.recognition.special_parameters.ChecksumValidationExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/special_parameters/ChecksumValidationExample.java" target="_blank" rel="noopener noreferrer">ChecksumValidationExample.java</a>

All examples below use EAN‑13, which always carries a mandatory check digit.

---

## ChecksumValidation modes

`ChecksumValidation` controls how the recognition engine treats barcodes whose checksum does not match the decoded data:

| Mode value                 | Behavior on valid symbol                  | Behavior on damaged or invalid checksum                | Typical use case                          |
|---------------------------|-------------------------------------------|--------------------------------------------------------|-------------------------------------------|
| `ChecksumValidation.ON`   | Valid codes are returned as usual         | Codes that fail checksum validation are **discarded**  | Production scanning, strict data quality  |
| `ChecksumValidation.OFF`  | Valid codes are still returned            | Codes may be returned **even if checksum is wrong**    | Forensics, debugging, best-effort reads   |
| `ChecksumValidation.DEFAULT` | Engine uses its **default policy** per symbology (for EAN/UPC it validates checksums) | Damaged codes are typically **filtered out** similar to `ON` | Safe defaults when you do not want to tune per type |

In all snippets below, the input image is created in the test fixture and then read with different checksum policies.

---

## 1. Reading a valid EAN‑13 with checksum enabled

The first test generates a **valid** EAN‑13 barcode with a correct check digit and reads it with `ChecksumValidation.ON`:

```java
String fileName = "ean13_valid.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.EAN_13, "5901234123457");
    barcodeGenerator.save(fullPath);
});

BarCodeReader barCodeReader =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.EAN_13);
barCodeReader.getBarcodeSettings().setChecksumValidation(ChecksumValidation.ON);

ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.EAN_13);
```

Key points:

- For a correct symbol, enabling checksum validation **does not change** recognition behavior.
- This is the **safest** configuration for production EAN/UPC scanners: any decoding error that breaks the checksum will automatically filter out the result.

---

## 2. Damaged EAN‑13 with ChecksumValidation.ON

The helper method `generateDamagedEan13` first creates a valid EAN‑13 and then draws a black stripe across part of the bar pattern:

```java
private void generateDamagedEan13(String data, String fileName, BaseEncodeType type) throws IOException {
    String testImagePath =
            ExampleAssist.generateTestBarcode(data, FOLDER, fileName, type);

    File testFile = new File(testImagePath);
    BufferedImage image = ImageIO.read(testFile);
    Graphics2D graphics = image.createGraphics();
    try {
        graphics.setColor(Color.BLACK);
        int width = image.getWidth();
        int height = image.getHeight();

        int stripeWidth = Math.max(6, width / 12);
        graphics.fillRect(width / 2 - stripeWidth / 2,
                          height / 5,
                          stripeWidth,
                          (int) (height * 0.6));
    } finally {
        graphics.dispose();
    }

    ImageIO.write(image, "PNG", Path.of(testImagePath).toFile());
}
```

When this **damaged** barcode is read with `ChecksumValidation.ON`, the engine detects that the checksum is no longer consistent and discards the result:

```java
String fileName = "ean13_damaged_on.png";
generateDamagedEan13("5901234123457", fileName, EncodeTypes.EAN_13);

BarCodeReader barCodeReader =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.EAN_13);
barCodeReader.getBarcodeSettings().setChecksumValidation(ChecksumValidation.ON);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
System.out.println("Checksum=ON, detected: " + barCodeResults.length);

ExampleAssist.assertRecognized(barCodeReader, fileName, 0, DecodeType.EAN_13);
```

Outcome:

- `barCodeResults.length` is expected to be **0**.
- This mirrors the default behavior of many retail scanners: if the checksum fails, the symbol is treated as unreadable.

---

## 3. Damaged EAN‑13 with ChecksumValidation.OFF

If you explicitly turn checksum validation **off**, the same damaged image can still produce results:

```java
String fileName = "ean13_damaged_off.png";
generateDamagedEan13("5901234123457", fileName, EncodeTypes.EAN_13);

BarCodeReader barCodeReader =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.EAN_13);
barCodeReader.getBarcodeSettings().setChecksumValidation(ChecksumValidation.OFF);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
System.out.println("Checksum=OFF, detected: " + barCodeResults.length);
for (BarCodeResult result : barCodeResults) {
    System.out.println("  -> " + result.getCodeTypeName()
            + " | " + result.getCodeText());
}

// Expect at least one "possibly wrong" result to pass through
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.EAN_13);
```

Here:

- The engine is allowed to return **best-effort** decodes even if the checksum is not valid.
- This is useful when:
    - you are analyzing severely damaged labels for **forensics or QA**, or
    - you want to log **what the engine “sees”** even if it does not fully trust the result.

In production user-facing flows, you usually keep validation enabled and only use this mode in diagnostic tools.

---

## 4. Damaged EAN‑13 with ChecksumValidation.DEFAULT

Many symbologies have recommended default behavior for checksum handling.  
For EAN/UPC, the default is to **enforce** the checksum, which is reflected in this test:

```java
String fileName = "ean13_damaged_auto.png";
generateDamagedEan13("5901234123457", fileName, EncodeTypes.EAN_13);

BarCodeReader barCodeReader =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.EAN_13);
barCodeReader.getBarcodeSettings().setChecksumValidation(ChecksumValidation.DEFAULT);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
System.out.println("Checksum=DEFAULT, detected: " + barCodeResults.length);

ExampleAssist.assertRecognized(barCodeReader, fileName, 0, DecodeType.EAN_13);
```

For this damaged EAN‑13:

- `ChecksumValidation.DEFAULT` behaves like `ChecksumValidation.ON` — the barcode is **filtered out**.
- This gives a good **out‑of‑the‑box safety level** when you do not want to manage rules per symbology.

---

## Choosing the right mode

A practical guideline for configuring `ChecksumValidation`:

| Scenario                                         | Recommended mode               | Rationale                                               |
|-------------------------------------------------|--------------------------------|---------------------------------------------------------|
| Retail point‑of‑sale, warehouse scanners        | `ChecksumValidation.ON`        | Strict data integrity; reject any inconsistent symbol. |
| General applications with mixed barcodes        | `ChecksumValidation.DEFAULT`   | Safe defaults per symbology; minimal tuning required.  |
| Debugging misreads, analyzing damaged labels    | `ChecksumValidation.OFF`       | Inspect even invalid decodes for diagnostics.          |
| Offline QA tools that compare print vs master   | `ChecksumValidation.OFF` or `ON` in two passes | Compare how often the checksum gate filters results.   |

When in doubt, start with `DEFAULT`:

- If you see **too many discarded symbols** on imperfect print quality, you can run experiments with `OFF` to see what data the engine is suppressing.
- If your business logic absolutely cannot accept corrupted codes, switch to `ON` explicitly.

---

## Summary

In Aspose.BarCode for Java, `ChecksumValidation` gives you direct control over how strictly recognition should honor checksum rules:

- `ON` — **filter out** any result that fails checksum validation.
- `OFF` — **return** results even if checksums do not match, for diagnostic or best‑effort scenarios.
- `DEFAULT` — follow the engine’s **built‑in policy** per symbology (for EAN/UPC, this usually enforces checksum).

The example class

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/special_parameters/ChecksumValidationExample.java" target="_blank" rel="noopener noreferrer">ChecksumValidationExample.java</a>

illustrates how these modes behave on valid and damaged EAN‑13 images.  
Use the same pattern in your own tests to tune checksum handling for your application’s requirements.
