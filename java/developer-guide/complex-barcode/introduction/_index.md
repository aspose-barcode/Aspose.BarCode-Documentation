---
title: "Introduction to Complex Barcodes"
description: "Learn how complex barcodes use typed business data models, carrier symbologies, and structured decoding workflows in Aspose.BarCode for Java."
type: docs
weight: 10
url: /java/developer-guide/complex-barcode/introduction/
---

# Introduction to Complex Barcodes

Complex barcodes represent structured business data through dedicated Java classes instead of requiring applications to assemble the final encoded text manually.

Aspose.BarCode for Java separates the business model, the physical carrier symbology, and the decoding step. This approach reduces formatting errors and makes decoded fields available through typed Java objects.

The complete source code for this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/complex/introduction/ComplexBarcodeIntroduction.java" target="_blank">View ComplexBarcodeIntroduction.java</a>

## Regular and complex barcode generation

A regular `BarcodeGenerator` receives the final payload directly:

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        constructedCodetext
);
```

A `ComplexBarcodeGenerator` receives an implementation of `IComplexCodetext`:

```java
SwissQRCodetext codetext = new SwissQRCodetext();

ComplexBarcodeGenerator generator =
        new ComplexBarcodeGenerator(codetext);
```

The complex codetext object constructs the standard-specific payload and selects the appropriate carrier symbology.

## Create typed business data

The following example initializes a Swiss QR payment model:

```java
SwissQRCodetext codetext = new SwissQRCodetext();

codetext.getBill().setVersion(QrBillStandardVersion.V2_0);
codetext.getBill().setAccount("CH4431999123000889012");
codetext.getBill().setAmount(100.25);
codetext.getBill().setCurrency("CHF");
```

The model exposes payment fields such as account, amount, currency, creditor, debtor, reference, and message.

## Supported complex barcode models

Aspose.BarCode for Java provides typed classes for Swiss QR, HIBC LIC, HIBC PAS, Royal Mail Mailmark, MaxiCode, and USA Driver ID.

The supported classes include:

- `SwissQRCodetext`;
- `HIBCLICCombinedCodetext`;
- `HIBCPASCodetext`;
- `MailmarkCodetext`;
- `Mailmark2DCodetext`;
- `MaxiCodeCodetextMode2`;
- `MaxiCodeCodetextMode3`;
- `USADriveIdCodetext`.

## Understand the carrier symbology

A complex barcode still uses a regular physical barcode type. For example:

- Swiss QR uses QR Code;
- Mailmark 2D uses Data Matrix;
- USA Driver ID uses PDF417;
- MaxiCode business data uses MaxiCode.

The carrier is recognized first. Its text is then passed to a complex codetext decoder.

## Complete processing workflow

```java
ComplexBarcodeGenerator generator =
        new ComplexBarcodeGenerator(sourceCodetext);

generator.save(outputPath, BarCodeImageFormat.PNG);

BarCodeReader reader =
        new BarCodeReader(outputPath, DecodeType.QR);

BarCodeResult[] results = reader.readBarCodes();

SwissQRCodetext decodedCodetext =
        ComplexCodetextReader.tryDecodeSwissQR(
                results[0].getCodeText()
        );
```

The workflow consists of creating a typed model, generating the carrier image, recognizing the carrier, and decoding its standardized text into a typed object.

## Recommendations

- Populate all required business fields before generation.
- Recognize the underlying carrier before complex decoding.
- Use the decoder that matches the expected complex standard.
- Validate decoded fields instead of checking only the raw text.
- Apply a valid license before generation and recognition tests.
