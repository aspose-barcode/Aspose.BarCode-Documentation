---
title: "Work with symbology types"
description: "Learn how to choose and configure barcode symbology types when using BarCodeReader in Aspose.BarCode for Java."
type: docs
weight: 40
url: /java/developer-guide/barcode-recognition/work-with-symbology-types
---

# Working with symbology types in recognition

When you recognize barcodes with `BarCodeReader`, it is not enough to just pass an image.  
You should also decide **which symbology types the engine is allowed to use**.

Configuring `DecodeType` values correctly helps you:

- improve performance by narrowing down the search space,
- reduce false positives by filtering out unexpected symbologies,
- make your intent explicit in the code and tests,
- document which barcode formats your application actually supports.

This article shows how to:

1. Use **symbology configuration strategies** (single type, small sets, grouped types, discovery).
2. Work with **common 1D symbologies** (Code 128, Code 39, EAN, UPC, Codabar, ITF-14).
3. Work with **2D symbologies** (QR, Micro QR, Data Matrix, GS1 Data Matrix, PDF417, Macro PDF417, Aztec).
4. Work with **postal barcodes**.
5. Recognize **multiple barcodes in one image**.

All examples are based on the sample classes:

- [`com.aspose.barcode.guide.recognition.choose_symbology.ChooseRecognitionSymbology`](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/choose_symbology/ChooseRecognitionSymbology.java)
- [`com.aspose.barcode.guide.recognition.barcode_properties.ConfigureSymbologyTypeExample`](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/ConfigureSymbologyTypeExample.java)

In the snippets below, helper methods such as `ExampleAssist.checkOrCreateImage`,  
`ExampleAssist.pathCombine`, `ExampleAssist.assertRecognized`, and `ExampleAssist.assertNotRecognized` come from the test infrastructure and are used to generate fixtures and verify results.

---

## 1. Symbology configuration strategies

This section focuses on **how** to configure `DecodeType`, not on individual barcode formats.

### 1.1 Using a single explicit symbology

If you know exactly which symbology you expect, the best option is to pass a **single explicit** `DecodeType` to `BarCodeReader`.  
This is both the fastest and the safest configuration.

The example below shows how to recognize a Code 128 symbol using `DecodeType.CODE_128` only:

```java
String imagePath = getFullPath(FILE_C128);

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.CODE_128);

ExampleAssist.assertRecognized(
        barCodeReader,
        FILE_C128,
        1,
        DecodeType.CODE_128
);
```

Use this pattern when:

- the business process strictly defines the symbology (for example, Code 128 for internal IDs),
- performance is important and you want to avoid checking other types,
- you want to minimize the chance of false positives from similar barcodes.

The same approach applies to other formats, such as `DecodeType.EAN_13`, `DecodeType.QR`, `DecodeType.DATA_MATRIX`, and so on.

---

### 1.2 Using the “most common” set

Sometimes you do not know the exact symbology, but you still want to keep the search limited to **popular types**.

In this case, use the grouped type `DecodeType.MOST_COMMON_TYPES`.  
Aspose.BarCode will try a curated set of commonly used symbologies:

```java
String imagePath = getFullPath(FILE_QR);

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.MOST_COMMON_TYPES);

ExampleAssist.assertRecognized(
        barCodeReader,
        FILE_QR,
        1,
        DecodeType.QR
);
```

This configuration is useful when:

- your system accepts several common barcode types,
- the input data is heterogeneous but still limited to typical retail or logistics formats.

---

### 1.3 Using grouped 1D and 2D types

Aspose.BarCode also provides grouped `DecodeType` values for **all 1D** and **all 2D** symbologies:

- `DecodeType.TYPES_1D` – restricts recognition to linear (1D) codes,
- `DecodeType.TYPES_2D` – restricts recognition to 2D codes such as QR, Data Matrix, PDF417, Aztec.

Example: recognize a Code 128 barcode with all 1D types allowed:

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

Example: recognize a Data Matrix barcode when all 2D types are allowed:

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

Use these grouped types when you know your application only uses **1D** or only **2D** barcodes.

---

### 1.4 Passing multiple explicit symbologies

You can configure `BarCodeReader` to use a **small explicit set** of symbologies.  
This combines the control of explicit types with more flexibility than a single type.

The test fixture contains a mixed image with a QR Code and a Code 128 symbol placed side by side.  
The following snippet shows how to recognize both of them by passing `DecodeType.QR` and `DecodeType.CODE_128`:

