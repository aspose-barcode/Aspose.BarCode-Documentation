---
title: "Code Text Raw"
description: "Learn how and when to use raw code bytes from BarCodeReader in Aspose.BarCode for Java."
type: docs
weight: 40
url: /java/developer-guide/barcode-recognition/barcode-properties/reading-code-text-raw
---

# Working with Raw Code Bytes

Besides human-readable code text, Aspose.BarCode for Java exposes the underlying **raw bytes** for each recognized barcode.  
These bytes are useful when you:

- work with **binary payloads** (DataMatrix, PDF417 in binary modes)
- handle **GS1** barcodes and need robust splitting by **FNC1** (`0x1D`) separators
- need to verify **leading zeros** in identifiers such as GTIN
- debug how the engine encodes or decodes data at the byte level

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.barcode_properties.ReadingCodeTextRawExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/ReadingCodeTextRawExample.java" target="_blank" rel="noopener noreferrer">ReadingCodeTextRawExample.java</a>

In the snippets below, variables like `imagePath` represent paths to barcode images in your application.

---

## 1. Accessing Raw Bytes from Recognition

Each `BarCodeResult` gives you both the decoded string and the raw byte stream:

```java
BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.DATA_MATRIX);
BarCodeResult[] results = reader.readBarCodes();

for (BarCodeResult result : results) {
    String codeText = result.getCodeText();
    byte[] rawBytes = result.getCodeBytes();

    System.out.println("CodeText: " + codeText);
    System.out.println("Raw length: " + (rawBytes != null ? rawBytes.length : 0));
}
```

Typical usage:

- Use `getCodeText()` for UI, logs, and most business logic.
- Use `getCodeBytes()` when you need exact bytes: binary application data, GS1 separators, or low-level validation.

The next sections show concrete scenarios where raw bytes are especially important.

---

## 2. Binary Payloads in DataMatrix

When DataMatrix is used in **binary mode**, the payload may contain bytes such as `0x00` or `0xFF` that are not safe to treat as text.  
In this case `getCodeBytes()` is the primary source of truth.

The test fixture encodes a specific byte sequence into a DataMatrix symbol. At recognition time, the test verifies that the raw bytes begin with the same sequence:

```java
String imagePath = "dm_binary.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.DATA_MATRIX);
BarCodeResult[] results = reader.readBarCodes();

BarCodeResult result = results[0];
byte[] raw = result.getCodeBytes();

byte[] expected = new byte[] {
        0x00, 0x01, (byte) 0xFF, 0x10, 0x20, 'D', 'M', '-', 'B', 'I', 'N'
};

byte[] prefix = prefix(raw, expected.length);
boolean matches = java.util.Arrays.equals(prefix, expected);
```

Helper for prefix comparison (copied from the example class):

```java
private static byte[] prefix(byte[] src, int n) {
    if (n >= src.length) {
        return java.util.Arrays.copyOf(src, src.length);
    }
    return java.util.Arrays.copyOf(src, n);
}
```

Key points:

- The **payload is treated as binary**, not as text.
- `getCodeBytes()` lets you verify or consume the exact sequence of bytes encoded into the symbol.
- Prefix comparison is often enough, because the symbol may also contain additional bytes related to encoding structure and error correction.

---

## 3. Binary Payloads in PDF417

PDF417 also supports **binary compaction**. The approach is similar: encode arbitrary bytes and check them on recognition via `getCodeBytes()`.

```java
String imagePath = "pdf417_bytes.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.PDF_417);
BarCodeResult[] results = reader.readBarCodes();

BarCodeResult result = results[0];
byte[] raw = result.getCodeBytes();

byte[] expected = hex("01 23 45 67 89 AB CD EF 00 11 22 33 44");
byte[] prefix = prefix(raw, expected.length);

boolean matches = java.util.Arrays.equals(prefix, expected);
```

Hex helper from the example class:

```java
private static byte[] hex(String spacedHex) {
    String[] parts = spacedHex.trim().split("\s+");
    byte[] out = new byte[parts.length];
    for (int i = 0; i < parts.length; i++) {
        out[i] = (byte) Integer.parseInt(parts[i], 16);
    }
    return out;
}
```

