---
title: Generate and Read Mailmark 4-State Barcodes in JavaScript
linktitle: Mailmark 4-State
type: docs
description: "This article explains how to Generate and Read Royal Mail Mailmark 4-State Barcodes using Aspose.BarCode for JavaScript via C++"
keywords: "Generate Mailmark Barcode, Royal Mail Mailmark Barcodes, Royal Mail Barcode, Aspose.BarCode, Generate Barcode JavaScript"
weight: 30
feedback: BARCODECOM
url: /javascript-cpp/mailmark-4state-barcodes/
---
## Overview
The *Mailmark 4-state* symbology was introduced by Royal Mail in the UK for encoding postal and shipping information. It is similar to the *RM4SCC* standard but uses a fixed data format without extra space for customer-specific data. The symbology supports numerical digits, uppercase English letters, and spaces. Additionally, *Mailmark 4-state* barcodes include a checksum and employ Reed-Solomon error correction.

### Mailmark 4-state Barcode Types
- **Type L**: Encodes 26 characters, designed for machine-readable Low Sort and Unsorted Retail and Access 70 services.
- **Type C**: Encodes 22 characters, used for consolidated machine-readable Low Sort and Unsorted Retail and Access 70 services.

***Aspose.BarCode for JavaScript via C++*** provides the [*MailmarkCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/mailmarkcodetext) class to work with *Mailmark 4-state* barcodes.

## Generate Mailmark 4-State Barcode
To create a *Mailmark 4-state* barcode instantiate the [*MailmarkCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/mailmarkcodetext) class and input the data to be encoded.

<p align="center"><img src="mailmark4state.png"></p>

Below is an example demonstrating how to generate *Mailmark 4-state* barcodes.

  
```javascript
//create Mailmark 4-State Barcode
var mailmarkCode = new BarCodeInstance.MailmarkCodetext();
mailmarkCode.Format = 4;
mailmarkCode.VersionID = 1;
mailmarkCode.Class = "0";
mailmarkCode.SupplychainID = 384224;
mailmarkCode.ItemID = 16563762;
mailmarkCode.DestinationPostCodePlusDPS = "EF61AH8T ";

// Encode Mailmark 4-State Barcode
var generator = mailmarkCode.GetGenerator();
generator.Parameters.Barcode.XDimension.Pixels = 4;
document.getElementById("img").src = generator.GenerateBarCodeImage(); // Display barcode image

mailmarkCode.delete();
generator.delete();

```


## **Read Mailmark 4-State Barcode**
To read and parse Royal Mail *Mailmark 4-state* barcodes in ***Aspose.BarCode for JavaScript via C++***, it is necessary to create an instance of class [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) and set it to the value *DecodeType.Mailmark*. After that, the fetched data must be parsed further using class [*ComplexCodetextReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/complexcodetextreader) by calling the [*TryDecodeMailmark*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/complexcodetextreader/methods/trydecodemailmark) method that returns an instance of [*MailmarkCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/mailmarkcodetext) with the decoded barcode contents.  
  
The following code snippet is given to demonstrate how to read *Mailmark 4-state* barcodes.
  
```javascript
//create Mailmark 4-State Barcode
var mailmarkCode = new BarCodeInstance.MailmarkCodetext();
mailmarkCode.Format = 4;
mailmarkCode.VersionID = 1;
mailmarkCode.Class = "0";
mailmarkCode.SupplychainID = 384224;
mailmarkCode.ItemID = 16563762;
mailmarkCode.DestinationPostCodePlusDPS = "EF61AH8T ";

// Encode Mailmark 4-State Barcode
var generator = mailmarkCode.GetGenerator();
generator.Parameters.Barcode.XDimension.Pixels = 4;
document.getElementById("img").src = generator.GenerateBarCodeImage(); // Display barcode image

generator.delete();

```