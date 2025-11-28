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

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/ReadingMetadataExample.java" target="_blank" rel="noopener noreferrer">ReadingMetadataExample.java</a>

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
System.out.println("Rect=" + region.getRectangle());

Quadrangle quad = region.getQuadrangle();
if (quad != null) {
     System.out.println("Quad LT=" + quad.getLeftTop()
           + " RT=" + quad.getRightTop()
           + " RB=" + quad.getRightBottom()
           + " LB=" + quad.getLeftBottom());
}

java.awt.Point[] points = region.getPoints();
    if (points != null) {
        IntStream.range(0, points.length).forEach(i -> {
            Point point = points[i];
            System.out.println("Point " + i + ": x=" + point.getX() + " y=" + point.getY());
        });
    }

// 1D-specific extended parameters (checksum)
BarCodeExtendedParameters extended = result.getExtended();
    if (extended != null && extended.getOneD() != null) {
        OneDExtendedParameters oneD = extended.getOneD();
        System.out.println("OneD checksum=" + oneD.getCheckSum());
        }
}
```

### Rectangle vs. Quadrangle vs. Points

The region geometry API describes **one and the same physical area** of the barcode at different levels of detail:

- `region.getRectangle()`  
  Returns an axis-aligned `java.awt.Rectangle` (bounding box).  
  The rectangle is always aligned to the X/Y axes and simply encloses the barcode.  
  Use it when you need:
    - a quick bounding box,
    - simple hit-testing,
    - or cropping a sub-image without caring about rotation.

- `region.getQuadrangle()`  
  Returns a `Quadrangle` with four named corners:
  `getLeftTop()`, `getRightTop()`, `getRightBottom()`, `getLeftBottom()`.  
  The quadrangle can be rotated or skewed and represents the **actual shape** of the barcode region.  
  Use it when you need:
    - to draw an accurate contour around a rotated code,
    - to analyze rotation/tilt,
    - to perform perspective transforms based on the four corners.

- `region.getPoints()`  
  Returns a `Point[]` with the corner points of the barcode region.  
  It contains the same physical points as the quadrangle, but in an array form that is convenient for loops and generic algorithms.  
  The order of points is defined by the engine implementation and should not be treated as
  “always left-top, right-top, right-bottom, left-bottom” by index. If you need semantically named
  corners, prefer `region.getQuadrangle()`.

Key points:

- `getRectangle()` — simple bounding box, minimal information, maximum simplicity.
- `getQuadrangle()` — full geometry with rotation and corner semantics.
- `getPoints()` — the same geometry as individual points in an array, useful for iteration and custom processing.

---

## 2. QR Extended Metadata (Error Level, Version)

For 2D QR barcodes, Aspose.BarCode provides QR-specific extended metadata via `QRExtendedParameters`.  
You can use it to inspect properties like:

- QR **error correction level** (Reed–Solomon)
- QR **version** (symbol size in modules)
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
        QRExtendedParameters qrExtendedParameters = extended.getQR();
        if (qrExtendedParameters != null) {
            QRErrorLevel errorLevel = qrExtendedParameters.getQRErrorLevel();
            int version = qrExtendedParameters.getQRVersion();

            System.out.println("QR error level=" + errorLevel);
            System.out.println("QR version=" + version);
        }
    }
}
```

### QR Error Correction Level (`QRErrorLevel`)

QR codes use Reed–Solomon error correction to restore data if part of the symbol is damaged or occluded.  
The QR standard defines four error correction levels, from lowest to highest redundancy:

| Error level | Enum value     | Approx. recoverable data | Description                         |
|-------------|----------------|--------------------------|-------------------------------------|
| L           | `LEVEL_L`      | ~7% of codewords         | Maximum capacity, lowest redundancy |
| M           | `LEVEL_M`      | ~15% of codewords        | Default in many applications        |
| Q           | `LEVEL_Q`      | ~25% of codewords        | Higher robustness                   |
| H           | `LEVEL_H`      | ~30% of codewords        | Maximum robustness, lower capacity  |

When you read a QR symbol, `qrExtendedParameters.getQRErrorLevel()` returns the **actual error correction level** that was used when this symbol was generated.

Practical notes:

- Higher error correction levels make the symbol more tolerant to damage (scratches, printing defects, partial occlusion).
- The trade‑off is lower payload capacity for the same QR version.
- When generating QR codes, you configure the level via `getQR().setQrErrorLevel(...)`.  
  When reading, you only inspect which level was used.

### QR Version (`QRVersion`)

The **QR version** defines the size of the QR matrix in modules (black/white squares).  
Standard QR codes use versions from 1 to 40:

- Version 1 → 21 × 21 modules
- Version 2 → 25 × 25 modules
- …
- Version 40 → 177 × 177 modules

The general formula for standard QR codes is:

> **modulesPerSide = 21 + 4 × (version − 1)**

In Aspose.BarCode, this is represented by the `QRVersion` enumeration when generating barcodes, and `QRExtendedParameters.getQRVersion()` returns the version of the **recognized** symbol.

Typical mapping (examples):

| QR version | Modules per side | Comment                                  |
|-----------:|------------------|------------------------------------------|
| 1          | 21 × 21          | Small symbols, short text / IDs         |
| 2          | 25 × 25          | Slightly larger, more data              |
| 10         | 57 × 57          | Medium size / structured payloads       |
| 20         | 97 × 97          | Large payloads in a single symbol       |
| 40         | 177 × 177        | Maximum standard QR size and capacity   |

Important points:

- **Version describes the symbol size in modules**, not in pixels.
- The final image size in pixels is determined by:
    - the QR version (number of modules), and
    - the module size (for example, `XDimension` in pixels per module).
- For Micro QR, legacy values `VERSION_M1..VERSION_M4` in `QRVersion` are deprecated.  
  Use the dedicated Micro QR barcode type and `MicroQRVersion` parameters instead.

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

Example: reading binary data from a QR symbol encoded from a UTF-8 byte array.

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
    - `getRegion()` with:
        - `getRectangle()` — axis-aligned bounding box
        - `getQuadrangle()` — rotated/skewed quadrilateral with named corners
        - `getPoints()` — corner points as an array for generic processing
- Extended parameters:
    - `getExtended().getOneD()` for 1D checksums and related data
    - `getExtended().getQR()` for QR error level and version
    - `getExtended().getPdf417()` for Macro PDF417 metadata
- Binary payload:
    - `getCodeBytes()` for raw data when barcodes are used as binary containers

All examples shown here are based on:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/ReadingMetadataExample.java" target="_blank" rel="noopener noreferrer">ReadingMetadataExample.java</a>

Use these patterns as a reference when integrating barcode metadata into your Java applications.
