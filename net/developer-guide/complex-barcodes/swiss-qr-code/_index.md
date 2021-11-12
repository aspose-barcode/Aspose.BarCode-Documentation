---
title: Swiss QR Code
type: docs
description: "This article explains how to Generate and Read Swiss QR Codes using Aspose.BarCode for .NET. The Swiss QR Code is used for the QR bill in the payments replacing the previous payment slips. The Swiss QR Code contains all the necessary payment information required to trigger payments or to process the QR invoice further."
keywords: "Generate Swiss QR Code, Swiss Code, Aspose.BarCode, Generate Barcode C#"
weight: 10
url: /net/swiss-qr-code/
---

## **Overview**
The *Swiss QR Code* symbology is used to work with QR bills in payments that replace previous payment slips. A Swiss QR Code label contains all necessary payment information required to launch payments or to process a QR invoice. ***Aspose.BarCode for .NET*** contains [*SwissQRBill*](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/swissqrbill) and [*SwissQRCodetext*](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/swissqrcodetext) classes that contain various properties to work with Swiss QR codes.

## **How to Generate Swiss QR Code**
To generate a barcode label using the *Swiss QR Code* symbology, it is necessary to create an instance of [*ComplexBarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexbarcodegenerator) and insertthe information to be encoded into [SwissQRCodetext](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/swissqrcodetext) property. The code sample given below demonstrates how to generate a Swiss QR code.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageComplexBarcodes-GenerateComplexBarcodes-GenerateComplexBarcodes.cs" >}}

## **How to Read Swiss QR Code**

<!--This article explains how to Read Swiss QR Code using Aspose.BarCode for .NET. The Swiss QR Code is used for the QR bill in the payments replacing the previous payment slips. The Swiss QR Code contains all the necessary payment information required to trigger payments or to process the QR invoice further.-->
***Aspose.BarCode for .NET*** includes [*ComplexCodetextReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexcodetextreader) class that decodes code text according to the specified complex barcode types, such as Swiss QR Code.

To realize this, it is necessary to create an instabce of [*ComplexCodetextReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexcodetextreader) and set *DecodeType* to "DecodeType.QR". The code snippet provided below illustrates how to read a Swiss QR code.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageComplexBarcodes-ReadComplexBarcodes-ReadComplexBarcodes.cs" >}}
