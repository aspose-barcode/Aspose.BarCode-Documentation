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

The mandatory AAMVA data includes identity, document, address, physical-description, and truncation fields. The following example matches the complete set used in the related TestNG class.

```java
USADriveIdCodetext.MandatoryFields fields =
        new USADriveIdCodetext.MandatoryFields();

fields.setVehicleClass("C");
fields.setRestrictionCodes("NONE");
fields.setEndorsementCodes("NONE");

fields.setExpirationDate(LocalDate.of(2030, 12, 31));

fields.setFamilyName("DOE");
fields.setFirstName("JOHN");
fields.setMiddleName("Q");

fields.setIssueDate(LocalDate.of(2026, 1, 1));

fields.setDateOfBirth(LocalDate.of(1990, 5, 20));

fields.setSex(USADriveIdSex.MALE);
fields.setEyeColor(USADriveIdEyeColor.BROWN);
fields.setHeight("070 in");

fields.setAddressStreet1("123 MAIN STREET");
fields.setAddressCity("ANYTOWN");
fields.setAddressState("CA");
fields.setAddressPostalCode("90210");

fields.setCustomerIDNumber("D1234567");
fields.setDocumentDiscriminator("DOC123456789");

fields.setCountryIdentification(USADriveIdCountry.US);

fields.setFamilyNameTruncation("N");
fields.setFirstNameTruncation("N");
fields.setMiddleNameTruncation("N");

codetext.setMandatoryElements(fields);
```

These values are serialized into the AAMVA data structure before the PDF417 carrier is generated.

## Configure optional fields

```java
USADriveIdCodetext.OptionalFields optional =
        new USADriveIdCodetext.OptionalFields();

optional.setHairColor(USADriveIdHairColor.BROWN);
optional.setOrganDonorIndicator("1");

codetext.setOptionalElements(optional);
```

Optional fields extend the cardholder data without replacing the mandatory AAMVA elements.

## Generate the PDF417 carrier

```java
ComplexBarcodeGenerator generator = new ComplexBarcodeGenerator(codetext);

generator.save("usa_driver_id.png",BarCodeImageFormat.PNG);
```

Recognize the generated image with `DecodeType.PDF_417`.

```java
BarCodeReader reader = new BarCodeReader("usa_driver_id.png",DecodeType.PDF_417);

BarCodeResult[] results = reader.readBarCodes();
```

## Decode Driver ID data

```java
USADriveIdCodetext decoded = ComplexCodetextReader.tryDecodeUSADriveId(results[0].getCodeText());
```

After decoding, the mandatory and optional objects can be accessed directly.

```java
String familyName = decoded.getMandatoryElements().getFamilyName();

String documentNumber = decoded.getMandatoryElements().getCustomerIDNumber();

USADriveIdHairColor hairColor = decoded.getOptionalElements().getHairColor();
```

Validate issuer, AAMVA version, identity, document, address, physical-description, truncation, and optional cardholder fields.

## Recommendations

- Populate every mandatory AAMVA field required by the selected format.
- Use the correct AAMVA and jurisdiction versions.
- Preserve required date, height, address, and document formats.
- Set truncation indicators explicitly when required by the data format.
- Recognize the carrier as PDF417.
- Validate both mandatory and optional decoded fields.
