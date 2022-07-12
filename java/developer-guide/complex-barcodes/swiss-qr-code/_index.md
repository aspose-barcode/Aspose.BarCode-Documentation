---
title: Swiss QR Code
type: docs
description: "This article explains how to Generate and Read Swiss QR Codes using Aspose.BarCode for Java"
keywords: "Generate Swiss QR Codes, How to Create Swiss Barcodes, Swiss QR Code, Aspose.BarCode, Generate Barcodes in Java"
weight: 10
url: /java/swiss-qr-code/
aliases:
- /barcode/java/read-swiss-qr-code/
- /barcode/java/generate-swiss-qr-code/
---

## **Overview**
The *Swiss QR Code* barcode starndard has been introduced by Switzerland to facilitate the automation of electronic payment operations. This approach implies adding *Swiss QR Code* barcodes encrypting payment information to all bills and receipts issued in Switzerland. Unlike common *QR Codes*, *Swiss QR Code* barcodes are designed with the Swiss cross sign.  
  
*Swiss QR Code* barcodes serve to process QR bills in digital payment operations. They store key payment data needed to execute payment procedures or generate QR invoices. To deal with the *Swiss QR Code* symbology, ***Aspose.BarCode for Java*** provides special classes [*SwissQRBill*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/SwissQRBill) and [*SwissQRCodetext*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/SwissQRCodetext).  
  
General principles of generating *Swiss QR Code* barcodes and processing QR payment documents are specified in a standard called ["Swiss Implementation Guidelines for the QR-bill"](https://www.paymentstandards.ch/dam/downloads/ig-qr-bill-en.pdf) that is based on ISO 20022.

## **Generation of Swiss QR Codes**
To create *Swiss QR Code* barcodes through ***Aspose.BarCode for Java***, first, it is needed to create an instance of class [*ComplexBarcodeGenerator*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/ComplexBarcodeGenerator) and enter data using the *SwissQRCodetext()* method of class [*SwissQRCodetext*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/SwissQRCodetext).  

<p align="center"><img src="swissqrbill.png"></p>
  
<!--The following code snippet explains how to create *Swiss QR Code* barcode images.
  
{{< highlight csharp>}}
//create Swiss QR Bill
SwissQRCodetext swissQRCode = new SwissQRCodetext();
swissQRCode.Bill.Version = SwissQRBill.QrBillStandardVersion.V2_0;
swissQRCode.Bill.Account = "CH4431999123000889012";
swissQRCode.Bill.Amount = 1000.25m;
swissQRCode.Bill.Currency = "CHF";
swissQRCode.Bill.Reference = "210000000003139471430009017";
swissQRCode.Bill.Creditor = new Address
{
    Name = "Muster & Söhne",
    Street = "Musterstrasse",
    HouseNo = "12b",
    PostalCode = "8200",
    Town = "Zürich",
    CountryCode = "CH"
};

swissQRCode.Bill.Debtor = new Address
{
    Name = "Muster AG",
    Street = "Musterstrasse",
    HouseNo = "1",
    PostalCode = "3030",
    Town = "Bern",
    CountryCode = "CH"
};

//encode Swiss QR Bill
ComplexBarcodeGenerator generator = new ComplexBarcodeGenerator(swissQRCode);
generator.Parameters.Barcode.XDimension.Pixels = 4;
generator.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.ECIEncoding;
generator.Parameters.Barcode.QR.QrECIEncoding = ECIEncodings.UTF8;
generator.Save($"{path}SwissQRBill.png");
{{< /highlight >}}-->

## **Reading Swiss QR Code Barcodes**
To read complex barcodes, ***Aspose.BarCode for Java*** provides class [*ComplexCodetextReader*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/ComplexCodetextReader) that can be used to recognize input data for different complex barcode symbologies, including *Swiss QR Code*. To perform *Swiss QR Code* recognition, developers need to start with creating an instance of class [*BarCodeReader*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) and setting it to *DecodeType.QR*. Thereafter, barcode data requires parsing through the *TryDecodeSwissQR(java.lang.String encodedCodetext)* method of class [*ComplexCodetextReader*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/ComplexCodetextReader) that generates an instance of [*SwissQRCodetext*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/SwissQRCodetext) containing barcode text. 
<!--The following code sample shows how to perform *Swiss QR Code* barcode reading.
  
{{< highlight csharp>}}
Console.OutputEncoding = Encoding.Unicode;
//recognize Swiss QR Code
BarCodeReader reader = new BarCodeReader($"{path}SwissQRBill.png", DecodeType.QR);
foreach (BarCodeResult result in reader.ReadBarCodes())
{
    SwissQRCodetext swissResult = ComplexCodetextReader.TryDecodeSwissQR(result.CodeText);
    if (null == swissResult) continue;
    Console.WriteLine($"Version:{swissResult.Bill.Version}");
    Console.WriteLine($"Account:{swissResult.Bill.Account}");
    Console.WriteLine($"Amount:{swissResult.Bill.Amount}");
    Console.WriteLine($"Currency:{swissResult.Bill.Currency}");
    Console.WriteLine($"Reference:{swissResult.Bill.Reference}");
    Console.WriteLine($"Creditor:{swissResult.Bill.Creditor.Name}");
    Console.WriteLine($"Debtor:{swissResult.Bill.Debtor.Name}");
}
{{< /highlight >}}-->