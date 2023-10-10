---
title: Decode FNC Symbols
type: docs
description: "This article describes how to decode FNC symbols in GS1 barcodes in Aspose.BarCode for C++ according to business needs"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcode C++"
notoc: true
weight: 20
url: /cpp/decode-fnc-symbols/
---

## **Decode GS1 Barcodes with FNC Symbols**
The GS1 association utilizes FNC symbols to manage decoding for *Code 128* and some other barcode types. There are four types of FNC symbols (FNC1-4) among which FNC1 is the most widespread one and is used for GS1 Application Identifier (AI) marking. When the library detects that a barcode does not correspond to any of GS1 types (e.g. *Code 128* or *GS1 Code 128*), the decoder outputs FNC symbols as “<FNC#>”. Such messages can be deleted from the recognition results by setting the [*StripFNC*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesettings/properties/stripfnc) property to false.  
  
  
<p align="center"><img src="code128fnc.png"></p>

