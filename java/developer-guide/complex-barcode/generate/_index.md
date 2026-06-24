---
title: "Generate Complex Barcodes"
description: "Learn how to create structured complex barcode data, generate images, configure appearance, and save output to files or streams."
type: docs
weight: 20
url: /java/developer-guide/complex-barcode/generate/
---

# Generate Complex Barcodes

Complex barcode generation starts with a typed business object. The model validates and constructs the standardized payload before the barcode image is created.

The complete source code for this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/complex/generate/GenerateComplexBarcodes.java" target="_blank">View GenerateComplexBarcodes.java</a>

## Create structured HIBC LIC data

HIBC LIC separates primary product identification from secondary production data:

```java
HIBCLICCombinedCodetext codetext =
        new HIBCLICCombinedCodetext();

codetext.setBarcodeType(EncodeTypes.HIBCQRLIC);

PrimaryData primaryData = new PrimaryData();
primaryData.setLabelerIdentificationCode("A999");
primaryData.setProductOrCatalogNumber("12345");
primaryData.setUnitOfMeasureID(1);
codetext.setPrimaryData(primaryData);
```

Add expiry date, quantity, lot number, serial number, and manufacture date through `SecondaryAndAdditionalData`.

## Generate a complex barcode image

```java
SwissQRCodetext codetext = createSwissQRCodetext();

ComplexBarcodeGenerator generator =
        new ComplexBarcodeGenerator(codetext);

generator.save(
        "generated_swiss_qr.png",
        BarCodeImageFormat.PNG
);
```

The generator obtains the final payload and carrier type from the complex codetext object.

## Configure appearance

Complex generators expose common generation parameters:

```java
generator.getParameters()
        .setBackColor(new Color(245, 248, 252));

generator.getParameters()
        .getBarcode()
        .setBarColor(new Color(20, 45, 90));

generator.getParameters()
        .getBarcode()
        .getXDimension()
        .setPixels(3);
```

Padding and borders can be configured in the same way as for regular barcode generation. These settings do not modify the business data.

## Save to a stream

```java
ByteArrayOutputStream outputStream =
        new ByteArrayOutputStream();

generator.save(
        outputStream,
        BarCodeImageFormat.PNG
);

byte[] imageBytes = outputStream.toByteArray();
```

Stream output is useful for web responses, cloud storage, document composition, and database workflows.

## Verify generated output

Recognize the generated image and compare its payload with `getConstructedCodetext()`:

```java
assertImageHasBarcodes(
        outputPath,
        1,
        List.of(
                expected(
                        DecodeType.QR,
                        codetext.getConstructedCodetext()
                )
        )
);
```

For critical workflows, decode the recognized text back into the typed model and compare business fields.

## Recommendations

- Build the typed model before creating the generator.
- Validate required fields before saving.
- Keep appearance configuration separate from business data.
- Use streams when intermediate files are unnecessary.
- Verify generated output through recognition and structured decoding.
