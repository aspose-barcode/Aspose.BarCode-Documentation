---
title: "Allow incorrect barcodes"
description: "Learn how to use the AllowIncorrectBarcodes parameter to return potentially invalid or damaged barcodes in Aspose.BarCode for Java."
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/special-parameters/allow-incorrect-barcodes
---

# AllowIncorrectBarcodes parameter

By default, Aspose.BarCode for Java validates checksums and internal consistency of each recognition result.  
If a barcode is badly damaged, has an invalid checksum, or contains inconsistent data, the engine usually **filters it out** and does not return it as a result.

In some scenarios, however, you may still want to see these *potentially invalid* barcodes:

- for debugging or diagnostics,
- for forensic analysis of damaged labels,
- for migration from less strict engines that returned such results.

For these cases, `QualitySettings.setAllowIncorrectBarcodes(true)` relaxes validation and allows such barcodes to be returned.

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.special_parameters.AllowIncorrectBarcodesExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/special_parameters/AllowIncorrectBarcodesExample.java" target="_blank" rel="noopener noreferrer">AllowIncorrectBarcodesExample.java</a>

Test images are created on the fly using `BarcodeGenerator` and a small helper that simulates a damaged Code 39 symbol.

---

## Default behavior: invalid barcodes are filtered out

When `AllowIncorrectBarcodes` is **false** (default), the recognition pipeline:

1. decodes a candidate symbol,
2. validates checksum and internal structure,
3. discards results that fail these checks.

For valid images this flag has no visible effect — everything is recognized normally.

Example: reading a valid Code 39 barcode with `AllowIncorrectBarcodes` disabled.

```java
String imagesFolder = ExampleAssist.getOrCreateResourceFolderPath(
        "recognition", "special_parameters", "allow_incorrect");

String fileName = "code39_valid.png";

// Generate a valid Code 39 sample if it does not exist yet
ExampleAssist.checkOrCreateImage(imagesFolder, fileName, fullPath -> {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.CODE_39, "VALID123");
    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
});

// Read with AllowIncorrectBarcodes = false (default)
String imagePath = ExampleAssist.pathCombine(imagesFolder, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_39);
barCodeReader.getQualitySettings().setAllowIncorrectBarcodes(false);

// At least one valid Code 39 result is expected
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.CODE_39);
```

Now consider a **damaged** Code 39.  
In the example class, a valid symbol is generated and then partially covered with a black rectangle so that its checksum is no longer valid. With `AllowIncorrectBarcodes` disabled, the engine will typically return **zero** results:

```java
String fileName = "code39_damaged_disallowed.png";
ExampleAssist.checkOrCreateImage(imagesFolder, fileName,
        fullPath -> generateDamagedCode39(fullPath));

String imagePath = ExampleAssist.pathCombine(imagesFolder, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_39);

// Keep validation strict
barCodeReader.getQualitySettings().setAllowIncorrectBarcodes(false);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
System.out.println("Detected count (AllowIncorrect=false): " + barCodeResults.length);

// In this example we expect zero valid results for the damaged code
ExampleAssist.assertRecognized(barCodeReader, fileName, 0, DecodeType.CODE_39);
```

This is the recommended behavior for most production workflows: if the barcode is not trustworthy, do not use it.

---

## Returning damaged or checksum-invalid barcodes

If you explicitly enable `AllowIncorrectBarcodes`, the engine will relax some validation rules and return **even potentially invalid** results:

- barcodes that fail checksum,
- barcodes that are partially occluded,
- barcodes that otherwise would be discarded.

This can be useful when:

- you want to inspect *what the engine sees* on heavily damaged labels,
- you collect diagnostic samples to improve printing or camera setup,
- you need to debug borderline recognition behavior.

Example: reading the same damaged Code 39 with `AllowIncorrectBarcodes = true`:

```java
String fileName = "code39_damaged_allowed.png";
ExampleAssist.checkOrCreateImage(imagesFolder, fileName,
        fullPath -> generateDamagedCode39(fullPath));

String imagePath = ExampleAssist.pathCombine(imagesFolder, fileName);
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_39);

// Relax validation: allow potentially incorrect barcodes
barCodeReader.getQualitySettings().setAllowIncorrectBarcodes(true);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
System.out.println("Detected count (AllowIncorrect=true): " + barCodeResults.length);

for (BarCodeResult barCodeResult : barCodeResults) {
    System.out.println("Code text (possibly invalid): " + barCodeResult.getCodeText());
}

// Now at least one damaged Code 39 is expected to be returned
ExampleAssist.assertRecognized(barCodeReader, fileName, 1, DecodeType.CODE_39);
```