Key points:

- In **BYTE / BINARY** modes (DataMatrix, PDF417), raw bytes carry application data directly.
- Do not rely on `getCodeText()` for binary payloads; it may involve character decoding that loses information.
- Always validate or process the data through `getCodeBytes()`.

---

## 4. GS1 and FNC1: Splitting Fields by Group Separator

GS1 barcodes use **FNC1** as a group separator, encoded as byte `0x1D` (Group Separator, GS).  
When you have **variable-length AIs**, splitting on `0x1D` is often more robust than parsing a printed string.

With GS1 Code 128, you can read raw bytes and split them by `0x1D`:

```java
String imagePath = "gs1_code128.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.GS_1_CODE_128);
BarCodeResult[] results = reader.readBarCodes();

BarCodeResult result = results[0];
byte[] raw = result.getCodeBytes();

int gsCount = count(raw, (byte) 0x1D);
String[] segments = splitByGS(raw);
```

Helpers used in the example:

```java
private static int count(byte[] data, byte b) {
    int c = 0;
    for (byte x : data) {
        if (x == b) {
            c++;
        }
    }
    return c;
}

private static String[] splitByGS(byte[] raw) {
    final byte GS = 0x1D;

    int segments = 1;
    for (byte x : raw) {
        if (x == GS) {
            segments++;
        }
    }

    String[] out = new String[segments];
    int start = 0;
    int idx = 0;

    for (int i = 0; i <= raw.length; i++) {
        if (i == raw.length || raw[i] == GS) {
            out[idx++] = new String(
                    java.util.Arrays.copyOfRange(raw, start, i),
                    java.nio.charset.StandardCharsets.ISO_8859_1
            );
            start = i + 1;
        }
    }
    return out;
}
```

Key points:

- Raw bytes let you **locate FNC1 (`0x1D`) precisely**.
- Splitting by `0x1D` is safer for variable-length fields than relying only on parentheses in the human-readable code text.
- You can convert each raw segment to a string using an appropriate encoding (often ISO-8859-1 for GS1).

---

## 5. QR Extended Codetext and Group Separators

When you use **extended QR codetext** with `QrExtCodetextBuilder`, you can combine ECI segments and insert **FNC1 group separators**.  
On the recognition side, the raw bytes will contain `0x1D` at the separator positions.

Recognition example:

```java
String imagePath = "qr_extended_fncs_eci.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.QR);
BarCodeResult[] results = reader.readBarCodes();

BarCodeResult result = results[0];
byte[] raw = result.getCodeBytes();

int gsCount = count(raw, (byte) 0x1D);
boolean hasSeparator = gsCount >= 1;
```

Key points:

- FNC1 group separators in extended QR codetext are encoded as `0x1D` in the raw stream.
- `getCodeBytes()` lets you check that separators are present and correctly positioned.
- This is especially useful when combining multiple ECI segments and control characters.

---

## 6. Leading Zeros in GS1 Identifiers

GTIN and other GS1 identifiers often include **leading zeros** that must be preserved.  
With GS1 DataMatrix, you can verify leading zeros both in the human-readable string and in the raw byte representation.

```java
String imagePath = "gs1_dm_zeros.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.GS_1_DATA_MATRIX);
BarCodeResult[] results = reader.readBarCodes();

BarCodeResult result = results[0];

String human = result.getCodeText();
boolean humanHasZeros = human.contains("(01)00012345678905");

String rawAsIso = new String(result.getCodeBytes(), java.nio.charset.StandardCharsets.ISO_8859_1);
boolean rawHasZeros = rawAsIso.contains("00012345678905");
```

Key points:

- The human-readable GS1 string should retain leading zeros in the `(01)` field.
- The raw bytes, interpreted with a suitable encoding, also contain the full GTIN including leading zeros.
- You can implement validation rules that ensure GTIN length and zero-padding are correct.

---

## 7. Raw Bytes and Character Encodings (Aztec / ECI)

