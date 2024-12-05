---
title: Generate and Read Swiss QR Code in JavaScript
linktitle: Swiss QR Code
type: docs
description: "This article explains how to Generate and Read Swiss QR Codes using Aspose.BarCode for JavaScript via C++"
keywords: "Generate Swiss QR Codes, How to Create Swiss Barcodes, Swiss QR Code, Aspose.BarCode, Generate Barcode JavaScript"
feedback: BARCODECOM
weight: 10
url: /javascript-cpp/swiss-qr-code/
---
## Overview
The *Swiss QR Code* symbology was developed in Switzerland to facilitate digital payments. Currently, all payment receipts and bills in Switzerland feature a *Swiss QR Code* that encodes payment details. Unlike standard *QR Code* barcodes, *Swiss QR Code* labels include the Swiss cross symbol at the center.

The *Swiss QR Code* standard is specifically designed for QR bills in electronic payments. A *Swiss QR Code* barcode contains all the payment information needed to process a payment or handle a QR invoice. ***Aspose.BarCode for JavaScript via C++*** offers [*SwissQRBill*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/swissqrbill) and [*SwissQRCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/swissqrcodetext) classes, which provide various properties for working with *Swiss QR Codes*.

The creation rules for *Swiss QR Code* barcodes and payment documents are detailed in the "Swiss Implementation Guidelines for the QR-bill," which follows the ISO 20022 standard and can be found [here](https://www.paymentstandards.ch/dam/downloads/ig-qr-bill-en.pdf).

## Generate Swiss QR Code
To generate a *Swiss QR Code* using ***Aspose.BarCode for JavaScript via C++***, create an instance of [*SwissQRCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/swissqrcodetext).

<p align="center"><img src="swissqrbill.png"></p>

The following code sample shows how to generate a *Swiss QR Code* barcode.

  
```javascript
// Create Swiss QR Bill
var swissQRCode = new BarCodeInstance.SwissQRCodetext();
swissQRCode.Bill.Version = BarCodeInstance.QrBillStandardVersion.V2_0;
swissQRCode.Bill.Account = "CH4431999123000889012";
swissQRCode.Bill.Amount = "1000.25";
swissQRCode.Bill.Currency = "CHF";
swissQRCode.Bill.Reference = "210000000003139471430009017";

swissQRCode.Bill.Creditor.Name = "Muster & Söhne";
swissQRCode.Bill.Creditor.Street = "Musterstrasse";
swissQRCode.Bill.Creditor.HouseNo = "12b";
swissQRCode.Bill.Creditor.PostalCode = "8200";
swissQRCode.Bill.Creditor.Town = "Zürich";
swissQRCode.Bill.Creditor.CountryCode = "CH";

swissQRCode.Bill.Debtor.Name = "Muster AG";
swissQRCode.Bill.Debtor.Street = "Musterstrasse";
swissQRCode.Bill.Debtor.HouseNo = "1";
swissQRCode.Bill.Debtor.PostalCode = "3030";
swissQRCode.Bill.Debtor.Town = "Bern";
swissQRCode.Bill.Debtor.CountryCode = "CH";

// Encode Swiss QR Bill
var generator = swissQRCode.GetGenerator();
generator.Parameters.Barcode.XDimension.Pixels = 4;
generator.Parameters.Barcode.QR.QrEncodeMode = BarCodeInstance.QREncodeMode.ECIEncoding;
generator.Parameters.Barcode.QR.QrECIEncoding = BarCodeInstance.ECIEncodings.UTF8;
document.getElementById("img").src = generator.GenerateBarCodeImage(); // Display QR code image

swissQRCode.delete();
generator.delete();

```

## Read Swiss QR Code
***Aspose.BarCode for JavaScript via C++*** provides the [*ComplexCodetextReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/complexcodetextreader) class for decoding complex barcode input, such as *Swiss QR Code*. To read a *Swiss QR Code* barcode, follow these steps:

1. Create an instance of [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) and set its value to *DecodeType.QR*.
2. Use the [*ComplexCodetextReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/complexcodetextreader) class to parse the barcode contents.
3. Call the [*TryDecodeSwissQR*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/complexcodetextreader/methods/trydecodeswissqr) method, which returns an instance of [*SwissQRCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/swissqrcodetext) containing the decoded information.

The code sample below demonstrates how to implement *Swiss QR Code* recognition.

```javascript

// Read Swiss QR Bill from the image
var reader = new BarCodeInstance.BarCodeReader(document.getElementById("img").src, "QR");
reader.ReadBarCodes();

if(reader.FoundCount == 1)
{
    var result = reader.FoundBarCodes(0);

    var swissResult = BarCodeInstance.ComplexCodetextReader.TryDecodeSwissQR(result.CodeText);
    if (swissResult.IsEmpty) return;
    
    console.log(`Version: ${swissResult.Bill.Version}`);
    console.log(`Account: ${swissResult.Bill.Account}`);
    console.log(`Amount: ${swissResult.Bill.Amount}`);
    console.log(`Currency: ${swissResult.Bill.Currency}`);
    console.log(`Reference: ${swissResult.Bill.Reference}`);
    console.log(`Creditor: ${swissResult.Bill.Creditor.Name}`);
    console.log(`Debtor: ${swissResult.Bill.Debtor.Name}`);
        
}
reader.delete();

```