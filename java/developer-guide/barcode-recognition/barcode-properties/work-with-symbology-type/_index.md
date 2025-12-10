---
title: "Work with symbology types"
description: "Learn how to choose and configure barcode symbology types when using BarCodeReader in Aspose.BarCode for Java."
type: docs
weight: 70
url: /java/developer-guide/barcode-recognition/barcode-properties/work-with-symbology-type
---

# Configuring symbology types for recognition

When you recognize barcodes with `BarCodeReader`, it is not enough to just pass an image.  
You should also decide **which symbology types the engine is allowed to use**.

Configuring `DecodeType` values correctly helps you:

- improve performance by narrowing down the search space,
- reduce false positives by filtering out unexpected symbologies,
- make your intent explicit in the code and tests.

This article focuses on **symbology type configuration strategies**, not on individual barcode formats.  
All examples are based on the sample class  
[`com.aspose.barcode.guide.recognition.barcode_properties.ConfigureSymbologyTypeExample`](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/barcode_properties/ConfigureSymbologyTypeExample.java).

The class covers these scenarios:

1. Single explicit symbology (best for speed and fewer false positives).
2. The “most common” set when the exact symbology is unknown.
3. All supported types for broad discovery.
4. Multiple selected symbologies at once (for example QR + Code 128).
5. Filtering: using a wrong type to ensure zero results.
6. Mixed images that contain more than one barcode.
7. Using an exact type for Data Matrix.

In the snippets below, helper methods such as `ExampleAssist.assertRecognized`,  
`ExampleAssist.assertNotRecognized`, and `ExampleAssist.checkOrCreateImage` come from the test infrastructure and are used to generate fixtures and verify results.

---

## 1. Using a single explicit symbology

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

---

## 2. Using the “most common” set

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
- the input data is heterogeneous, but still limited to typical retail or logistics formats.

---

## 3. Using all supported types for discovery

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

## 4. Passing multiple explicit symbologies

You can also configure `BarCodeReader` to use a **small explicit set** of symbologies.  
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

- your application supports a limited list of types (for example QR and Code 128),
- you want to avoid the overhead of `ALL_SUPPORTED_TYPES`,
- you want more control than `MOST_COMMON_TYPES` provides.

---

## 5. Filtering to avoid false positives

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

## 6. Restricting a mixed image to a single type

The same mixed image with QR + Code 128 can be used to demonstrate **selective recognition**.

If you configure `BarCodeReader` with `DecodeType.CODE_128` only, the QR Code will be ignored,  
and only the Code 128 symbol will be recognized:

```java
String imagePath = getFullPath(FILE_MIX);

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.CODE_128);

BarCodeResult[] results = barCodeReader.readBarCodes();

Assert.assertTrue(results.length >= 1, "Expected at least one Code128 result");
Assert.assertTrue(
        ExampleAssist.hasDecodeType(results, DecodeType.CODE_128),
        "Expected Code128 in results"
);
Assert.assertFalse(
        ExampleAssist.hasDecodeType(results, DecodeType.QR),
        "QR must be ignored when only Code128 is allowed"
);
```

This pattern is helpful when:

- you scan documents that may contain multiple barcode types but you only care about one of them,
- you want to ensure that unrelated barcodes on the same page do not affect the results.

---

## 7. Mixed image with the “most common” set

The same mixed image can be recognized using the `MOST_COMMON_TYPES` group.  
Since both QR and Code 128 are typically included in this group, you can still retrieve both barcodes:

```java
String imagePath = getFullPath(FILE_MIX);

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.MOST_COMMON_TYPES);

BarCodeResult[] results = barCodeReader.readBarCodes();

Assert.assertTrue(
        results.length >= 2,
        "Expected at least two results on a mixed image"
);
Assert.assertTrue(
        ExampleAssist.hasDecodeType(results, DecodeType.QR),
        "Expected QR in results"
);
Assert.assertTrue(
        ExampleAssist.hasDecodeType(results, DecodeType.CODE_128),
        "Expected Code128 in results"
);
```

Use this configuration if:

- you expect typical symbologies (such as QR and Code 128),
- but you do not want to maintain an explicit list in code.

---

## 8. Using an exact type for Data Matrix

For 2D barcodes like Data Matrix, it is often safer to use the **exact** `DecodeType`.  
When you already know that the image contains a specific 2D barcode type (for example, Data Matrix), specifying the exact DecodeType lets the engine skip other 2D symbologies, which improves performance and can make recognition more robust on low-quality images.

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

## 9. Test fixtures and sample images

The `ConfigureSymbologyTypeExample` class also contains helper code that generates example images used in the tests.  
Images are created on demand using `BarcodeGenerator` and then stored under the `symbology_type` resource folder.

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
- Use `DecodeType.ALL_SUPPORTED_TYPES` only for **discovery** and diagnostic purposes.
- Pass **multiple explicit types** when your application supports a small, well-defined set of symbologies.
- Use strict filtering (for example, a wrong `DecodeType`) in tests to catch false positives.
- For mixed images, combine broad or grouped types with result inspection to verify that all expected symbologies are present.
- For 2D codes such as Data Matrix, prefer the **exact** `DecodeType` to avoid ambiguity.

All code examples in this article are derived from the  
`ConfigureSymbologyTypeExample` class in the Aspose.BarCode for Java test suite.  
Use it as a reference when designing your own symbology selection and recognition strategy.
