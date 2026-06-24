---
title: "HIBC Barcodes"
description: "Learn how to generate and read HIBC LIC and HIBC PAS barcodes with structured healthcare data."
type: docs
weight: 60
url: /java/developer-guide/complex-barcode/supported_types/hibc/
---

# HIBC Barcodes

Aspose.BarCode for Java supports structured HIBC LIC and HIBC PAS models. LIC combines product identification with secondary production data, while PAS stores typed healthcare process records.

The complete source code for this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/complex/supported_types/hibc/HIBCBarcodes.java" target="_blank">View HIBCBarcodes.java</a>

## Configure HIBC LIC primary data

```java
PrimaryData primaryData = new PrimaryData();

primaryData.setLabelerIdentificationCode("A999");
primaryData.setProductOrCatalogNumber("12345");
primaryData.setUnitOfMeasureID(1);
```

## Configure HIBC LIC secondary data

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
```

## Generate and decode HIBC LIC

```java
HIBCLICCombinedCodetext codetext =
        new HIBCLICCombinedCodetext();

codetext.setBarcodeType(EncodeTypes.HIBCQRLIC);
codetext.setPrimaryData(primaryData);
codetext.setSecondaryAndAdditionalData(secondaryData);

ComplexBarcodeGenerator generator =
        new ComplexBarcodeGenerator(codetext);
```

Decode the recognized text with `ComplexCodetextReader.tryDecodeHIBCLIC` and verify the returned subtype before casting.

## Create HIBC PAS records

```java
HIBCPASCodetext codetext =
        new HIBCPASCodetext();

codetext.setDataLocation(
        HIBCPASDataLocation.PATIENT
);

codetext.addRecord(
        HIBCPASDataType.LABELER_IDENTIFICATION_CODE,
        "A123"
);

codetext.addRecord(
        HIBCPASDataType.MANUFACTURER_SERIAL_NUMBER,
        "SERIAL123"
);

codetext.setBarcodeType(
        EncodeTypes.HIBC_DATA_MATRIX_PAS
);
```

## Decode HIBC PAS

```java
HIBCPASCodetext decoded =
        ComplexCodetextReader.tryDecodeHIBCPAS(
                results[0].getCodeText()
        );
```

Validate the data location and record collection after decoding.

## Recommendations

- Select the correct HIBC carrier type.
- Keep primary and secondary LIC data separate.
- Use the matching expiry-date format.
- Use typed PAS identifiers for every record.
- Validate decoded records and business fields.