Important notes:

- Returned text and symbology are **not guaranteed to be correct** when this flag is enabled.
- You should treat these results as *best-effort guesses*, not as validated data.
- Any business logic must perform its own validation on top of the decoded values.

---

## Comparing both modes on the same image

To clearly see the effect of `AllowIncorrectBarcodes`, the example class also runs recognition twice on the same damaged image:

1. with `AllowIncorrectBarcodes = false`,
2. with `AllowIncorrectBarcodes = true`.

```java
String fileName = "code39_compare.png";
ExampleAssist.checkOrCreateImage(FOLDER, fileName,
        fullPath -> generateDamagedCode39(fullPath));

String imagePath = ExampleAssist.pathCombine(FOLDER, fileName);

// 1) Strict validation: incorrect results are filtered out
BarCodeReader strictReader = new BarCodeReader(imagePath, DecodeType.CODE_39);
strictReader.getQualitySettings().setAllowIncorrectBarcodes(false);
BarCodeResult[] strictResults = strictReader.readBarCodes();

// 2) Relaxed validation: potentially incorrect barcodes are returned
BarCodeReader relaxedReader = new BarCodeReader(imagePath, DecodeType.CODE_39);
relaxedReader.getQualitySettings().setAllowIncorrectBarcodes(true);
BarCodeResult[] relaxedResults = relaxedReader.readBarCodes();

System.out.println("AllowIncorrect(false): " + strictResults.length + " result(s)");
System.out.println("AllowIncorrect(true):  " + relaxedResults.length + " result(s)");

if (relaxedResults.length > 0) {
    System.out.println("Recovered text: " + relaxedResults[0].getCodeText());
}

// For the documentation sample we expect at least one result when the flag is enabled
ExampleAssist.assertRecognized(relaxedReader, fileName, 1, DecodeType.CODE_39);
```

Typical outcome on the provided sample:

- strict mode → `0` results, because checksum validation rejects the damaged symbol;
- relaxed mode → `1` result, showing what text the engine is still able to reconstruct.

---

## How the damaged sample is generated

The helper method `generateDamagedCode39` creates a damaged fixture in a deterministic way:

1. generate a valid Code 39 with text like `"BROKEN999"`,
2. draw a black rectangle over the central part of the symbol,
3. save the modified image.

Conceptually, it looks like this:

```java
private void generateDamagedCode39(String fullPath) throws IOException {
    // 1) Render a valid Code 39 symbol to a temporary image
    String tempPath = fullPath + "_temp.png";
    BarcodeGenerator barcodeGenerator = new BarcodeGenerator(EncodeTypes.CODE_39, "BROKEN999");
    barcodeGenerator.save(tempPath, BarCodeImageFormat.PNG);

    // 2) Load and cover part of the bars
    BufferedImage bufferedImage = ImageIO.read(Paths.get(tempPath).toFile());
    Graphics2D graphics = bufferedImage.createGraphics();

    graphics.setColor(Color.BLACK);
    int coverWidth = bufferedImage.getWidth() / 4;
    int coverHeight = bufferedImage.getHeight() / 2;
    graphics.fillRect(
            bufferedImage.getWidth() / 3,
            bufferedImage.getHeight() / 3,
            coverWidth,
            coverHeight
    );
    graphics.dispose();

    // 3) Save damaged image and delete the temporary file
    ImageIO.write(bufferedImage, "PNG", Paths.get(fullPath).toFile());
    java.nio.file.Files.deleteIfExists(Paths.get(tempPath));
}
```

The resulting image still visually resembles a barcode but fails internal validation checks, which makes it ideal for demonstrating how `AllowIncorrectBarcodes` works.

---

## When to use AllowIncorrectBarcodes

Use `AllowIncorrectBarcodes = true` **only when you explicitly need it**, for example:

- you analyze heavily damaged labels and want to see partial or approximate data;
- you debug recognition behavior on borderline inputs;
- you compare different recognition engines and want to inspect candidates that would normally be discarded.

In most production scenarios you should keep the default:

```java
barCodeReader.getQualitySettings().setAllowIncorrectBarcodes(false);
```

and rely on checksums and structural validation to guarantee that returned barcodes are consistent and trustworthy.

If you do enable this flag:

- treat the output as *untrusted* until it is validated by your own business rules;
- log or highlight such results as “suspect” in your application UI;
- consider using them only as a last-resort hint for manual review, not as automatic input.

This approach lets you balance robustness and safety: you can inspect what the engine is able to decode from damaged barcodes, while still keeping production data flows strict and reliable.
