---
title: "Choose Recognition Symbology"
description: "Learn how to choose and configure barcode symbologies when using BarCodeReader in Aspose.BarCode for Java."
type: docs
weight: 20
url: /java/developer-guide/barcode-recognition/choose-symbology

---

# Working with barcode symbologies in recognition

When you recognize barcodes, one of the most important decisions is **which symbologies to enable**.  
Choosing appropriate `DecodeType` values helps you:

- improve performance (the engine does not have to try every possible symbology),
- reduce false positives,
- and make the intent of your code explicit.

This article shows how to:

1. Recognize **specific 1D symbologies** (Code 128, Code 39, EAN, UPC, Codabar, ITF-14).
2. Recognize **2D symbologies** (QR, Micro QR, Data Matrix, GS1 Data Matrix, PDF417, Macro PDF417, Aztec).
3. Work with **postal barcodes**.
4. Use **combined `DecodeType` values** (`ALL_SUPPORTED_TYPES`, `TYPES_1D`, `TYPES_2D`, custom sets).
5. Recognize **multiple barcodes in one image**.

All code snippets are based on the sample class:

[`com.aspose.barcode.guide.recognition.choose_symbology.ChooseRecognitionSymbology`](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/choose_symbology/ChooseRecognitionSymbology.java)

You can find the full source on GitHub:

[ChooseRecognitionSymbology.java](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/choose_symbology/ChooseRecognitionSymbology.java)

In the snippets below, helper methods like `ExampleAssist.checkOrCreateImage` and `ExampleAssist.pathCombine` come from the test infrastructure and are used only to generate and locate sample images.

```java
ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.CODE_128, "123456789");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});
```

```java
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.CODE_128);
```

---

## 1. Recognizing specific 1D symbologies

In production code you often know exactly which 1D symbology you expect: Code 128 for logistics labels, EAN/UPC for retail, ITF-14 for cartons, and so on.  
In such cases, pass the **exact** `DecodeType` to `BarCodeReader`.

### 1.1 Code 128

```java
String fileName = "code128.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.CODE_128, "123456789");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.CODE_128);
```

Use this pattern when you work with logistics labels, internal IDs, or other generic Code 128 data and want fast, precise recognition.

### 1.2 Code 39 and Code 39 Full ASCII

```java
String fileName = "code39.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.CODE_39, "CODE39-123");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_39);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.CODE_39);
```

```java
String fileName = "code39_full_ascii.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.CODE_39_FULL_ASCII, "Full+ASCII/%$-123");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.CODE_39_FULL_ASCII);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.CODE_39_FULL_ASCII);
```

Use Code 39 Full ASCII when you need the extended character set beyond the basic Code 39 alphabet.

### 1.3 EAN-13 and EAN-13 with supplement

```java
String fileName = "ean13.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.EAN_13, "5901234123457");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.EAN_13);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.EAN_13);
```

```java
String fileName = "ean13_supplement.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.EAN_13, "5901234123457");
    barcodeGenerator.getParameters().getBarcode().getSupplement().setSupplementData("12345");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.EAN_13);
barCodeReader.getBarcodeSettings().setDetectEncoding(true);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.EAN_13);
```

EAN-13 with a 2‑ or 5‑digit supplement is common for magazines and books. The main symbology is still EAN-13, so `DecodeType.EAN_13` is used.

### 1.4 EAN-8

```java
String fileName = "ean8.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.EAN_8, "12345670");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.EAN_8);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.EAN_8);
```

Use EAN-8 for small products where a full EAN-13 symbol would not fit.

### 1.5 UPC-A and UPC-E

```java
String fileName = "upca.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.UPCA, "123456789012");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.UPCA);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.UPCA);
```

```java
String fileName = "upce.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.UPCE, "123456");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.UPCE);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.UPCE);
```

UPC-A and UPC-E are widely used in North America for retail items. Use the matching `DecodeType` for the symbology you expect on your labels.

### 1.6 Codabar

```java
String fileName = "codabar.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.CODABAR, "A123456A");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODABAR);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.CODABAR);
```

Codabar is often used in logistics, libraries, and medical applications where start/stop characters carry additional meaning.

### 1.7 ITF-14

```java
String fileName = "itf14.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.ITF_14, "12345678901231");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.ITF_14);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.ITF_14);
```

ITF-14 is used for shipping containers and outer packaging, usually encoding GTIN-14 values.

---

## 2. Recognizing 2D symbologies

