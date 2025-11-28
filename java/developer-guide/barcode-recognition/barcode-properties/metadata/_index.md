---
title: "Reading Metadata"
description: "Learn how to access and use barcode metadata returned by BarCodeReader in Aspose.BarCode for Java."
type: docs
weight: 50
url: /java/developer-guide/barcode-recognition/barcode-properties/metadata
---

# Reading Barcode Metadata

In addition to barcode text and type, Aspose.BarCode for Java returns rich **metadata** for every recognized symbol.  
This metadata is exposed through `BarCodeResult` and related classes and can be used to:

- inspect the **symbology** and decoded text
- evaluate **recognition confidence**
- access **geometry** (position and shape) of the barcode region
- read **symbology-specific extended parameters** (QR, PDF417, 1D, etc.)
- work with **binary payloads** via raw bytes

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.barcode_properties.ReadingMetadataExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose-barcode/guide/recognition/barcode_properties/ReadingMetadataExample.java" target="_blank" rel="noopener noreferrer">ReadingMetadataExample.java</a>

In the snippets below, variables like `imagePath` represent paths to barcode images in your application.

---

## 1. Basic Metadata for 1D Barcodes

For every recognized barcode, `BarCodeResult` provides core metadata such as:

- barcode type (`DecodeType`)
- human-readable code text
- recognition confidence (0–100)
- region geometry (`BarCodeRegionParameters`)
- extended parameters (`BarCodeExtendedParameters`), including checksums for 1D symbologies

Example: reading metadata from a GS1 Code 128 symbol.

```java
String imagePath = "gs1_code128.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.GS_1_CODE_128);
BarCodeResult[] results = reader.readBarCodes();

if (results.length > 0) {
    BarCodeResult result = results[0];

    // Basic type and text
    DecodeType type = result.getCodeType();
    String typeName = result.getCodeTypeName();
    String codeText = result.getCodeText();

    System.out.println("Type=" + typeName + " Text=" + codeText);

    // Confidence (0..100)
    int confidence = result.getConfidence();
    System.out.println("Confidence=" + confidence);

    // Region geometry
    BarCodeRegionParameters region = result.getRegion();
    java.awt.Rectangle rect = region.getRectangle();
    System.out.println("Rect=" + rect);

    Quadrangle quad = region.getQuadrangle();
    if (quad != null) {
        System.out.println("Quad LT=" + quad.getLeftTop()
                + " RT=" + quad.getRightTop()
                + " RB=" + quad.getRightBottom()
                + " LB=" + quad.getLeftBottom());
    }

    // 1D-specific extended parameters (checksum)
    BarCodeExtendedParameters extended = result.getExtended();
    if (extended != null && extended.getOneD() != null) {
        OneDExtendedParameters oneD = extended.getOneD();
        System.out.println("OneD checksum=" + oneD.getCheckSum());
    }
}
```

Key points:

- `getCodeType()` / `getCodeTypeName()` identify the symbology (for example, `GS_1_CODE_128`).
- `getCodeText()` returns decoded text (such as a GS1 string with AIs).
- `getConfidence()` is a score in the range 0–100 that can be used for quality checks.
- `getRegion()` provides both an axis-aligned rectangle and an optional quadrangle for rotated or skewed codes.
- For 1D barcodes, `getExtended().getOneD()` exposes additional details such as the checksum.

---

## 2. QR Extended Metadata (Error Level, Version)

For 2D QR barcodes, Aspose.BarCode provides QR-specific extended metadata via `QRExtendedParameters`.  
You can use it to inspect properties like:

- QR **error correction level** (L, M, Q, H)
- QR **version** (module size / symbol size)
- other QR-related flags (for example, structured append, if used)

Example: reading QR metadata from a symbol generated with high error correction (Level H).

```java
String imagePath = "qr_high_ec.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.QR);
reader.setQualitySettings(QualitySettings.getHighQuality());

BarCodeResult[] results = reader.readBarCodes();

if (results.length > 0) {
    BarCodeResult result = results[0];

    int confidence = result.getConfidence();
    System.out.println("Confidence=" + confidence);

    BarCodeExtendedParameters extended = result.getExtended();
    if (extended != null) {
        QRExtendedParameters qrExt = extended.getQR();
        if (qrExt != null) {
            QRErrorLevel errorLevel = qrExt.getQRErrorLevel();
            int version = qrExt.getQRVersion();

            System.out.println("QR error level=" + errorLevel);
            System.out.println("QR version=" + version);
        }
    }
}
```

