---
title: "Australian Post Parameters"
description: "Learn how to configure AustralianPost customer information interpreting types (C_TABLE, N_TABLE, OTHER) in Aspose.BarCode for Java."
type: docs
weight: 20
url: /java/developer-guide/barcode-recognition/special-parameters/australian-post-parameters
---

# AustralianPost parameters

Aspose.BarCode for Java provides dedicated settings for AustralianPost barcodes that control how the **Customer Information** field is encoded and interpreted.

This article shows how to:

- generate AustralianPost barcodes with specific **encoding tables**
- read them with matching **customer information interpreting types**
- choose between `C_TABLE`, `N_TABLE`, and `OTHER` depending on your payload

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.special_parameters.AustralianPostParametersExample`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/special_parameters/AustralianPostParametersExample.java" target="_blank" rel="noopener noreferrer">AustralianPostParametersExample.java</a>

---

## Customer information interpreting types

AustralianPost barcodes contain a **Customer Information** field whose content can be interpreted in different ways. Aspose.BarCode exposes this via the `CustomerInformationInterpretingType` enumeration, used in both generator and reader APIs.

The three main modes are:

| Interpreting type | Enum value                                        | Payload characteristics                                      | Typical usage                          |
|-------------------|---------------------------------------------------|--------------------------------------------------------------|----------------------------------------|
| C table           | `CustomerInformationInterpretingType.C_TABLE`    | Alphanumeric (letters, digits, space, `#`)                   | Customer IDs, short codes, labels      |
| N table           | `CustomerInformationInterpretingType.N_TABLE`    | Numeric-only digits                                          | Account numbers, postal references     |
| Other             | `CustomerInformationInterpretingType.OTHER`      | Raw data, 0–3 symbolic characters, no semantic interpretation | Special/custom integrations, binary tags |

When **generating** barcodes, you configure the encoding table on the generator:

```java
BarcodeGenerator barcodeGenerator =
        new BarcodeGenerator(EncodeTypes.AUSTRALIA_POST, "5912345678ABCde");
barcodeGenerator.getParameters()
        .getBarcode()
        .getAustralianPost()
        .setAustralianPostEncodingTable(CustomerInformationInterpretingType.C_TABLE);
```

When **reading** barcodes, you configure how the engine interprets the customer information:

```java
BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.AUSTRALIA_POST);
barCodeReader.getBarcodeSettings()
        .getAustraliaPost()
        .setCustomerInformationInterpretingType(CustomerInformationInterpretingType.C_TABLE);
```

> Always keep the encoding table on the generator and the interpreting type on the reader **in sync**.  
> A mismatch (for example, encoding with `C_TABLE` but reading with `N_TABLE`) may lead to incorrect or failed decoding.

---

## Example 1. Reading AustralianPost with C table (alphanumeric)

The `C_TABLE` mode supports a subset of ASCII characters: uppercase letters, digits, space, and `#`. This is convenient for compact alphanumeric identifiers such as customer codes.

In the example class, the test `readAustralianPostCTable()` uses:

- **Generator**: `C_TABLE` encoding with mixed letters and digits
- **Reader**: `C_TABLE` interpreting type to correctly decode the payload

### Generating an AustralianPost barcode with C table

```java
private void generateCTable(String fullPath) throws IOException {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.AUSTRALIA_POST, "5912345678ABCde");

    barcodeGenerator.getParameters()
            .getBarcode()
            .getAustralianPost()
            .setAustralianPostEncodingTable(CustomerInformationInterpretingType.C_TABLE);

    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
}
```

### Reading with C table interpreting type

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "australian_post_ctable.png");

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.AUSTRALIA_POST);

// Interpret customer information as C table (alphanumeric)
barCodeReader.getBarcodeSettings()
        .getAustraliaPost()
        .setCustomerInformationInterpretingType(CustomerInformationInterpretingType.C_TABLE);

// Expect exactly one AustralianPost barcode in this sample
ExampleAssist.assertRecognized(barCodeReader,
        "australian_post_ctable.png", 1, DecodeType.AUSTRALIA_POST);