For 2D barcodes you also choose specific `DecodeType` values.  
Here are the basic patterns for QR, Micro QR, Data Matrix, GS1 Data Matrix, PDF417, Macro PDF417, and Aztec.

### 2.1 QR Code and Micro QR

```java
String fileName = "qrcode.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.QR, "Hello QR");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.QR);
```

```java
String fileName = "microqr.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.MICRO_QR, "MQR");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.MICRO_QR);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.MICRO_QR);
```

Micro QR is useful when you have very little space and short payloads.

### 2.2 QR with high-quality settings (damaged or low-quality images)

```java
String fileName = "qrcode_damaged.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.QR, "Damaged?");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);
barCodeReader.setQualitySettings(QualitySettings.getHighQuality());
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.QR);
```

`QualitySettings.getHighQuality()` enables more aggressive image processing and can improve recognition of noisy or partially damaged symbols at the cost of performance.

### 2.3 Data Matrix and GS1 Data Matrix

```java
String fileName = "datamatrix.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.DATA_MATRIX, "DMATRIX-12345");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.DATA_MATRIX);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.DATA_MATRIX);
```

```java
String fileName = "datamatrix_gs1.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    String gs1CodeText = "(01)12345678901231(10)ABCD1234";
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.GS_1_DATA_MATRIX, gs1CodeText);
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.GS_1_DATA_MATRIX);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.GS_1_DATA_MATRIX);
```

Use `DecodeType.GS_1_DATA_MATRIX` when you expect GS1 AIs with FNC1 separators inside the symbol.

### 2.4 PDF417 and Macro PDF417

```java
String fileName = "pdf417.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.PDF_417, "PDF417 sample");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.PDF_417);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.PDF_417);
```

```java
String fileName = "pdf417_macro.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.MACRO_PDF_417, "Macro segment");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.MACRO_PDF_417);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.MACRO_PDF_417);
```

Use Macro PDF417 when your payload is split across multiple PDF417 symbols and you need macro metadata (file ID, segment index, segments count).

### 2.5 Aztec

```java
String fileName = "aztec.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.AZTEC, "AZTEC-OK");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.AZTEC);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.AZTEC);
```

Aztec codes are common in transportation, tickets, and documents where high information density and robust reading are required.

---

## 3. Postal barcodes

Postal symbologies have dedicated `DecodeType` values.  
The examples below show how to generate and recognize POSTNET, PLANET, and Australia Post barcodes.

### 3.1 POSTNET

```java
String fileName = "postnet.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.POSTNET, "12345");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.POSTNET);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.POSTNET);
```

### 3.2 PLANET

```java
String fileName = "planet.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.PLANET, "401234567890");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.PLANET);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.PLANET);
```

### 3.3 Australia Post

```java
String fileName = "australia_post.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    String codeText = "11" + "12345678";
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.AUSTRALIA_POST, codeText);
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.AUSTRALIA_POST);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.AUSTRALIA_POST);
```

Use postal-specific `DecodeType` values when integrating with national postal systems.

---

## 4. Using combined `DecodeType` values

Sometimes you do not know the exact symbology, but you can still restrict recognition to a **group** of types.  
Aspose.BarCode provides several ways to do this:

- pre-defined grouped types: `ALL_SUPPORTED_TYPES`, `TYPES_1D`, `TYPES_2D`
- explicit sets via `setBarCodeReadType(...)`

### 4.1 All supported types

```java
String fileName = "all_types.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.QR, "MIXED");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.ALL_SUPPORTED_TYPES);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.QR);
```

Use `DecodeType.ALL_SUPPORTED_TYPES` when you truly do not know the symbology in advance and are willing to trade performance for flexibility.

### 4.2 All 1D types

```java
String fileName = "types_1D_barcodes.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.CODE_128, "1D-SET");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.TYPES_1D);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.CODE_128);
```

`DecodeType.TYPES_1D` restricts recognition to all 1D symbologies. This is a good default when you know your application only uses linear codes.

### 4.3 All 2D types

```java
String fileName = "types_2D_barcodes.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.DATA_MATRIX, "2D-SET");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.TYPES_2D);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.DATA_MATRIX);
```

`DecodeType.TYPES_2D` is useful when your application uses QR, Data Matrix, PDF417, Aztec, and similar 2D symbologies, but does not rely on 1D codes.

### 4.4 Custom set of symbologies with `setBarCodeReadType`

```java
String fileName = "specific_types.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.DATA_MATRIX, "Specific types");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.ALL_SUPPORTED_TYPES);

barCodeReader.setBarCodeReadType(
        DecodeType.CODE_128,
        DecodeType.QR,
        DecodeType.DATA_MATRIX
);

ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.DATA_MATRIX);
```

