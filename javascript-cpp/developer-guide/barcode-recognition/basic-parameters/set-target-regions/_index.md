---
title: Set Target Regions for Recognition
linktitle: Set Target Regions
feedback: BARCODECOM
type: docs
description: "This Article Describes How to Set Target Regions in Source Image for Recognition"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcode JavaScript"
weight: 30
url: /javascript-cpp/set-target-regions/
---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
***Aspose.BarCode for JavaScript via C++*** enables setting one or many objects of the [*Rectangle*](https://docs.microsoft.com/dotnet/api/system.drawing.rectangle) type to limit target areas for barcode detection. This property allows improving recognition efficiency and avoiding the recognition of irrelevant barcodes placed in the areas out of interest. At the same time, it is necessary to select target regions justifiably because the Aspose library applies heuristic methods to localize regions for barcode recognition; hence, simply enumerating multiple areas can deteriorate reading efficiency.

## **Set Single Region**
To set a target region for barcode recognition, it is necessary to define an object of the [*Rectangle*](https://docs.microsoft.com/dotnet/api/system.drawing.rectangle) type using the [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) constructor or the [*SetBarCodeImage*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition.barcodereader/setbarcodeimage/methods/1) method.  
  
The following code samples illustrate how to set a target recognition region in the source image using the two ways mentioned above.

**Set Target Region Using Class BarCodeReader**

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

**Set Target Region Using SetBarCodeImage Method**
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
{{< /highlight >}}

## **Set Multiple Target Regions**
In cases when it is required to specify several regions for barcode reading in the same source image, developers can define target areas in the same way as for the single region, namely, using the [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) constructor or the [*SetBarCodeImage*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition.barcodereader/setbarcodeimage/methods/1) method.  
  
The following code snippet explains how to multiple target areas for barcode reading in the source image.
  
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
{{< /highlight >}}
