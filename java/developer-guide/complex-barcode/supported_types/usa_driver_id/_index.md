---
title: "USA Driver ID Barcodes"
description: "Learn how to generate and read AAMVA USA Driver ID data stored in PDF417 barcodes."
type: docs
weight: 90
url: /java/developer-guide/complex-barcode/supported_types/usa_driver_id/
---

# USA Driver ID Barcodes

USA Driver ID data is represented as a structured AAMVA payload stored in a PDF417 carrier. The typed model separates header information, mandatory fields, and optional fields.

The complete source code for this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/complex/supported_types/usa_driver_id/USADriverIDBarcodes.java" target="_blank">View USADriverIDBarcodes.java</a>

## Configure the AAMVA header

```java
USADriveIdCodetext codetext =
        new USADriveIdCodetext();

codetext.setIssuerIdentificationNumber("636026");
codetext.setAAMVAVersionNumber("08");
codetext.setJurisdictionVersionNumber("00");
codetext.setNumberOfEntries(1);

codetext.setSubfileDesignator(
        List.of(
                new USADriveIdCodetext
                        .SubfileProperties("DL")
        )
);
```

## Configure mandatory fields

```java
USADriveIdCodetext.MandatoryFields fields =
        new USADriveIdCodetext.MandatoryFields();

fields.setVehicleClass("C");
fields.setExpirationDate(
        LocalDate.of(2030, 12, 31)
);
fields.setFamilyName("DOE");
fields.setFirstName("JOHN");
fields.setDateOfBirth(
        LocalDate.of(1990, 5, 20)
);
fields.setSex(USADriveIdSex.MALE);
fields.setEyeColor(
        USADriveIdEyeColor.BROWN
);
fields.setAddressState("CA");
fields.setCustomerIDNumber("D1234567");

codetext.setMandatoryElements(fields);
```

## Configure optional fields

```java
USADriveIdCodetext.OptionalFields optional =
        new USADriveIdCodetext.OptionalFields();

optional.setHairColor(
        USADriveIdHairColor.BROWN
);
optional.setOrganDonorIndicator("1");

codetext.setOptionalElements(optional);
```

## Generate the PDF417 carrier

```java
ComplexBarcodeGenerator generator =
        new ComplexBarcodeGenerator(codetext);

generator.save(
        "usa_driver_id.png",
        BarCodeImageFormat.PNG
);
```

Recognize the result with `DecodeType.PDF_417`.

## Decode Driver ID data

```java
USADriveIdCodetext decoded =
        ComplexCodetextReader.tryDecodeUSADriveId(
                results[0].getCodeText()
        );
```

Validate issuer, AAMVA version, identity, document, address, physical-description, and optional cardholder fields.

## Recommendations

- Populate every mandatory AAMVA field.
- Use the correct AAMVA and jurisdiction versions.
- Preserve required field formats.
- Recognize the carrier as PDF417.
- Validate mandatory and optional decoded fields.
