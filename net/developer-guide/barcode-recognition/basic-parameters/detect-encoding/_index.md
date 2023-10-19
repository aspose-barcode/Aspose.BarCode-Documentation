---
title: Read Barcodes with Unicode Encodings
type: docs
description: "This article describes how to decode barcodes with Unicode encoding"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcode C#"
weight: 80
feedback: BARCODECOM
url: /net/read-unicode-encodings/
---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

In ***Aspose.BarCode for .NET***, there is a special parameter called [*DetectEncoding*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesettings/properties/detectencoding) that allows enabling the automatic recognition of UTF8 and UTF16 Unicode encodings for 2D barcode recognition, as well as re-encoding the data into a Unicode string. When this mode is disabled, the barcode data can be read and decoded manually using the required encoding.  
  
The following code snippet shows how to automatically decode barcodes with UTF8 and UTF16 Unicode encodings (a sample *QR Code* barcode image shown below has been considered). 

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
{{< /highlight >}}
  
<p align="center"><img src="qrdetectencoding.png"></p>

