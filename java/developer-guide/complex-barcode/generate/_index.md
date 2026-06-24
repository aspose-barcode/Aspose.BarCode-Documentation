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

```java
SecondaryAndAdditionalData secondaryData =
        new SecondaryAndAdditionalData();

secondaryData.setExpiryDateFormat(
        HIBCLICDateFormat.YYYYMMDD
);

secondaryData.setExpiryDate(
        LocalDateTime.of(2027, 12, 31, 0, 0)
);

secondaryData.setQuantity(30);
secondaryData.setLotNumber("LOT123");
secondaryData.setSerialNumber("SERIAL123");
secondaryData.setDateOfManufacture(
        LocalDateTime.of(2026, 1, 15, 0, 0)
);

codetext.setSecondaryAndAdditionalData(
        secondaryData
);
```

The model constructs the standard-compliant HIBC LIC payload automatically.

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

Padding and borders can be configured in the same way as for regular barcode generation.

```java
generator.getParameters()
        .getBarcode()
        .getPadding()
        .getLeft()
        .setPixels(12);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getRight()
        .setPixels(12);

generator.getParameters()
        .getBorder()
        .setVisible(true);

generator.getParameters()
        .getBorder()
        .setColor(Color.GRAY);

generator.getParameters()
        .getBorder()
        .getWidth()
        .setPixels(2);
```

These settings affect only the generated image and do not modify the structured business data.

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

Use `BarCodeReader` to recognize the generated carrier barcode and compare the recognized payload with `getConstructedCodetext()`.

```java
BarCodeReader reader = new BarCodeReader(
        "generated_swiss_qr.png",
        DecodeType.QR
);

BarCodeResult[] results =
        reader.readBarCodes();

if (results.length != 1) {
    throw new IllegalStateException(
            "Expected exactly one QR barcode."
    );
}

if (!results[0].getCodeType().equals(
        DecodeType.QR
)) {
    throw new IllegalStateException(
            "Unexpected barcode type: "
                    + results[0].getCodeType()
    );
}

if (!results[0].getCodeText().equals(
        codetext.getConstructedCodetext()
)) {
    throw new IllegalStateException(
            "Recognized payload does not match "
                    + "the constructed codetext."
    );
}
```

This example uses only the public Aspose.BarCode API.

For critical workflows, decode the recognized text back into the typed model and compare business fields.

```java
SwissQRCodetext decodedCodetext =
        ComplexCodetextReader.tryDecodeSwissQR(
                results[0].getCodeText()
        );

if (decodedCodetext == null) {
    throw new IllegalStateException(
            "The recognized payload could not be "
                    + "decoded as Swiss QR."
    );
}

if (!decodedCodetext.getBill()
        .getAccount()
        .equals(codetext.getBill().getAccount())) {
    throw new IllegalStateException(
            "Decoded account does not match "
                    + "the source data."
    );
}
```

## Recommendations

- Build the typed model before creating the generator.
- Validate required fields before saving.
- Keep appearance configuration separate from business data.
- Use streams when intermediate files are unnecessary.
- Recognize the generated carrier with `BarCodeReader`.
- Decode the recognized text with the matching complex codetext reader.
- Compare important business fields after decoding.