```java
String imagePath = getFullPath(FILE_MIX);

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.QR, DecodeType.CODE_128);

BarCodeResult[] results = barCodeReader.readBarCodes();

Assert.assertTrue(results.length >= 2, "Expected at least QR + Code128");

boolean hasQR = ExampleAssist.hasDecodeType(results, DecodeType.QR);
boolean hasC128 = ExampleAssist.hasDecodeType(results, DecodeType.CODE_128);

Assert.assertTrue(hasQR && hasC128, "Mixed image must contain QR and Code128");
```

Use this approach when:

- your application supports a limited list of types (for example, QR and Code 128),
- you want to avoid the overhead of `ALL_SUPPORTED_TYPES`,
- you want more control than `MOST_COMMON_TYPES` provides.

---

### 1.5 Defining a custom subset with `setBarCodeReadType`

In addition to constructor parameters, you can configure a **custom subset** of symbologies at runtime using `setBarCodeReadType(...)`.

In the following example, the reader is limited to three symbologies: Code 128, QR, and Data Matrix:

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

Use this pattern when:

- your application supports a known subset of symbologies,
- you want to avoid checking all others,
- you need to configure the subset dynamically.

---

### 1.6 Using all supported types for discovery

For exploratory scenarios, you may want to detect **any** supported symbology present in the image.  
This is the broadest search and therefore the slowest and most permissive.

Use `DecodeType.ALL_SUPPORTED_TYPES`:

```java
String imagePath = getFullPath(FILE_EAN13);

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.ALL_SUPPORTED_TYPES);

ExampleAssist.assertRecognized(
        barCodeReader,
        FILE_EAN13,
        1,
        DecodeType.EAN_13
);
```

Typical use cases:

- diagnostics and debugging when you are not sure which symbology is printed,
- tools that must handle arbitrary barcodes without prior knowledge,
- migrating legacy systems where symbology usage is unknown.

---

### 1.7 Filtering to avoid false positives

Restricting `DecodeType` not only improves speed, but also helps **reject invalid images**.

The following example intentionally misconfigures the reader:  
it tries to read a Code 128 barcode while allowing only `DecodeType.QR`.  
In this case you expect **zero** results:

```java
String imagePath = getFullPath(FILE_C128);

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.QR);

ExampleAssist.assertNotRecognized(barCodeReader, FILE_C128);
```

This pattern is useful when:

- you want to be strict about accepted symbologies,
- you treat any result of an unexpected type as a potential false positive,
- you implement validation logic in tests or QA tools.

---

### 1.8 Using an exact type for 2D barcodes such as Data Matrix

For 2D barcodes like Data Matrix, it is often safer to use the **exact** `DecodeType`.  
When you already know that the image contains a specific 2D barcode type (for example, Data Matrix), specifying the exact `DecodeType` lets the engine skip other 2D symbologies, which improves performance and can make recognition more robust on low-quality images.

The example below uses `DecodeType.DATA_MATRIX` to recognize a Data Matrix symbol:

```java
String imagePath = getFullPath(FILE_DM);

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.DATA_MATRIX);

ExampleAssist.assertRecognized(
        barCodeReader,
        FILE_DM,
        1,
        DecodeType.DATA_MATRIX
);
```

This approach is recommended when:

- your process standardizes on a specific 2D symbology (for example Data Matrix on labels),
- you use GS1 or other structured data encoded in 2D barcodes,
- you want predictable behavior and clear expectations in tests.

---

## 2. Examples for common 1D symbologies

This section shows how to apply the configuration strategies to **specific 1D formats** using `ChooseRecognitionSymbology`.

In production code you often know exactly which 1D symbology you expect: Code 128 for logistics labels, EAN/UPC for retail, ITF-14 for cartons, and so on.  
In such cases, pass the **exact** `DecodeType` to `BarCodeReader`.

### 2.1 Code 128

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

---

### 2.2 Code 39 and Code 39 Full ASCII

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

---

### 2.3 EAN-13 and EAN-13 with supplement

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

EAN-13 with a 2- or 5-digit supplement is common for magazines and books.  
The main symbology is still EAN-13, so `DecodeType.EAN_13` is used.

---

### 2.4 EAN-8

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

---

### 2.5 UPC-A and UPC-E

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

UPC-A and UPC-E are widely used in North America for retail items.  
Use the matching `DecodeType` for the symbology you expect on your labels.

---

### 2.6 Codabar

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

---

### 2.7 ITF-14

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

## 3. Examples for 2D symbologies

For 2D barcodes you also choose specific `DecodeType` values.  
This section shows basic patterns for QR, Micro QR, Data Matrix, GS1 Data Matrix, PDF417, Macro PDF417, and Aztec.

### 3.1 QR Code and Micro QR

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

---

### 3.2 QR with high-quality settings (damaged or low-quality images)

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

---

