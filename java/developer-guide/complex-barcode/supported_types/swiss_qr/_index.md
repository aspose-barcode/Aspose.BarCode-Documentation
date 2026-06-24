---
title: "Swiss QR Barcodes"
description: "Learn how to generate Swiss QR Bills and decode payment data with Aspose.BarCode for Java."
type: docs
weight: 50
url: /java/developer-guide/complex-barcode/supported_types/swiss_qr/
---

# Swiss QR Barcodes

Swiss QR stores structured payment information in a QR Code carrier. The typed model includes account, amount, currency, creditor, debtor, payment reference, and additional messages.

The complete source code for this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/complex/supported_types/swiss_qr/SwissQRBarcodes.java" target="_blank">View SwissQRBarcodes.java</a>

## Create the payment model

```java
SwissQRCodetext codetext =
        new SwissQRCodetext();

codetext.getBill()
        .setVersion(QrBillStandardVersion.V2_0);

codetext.getBill()
        .setAccount("CH4431999123000889012");

codetext.getBill()
        .setAmount(100.25);

codetext.getBill()
        .setCurrency("CHF");
```

## Configure addresses

```java
Address creditor = new Address();
creditor.setName("Robert Schneider AG");
creditor.setStreet("Rue du Lac");
creditor.setHouseNo("1268");
creditor.setPostalCode("2501");
creditor.setTown("Biel");
creditor.setCountryCode("CH");

codetext.getBill().setCreditor(creditor);
```

Configure the debtor with another `Address` object.

## Add reference and messages

```java
codetext.getBill().setReference(
        "210000000003139471430009017"
);

codetext.getBill().setUnstructuredMessage(
        "Invoice 2026-001"
);

codetext.getBill().setBillInformation(
        "//S1/10/2026001"
);
```

## Generate the QR image

```java
ComplexBarcodeGenerator generator =
        new ComplexBarcodeGenerator(codetext);

generator.save(
        "swiss_qr_bill.png",
        BarCodeImageFormat.PNG
);
```

## Read and decode payment data

```java
BarCodeReader reader =
        new BarCodeReader(outputPath, DecodeType.QR);

BarCodeResult[] results = reader.readBarCodes();

SwissQRCodetext decoded =
        ComplexCodetextReader.tryDecodeSwissQR(
                results[0].getCodeText()
        );
```

Validate account, amount, currency, reference, creditor, and debtor values.

## Recommendations

- Use a valid Swiss QR IBAN.
- Populate required creditor fields.
- Use supported currency values.
- Validate reference format before generation.
- Decode generated symbols in automated tests.
- Compare all important payment fields after decoding.
