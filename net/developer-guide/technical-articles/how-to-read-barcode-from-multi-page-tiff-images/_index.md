---
title: Read Barcodes from Multipage TIFF Images in C#
linktitle: Read Barcodes from TIFF
description: "How to Recognize Barcodes from TIFF Files"
keywords: "read barcodes from tiff, barcodes in tiff file, multi-page tiff document, recognize barcode from tiff, find barcodes in tiff document"
type: docs
weight: 10
feedback: BARCODECOM
url: /net/read-barcode-from-multipage-tiff/
aliases:
- /net/how-to-read-barcode-from-multi-page-tiff-images/
---

## **Overview**

It is often required to read barcodes from multi-page TIFF files. TIFF is a common raster graphics format that allows storing several high-quality images in one document. This format is widely used to save data during automatic scanning.
***Aspose.BarCode*** enables recognizing barcodes from TIFF documents but it can only read from the first page (or “frame”). To detect barcodes in other frames, it is necessary to process them using side libraries first and then pass the obtained raster images to class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader). The recognition process includes the following steps:
1.	Open the source multi-page TIFF file
2.	Selected the requested frame that often represents a page of the scanned document
3.	Read barcodes from the frame
4.	Repeat Steps 2 and 3 until all target pages are processed  


## **Read Barcodes from Multi-page TIFF Document**
Further in the article, you can find code examples for extracting frames from a document scanned in the TIFF format and recognizing barcodes in those frames. The sample source TIFF file can be viewed [*here*](multipagetiffwithbarcodes.tiff).

### **Using Aspose.Imaging**

This example explains how to read barcodes from multi-page TIFF documents using the [**Aspose.Imaging**](https://products.aspose.com/imaging/net/) library that is fully cross-platform and the most convenient way to implement such tasks. The barcode recognition process comprises the following steps:
1.	Open the source multi-page TIFF document using [*TiffImage*]( https://reference.aspose.com/imaging/net/aspose.imaging.fileformats.tiff/tiffimage/)
2.	Select the required page using [*TiffFrame*]( https://reference.aspose.com/imaging/net/aspose.imaging.fileformats.tiff/tiffframe/)
3.	Process the obtained image through class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) to read barcodes
4.	Repeat Steps 2 and 3 until all target pages are processed   
  
The following code snippet illustrates how to work with this approach.
  
{{< highlight csharp>}}
//open the required image
using (Aspose.Imaging.Image openImage = Aspose.Imaging.Image.Load($"{path}MultiPageTiffWithBarcodes.tiff"))
{
    //cast it as a multi-page TIFF file
    Aspose.Imaging.FileFormats.Tiff.TiffImage tiffImage = openImage as Aspose.Imaging.FileFormats.Tiff.TiffImage;
    if (null == tiffImage) return;

    //process each TIFF frame
    foreach(Aspose.Imaging.FileFormats.Tiff.TiffFrame tiffFrame in tiffImage.Frames)
    {
        //save the TIFF frame to the stream as PNG
        MemoryStream ms = new MemoryStream();
        tiffFrame.Save(ms, new Aspose.Imaging.ImageOptions.PngOptions());
        ms.Position = 0;

        //recognize PDF417, QR Code, Data Matrix, and Aztec barcode types from the rendered image of the page
        BarCodeReader reader = new BarCodeReader(ms, DecodeType.Pdf417, DecodeType.QR, DecodeType.DataMatrix, DecodeType.Aztec);
        foreach (BarCodeResult result in reader.ReadBarCodes())
            Console.WriteLine($"Barcode type:{result.CodeTypeName}, Barcode Data:{result.CodeText}");
    }
}
{{< /highlight >}}
  
### **Using System.Drawing**

It is possible to use the standard library called [*System.Drawing*](https://docs.microsoft.com/dotnet/api/system.drawing?view=netframework-4.8) to recognize barcodes from multi-page TIFF files. This library cannot be considered fully cross-platform but works efficiently on Windows-based systems. Barcode recognition includes the following steps:
1.	Open the source TIFF document using class [*Image*](https://docs.microsoft.com/dotnet/api/system.drawing.image)     
2.	Select the required page using [*SelectActiveFrame*]( https://docs.microsoft.com/dotnet/api/system.drawing.image.selectactiveframe)
3.	Process the obtained image using class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) to detect and recognize barcodes
4.	Repeat Steps 2 and 3 until all target pages are processed
  
The following code sample explains how to implement this option.
  
{{< highlight csharp>}}
//open the required TIFF image
using (System.Drawing.Image tiffImage = System.Drawing.Image.FromFile($"{path}MultiPageTiffWithBarcodes.tiff"))
{
    //get the frame count
    int tiffFrameCount = tiffImage.GetFrameCount(System.Drawing.Imaging.FrameDimension.Page);
    
    //process each tiff frame
    for (int i = 0; i < tiffFrameCount; i++)
    {
        //select an active frame
        tiffImage.SelectActiveFrame(System.Drawing.Imaging.FrameDimension.Page, i);
        
        //save the TIFF frame to the stream as PNG
        MemoryStream ms = new MemoryStream();
        tiffImage.Save(ms, System.Drawing.Imaging.ImageFormat.Png);
        ms.Position = 0;

        //recognize PDF417, QR Code, Data Matrix, and Aztec barcode types from the rendered image of the page
        BarCodeReader reader = new BarCodeReader(ms, DecodeType.Pdf417, DecodeType.QR, DecodeType.DataMatrix, DecodeType.Aztec);
        foreach (BarCodeResult result in reader.ReadBarCodes())
            Console.WriteLine($"Barcode type:{result.CodeTypeName}, Barcode Data:{result.CodeText}");
    }
}
{{< /highlight >}}
  
