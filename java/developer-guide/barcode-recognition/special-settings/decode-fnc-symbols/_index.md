---
title: Decode FNC Symbols
type: docs
description: "This article describes how to decode FNC symbols in GS1 barcodes in Aspose.BarCode for .NET according to business needs"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcode in Java"
weight: 20
feedback: BARCODECOM
notoc: true
url: /java/decode-fnc-symbols/
---

The GS1 association suggests using FNC characters to decode some symbologies, including *Code 128* and *Code 128*. Four types of FNC symbols (FNC1-4) are supported. FNC1 is the most widely used one that is intended for GS1 Application Identifier (AI) marking. When a barcode does not relate to any of GS1 types (e.g. *Code 128* or *GS1 Code 128*), the decoder processes FNC symbols as *<FNC#>*. These symbols can be removed from decoding results by passing the *False* value to the *setStripFNC* method.  
  
<!--The following code snippet explains how to manage FCN symbols.

{{< highlight csharp>}}
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
{{< /highlight >}}-->
  
<p align="center"><img src="code128fnc.png"></p>
