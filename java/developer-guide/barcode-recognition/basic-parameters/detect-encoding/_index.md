---
title: Read Barcodes with Unicode Encodings
type: docs
feedback: BARCODECOM
description: "This article describes how to decode barcodes with Unicode encoding"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcode C#"
weight: 80
url: /java/read-unicode-encodings/
---

***Aspose.BarCode for Java*** provides class [*BarcodeSettings*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarcodeSettings) that contains a special method called *setDetectEncoding* that enables the automatic recognition of UTF8 and UTF16 Unicode encodings for 2D symbologies and allows re-encoding barcode information into a string with Unicode characters. If this recognition mode is turned off, barcode information can be scanned and decoded manually based on the desired encoding.  
  
<!--The following code sample explains how to decode barcodes with UTF8 and UTF16 Unicode encodings automatically (namely, *QR Code* has been used). 

{{< highlight csharp>}}
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "بالقمة Aspose"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.QR.CodeTextEncoding = Encoding.UTF8;
    gen.Save($"{path}QRDetectEncoding.png", BarCodeImageFormat.Png);
}

Console.WriteLine("ReadDetectEncoding:");
//read barcode image with DetectEncoding set to true
Console.WriteLine("DetectEncoding: true");
using (BarCodeReader read = new BarCodeReader($"{path}QRDetectEncoding.png", DecodeType.QR))
{
    read.BarcodeSettings.DetectEncoding = true;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}

//read barcode image with DetectEncoding set to False
Console.WriteLine("DetectEncoding: false");
using (BarCodeReader read = new BarCodeReader($"{path}QRDetectEncoding.png", DecodeType.QR))
{
    read.BarcodeSettings.DetectEncoding = false;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
{{< /highlight >}}-->
  
<p align="center"><img src="qrdetectencoding.png"></p>
