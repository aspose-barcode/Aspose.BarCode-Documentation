---
title: "Reading Code Text"
description: "Learn how to read and interpret barcode code text and raw data with BarCodeReader in Aspose.BarCode for Java."
type: docs
weight: 30
url: /java/developer-guide/barcode-recognition/barcode-properties/reading-code-text
---

# Reading Code Text and Raw Data

When Aspose.BarCode for Java recognizes a barcode, it returns both:

- human-readable **code text** as a `String`
- underlying **raw bytes** as a `byte[]`

Understanding the difference between these two representations is important when you:

- work with non-ASCII encodings (UTF-8, Unicode payloads)
- process GS1 barcodes with Application Identifiers (AIs)
- need a machine-readable representation with control characters (such as FNC1, 0x1D)
- debug how data is actually encoded into the symbol

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.barcode_properties.ReadingCodeTextExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/ReadingCodeTextExample.java" target="_blank" rel="noopener noreferrer">ReadingCodeTextExample.java</a>

---

## 1. Code Text vs Raw Bytes

For every recognized barcode, `BarCodeResult` exposes both a decoded string and raw bytes:

```java
BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.CODE_128);
BarCodeResult[] results = reader.readBarCodes();

for (BarCodeResult result : results) {
    String codeText = result.getCodeText();
    byte[] rawBytes = result.getCodeBytes();
}
```

Typical usage:

- `codeText` — use in UI, logs, and business logic.
- `rawBytes` — use for low-level inspection, binary protocols, GS1/FNC1 handling, or hex dumps.

The following sections show how this behaves with ASCII payloads, Unicode text, and GS1 barcodes.

---

## 2. Default Code Text for ASCII Code 128

For plain ASCII payloads, the decoded `codeText` string and the raw bytes usually match directly when interpreted as US-ASCII.

```java
String imagePath = "code128_ascii.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.CODE_128);
BarCodeResult[] results = reader.readBarCodes();

for (BarCodeResult result : results) {
    String codeText = result.getCodeText();
    byte[] rawBytes = result.getCodeBytes();

    System.out.println("CodeText: " + codeText);
    System.out.println("RawHex : " + bytesToHex(rawBytes));

    String fromBytes = new String(rawBytes, java.nio.charset.StandardCharsets.US_ASCII);
    boolean equal = fromBytes.equals(codeText);
}
```

In this scenario:

- `codeText` contains the original ASCII payload, such as `"ASCII-1234-OK"`.
- `rawBytes` hold the same characters as ASCII bytes.
- Converting `rawBytes` back using `US_ASCII` yields the same string as `getCodeText()`.

A simple helper method for hex output (as in the example class):

```java
private static String bytesToHex(byte[] data) {
    if (data == null) {
        return "(null)";
    }
    StringBuilder sb = new StringBuilder(3 * data.length);
    for (byte b : data) {
        sb.append(String.format("%02X ", b));
    }
    return sb.toString().trim();
}
```

---

## 3. Unicode Payloads and `DetectEncoding` (QR + UTF-8)

When the barcode payload contains non-ASCII characters (for example, Cyrillic text), it is important to decode it using the correct encoding.  
Aspose.BarCode allows you to enable automatic encoding detection via `DetectEncoding`.

The sample uses a QR code with the UTF-8 payload `"Привет QR / Hello"`:

```java
String imagePath = "qr_utf8.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.QR);
reader.getBarcodeSettings().setDetectEncoding(true);

BarCodeResult[] results = reader.readBarCodes();

for (BarCodeResult result : results) {
    String codeText = result.getCodeText();
    byte[] rawBytes = result.getCodeBytes();

    System.out.println("CodeText (decoded): " + codeText);
    System.out.println("RawHex            : " + bytesToHex(rawBytes));

    boolean containsCyrillic = codeText.contains("Привет");
}
```

Key points:

- `setDetectEncoding(true)` lets the engine automatically detect the payload encoding and return a correct Java `String`.
- `codeText` contains the full Unicode text, including Cyrillic characters.
- `rawBytes` represent the original byte stream (typically UTF-8 with an ECI marker inside the symbol).

This pattern should be used whenever you expect non-ASCII content in the barcode.

---

## 4. GS1 DataMatrix: Human-Readable Code Text vs FNC1 Raw Stream

GS1 barcodes use **Application Identifiers (AIs)** and the **FNC1** (group separator, byte `0x1D`) to separate variable-length fields.

Aspose.BarCode returns:

- In `codeText` — a **human-readable** form with AIs in parentheses, for example:  
  `(01)12345678901231(10)BATCH42(17)251231`
