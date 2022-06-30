---
title: Read Barcodes from Word Documents
description: "How to Read Barcodes from MS Word Files Using Aspose.BarCode and Aspose.Words for .NET"
keywords:
type: docs
weight: 20
url: /net/recognize-barcode-from-word-document/
---
## **Overview**
It is often required to read barcodes from a Word document. Barcode images can be added as raster or vector graphics, as well as OLE objects generated in [*OLEFormat*](https://docs.microsoft.com/office/vba/api/word.oleformat). To read and decode barcodes through an Aspose class called [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader), document pages must be converted to raster images through rendering. The other way is to extract barcode images from a Word file first. However, it does not apply to cases when barcodes are in any non-raster formats. Rendering is the most universal and robust approach used to recognize barcodes. To perform the rendering of pages in a Word document, it is recommended to set a resolution of 300 dpi, which is the most optimal value for successful scanning and decoding.

In the examples below, we use the [***Aspose.Word***](https://products.aspose.com/words/net/) library as it is the most convenient tool for such operations.
  
## **How to Read Barcodes from Word Documents**
Here, you can learn how to read barcodes from Word files using [**Aspose.Word**](https://reference.aspose.com/words/net/) and [**Aspose.BarCode**](https://reference.aspose.com/barcode/net/) libraries. Code examples given below can be run using the [sample Word file](worddocwithbarcodes.docx) with barcodes.

### **Rendering of Word Pages to Raster Images**

This example explains how to recognize barcodes from a multi-page Word document by rendering each page to a raster image in the PNG format with a resolution of 300 dpi. This operation includes the following steps:
1.	Open the source Word document
2.	Set [*Resolution*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/resolution) and [*PageSet*](https://apireference.aspose.com/words/net/aspose.words.saving/pageset) for each page using [*ImageSaveOptions*](https://apireference.aspose.com/words/net/aspose.words.saving/imagesaveoptions)
3.	Pass the obtained image wrapped in an object of [*MemoryStream*](https://docs.microsoft.com/dotnet/api/system.io.memorystream) to class [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) for recognition
4.	Process the decoded data and output the results  
  
{{< highlight csharp>}}
//open the Word document
Aspose.Words.Document wordDoc = new Aspose.Words.Document($"{path}WordDocWithBarcodes.docx");

//process all word pages
for (int i = 0; i < wordDoc.PageCount; ++i)
{
    //create options to save
    Aspose.Words.Saving.ImageSaveOptions wordSaveOptions = new Aspose.Words.Saving.ImageSaveOptions(Aspose.Words.SaveFormat.Png);
    //set required page
    wordSaveOptions.PageSet = new Aspose.Words.Saving.PageSet(i);
    //set rendering resolution to 300 dpi
    wordSaveOptions.Resolution = 300;//300 dpi

    //render pages to a memory stream
    MemoryStream ms = new MemoryStream();
    wordDoc.Save(ms, wordSaveOptions);
    ms.Position = 0;

    //recognize PDF417, QR Code, Data Matrix, and Aztec barcode types from the rendered image of the page
    BarCodeReader reader = new BarCodeReader(ms, DecodeType.Pdf417, DecodeType.QR, DecodeType.DataMatrix, DecodeType.Aztec);
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"Barcode type:{result.CodeTypeName}, Barcode Data:{result.CodeText}");
}
{{< /highlight >}}
  
### **Extraction of Barcode Images**

The other way to recognize barcodes embedded in a Word document is to extract barcode images before decoding them. This method has several drawbacks. First, it does not allow keeping track of page numbers corresponding to barcodes. Moreover, barcode images can be stored in vector formats. Such barcodes may be extracted with errors and losses.  
This method can be executed following the steps listed below:
1.	Open the source Word file
2.	Extract the entire set of [*Shapes*](https://apireference.aspose.com/words/net/aspose.words.drawing/shape) from the document verifying for each object whether is it an image
3.	Attempt to recognize the extracted images through class [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader)
4.	Process the decoded data and output the results 
  
{{< highlight csharp>}}
//open the Word document
Aspose.Words.Document wordDoc = new Aspose.Words.Document($"{path}WordDocWithBarcodes.docx");

foreach (Aspose.Words.Drawing.Shape wordShape in wordDoc.GetChildNodes(Aspose.Words.NodeType.Shape, true))
{
    //we need only images
    if (!wordShape.HasImage) continue;

    //save the image data into a memory stream
    MemoryStream ms = new MemoryStream(wordShape.ImageData.ImageBytes);

    //recognize Pdf417, QR Code, Data Matrix, and Aztec barcode types from the rendered image of the page
    BarCodeReader reader = new BarCodeReader(ms, DecodeType.Pdf417, DecodeType.QR, DecodeType.DataMatrix, DecodeType.Aztec);
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"Barcode type:{result.CodeTypeName}, Barcode Data:{result.CodeText}");
}
{{< /highlight >}}
  