```

Key points:

- The payload `5912345678ABCde` follows C table rules (digits + letters).
- Both generator and reader are aligned to `C_TABLE`.
- Use this mode whenever you need compact alphanumeric customer information.

---

## Example 2. Reading AustralianPost with N table (numeric)

The `N_TABLE` mode is restricted to **digits only**. This is suitable for purely numeric customer data such as account numbers, shipment IDs, or internal numeric references.

The test `readAustralianPostNTable()` demonstrates this alignment.

### Generating an AustralianPost barcode with N table

```java
private void generateNTable(String fullPath) throws IOException {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.AUSTRALIA_POST, "59123456781234567");

    barcodeGenerator.getParameters()
            .getBarcode()
            .getAustralianPost()
            .setAustralianPostEncodingTable(CustomerInformationInterpretingType.N_TABLE);

    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
}
```

### Reading with N table interpreting type

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "australian_post_ntable.png");

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.AUSTRALIA_POST);

// Interpret customer information as numeric-only table
barCodeReader.getBarcodeSettings()
        .getAustraliaPost()
        .setCustomerInformationInterpretingType(CustomerInformationInterpretingType.N_TABLE);

ExampleAssist.assertRecognized(barCodeReader,
        "australian_post_ntable.png", 1, DecodeType.AUSTRALIA_POST);
```

Notes:

- Use `N_TABLE` when you know the customer information is strictly numeric.
- If non-digit characters appear in the payload, decoding in this mode may fail or produce invalid results.

---

## Example 3. Reading AustralianPost with OTHER (raw data)

The `OTHER` mode disables semantic interpretation and treats the customer information as **raw data**. According to the AustralianPost specification, this mode allows 0–3 symbolic characters and is intended for special-purpose use cases.

In the test `readAustralianPostOther()`:

- The generator uses `OTHER` as encoding table and a longer payload.
- The reader uses `OTHER` as interpreting type to read the barcode without applying C/N table rules.

### Generating an AustralianPost barcode with OTHER

```java
private void generateOther(String fullPath) throws IOException {
    BarcodeGenerator barcodeGenerator =
            new BarcodeGenerator(EncodeTypes.AUSTRALIA_POST,
                    "59123456780123012301230123");

    barcodeGenerator.getParameters()
            .getBarcode()
            .getAustralianPost()
            .setAustralianPostEncodingTable(CustomerInformationInterpretingType.OTHER);

    barcodeGenerator.save(fullPath, BarCodeImageFormat.PNG);
}
```

### Reading with OTHER interpreting type

```java
String imagePath = ExampleAssist.pathCombine(FOLDER, "australian_post_other.png");

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.AUSTRALIA_POST);

// Do not apply C/N tables; interpret payload as raw customer information
barCodeReader.getBarcodeSettings()
        .getAustraliaPost()
        .setCustomerInformationInterpretingType(CustomerInformationInterpretingType.OTHER);

ExampleAssist.assertRecognized(barCodeReader,
        "australian_post_other.png", 1, DecodeType.AUSTRALIA_POST);
```

When to use `OTHER`:

- You need to carry special-purpose data that does not fit neatly into C or N tables.
- The receiving side knows how to interpret the raw customer information.
- You want full control over how the payload is parsed at the application level.

---

## Summary

AustralianPost barcodes in Aspose.BarCode for Java provide flexible configuration for the **Customer Information** field via `CustomerInformationInterpretingType`:

- **C table (`C_TABLE`)** — alphanumeric (letters, digits, space, `#`), good for IDs and short labels.
- **N table (`N_TABLE`)** — digits only, suitable for numeric codes and references.
- **Other (`OTHER`)** — raw data mode, intended for specialized integrations.

To use these options effectively:

1. Configure the encoding table on the **generator**:

   ```java
   barcodeGenerator.getParameters()
           .getBarcode()
           .getAustralianPost()
           .setAustralianPostEncodingTable(CustomerInformationInterpretingType.C_TABLE);
   ```

2. Configure the interpreting type on the **reader** to match:

   ```java
   barCodeReader.getBarcodeSettings()
           .getAustraliaPost()
           .setCustomerInformationInterpretingType(CustomerInformationInterpretingType.C_TABLE);
   ```

3. Keep both sides in sync (same mode) to ensure stable and predictable decoding.

Use the patterns from `AustralianPostParametersExample` as a reference when integrating AustralianPost barcodes into your Java applications.