### 3.3 Data Matrix and GS1 Data Matrix

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

---

### 3.4 PDF417 and Macro PDF417

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

---

### 3.5 Aztec

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

### 3.6 GS1-128 only

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

## 4. Postal barcodes

Postal symbologies have dedicated `DecodeType` values.  
The examples below show how to generate and recognize POSTNET, PLANET, and Australia Post barcodes.

### 4.1 POSTNET

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

---

### 4.2 PLANET

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

---

### 4.3 Australia Post

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

## 5. Mixed and multiple barcodes in one image

You can also recognize images that contain more than one barcode.

In this scenario you typically use a broader `DecodeType` (for example `ALL_SUPPORTED_TYPES` or `MOST_COMMON_TYPES`)  
and then inspect each `BarCodeResult` returned by `readBarCodes()`.

The following example uses two symbols (Code 128 and QR) drawn on a single canvas:

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

`BarCodeReader` returns both results, and the helper `assertRecognized` verifies that at least one Code 128 and one QR code were found.

You can combine this pattern with the strategies from section 1:

- restrict the image to a **single** type to ignore unrelated symbols (for example Code 128 only),
- use `MOST_COMMON_TYPES` to get only typical formats from a mixed page,
- use strict filtering in tests to ensure that unwanted symbologies are ignored.

---

## 6. Test fixtures and sample images

Both sample classes (`ChooseRecognitionSymbology` and `ConfigureSymbologyTypeExample`) contain helper code that generates example images used in the tests.  
Images are created on demand using `BarcodeGenerator` and then stored under the corresponding resource folders.

For example, a Code 128 barcode fixture is created as follows:

```java
ExampleAssist.checkOrCreateImage(FOLDER, FILE_C128, fullPath -> {
    BarcodeGenerator generator =
            new BarcodeGenerator(EncodeTypes.CODE_128, "C128-DEMO");
    generator.save(fullPath, BarCodeImageFormat.PNG);
});
```

The mixed QR + Code 128 image is built by generating two separate barcodes and placing them on a single canvas:

```java
String qrTemp = Paths.get(FOLDER, "_tmp_qr.png").toString();
String c128Temp = Paths.get(FOLDER, "_tmp_c128.png").toString();

BarcodeGenerator qrGen = new BarcodeGenerator(EncodeTypes.QR, "QR-MIX");
qrGen.save(qrTemp, BarCodeImageFormat.PNG);

BarcodeGenerator c128Gen = new BarcodeGenerator(EncodeTypes.CODE_128, "C128-MIX");
c128Gen.save(c128Temp, BarCodeImageFormat.PNG);

BufferedImage qr = ImageIO.read(new File(qrTemp));
BufferedImage c128 = ImageIO.read(new File(c128Temp));

int pad = 20;
int w = qr.getWidth() + c128.getWidth() + pad * 3;
int h = Math.max(qr.getHeight(), c128.getHeight()) + pad * 2;

BufferedImage canvas = new BufferedImage(w, h, BufferedImage.TYPE_INT_RGB);
Graphics2D g = canvas.createGraphics();
try {
    g.setColor(Color.WHITE);
    g.fillRect(0, 0, w, h);
    g.drawImage(qr, pad, pad, null);
    g.drawImage(c128, pad * 2 + qr.getWidth(), pad, null);
} finally {
    g.dispose();
}

ImageIO.write(canvas, "PNG", new File(outPath));
```

You can reuse this pattern in your own tests to create controlled multi-barcode images.

---

## Summary

To configure symbology types effectively when using `BarCodeReader` in Aspose.BarCode for Java:

- Use a **single explicit** `DecodeType` whenever you know the exact symbology (fastest and most robust).
- Use `DecodeType.MOST_COMMON_TYPES` when you expect popular formats but do not want to maintain a list.
- Use grouped types such as `DecodeType.TYPES_1D` and `DecodeType.TYPES_2D` when your application is limited to linear or 2D codes.
- Use `DecodeType.ALL_SUPPORTED_TYPES` only for **discovery** and diagnostic purposes.
- Pass **multiple explicit types** or configure a custom subset with `setBarCodeReadType(...)` when your application supports a small, well-defined set of symbologies.
- Use strict filtering (for example, a deliberately wrong `DecodeType`) in tests to catch false positives.
- For mixed images, combine broad or grouped types with result inspection to verify that all expected symbologies are present.
- For 2D codes such as Data Matrix, prefer the **exact** `DecodeType` to avoid ambiguity and improve robustness.

Use the `ChooseRecognitionSymbology` and `ConfigureSymbologyTypeExample` classes as references when designing your own symbology selection and recognition strategy.