Here, the reader is limited to three symbologies: Code 128, QR, and Data Matrix.  
Use this pattern when your application supports a known subset of types and you want to avoid checking all others.

### 4.5 GS1-128 only

```java
String fileName = "gs1_128.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, fullPath -> {
    String gs1CodeText = "(01)09501101530008(17)251231(10)BATCH-42";
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.GS_1_CODE_128, gs1CodeText);
    barcodeGenerator.getParameters().getBarcode().getXDimension().setPixels(2);
    barcodeGenerator.getParameters().getBarcode().getBarHeight().setPixels(60);
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);
BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.GS_1_CODE_128);
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.GS_1_CODE_128);
```

Use `DecodeType.GS_1_CODE_128` when you expect GS1 application identifiers encoded in a Code 128 symbol.

---

## 5. Multiple barcodes in one image

You can also recognize images that contain more than one barcode.  
In this scenario you typically use a broad `DecodeType` (for example `ALL_SUPPORTED_TYPES`) and then inspect each `BarCodeResult` returned by `readBarCodes()`.

```java
String fileName = "multi.png";

String tempCode128Path = ExampleAssist.pathCombine(FOLDER, "tmp_multi_code128.png");
String tempQrPath = ExampleAssist.pathCombine(FOLDER, "tmp_multi_qr.png");

BarcodeGenerator barcodeGenerator1 =
        new BarcodeGenerator(EncodeTypes.CODE_128, "MULTI-1-C128");
barcodeGenerator1.getParameters().getBarcode().getXDimension().setPixels(2);
barcodeGenerator1.getParameters().getBarcode().getBarHeight().setPixels(60);
barcodeGenerator1.save(tempCode128Path, BarCodeImageFormat.PNG);

BarcodeGenerator barcodeGenerator2 =
        new BarcodeGenerator(EncodeTypes.QR, "MULTI-2-QR");
barcodeGenerator2.getParameters().getBarcode().getXDimension().setPixels(4);
barcodeGenerator2.save(tempQrPath, BarCodeImageFormat.PNG);

BufferedImage leftImage = ImageIO.read(java.nio.file.Paths.get(tempCode128Path).toFile());
BufferedImage rightImage = ImageIO.read(java.nio.file.Paths.get(tempQrPath).toFile());

int gap = 20;
int width = leftImage.getWidth() + gap + rightImage.getWidth();
int height = Math.max(leftImage.getHeight(), rightImage.getHeight());

BufferedImage canvas = new BufferedImage(width, height, BufferedImage.TYPE_INT_ARGB);
Graphics2D graphics = canvas.createGraphics();
graphics.drawImage(leftImage, 0, 0, null);
graphics.drawImage(rightImage, leftImage.getWidth() + gap, 0, null);
graphics.dispose();

String multiImagePath = ExampleAssist.pathCombine(FOLDER, fileName);
ImageIO.write(canvas, "PNG", java.nio.file.Paths.get(multiImagePath).toFile());

BarCodeReader barCodeReader =
        new BarCodeReader(multiImagePath, DecodeType.ALL_SUPPORTED_TYPES);
ExampleAssist.assertRecognized(barCodeReader, fileName, 2, DecodeType.CODE_128, DecodeType.QR);
```

In this example, two symbols (Code 128 and QR) are drawn on a single canvas.  
`BarCodeReader` returns both results, and the helper `assertRecognized` verifies that at least one Code 128 and one QR code were found.

---

## Summary

To get the best results from `BarCodeReader` in Aspose.BarCode for Java:

- **Specify concrete symbologies** (`DecodeType.CODE_128`, `DecodeType.EAN_13`, `DecodeType.QR`, and so on) whenever you know what to expect.
- Use **grouped types** (`TYPES_1D`, `TYPES_2D`, `ALL_SUPPORTED_TYPES`) when you need more flexibility.
- Use `setBarCodeReadType(...)` to define a **custom subset** of symbologies tailored to your application.
- Combine these choices with `QualitySettings` when working with low-quality or damaged images.
- For images containing **multiple barcodes**, use a broader `DecodeType` and iterate over all `BarCodeResult` instances returned by `readBarCodes()`.

All code examples in this article are derived from:

[ChooseRecognitionSymbology.java](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/choose_symbology/ChooseRecognitionSymbology.java)

Use this class as a reference when configuring symbology handling in your own Java applications.
