---
title: "Generate GS1-128 Barcodes"
description: "Learn how to generate GS1-128 barcodes in Aspose.BarCode for Java, encode Application Identifiers, handle variable-length fields, configure print dimensions, and create compact layouts."
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/generate-gs1-128/
---

# Generate GS1-128 Barcodes

GS1-128 is based on Code 128 and uses GS1 Application Identifiers to encode structured supply-chain data such as GTIN, expiration date, batch number, and serial number.

In Aspose.BarCode for Java, use `EncodeTypes.GS_1_CODE_128`. Application Identifiers can be written in parentheses, for example `(01)` for GTIN or `(17)` for expiration date. The generator processes the structured input and inserts FNC1 separators where required.

The complete source code for the examples in this article is available on GitHub:

[View GenerateGS1_128.java](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/GenerateGS1_128.java)

You can also browse all barcode generation examples in the [Generation examples directory](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation).

## Generate a basic GS1-128 barcode

The following example encodes GTIN, expiration date, and batch number.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.GS_1_CODE_128,
        "(01)09501101530008(17)251231(10)BATCH-42"
);

generator.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
generator.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);
generator.getParameters().setResolution(300.0f);

generator.save("gs1_128.png", BarCodeImageFormat.PNG);
```

The code text contains the following Application Identifiers:

- `(01)` — GTIN;
- `(17)` — expiration date in `YYMMDD` format;
- `(10)` — batch or lot number.

## Encode common Application Identifiers

Multiple fixed-length and variable-length data fields can be combined in one GS1-128 symbol.

```java
String gs1CodeText = "(01)09512345678900"
        + "(17)260630"
        + "(10)LOT2025A"
        + "(21)SERIAL123456";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.GS_1_CODE_128,
        gs1CodeText
);

generator.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
generator.getParameters().getBarcode().getBarHeight().setMillimeters(16.0f);
generator.getParameters().setResolution(300.0f);

// Configure left and right quiet zones
generator.getParameters().getBarcode().getPadding().getLeft().setMillimeters(3.3f);
generator.getParameters().getBarcode().getPadding().getRight().setMillimeters(3.3f);

// Show human-readable text below the barcode
generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setLocation(CodeLocation.BELOW);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .getFont()
        .setFamilyName("Arial");

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .getFont()
        .getSize()
        .setPoint(9);

generator.save("gs1_128_complete.png", BarCodeImageFormat.PNG);
```

This layout is suitable for printed labels where dimensions and readable text must be controlled explicitly.

## Handle variable-length fields and FNC1

Some GS1 Application Identifiers have variable-length values. If another field follows, a separator is required to mark the end of the variable-length data.

When Application Identifiers are supplied in parenthesized form, Aspose.BarCode inserts FNC1 where required.

```java
String gs1CodeText = "(01)09501101530008"
        + "(10)LOT-ABC-999"
        + "(21)SN00004567";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.GS_1_CODE_128,
        gs1CodeText
);

generator.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
generator.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);
generator.getParameters().setResolution(300.0f);

generator.save("gs1_128_varlen.png", BarCodeImageFormat.PNG);
```

Here `(10)` contains a variable-length lot number and is followed by `(21)`. The required field separator is handled by the generator.

## Fit GS1-128 into a target image box

Use `ImageWidth`, `ImageHeight`, and `AutoSizeMode.NEAREST` when the generated barcode must fit a predefined bitmap area.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.GS_1_CODE_128,
        "(01)09501101530008(17)251231(10)BATCH-42"
);

generator.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
generator.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);

generator.getParameters().getImageWidth().setPixels(500);
generator.getParameters().getImageHeight().setPixels(200);
generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);
generator.getParameters().setResolution(300.0f);

generator.save("gs1_128_box.png", BarCodeImageFormat.PNG);
```

The target image box must still be large enough for the encoded content and the selected X-Dimension.

## Create a compact GS1-128 layout

The human-readable text can be hidden to reduce image height. Top and bottom padding can also be reduced.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.GS_1_CODE_128,
        "(01)09501101530008(17)251231(10)BATCH-42"
);

generator.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
generator.getParameters().getBarcode().getBarHeight().setMillimeters(12.0f);
generator.getParameters().setResolution(300.0f);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setLocation(CodeLocation.NONE);

generator.getParameters().getBarcode().getPadding().getTop().setMillimeters(1.0f);
generator.getParameters().getBarcode().getPadding().getBottom().setMillimeters(1.0f);

generator.save("gs1_128_minimal.png", BarCodeImageFormat.PNG);
```

Keep sufficient left and right quiet zones even when reducing the vertical layout.

## Recommendations

- Use `EncodeTypes.GS_1_CODE_128`, not regular `CODE_128`, for GS1-128 data.
- Enter Application Identifiers in parenthesized form to make structured input readable.
- Use valid data lengths and formats for each Application Identifier.
- Allow the generator to insert FNC1 separators for variable-length fields.
- Use physical units and an explicit resolution for print-oriented labels.
- Test the final output with the actual label size, printer, and scanner.
