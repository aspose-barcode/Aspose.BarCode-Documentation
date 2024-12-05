---
title: Decode FNC Symbols
type: docs
description: "This article describes how to decode FNC symbols in GS1 barcodes in Aspose.BarCode for JavaScript via C++ according to business needs"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcode JavaScript"
weight: 20
feedback: BARCODECOM
notoc: true
url: /javascript-cpp/decode-fnc-symbols/
---

The GS1 association utilizes FNC symbols to manage decoding for *Code 128* and some other barcode types. There are four types of FNC symbols (FNC1-4) among which FNC1 is the most widespread one and is used for GS1 Application Identifier (AI) marking. When the library detects that a barcode does not correspond to any of GS1 types (e.g. *Code 128* or *GS1 Code 128*), the decoder outputs FNC symbols as “<FNJavaScript>”. Such messages can be deleted from the recognition results by setting the [*StripFNC*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodesettings/properties/stripfnc) property to false.  
  
The following code sample shows how to work with FCN symbols while reading a *Code 128* barcode demonstrated below.

```javascript
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "Aspose" + FNC1 + FNC2 + FNC3))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Save($"{path}Code128FNC.png", BarCodeImageFormat.Png);
}

//read barcode image with StripFNC set to False
Console.WriteLine("ReadWithStripFNC:");
Console.WriteLine("StripFNC: false");
using (BarCodeReader read = new BarCodeReader($"{path}Code128FNC.png", DecodeType.Code128))
{
    read.BarcodeSettings.StripFNC = false;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}

//read barcode image with StripFNC set to True
Console.WriteLine("StripFNC: true");
using (BarCodeReader read = new BarCodeReader($"{path}Code128FNC.png", DecodeType.Code128))
{
    read.BarcodeSettings.StripFNC = true;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
```
  
<p align="center"><img src="code128fnc.png"></p>

