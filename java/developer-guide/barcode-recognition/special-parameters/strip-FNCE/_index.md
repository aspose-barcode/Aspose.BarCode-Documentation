---
title: "Strip FNC"
description: "Learn how to control function code (FNC) characters in Code 128 and GS1-128 recognition using the StripFNC parameter."
type: docs
weight: 50
url: /java/developer-guide/barcode-recognition/strip-fnc
---

# Strip FNC

This article explains how to control handling of **FNC (function code)** characters when reading Code 128 and GS1-128 barcodes with Aspose.BarCode for Java. The `StripFNC` parameter lets you choose whether these non-printable control symbols are removed from the recognized text or preserved for post-processing.

The examples in this article are based on the test class  
[`StripFNCExample.java`](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/special_parameters/StripFNCExample.java).

## What are FNC characters?

FNC (function code) symbols are special control characters that can appear in Code 128 and GS1-128 symbols. They are not part of the human-readable payload, but are used to:

- mark **GS1 application identifier (AI)** boundaries (typically FNC1);
- represent **separators** between fields;
- support **structured append** and other protocol-level features.

In many applications you only want the **clean business data** (for example, parsed GS1 AI values) and do not need to see FNC characters in the decoded string. In other scenarios, you may want full access to the raw content, including FNC markers.

## The StripFNC parameter

`StripFNC` is exposed via barcode recognition settings:

```java
BarCodeReader reader = new BarCodeReader(path, DecodeType.CODE_128);

// Remove FNC control characters from the decoded text (default)
reader.getBarcodeSettings().setStripFNC(true);

// Or preserve FNC control characters
reader.getBarcodeSettings().setStripFNC(false);
```

- **`StripFNC = true`** (default): FNC characters are **removed** from `getCodeText()`.  
  Use this mode for most business scenarios where you need clean, human-readable data.

- **`StripFNC = false`**: FNC characters are **preserved** in `getCodeText()`.  
  Use this when you implement custom GS1 parsing, debugging, or protocol-level processing.

## Example: StripFNC enabled (default clean output)

The following example shows typical use of `StripFNC` for Code 128. A barcode is generated and read with `StripFNC` left enabled, so the output string contains no FNC markers:

```java
String fileName = "code128_stripfnc_enabled.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, path -> {
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "FNC1TEST123");
    generator.save(path, BarCodeImageFormat.PNG);
});

BarCodeReader reader =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.CODE_128);

// Default behavior: FNC is stripped from the decoded text
reader.getBarcodeSettings().setStripFNC(true);

ExampleAssist.assertRecognized(reader, fileName, 1, DecodeType.CODE_128);
```

In this configuration:

- the symbol may internally contain FNC characters (for example, FNC1);
- the recognized `codeText` is returned **without** FNC characters, suitable for direct display or logging.

## Example: StripFNC disabled (raw FNC preserved)

To inspect or reuse FNC markers, disable stripping:

```java
String fileName = "code128_stripfnc_disabled.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, path -> {
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "FNC1TEST123");
    generator.save(path, BarCodeImageFormat.PNG);
});

BarCodeReader reader =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.CODE_128);

// Preserve FNC control characters in the decoded text
reader.getBarcodeSettings().setStripFNC(false);

ExampleAssist.assertRecognized(reader, fileName, 1, DecodeType.CODE_128);
```

Now `getCodeText()` may include:

- explicit FNC markers, or
- reserved placeholders that your application interprets as FNC:

```java
BarCodeResult[] results = reader.readBarCodes();
for (BarCodeResult result : results) {
    System.out.println("Code type: " + result.getCodeTypeName());
    System.out.println("Code text (FNC preserved): " + result.getCodeText());
}
```

This mode is useful if you:

- implement **custom GS1 AI parsers** that need to see FNC1 as a field separator;
- compare raw payloads between different systems;
- debug encoding/decoding issues.

## Comparing results with StripFNC on and off

The following pattern compares decoded text for the same image when `StripFNC` is enabled and disabled:

```java
String fileName = "code128_compare.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, path -> {
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "FNC1DATA555");
    generator.save(path, BarCodeImageFormat.PNG);
});

// StripFNC = true
BarCodeReader reader1 =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.CODE_128);
reader1.getBarcodeSettings().setStripFNC(true);
BarCodeResult[] results1 = reader1.readBarCodes();

// StripFNC = false
BarCodeReader reader2 =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.CODE_128);
reader2.getBarcodeSettings().setStripFNC(false);
BarCodeResult[] results2 = reader2.readBarCodes();

System.out.println("With StripFNC(true):  " + results1[0].getCodeText());
System.out.println("With StripFNC(false): " + results2[0].getCodeText());

ExampleAssist.assertRecognized(reader1, fileName, 1, DecodeType.CODE_128);
ExampleAssist.assertRecognized(reader2, fileName, 1, DecodeType.CODE_128);
```

Key points:

- **Recognition succeeds in both cases** — `StripFNC` does not affect detection, only post-processing of the decoded text.
- The only difference is **whether FNC markers are visible in the returned string**.

## GS1-128 encoded and read as Code 128

Even when a barcode is encoded as **GS1-128**, you may still choose to read it with `DecodeType.CODE_128`. The `StripFNC` option is still respected:

```java
String fileName = "gs1encoded_as_code128.png";

ExampleAssist.checkOrCreateImage(FOLDER, fileName, path -> {
    // GS1-128: FNC1 is inserted automatically based on AI syntax
    BarcodeGenerator generator =
            new BarcodeGenerator(EncodeTypes.GS_1_CODE_128, "(01)09501101530008(10)ABC123");
    generator.save(path, BarCodeImageFormat.PNG);
});

// Read as Code128 with StripFNC enabled
BarCodeReader reader1 =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.CODE_128);
reader1.getBarcodeSettings().setStripFNC(true);
BarCodeResult[] results1 = reader1.readBarCodes();

// Read as Code128 with StripFNC disabled
BarCodeReader reader2 =
        new BarCodeReader(ExampleAssist.pathCombine(FOLDER, fileName), DecodeType.CODE_128);
reader2.getBarcodeSettings().setStripFNC(false);
BarCodeResult[] results2 = reader2.readBarCodes();

System.out.println("Decoded as CODE_128 with StripFNC(true):  " + results1[0].getCodeText());
System.out.println("Decoded as CODE_128 with StripFNC(false): " + results2[0].getCodeText());

ExampleAssist.assertRecognized(reader1, fileName, 1, DecodeType.CODE_128);
ExampleAssist.assertRecognized(reader2, fileName, 1, DecodeType.CODE_128);
```

This pattern allows you to:

- reuse a **single recognition pipeline** based on `DecodeType.CODE_128`;
- still decide whether you want **clean GS1 text** (FNC stripped) or **raw GS1 data** (FNC preserved).

## When to use each mode

Use **StripFNC = true** when:

- you only need business data and human-readable text;
- you parse GS1 strings using higher-level APIs that do not rely on explicit FNC markers;
- you log or display code text directly to users.

Use **StripFNC = false** when:

- you implement **custom or low-level GS1 logic** and need to see exact field separators;
- you debug encoding/decoding issues or compare payloads across systems;
- you integrate with systems that expect FNC markers to be present in the decoded string.

## Complete example

You can find the full, runnable example in the Aspose.BarCode for Java repository:

- [`StripFNCExample.java` on GitHub](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/special_parameters/StripFNCExample.java)
