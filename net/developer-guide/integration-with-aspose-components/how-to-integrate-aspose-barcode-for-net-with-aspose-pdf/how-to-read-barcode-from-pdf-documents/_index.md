---
title: Read Barcodes from PDF Documents
description: "How to Recognize Barcodes from PDF Files"
keywords:
type: docs
feedback: BARCODECOM
ai_search_scope: "barcode_dotnet_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 20
url: /net/read-barcode-from-pdf-document/
aliases: 
- /net/export-pdf-pages-to-images-and-recognize-barcode/
---

## **Overview** 

Often there is a need to read barcodes from PDF documents. Barcodes can be embedded into PDF documents as images in raster or special PDF vector graphics formats. In ***Aspose.BarCode***, to read and decode barcodes through class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader), the source page of a PDF document must be represented as a raster image that may be obtained through the rendering procedure. When it is known that the source PDF document does not contain barcode images in a vector format, it is possible to extract them from the document before decoding. In this case, a single barcode image may get split into several parts thus making it unreadable. The rendering of page contents to a raster image is the most convenient and fault-tolerant way. It is recommended to set the most optimal resolution that equals 300 dpi.  
  
[**Aspose.PDF**](https://products.aspose.com/pdf/net/) library can be used to read barcodes from PDF documents. The recognition process includes the following steps:
1.	Open the source PDF document and render its pages to raster images
2.	Process the obtained images through class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) to detect and decode barcodes
3.	Further processing of the decoding results
  
