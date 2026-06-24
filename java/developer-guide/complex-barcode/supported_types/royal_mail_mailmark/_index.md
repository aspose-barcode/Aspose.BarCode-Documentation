---
title: "Royal Mail Mailmark Barcodes"
description: "Learn how to generate and read Royal Mail Mailmark 1D and 2D barcodes."
type: docs
weight: 70
url: /java/developer-guide/complex-barcode/supported_types/royal_mail_mailmark/
---

# Royal Mail Mailmark Barcodes

Aspose.BarCode for Java supports typed Royal Mail Mailmark 1D and Mailmark 2D payloads with postal routing and item-identification fields.

The complete source code for this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/complex/supported_types/royal_mail_mailmark/RoyalMailMailmarkBarcodes.java" target="_blank">View RoyalMailMailmarkBarcodes.java</a>

## Generate Mailmark 1D

```java
MailmarkCodetext codetext =
        new MailmarkCodetext();

codetext.setFormat(1);
codetext.setVersionID(1);
codetext.setClass("1");
codetext.setSupplychainID(99);
codetext.setItemID(12345678);
codetext.setDestinationPostCodePlusDPS(
        "XY11     "
);
```

Generate the image with `ComplexBarcodeGenerator` and recognize it with `DecodeType.MAILMARK`.

## Decode Mailmark 1D

```java
MailmarkCodetext decoded =
        ComplexCodetextReader.tryDecodeMailmark(
                results[0].getCodeText()
        );
```

Verify format, version, class, supply-chain ID, item ID, and destination postcode plus DPS.

## Generate Mailmark 2D

```java
Mailmark2DCodetext codetext =
        new Mailmark2DCodetext();

codetext.setUPUCountryID("JGB ");
codetext.setInformationTypeID("0");
codetext.setVersionID("1");
codetext.setclass("1");
codetext.setSupplyChainID(1234567);
codetext.setItemID(12345678);
codetext.setDestinationPostCodeAndDPS("XY11     ");
codetext.setRTSFlag("0");
codetext.setReturnToSenderPostCode("B1 1AA");
codetext.setCustomerContent("ABC123");
codetext.setDataMatrixType(
        Mailmark2DType.TYPE_7
);
```

## Decode Mailmark 2D

Mailmark 2D uses a Data Matrix carrier:

```java
Mailmark2DCodetext decoded =
        ComplexCodetextReader.tryDecodeMailmark2D(
                results[0].getCodeText()
        );
```

Validate routing, return-to-sender, supply-chain, item, and customer-content fields.

## Recommendations

- Preserve required field lengths and padding.
- Use the correct Mailmark 2D type.
- Validate item and supply-chain identifiers.
- Recognize the correct carrier symbology.
- Compare decoded postal fields in regression tests.
