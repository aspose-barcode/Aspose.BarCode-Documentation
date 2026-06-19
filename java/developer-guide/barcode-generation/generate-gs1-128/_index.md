---
title: "Generate GS1-128 Barcodes"
description: "Learn how to generate GS1-128 barcodes in Aspose.BarCode for Java, encode Application Identifiers, handle variable-length fields, configure physical dimensions, and create compact or box-driven layouts."
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/generate-gs1-128/
---

# Generate GS1-128 Barcodes

GS1-128 is based on Code 128 and uses GS1 Application Identifiers to encode structured supply-chain data such as GTIN, expiration date, batch or lot number, and serial number.

In Aspose.BarCode for Java, use `EncodeTypes.GS_1_CODE_128`. Application Identifiers must be supplied in parenthesized form, for example `(01)` for GTIN and `(17)` for an expiration date. The parentheses make the structured input readable but are not encoded as ordinary data characters. The generator inserts the required GS1 field separator after a non-final variable-length field where needed.

The complete source code for the examples in this article is available on GitHub:

[View GenerateGS1_128.java](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/GenerateGS1_128.java)

You can also browse all barcode generation examples in the [Generation examples directory](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation).

## Generate a basic GS1-128 barcode

The following example encodes a GTIN, expiration date, and batch number.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.GS_1_CODE_128,
        "(01)09501101530003(17)251231(10)BATCH-42"
);

// Example dimensions; verify them against the applicable GS1 specification
generator.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
generator.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);
generator.getParameters().setResolution(300.0f);

// Reserve horizontal quiet zones
generator.getParameters().getBarcode().getPadding().getLeft().setMillimeters(3.5f);
generator.getParameters().getBarcode().getPadding().getRight().setMillimeters(3.5f);

generator.save("gs1_128.png", BarCodeImageFormat.PNG);
```

The code text contains the following Application Identifiers:

- `(01)` — a 14-digit GTIN including its check digit;
- `(17)` — an expiration date in `YYMMDD` format;
- `(10)` — a variable-length batch or lot number.

The dimensions in this example illustrate configuration in physical units. Required dimensions depend on the applicable GS1 application specification, label size, printing process, and scanning environment.

## Encode common Application Identifiers

Multiple fixed-length and variable-length element strings can be combined in one GS1-128 symbol.

```java
String gs1CodeText = "(01)09512345678901"
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

generator.getParameters().getBarcode().getPadding().getLeft().setMillimeters(3.5f);
generator.getParameters().getBarcode().getPadding().getRight().setMillimeters(3.5f);

CodetextParameters codeTextParameters = generator.getParameters()
        .getBarcode()
        .getCodeTextParameters();

codeTextParameters.setLocation(CodeLocation.BELOW);
codeTextParameters.setFontMode(FontMode.MANUAL);
codeTextParameters.getFont().setFamilyName("Arial");
codeTextParameters.getFont().getSize().setPoint(9);

generator.save("gs1_128_complete.png", BarCodeImageFormat.PNG);
```

`FontMode.MANUAL` is required when the explicitly configured font size must be used. In automatic font mode, the library calculates the font size from the barcode dimensions.

The selected font family must be available in the runtime environment. Otherwise, Java may substitute another installed font.

## Handle variable-length fields and GS1 separators

Some GS1 Application Identifiers contain variable-length values. If another element string follows, the previous field must be terminated by a GS1 field separator.

```java
String gs1CodeText = "(01)09501101530003"
        + "(10)LOT-ABC-999"
        + "(21)SN00004567";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.GS_1_CODE_128,
        gs1CodeText
);

generator.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
generator.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);
generator.getParameters().setResolution(300.0f);

generator.getParameters().getBarcode().getPadding().getLeft().setMillimeters(3.5f);
generator.getParameters().getBarcode().getPadding().getRight().setMillimeters(3.5f);

generator.save("gs1_128_varlen.png", BarCodeImageFormat.PNG);
```

AI `(10)` contains a variable-length lot number and is followed by AI `(21)`. The generator inserts the required GS1 field separator between these element strings. A final variable-length field does not require a trailing separator.

## Fit GS1-128 into a target image box

Use `ImageWidth`, `ImageHeight`, and `AutoSizeMode.NEAREST` when the barcode must fit a predefined bitmap area.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.GS_1_CODE_128,
        "(01)09501101530003(17)251231(10)BATCH-42"
);

generator.getParameters().setResolution(300.0f);
generator.getParameters().getImageWidth().setPixels(500);
generator.getParameters().getImageHeight().setPixels(200);
generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);

generator.save("gs1_128_box.png", BarCodeImageFormat.PNG);
```

`AutoSizeMode.NEAREST` calculates the effective X-dimension and bar height required to fit the symbol into the specified image box. Explicit `XDimension` and `BarHeight` values are ignored in this mode.

A fixed bitmap box does not guarantee compliance with physical print requirements. Validate the resulting module width, quiet zones, print size, and scanner readability for the intended application.

## Create a compact GS1-128 layout

The human-readable text can be hidden and vertical padding can be reduced to lower the overall image height. Horizontal quiet-zone space must still be preserved.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.GS_1_CODE_128,
        "(01)09501101530003(17)251231(10)BATCH-42"
);

generator.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
generator.getParameters().getBarcode().getBarHeight().setMillimeters(12.0f);
generator.getParameters().setResolution(300.0f);

// Disable human-readable text to reduce image height
generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setLocation(CodeLocation.NONE);

// Reduce vertical padding
generator.getParameters().getBarcode().getPadding().getTop().setMillimeters(1.0f);
generator.getParameters().getBarcode().getPadding().getBottom().setMillimeters(1.0f);

// Preserve horizontal quiet zones
generator.getParameters().getBarcode().getPadding().getLeft().setMillimeters(3.5f);
generator.getParameters().getBarcode().getPadding().getRight().setMillimeters(3.5f);

generator.save("gs1_128_minimal.png", BarCodeImageFormat.PNG);
```

Reducing human-readable text and vertical padding does not reduce the required horizontal quiet zones. A compact symbol must still be validated against the applicable GS1 application specification and tested with the intended printer and scanner.

## Recommendations

- Use `EncodeTypes.GS_1_CODE_128`, not regular `CODE_128`, for GS1-128 data.
- Supply Application Identifiers in parenthesized form.
- Use valid field lengths, formats, and check digits for every Application Identifier.
- Let the generator insert separators after non-final variable-length fields.
- Use `FontMode.MANUAL` when you need an explicitly configured human-readable text size.
- Do not combine explicit `XDimension` and `BarHeight` values with `AutoSizeMode.NEAREST`.
- Treat physical dimensions and quiet-zone sizes as application-specific values, not universal defaults.
- Test the final symbol with the actual label size, printer, scanner, and operating environment.