## **How to Read Barcode from PDF Documents**
Further, you can find a detailed explanation for various methods to read barcode images from PDF documents using [**Aspose.PDF**](https://reference.aspose.com/pdf/net/) and [**Aspose.BarCode**](https://reference.aspose.com/barcode/net/) libraries. Code examples provided below can be run using the sample PDF file with barcodes that can be seen [here](pdfdocumentwithpdf417.pdf).

### **Using PdfConverter**

This example demonstrates how to read barcodes from a multi-page PDF document using class [*PdfConverter*](https://reference.aspose.com/pdf/net/aspose.pdf.facades/pdfconverter). Setting resolution to 300 dpi provides the most accurate recognition results.

{{< highlight csharp>}}
using (Aspose.Pdf.Document pdfDoc = new Aspose.Pdf.Document($"{path}PDFDocumentWithPdf417.pdf"))
{
    Aspose.Pdf.Facades.PdfConverter pdfConverter = new Aspose.Pdf.Facades.PdfConverter(pdfDoc);
    pdfConverter.RenderingOptions.BarcodeOptimization = true;

    //set resolution to the page
    //300 dpi is standard resolution
    pdfConverter.Resolution = new Aspose.Pdf.Devices.Resolution(300);

    //set all pages to render into images
    pdfConverter.StartPage = 1;//starts from 1
    pdfConverter.EndPage = pdfConverter.Document.Pages.Count;

    //render selected pages to the images
    pdfConverter.DoConvert();
    while (pdfConverter.HasNextImage())
    {
        //render current page to memory stream as png image
        MemoryStream ms = new MemoryStream();
        pdfConverter.GetNextImage(ms, ImageFormat.Png);
        ms.Position = 0;

        //recognize Pdf417, QR and DataMatrix barcode types from rendered image of the page
        BarCodeReader reader = new BarCodeReader(ms, DecodeType.Pdf417, DecodeType.QR, DecodeType.DataMatrix);
        foreach (BarCodeResult result in reader.ReadBarCodes())
            Console.WriteLine($"Barcode type:{result.CodeTypeName}, Barcode Data:{result.CodeText}");
    }
}
{{< /highlight >}}


### **Using PngDevice**
This example describes an option that is similar to the approach described above. Here, rendering of the contents from the source PDF file is performed using [*PngDevice*](https://reference.aspose.com/pdf/net/aspose.pdf.devices/pngdevice), a special class that facilitates converting PDF document pages to PNG images.
  
{{< highlight csharp>}}
using (Aspose.Pdf.Document pdfDoc = new Aspose.Pdf.Document($"{path}PDFDocumentWithPdf417.pdf"))
{
    //create png device with 300 dpi standard resolution
    Aspose.Pdf.Devices.PngDevice pngDevice = new Aspose.Pdf.Devices.PngDevice(new Aspose.Pdf.Devices.Resolution(300));

    //proceed all pdf pages, pages start from 1
    for (int i = 1; i <= pdfDoc.Pages.Count; ++i)
    {
        //render pdf page to the stream
        MemoryStream ms = new MemoryStream();
        pngDevice.Process(pdfDoc.Pages[i], ms);
        ms.Position = 0;

        //recognize Pdf417, QR and DataMatrix barcode types from rendered image of the page
        BarCodeReader reader = new BarCodeReader(ms, DecodeType.Pdf417, DecodeType.QR, DecodeType.DataMatrix);
        foreach (BarCodeResult result in reader.ReadBarCodes())
            Console.WriteLine($"Barcode type:{result.CodeTypeName}, Barcode Data:{result.CodeText}");
    }
}
{{< /highlight >}}


### **Direct Rendering of PDF Pages**

In this example, an object of [*AsposePdf.Page*](https://reference.aspose.com/pdf/net/aspose.pdf/page) representing the source page of the PDF document is converted to a raster image using the [*ConvertToPNGMemoryStream*](https://reference.aspose.com/pdf/net/aspose.pdf/page/methods/converttopngmemorystream) method. Unlike for [*PngDevice*](https://reference.aspose.com/pdf/net/aspose.pdf.devices/pngdevice), the resolution is set automatically and may not always be suitable for successful barcode recognition.
  
{{< highlight csharp>}}
using (Aspose.Pdf.Document pdfDoc = new Aspose.Pdf.Document($"{path}PDFDocumentWithPdf417.pdf"))
{
    //proceed all pdf pages, pages start from 1
    for (int i = 1; i <= pdfDoc.Pages.Count; ++i)
    {
        //render pdf page to the stream
        MemoryStream ms = pdfDoc.Pages[i].ConvertToPNGMemoryStream();
        ms.Position = 0;

        //recognize Pdf417, QR and DataMatrix barcode types from rendered image of the page
        BarCodeReader reader = new BarCodeReader(ms, DecodeType.Pdf417, DecodeType.QR, DecodeType.DataMatrix);
        foreach (BarCodeResult result in reader.ReadBarCodes())
            Console.WriteLine($"Barcode type:{result.CodeTypeName}, Barcode Data:{result.CodeText}");
    }
}
{{< /highlight >}}
  
### **Using Extracted Barcode Images**
In some cases, it is possible to extract embedded barcode images from the source PDF document and then decode them. This can be done using class [*ImagePlacementAbsorber*](https://reference.aspose.com/pdf/net/aspose.pdf/imageplacementabsorber).
The advantage of this method is that it allows recognizing barcodes with original resolution. The drawback is that barcode images in vector formats cannot be extracted as raster ones. Moreover, there is a risk that a single barcode will be split into several unreadable parts as a result of extraction. This approach is recommended for advanced users of the ***Aspose*** library. 
  
{{< highlight csharp>}}
using (Aspose.Pdf.Document pdfDoc = new Aspose.Pdf.Document($"{path}PDFDocumentWithPdf417.pdf"))
{
    //process all PDF pages in the document, page numeration starts from 1
    for (int i = 1; i <= pdfDoc.Pages.Count; ++i)
    {
        //create an image extractor and bind it to the page
        Aspose.Pdf.ImagePlacementAbsorber imagePlacementAbsorber = new Aspose.Pdf.ImagePlacementAbsorber();
        imagePlacementAbsorber.Visit(pdfDoc.Pages[i]);

        //extract all images from the PDF page
        foreach (Aspose.Pdf.ImagePlacement imagePlacement in imagePlacementAbsorber.ImagePlacements)
        {
            //convert an image from the pdf page to the stream
            MemoryStream ms = new MemoryStream();
            imagePlacement.Save(ms, ImageFormat.Png);
            ms.Position = 0;

            //recognize Pdf417, QR, and DataMatrix barcode types from extracted images from the page
            BarCodeReader reader = new BarCodeReader(ms, DecodeType.Pdf417, DecodeType.QR, DecodeType.DataMatrix);
            foreach (BarCodeResult result in reader.ReadBarCodes())
                Console.WriteLine($"Barcode type:{result.CodeTypeName}, Barcode Data:{result.CodeText}");
        }
    }
}
{{< /highlight >}}