- In `codeBytes` — a byte stream based on this string.

In some integrations you also need a **machine-readable** representation where:

- AIs are written without parentheses,
- variable-length fields are separated by the `0x1D` FNC1 byte.

The sample demonstrates how to build such a machine-readable form from the human-readable GS1 string.

```java
String imagePath = "gs1_dm.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.GS_1_DATA_MATRIX);
reader.getBarcodeSettings().setDetectEncoding(true);
reader.setQualitySettings(QualitySettings.getNormalQuality());

BarCodeResult[] results = reader.readBarCodes();

for (BarCodeResult result : results) {
    String humanCodeText = result.getCodeText();
    byte[] apiBytes = result.getCodeBytes();

    System.out.println("GS1 DM human: " + humanCodeText);
    System.out.println("API bytes   : " + bytesToHex(apiBytes));

    String machineReadable = toGs1MachineReadable(humanCodeText);
    byte[] machineBytes = machineReadable.getBytes(java.nio.charset.StandardCharsets.US_ASCII);

    System.out.println("GS1 DM raw*: " + bytesToHex(machineBytes));

    boolean hasFnc1 = containsByte(machineBytes, (byte) 0x1D);
}
```

The helper from the sample class that converts the human-readable GS1 code text into a machine-readable stream:

```java
private static String toGs1MachineReadable(String human) {
    // Input example: (01)12345678901231(10)BATCH42(17)251231
    String gtin = human.replaceAll("^.*\(01\)(\d{14}).*$", "$1");
    String lot  = human.replaceAll("^.*\(10\)([^()]+).*$", "$1");
    String exp  = human.replaceAll("^.*\(17\)(\d{6}).*$", "$1");
    // Machine-readable form: [01][GTIN][10][LOT][FNC1][17][EXP]
    return "01" + gtin + "10" + lot + '\u001D' + "17" + exp;
}

private static boolean containsByte(byte[] arr, byte val) {
    if (arr == null) {
        return false;
    }
    for (byte b : arr) {
        if (b == val) {
            return true;
        }
    }
    return false;
}
```

Key points:

- `codeText` is convenient for displaying and parsing AIs with parentheses.
- `toGs1MachineReadable(...)` reconstructs a machine-friendly representation with FNC1 separators between variable-length fields.
- The example checks that the resulting byte stream contains the `0x1D` separator.

---

## 5. GS1 Code 128: Same Idea, Different Symbology

The same pattern applies to GS1 Code 128.  
The data model (AIs and FNC1 separators) is identical; only the symbology changes.

```java
String imagePath = "gs1_code128.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.GS_1_CODE_128);
reader.getBarcodeSettings().setDetectEncoding(true);
reader.setQualitySettings(QualitySettings.getNormalQuality());

BarCodeResult[] results = reader.readBarCodes();

for (BarCodeResult result : results) {
    String humanCodeText = result.getCodeText();
    byte[] apiBytes = result.getCodeBytes();

    System.out.println("GS1 C128 human: " + humanCodeText);
    System.out.println("GS1 C128 raw  : " + bytesToHex(apiBytes));

    String machineReadable = toGs1MachineReadable(humanCodeText);
    byte[] machineBytes = machineReadable.getBytes(java.nio.charset.StandardCharsets.US_ASCII);

    System.out.println("GS1 C128 raw*: " + bytesToHex(machineBytes));

    boolean hasFnc1 = containsByte(machineBytes, (byte) 0x1D);
}
```

Key points:

- Use `DecodeType.GS_1_CODE_128` to read GS1 Code 128 symbols.
- `codeText` still contains AIs in parentheses.
- The same `toGs1MachineReadable(...)` helper produces a machine-readable representation with FNC1.

---

## Summary

When reading barcodes, Aspose.BarCode for Java gives you access to both human-readable text and raw data:

- `getCodeText()` returns a processed string suitable for UI and business logic.
- `getCodeBytes()` returns the underlying byte stream useful for debugging, binary processing, and GS1/FNC1 scenarios.
- `setDetectEncoding(true)` ensures correct decoding of Unicode payloads (for example, UTF-8 in QR codes).
- For GS1 barcodes, you can:
    - use `codeText` as a convenient, human-readable format with AIs, and
    - convert it into a machine-readable representation with FNC1 separators when needed.

All examples shown here are based on:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose-barcode/guide/recognition/barcode_properties/ReadingCodeTextExample.java" target="_blank" rel="noopener noreferrer">ReadingCodeTextExample.java</a>

Use these patterns as a reference when working with code text and raw data in your own Java applications.
