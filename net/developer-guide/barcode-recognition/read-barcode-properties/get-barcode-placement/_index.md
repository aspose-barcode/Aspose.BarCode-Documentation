---
title: Get Barcode Placement Region and Orientation Angle
linktitle: Get Placement Region and Orientation
type: docs
description: "This article describes how to read barcode parameters"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode C#"
feedback: BARCODECOM
weight: 20
url: /net/get-placement-and-orientation/
---  
  
In some cases, developers may need to get information about the placement region of a source barcode and its orientation angle. To enable such a possibility, ***Aspose.BarCode for .NET*** provides a group of properties called [*RegionParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderegionparameters) that stores the following information:
-	Quadrangle – a quadrangle object that bounds a barcode
-	Rectangle - a rectangle object that bounds a barcode
-	Points – an array of points constituting a barcode
-	Angle – an orientation angle in degrees
  
The following code sample illustrates how to get the information about barcode placement region and orientation angle for the example barcode image provided below.

{{< highlight csharp>}}
//recognize image
Console.WriteLine("ReadExtRegion:");
using (BarCodeReader read = new BarCodeReader($"{path}qr_code128.png", DecodeType.QR, DecodeType.Code128))
{
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine($"Quadrangle:{result.Region.Quadrangle.ToString()}");
        Console.WriteLine($"Angle:{result.Region.Angle.ToString()}");
        Console.WriteLine($"Rectangle:{result.Region.Rectangle.ToString()}");
        string ptStr = "";
        foreach (Point pt in result.Region.Points)
            ptStr += pt.ToString() + "";
        Console.WriteLine($"Points:{ptStr}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="qr_code128.png" width="20%" height="20%"></p>