Key points:

- `setQualitySettings(QualitySettings.getHighQuality())` can improve recognition robustness for QR codes.
- `getExtended().getQR()` returns `QRExtendedParameters` with QR-specific details.
- `getQRErrorLevel()` reflects the error correction level used when generating the symbol.
- `getQRVersion()` indicates the QR version (1–40), which corresponds to symbol size and capacity.

---

## 3. Macro PDF417 Metadata

Macro PDF417 barcodes can split large payloads across multiple symbols.  
For such barcodes, `Pdf417ExtendedParameters` expose metadata like:

- macro file ID
- total number of segments
- current segment ID

Example: reading Macro PDF417 metadata.

```java
String imagePath = "pdf417_macro.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.MACRO_PDF_417);
BarCodeResult[] results = reader.readBarCodes();

if (results.length > 0) {
    BarCodeResult result = results[0];

    int confidence = result.getConfidence();
    System.out.println("Confidence=" + confidence);

    BarCodeExtendedParameters extended = result.getExtended();
    if (extended != null) {
        Pdf417ExtendedParameters pdf417Ext = extended.getPdf417();
        if (pdf417Ext != null) {
            int segmentsCount = pdf417Ext.getMacroPdf417SegmentsCount();
            int segmentId = pdf417Ext.getMacroPdf417SegmentID();
            String fileId = pdf417Ext.getMacroPdf417FileID();

            System.out.println("Macro file ID      = " + fileId);
            System.out.println("Macro segments     = " + segmentsCount);
            System.out.println("Macro segment index= " + segmentId);
        }
    }
}
```

Key points:

- Use `DecodeType.MACRO_PDF_417` when reading Macro PDF417 symbols.
- `getExtended().getPdf417()` returns `Pdf417ExtendedParameters`.
- Macro metadata is essential for reassembling payloads split across multiple PDF417 symbols.

---

## 4. Binary Payload via `getCodeBytes()`

Some barcodes store binary data rather than plain text.  
In these cases, you should use `getCodeBytes()` to obtain the exact payload bytes and process them with an appropriate encoding or binary protocol.

Example: reading binary data from a QR symbol encoded from a UTF‑8 byte array.

```java
String imagePath = "qr_binary_data.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.QR);
BarCodeResult[] results = reader.readBarCodes();

if (results.length > 0) {
    BarCodeResult result = results[0];

    int confidence = result.getConfidence();
    System.out.println("Confidence=" + confidence);

    byte[] rawBytes = result.getCodeBytes();
    if (rawBytes != null) {
        System.out.println("Binary data length: " + rawBytes.length + " bytes");

        byte[] expected = "Hello, Metadata!".getBytes(java.nio.charset.StandardCharsets.UTF_8);
        boolean matches = java.util.Arrays.equals(rawBytes, expected);
        System.out.println("Payload matches expected UTF-8: " + matches);
    }
}
```

Key points:

- `getCodeBytes()` returns the recognized payload as a byte array.
- You can compare it against an expected byte sequence or decode it using `StandardCharsets.UTF_8` (or another encoding, depending on your data).
- This is useful for QR codes and other symbologies used as carriers for binary application data.

---

## Summary

Aspose.BarCode for Java provides detailed metadata for each recognized barcode through `BarCodeResult` and its related classes:

- Core metadata:
    - `getCodeType()`, `getCodeTypeName()` — symbology information
    - `getCodeText()` — decoded text
    - `getConfidence()` — recognition confidence score (0–100)
- Geometry:
    - `getRegion()` with `Rectangle` and `Quadrangle`
- Extended parameters:
    - `getExtended().getOneD()` for 1D checksums and related data
    - `getExtended().getQR()` for QR error level and version
    - `getExtended().getPdf417()` for Macro PDF417 metadata
- Binary payload:
    - `getCodeBytes()` for raw data when barcodes are used as binary containers

All examples shown here are based on:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose-barcode/guide/recognition/barcode_properties/ReadingMetadataExample.java" target="_blank" rel="noopener noreferrer">ReadingMetadataExample.java</a>

Use these patterns as a reference when integrating barcode metadata into your Java applications.
