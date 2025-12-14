---
title: "Reading CodeText (Raw Bytes, Encodings)"
description: "How to read CodeText, use getCodeBytes(), and handle encodings with DetectEncoding."
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/barcode-properties/reading-codetext
---

# Reading CodeText (Raw Bytes, Encodings)

Recognition results provide both:

- `getCodeText()` as a `String`.
- `getCodeBytes()` as a `byte[]`.

Use `CodeText` for most business logic.
Use raw bytes when payload is binary, when you need precise separators (GS1 / FNC1), or when you want to debug encoding.

## Read CodeText and raw bytes

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

String imagePath = "code128.png";
BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.CODE_128);
BarCodeResult[] results = reader.readBarCodes();

for (BarCodeResult result : results) {
    String codeText = result.getCodeText();
    byte[] rawBytes = result.getCodeBytes();
}
```

## Enable encoding detection (DetectEncoding)

Use this when payload can contain non-ASCII text.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

String imagePath = "qr_utf8.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.QR);
reader.getBarcodeSettings().setDetectEncoding(true);

for (BarCodeResult result : reader.readBarCodes()) {
    System.out.println(result.getCodeText());
}
```

## GS1 example: split raw bytes by FNC1 separator (0x1D)

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import java.nio.charset.StandardCharsets;
import java.util.Arrays;

BarCodeReader reader = new BarCodeReader("gs1_code128.png", DecodeType.GS_1_CODE_128);
BarCodeResult[] results = reader.readBarCodes();

byte[] raw = results[0].getCodeBytes();

final byte GS = 0x1D;
int start = 0;
for (int i = 0; i <= raw.length; i++) {
    if (i == raw.length || raw[i] == GS) {
        byte[] segment = Arrays.copyOfRange(raw, start, i);
        String s = new String(segment, StandardCharsets.ISO_8859_1);
        System.out.println("Segment: " + s);
        start = i + 1;
    }
}
```