For **Unicode text**, especially when using Aztec or QR with ECI, it is important to understand the limits of `getCodeBytes()`:

- `getCodeText()` is designed to return a correct Java `String` for the recognized content.
- `getCodeBytes()` is not guaranteed to be the original UTF‑8 (or other) byte stream for arbitrary Unicode.
- For **Latin‑1 safe** payloads, you can reliably treat raw bytes as ISO‑8859‑1.

### 7.1 Aztec Without ECI: Non‑Latin‑1 Data Is Lost in Raw Bytes

If you generate an Aztec symbol **without** ECI for a string that contains characters outside the Latin‑1 range, the raw bytes cannot represent the original Unicode sequence.

```java
String imagePath = "aztec_no_eci.png";
String original = "犬Right狗";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.AZTEC);
BarCodeResult[] results = reader.readBarCodes();

BarCodeResult result = results[0];
byte[] raw = result.getCodeBytes();

String decodedFromRaw = new String(raw, java.nio.charset.StandardCharsets.UTF_8);
boolean preserved = decodedFromRaw.equals(original); // typically false
```

Key points:

- Without ECI, non‑Latin‑1 characters may be replaced or mapped in a way that is not UTF‑8 round‑trippable.
- Do not assume that `getCodeBytes()` can be decoded back to the original string with UTF‑8 in such cases.
- For Unicode‑heavy payloads, rely primarily on `getCodeText()`.

### 7.2 Aztec with ECI UTF‑8: Rely on Code Text

When you generate Aztec with **ECI UTF‑8**, the engine can preserve Unicode text in `getCodeText()`:

```java
String imagePath = "aztec_eci_utf8_text_only.png";
String original = "犬Right狗";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.AZTEC);
BarCodeResult[] results = reader.readBarCodes();

BarCodeResult result = results[0];
String codeText = result.getCodeText();
boolean ok = codeText.equals(original);
```

Key points:

- ECI UTF‑8 ensures the **decoded text** is correct.
- The example class explicitly avoids asserting a UTF‑8 round‑trip for `getCodeBytes()` here.
- Treat `getCodeText()` as authoritative for Unicode payloads.

### 7.3 Aztec with Latin‑1 Payload: Raw Bytes Match Encoding

For payloads that are safe in **ISO‑8859‑1** (Latin‑1), you can assert that raw bytes equal the text encoded with this charset:

```java
String imagePath = "aztec_raw_latin1_safe.png";
String latin1 = "Café-123"; // "Café-123"

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.AZTEC);
BarCodeResult[] results = reader.readBarCodes();

BarCodeResult result = results[0];

String codeText = result.getCodeText(); // "Café-123"
byte[] raw = result.getCodeBytes();
byte[] expected = latin1.getBytes(java.nio.charset.StandardCharsets.ISO_8859_1);

boolean bytesMatch = java.util.Arrays.equals(raw, expected);
```

Key points:

- For Latin‑1 text and Aztec with `ECIEncodings.ISO_8859_1`, raw bytes can be compared directly against ISO‑8859‑1 encoding of the string.
- This is a safe way to validate raw bytes when payload is restricted to the Latin‑1 range.

---

## Summary

Raw code bytes from `BarCodeResult.getCodeBytes()` are a powerful tool when you need more than just a decoded string:

- For **DataMatrix** and **PDF417** in binary modes, raw bytes are the primary representation of your payload.
- For **GS1** barcodes, raw bytes expose FNC1 (`0x1D`) separators so you can robustly split variable‑length fields.
- For **GS1 identifiers** like GTIN, both code text and raw data preserve leading zeros.
- For **Unicode payloads**, use ECI where appropriate and treat `getCodeText()` as authoritative; rely on raw bytes only when you fully control the encoding (for example, Latin‑1).

All examples shown here are based on:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/ReadingCodeTextRawExample.java" target="_blank" rel="noopener noreferrer">ReadingCodeTextRawExample.java</a>

Use these patterns as a reference when integrating raw byte handling into your Java barcode workflows.
