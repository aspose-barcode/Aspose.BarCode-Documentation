---
title: Set Target Regions for Recognition
linktitle: Set Target Regions
type: docs
description: "This Article Describes How to Set Target Regions in Source Image for Recognition"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcode Java"
weight: 30
feedback: BARCODECOM
url: /java/set-target-regions/
aliases:
- /java/barcode-regions/
---

## **Overview**
In ***Aspose.BarCode for Java***, it is possible to specify target areas for barcode detection by creating one or several objects of the [*Rectangle*](https://reference.aspose.com/imaging/java/com.aspose.imaging/Rectangle) type. Setting target regions allows improving recognition efficiency and avoiding the regions without any barcodes. Target areas have to be determined accurately as the Aspose library applies heuristic approaches to identify target barcode detection areas. Focusing on too many image regions can lead to recognition efficiency deterioration.

## **Set Unique Target Region**
To set one target area for barcode recognition, it is necessary to create an object of the [*Rectangle*](https://reference.aspose.com/imaging/java/com.aspose.imaging/Rectangle) type and then pass it to the *BarCodeReader* constructor or the *setBarCodeImage* method.  
  
<!--The following code samples explain how to specify one target region in the source image.

**Setting Target Region Using Class BarCodeReader**

{{< highlight csharp>}}
//specify the rectangle of a 2D barcode in the source image
Rectangle rect2D = new Rectangle(0, 0, 430, 440);
using (Bitmap bmp = new Bitmap($"{path}multiple_codes.png"))
using (BarCodeReader reader = new BarCodeReader(bmp, rect2D, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadWithRegion:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

**Setting Target Region Using SetBarCodeImage Method**
{{< highlight csharp>}}
//specify the rectangle of a 2D barcode in the source image
Rectangle rect2D = new Rectangle(0, 0, 430, 440);
using (Bitmap bmp = new Bitmap($"{path}multiple_codes.png"))
using (BarCodeReader reader = new BarCodeReader())
{
    reader.SetBarCodeImage(bmp, rect2D);
    reader.SetBarCodeReadType(DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR, DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC);
    Console.WriteLine("ReadSetBarCodeRegion:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

## **Set Several Target Regions**
It is also possible to set several target areas for barcode detection within one source image. This can be done in the same way as described above for one target region, i.e., using the *BarCodeReader* constructor or the *setBarCodeImage* method.  
  
<!--The following code snippet shows how to specify several target regions in the source image.
  
{{< highlight csharp>}}
using (Bitmap bmp = new Bitmap($"{path}multiple_codes.png"))
using (BarCodeReader reader = new BarCodeReader())
{
    //detecting the rectangle of a 2D barcode in the source image
    Rectangle rect2D = new Rectangle(0, 0, 430, 440);
    //rectangle of Code128 barcode in the source image
    Rectangle rectCode128 = new Rectangle(460, 111, 360, 150);
    reader.SetBarCodeImage(bmp, new Rectangle[] { rect2D, rectCode128 });
    reader.SetBarCodeReadType(DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR, DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC);
    Console.WriteLine("ReadMultipleRegions:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->
