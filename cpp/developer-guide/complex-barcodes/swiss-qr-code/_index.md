---
title: Generate and Read Swiss QR Code in C++
linktitle: Swiss QR Code
type: docs
description: "This article explains how to Generate and Read Swiss QR Codes using Aspose.BarCode for C++"
keywords: "Generate Swiss QR Codes, How to Create Swiss Barcodes, Swiss QR Code, Aspose.BarCode, Generate Barcode C++"
weight: 10
url: /cpp/swiss-qr-code/
---

## **Overview**
The *Swiss QR Code* symbology has been developed in Switzerland to automate digital payments. At present, all payment receipts and bills in Switzerland are intended to have a *Swiss QR Code* barcode that encrypts payment details. To distinguish from basic *QR Code*, *Swiss QR Code* labels have the Swiss cross sign in the center.  
  
Specifically, the *Swiss QR Code* standard is used to work with QR bills in electronic payments. A *Swiss QR Code* barcode contains all necessary payment information required to launch payments or to process a QR invoice. ***Aspose.BarCode for C++*** includes [*SwissQRBill*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/swissqrbill) and [*SwissQRCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/swissqrcodetext) classes that provide various properties to work with *Swiss QR* codes.  
  
The general rules for creating *Swiss QR Code* barcodes and corresponding payment documents are defined in a specific standard called ["Swiss Implementation Guidelines for the QR-bill"](https://www.paymentstandards.ch/dam/downloads/ig-qr-bill-en.pdf) that relies on the ISO 20022 standard.

## **Generate Swiss QR Code**
To generate a *Swiss QR Code* barcode using  ***Aspose.BarCode for C++***, it is necessary to create an instance of [*ComplexBarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexbarcodegenerator) and specify the information to be encoded into [*SwissQRCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/swissqrcodetext).  

<p align="center"><img src="swissqrbill.png"></p>
  

## **Read Swiss QR Code**
***Aspose.BarCode for C++*** includes class [*ComplexCodetextReader*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexcodetextreader) that is used to decode barcode input text according to the specified complex barcode type, in this case, *Swiss QR Code*. To read *Swiss QR Code* barcodes, first, it is necessary to create an instance of class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) and set it to the value *DecodeType.QR*; then, the obtained barcode contents need to be parsed in class [*ComplexCodetextReader*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexcodetextreader) by calling the [*TryDecodeSwissQR*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexcodetextreader/methods/trydecodeswissqr) method that returns an instance of [*SwissQRCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/swissqrcodetext) with the decoded barcode information. 