---
title: "Detect Encoding"
description: "Learn how to control automatic character encoding detection when reading barcodes in Aspose.BarCode for Java."
type: docs
weight: 40
url: /java/developer-guide/barcode-recognition/detect-encoding
---

# Detect encoding in barcode recognition

Many 2D barcodes (for example QR and Data Matrix) can store arbitrary byte sequences rather than plain ASCII text.  
In practice this means that:

- barcodes may contain text encoded in UTF-8, Shift-JIS, Windows-1251, ISO-8859-5, and many other encodings;
- the same byte sequence can be displayed either correctly or as unreadable "mojibake" depending on the chosen encoding.

Aspose.BarCode for Java exposes the `DetectEncoding` flag to control how the recognition engine converts raw bytes into strings.

This article is based on the test class  
[`DetectEncodingExample`](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/special_parameters/DetectEncodingExample.java).

## When to use DetectEncoding

Use `DetectEncoding` when:

- you expect barcodes to contain text in non‑ASCII encodings (for example Japanese, Chinese or mixed Unicode text);
- you receive barcodes produced by external systems that may use various legacy code pages;
- you need to compare how the same barcode is interpreted with and without automatic encoding detection.

If all of your barcodes are guaranteed to contain only ASCII or a single known encoding, you can keep defaults or explicitly disable automatic detection.

## Enable automatic encoding detection (UTF‑8 QR)

The first example shows how to read a UTF‑8 QR code with `DetectEncoding` enabled.

```java
String fileName = "qr_utf8_detectencoding_enabled.png";

// Generate QR with UTF-8 text once
ExampleAssist.checkOrCreateImage(FOLDER, fileName, path -> {
    String utf8Text = "Hello, 世界!"; // mixed Latin + CJK characters
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, utf8Text);
    generator.save(path, BarCodeImageFormat.PNG);
});

// Read with automatic encoding detection
BarCodeReader reader =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.QR);
reader.getBarcodeSettings().setDetectEncoding(true);

BarCodeResult[] results = reader.readBarCodes();
System.out.println("Detected text: " + results[0].getCodeText());
```

With `DetectEncoding = true` (this is also the default), the engine:

- analyzes the internal byte stream of the QR code;
- automatically detects UTF‑8;
- returns a correct Java `String` with all Unicode characters preserved.

This mode is recommended for most modern applications that work with multilingual content.

## Disable encoding detection to inspect raw bytes

Sometimes you may want to see the raw byte‑to‑character mapping instead of decoded Unicode text.  
The second example disables `DetectEncoding` for the same logical payload.

```java
String fileName = "qr_utf8_detectencoding_disabled.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, path -> {
    String utf8Text = "Hello, 世界!";
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, utf8Text);
    generator.save(path, BarCodeImageFormat.PNG);
});

BarCodeReader reader =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.QR);
reader.getBarcodeSettings().setDetectEncoding(false);

BarCodeResult[] results = reader.readBarCodes();
System.out.println("Raw text (DetectEncoding=false): " + results[0].getCodeText());
```

With `DetectEncoding = false`:

- the engine does **not** perform charset detection;
- bytes are interpreted using an internal default mapping;
- the resulting string may contain incorrect characters.

This mode is useful for debugging, forensics, or when you plan to re‑interpret `getCodeBytes()` yourself using a specific `Charset`.

## Compare results for a legacy code page (Windows‑1251)

The next example demonstrates how the same image is interpreted when it contains text originally encoded in a legacy code page (for example Windows‑1251).

The test:

1. Encodes a Unicode string into Windows‑1251 bytes.
2. Re‑interprets these bytes as ISO‑8859‑1 to store them inside a QR code.
3. Reads the code twice: with `DetectEncoding` enabled and disabled.

```java
String fileName = "qr_windows1251_compare.png";
String originalText = "Encoding check sample";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, path -> {
    byte[] bytes = originalText.getBytes(Charset.forName("windows-1251"));
    String encoded = new String(bytes, Charset.forName("ISO-8859-1"));
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, encoded);
    generator.save(path, BarCodeImageFormat.PNG);
});

// DetectEncoding = true
BarCodeReader reader1 =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.QR);
reader1.getBarcodeSettings().setDetectEncoding(true);
BarCodeResult[] results1 = reader1.readBarCodes();

// DetectEncoding = false
BarCodeReader reader2 =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.QR);
reader2.getBarcodeSettings().setDetectEncoding(false);
BarCodeResult[] results2 = reader2.readBarCodes();

System.out.println("DetectEncoding(true): " + results1[0].getCodeText());
System.out.println("DetectEncoding(false): " + results2[0].getCodeText());
```

In practice you will see:

- with detection enabled, the text is reconstructed as readable Unicode;
- with detection disabled, the same bytes are treated as ISO‑8859‑1 and displayed incorrectly.

This pattern is typical when dealing with barcodes produced by older systems that use legacy regional encodings.

## Use DetectEncoding with multiple symbologies

`DetectEncoding` is not limited to QR codes. The last example shows the same UTF‑8 text stored in QR and Data Matrix barcodes.

```java
String qrFile = "qr_utf8_multi.png";
String dmFile = "datamatrix_utf8_multi.png";
String text = "こんにちは世界"; // Japanese "Hello, world"

ExampleAssist.checkOrCreateImage(FOLDER, qrFile, path -> {
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, text);
    generator.save(path, BarCodeImageFormat.PNG);
});

ExampleAssist.checkOrCreateImage(FOLDER, dmFile, path -> {
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.DATA_MATRIX, text);
    generator.save(path, BarCodeImageFormat.PNG);
});

// QR
BarCodeReader qrReader =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, qrFile), DecodeType.QR);
qrReader.getBarcodeSettings().setDetectEncoding(true);
BarCodeResult[] qrResults = qrReader.readBarCodes();
System.out.println("QR decoded text: " + qrResults[0].getCodeText());

// Data Matrix
BarCodeReader dmReader =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, dmFile), DecodeType.DATA_MATRIX);
dmReader.getBarcodeSettings().setDetectEncoding(true);
BarCodeResult[] dmResults = dmReader.readBarCodes();
System.out.println("Data Matrix decoded text: " + dmResults[0].getCodeText());
```

As long as `DetectEncoding` is enabled, both symbologies correctly return the same Unicode string.

## Recommendations and best practices

- **Keep DetectEncoding enabled by default**  
  This is the safest choice for modern applications that handle multilingual data or unknown producers.

- **Disable DetectEncoding for byte‑level diagnostics**  
  Turn it off when you need to analyze raw byte patterns or implement custom charset handling.

- **Be explicit for legacy systems**  
  If you know that all barcodes come from a particular code page, you can:
    - either rely on `DetectEncoding` to guess it,
    - or keep detection disabled and re‑interpret `getCodeBytes()` using your own `Charset`.

- **Test with real samples**  
  Encoding issues are highly data‑dependent. Use your production barcodes in tests similar to those above to confirm correct behavior before deployment.
