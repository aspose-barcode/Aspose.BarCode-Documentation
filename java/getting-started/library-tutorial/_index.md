---
title: Code Examples
type: docs
weight: 80
feedback: BARCODECOM
url: /java/barcode-generation-and-recognition-tutorial/
---


## **How to Work with Non-ASCII Symbols**
This example demonstrates how to generate and read a PDF417 barcode containing non-ASCII text using Aspose.BarCode for Java.


{{<highlight java>}}
    ByteArrayOutputStream outputStream = new ByteArrayOutputStream();
    BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.PDF_417);
    gen.setCodeText("sýkora je malý pták", StandardCharsets.UTF_8);
    gen.save(outputStream, BarCodeImageFormat.PNG);
    BarCodeReader reader = new BarCodeReader(new ByteArrayInputStream(outputStream.toByteArray()), DecodeType.PDF_417);
    BarCodeResult[] results = reader.readBarCodes();
    System.out.printf("Code Type: %s%n", results[0].getCodeTypeName());
    System.out.printf("Code Text: %s%n", results[0].getCodeText(StandardCharsets.UTF_8));

{{</highlight>}}
