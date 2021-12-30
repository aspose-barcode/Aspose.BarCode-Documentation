---
title: Swiss QR Code
type: docs
description: "This article explains how to Generate and Read Swiss QR Codes using Aspose.BarCode for .NET"
keywords: "Generate Swiss QR Codes, How to Create Swiss Barcodes, Swiss QR Code, Aspose.BarCode, Generate Barcode C#"
weight: 10
url: /net/swiss-qr-code/
---

## Overview
The *Swiss QR Code* symbology has been developed in Switzerland to automate digital payments. At present, all payment receipts and bills in Switzerland are intended to have a *Swiss QR Code* barcode encrypting payment details. To distinguish from basic *QR Code*, *Swiss QR Code* labels have the Swiss cross sign in the center.  
  
Specifically, the *Swiss QR Code* standard is used to work with QR bills in electronic payments. A *Swiss QR Code* barcode contains all necessary payment information required to launch payments or to process a QR invoice. ***Aspose.BarCode for .NET*** includes [*SwissQRBill*](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/swissqrbill) and [*SwissQRCodetext*](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/swissqrcodetext) classes that provide various properties to work with *Swiss QR* codes.  
  
The rules for creating *Swiss QR Code* barcodes and corresponding payment documents are defined in a specific standard called "[Swiss Implementation Guidelines for the QR-bill](https://www.paymentstandards.ch/dam/downloads/ig-qr-bill-en.pdf)" that relies on ISO 20022 standard.

## How to Generate Swiss QR Code
To generate a *Swiss QR Code* barcode using  ***Aspose.BarCode for .NET***, it is necessary to create an instance of [*ComplexBarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexbarcodegenerator) and specify the information to be encoded into [*SwissQRCodetext*](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/swissqrcodetext).  

<p align="center"><img src="swissqrbill.png"></p>
  
The code sample given below demonstrates how to generate a *Swiss QR Code* barcode.
  
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

//encode it
ComplexBarcodeGenerator generator = new ComplexBarcodeGenerator(swissQRCode);
generator.Parameters.Barcode.XDimension.Pixels = 4;
generator.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.ECIEncoding;
generator.Parameters.Barcode.QR.QrECIEncoding = ECIEncodings.UTF8;
generator.Save($"{path}SwissQRBill.png");
{{< /highlight >}}

## How to Read Swiss QR Code
***Aspose.BarCode for .NET*** includes class [*ComplexCodetextReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexcodetextreader) that is used to decode barcode input text according to the specified complex barcode type, such as *Swiss QR Code*. To perform *Swiss QR Code* recognition, first, it is necessary to create an instance of class [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) and set it to the value *DecodeType.QR*; then, the obtained barcode contents need to be parsed in class [*ComplexCodetextReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexcodetextreader) by calling the [*TryDecodeSwissQR*](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexcodetextreader/methods/trydecodeswissqr) method that returns an instance of [SwissQRCodetext](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/swissqrcodetext) with the decoded barcode information. The code snippet below illustrates how to implement Swiss QR code recognition.
  
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
{{< /highlight >}}