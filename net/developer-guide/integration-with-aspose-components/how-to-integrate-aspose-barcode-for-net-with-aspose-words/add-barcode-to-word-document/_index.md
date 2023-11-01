---
title: Add Barcodes to Word Documents
description: "How to Add Barcodes to MS Word Files Using Aspose.BarCode and Aspose.Words"
keywords:
type: docs
feedback: BARCODECOM
weight: 10
url: /net/add-barcode-to-word-document/
---

## **Overview**

It may often be needed to add one or more barcode images to a Microsoft Word document. This task requires first generating a barcode in a raster (raster graphics) o vector (Windows metafile) format and then inserting it into a Word file.

For raster images, it is very important to set an appropriate value of [*Resolution*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/resolution). By default, [*Resolution*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/resolution) equals 96 dpi. For high-quality printing, it should be set in a range from 300 to 600 dpi. For vector formats, the resolution does not have a large impact. This parameter is still important to convert millimeters and inches to internal vector units for fonts and sizing parameters. Word documents use points instead of pixels as measurement units (one inch equals 72 points).

The [*Aspose.Word*](https://products.aspose.com/words/net/) library is the most convenient tool to work with Word files and can be used to insert barcodes into Word files. This operation includes the following steps:
1.	Create or open a Word document through [*Aspose.Words.Document*](https://reference.aspose.com/words/net/aspose.words/document)
2.	Generate a barcode image in a raster or vector format (see the list of supported formats [here](https://docs.aspose.com/barcode/net/barcode-types-and-image-formats/))) using class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator)  
3.	Add the barcode to the Word file in the desired positions using [*Aspose.Word.DocumentBuilder*](https://reference.aspose.com/words/net/aspose.words/documentbuilder)
4.	Save the document
  
Class [*DocumentBuilder*](https://reference.aspose.com/words/net/aspose.words/documentbuilder) facilitates the process of creating objects of class [*Document*](https://reference.aspose.com/words/net/aspose.words/document). [*DocumentBuilder*](https://reference.aspose.com/words/net/aspose.words/documentbuilder) serves as a simplification (so-called "facade") for the complex structure of [*Document*](https://reference.aspose.com/words/net/aspose.words/document) and allows adding contents and formatting in a quick and easy way.

## **How to Add Barcode Images to Word Documents**
### **Using Cursor Position**
This example explains how to insert a barcode image created through class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) into a Word file represented as an object of [*Aspose.Words.Document*](https://reference.aspose.com/words/net/aspose.words/documentbuilder) using the cursor position. The DocumentBuilder has an internal cursor where the text will be inserted when you call *Write()*, *Writeln()*, *InsertBreak()*, and other methods. You can navigate the [*DocumentBuilder*](https://reference.aspose.com/words/net/aspose.words/documentbuilder) cursor to a different location in a document using various *MoveTo* methods. The barcode image is generated with a resolution of 300 dpi and then is added between lines of text at the current position of the cursor. The size of the image gets converted to points.  
  
The following code snippet shows how to implement this approach. The resulting Word document is given below. 
  
{{< highlight csharp>}}
int Resolution = 300;//300 dpi high resolution of the barcode image

//create a Word document
Aspose.Words.Document wordDoc = new Aspose.Words.Document();
Aspose.Words.DocumentBuilder wordBuilder = new Aspose.Words.DocumentBuilder(wordDoc);

//create a barcode image
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Pdf417, "Aspose.Barcode Pdf417 Example");
generator.Parameters.Resolution = Resolution;//set the barcode image resolution
Bitmap image = generator.GenerateBarCodeImage();
MemoryStream imageStream = new MemoryStream();
generator.Save(imageStream, BarCodeImageFormat.Png);

//insert the barcode image into text
wordBuilder.Write("First Sentence.");
wordBuilder.InsertImage(imageStream.ToArray(), (image.Width * 72) / Resolution, (image.Height * 72) / Resolution);
wordBuilder.Write("Second Sentence.");

//save the document
wordDoc.Save($"{path}AddBarcodeToWordDocumentInline.docx", Aspose.Words.SaveFormat.Docx);
{{< /highlight >}}
  
[**Sample Output for Using Cursor Position**](addbarcodetowordsocumentinline.docx)

### **Using Floating Window**
This example is similar to the previous one with the difference that [*Aspose.Words.DocumentBuilder*](https://reference.aspose.com/words/net/aspose.words/documentbuilder) inserts the generated barcode in a floating window. The barcode image is positioned relative to the page edges instead of using the cursor position. 
  
The following code sample demonstrates how to work with this option. The resulting Word file is provided below.
  
{{< highlight csharp>}}
int Resolution = 300;//300 dpi high resolution of the barcode image
int leftBarcodePosition = 10;//left position of the barcode image
int topBarcodePosition = 20;//top pistion of the barcode image

//create a Word document
Aspose.Words.Document wordDoc = new Aspose.Words.Document();
Aspose.Words.DocumentBuilder wordBuilder = new Aspose.Words.DocumentBuilder(wordDoc);

//create a barcode image
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Pdf417, "Aspose.Barcode Pdf417 Example");
generator.Parameters.Resolution = Resolution;//set the barcode image resolution
Bitmap image = generator.GenerateBarCodeImage();
MemoryStream imageStream = new MemoryStream();
generator.Save(imageStream, BarCodeImageFormat.Png);

//insert the barcode image as floating image from the top/left position of the page
wordBuilder.Write("First Sentence.");
wordBuilder.InsertImage(imageStream.ToArray(),
    Aspose.Words.Drawing.RelativeHorizontalPosition.Page, leftBarcodePosition,
    Aspose.Words.Drawing.RelativeVerticalPosition.Page, topBarcodePosition,
    (image.Width * 72) / Resolution, (image.Height * 72) / Resolution, Aspose.Words.Drawing.WrapType.Square);
wordBuilder.Write("Second Sentence.");

//save the document
wordDoc.Save($"{path}AddBarcodeToWordDocumentFloating.docx", Aspose.Words.SaveFormat.Docx);
{{< /highlight >}}
  
[**Sample Output for Using Floating Window**](addbarcodetoworddocumentfloating.docx)
  
### **Using Barcode Images in Vector Formats**
This example demonstrates how to add a barcode image generated in a vector format through class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) to a Word document. Here, the barcode having the Windows Metafile format gets inserted into a floating window through class [*Aspose.Words.DocumentBuilder*](https://reference.aspose.com/words/net/aspose.words/documentbuilder) and is positioned relative to the page edges.  
  
The following code snippet explains how to work with barcodes in vector formats. The resulting Word file can be seen below.
  
{{< highlight csharp>}}
int Resolution = 300;//300 dpi high resolution of the barcode image
int leftBarcodePosition = 10;//left position of the barcode image
int topBarcodePosition = 20;//top pistion of the barcode image

//create a Word document
Aspose.Words.Document wordDoc = new Aspose.Words.Document();
Aspose.Words.DocumentBuilder wordBuilder = new Aspose.Words.DocumentBuilder(wordDoc);

//create a barcode image
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Pdf417, "Aspose.Barcode Pdf417 Example");
generator.Parameters.Resolution = Resolution;//set the barcode image resolution
Bitmap image = generator.GenerateBarCodeImage();
MemoryStream imageStream = new MemoryStream();
generator.Save(imageStream, BarCodeImageFormat.Emf);

//insert the barcode image as a floating image from the top/left position of the page
wordBuilder.Write("First Sentence.");
wordBuilder.InsertImage(imageStream.ToArray(),
    Aspose.Words.Drawing.RelativeHorizontalPosition.Page, leftBarcodePosition,
    Aspose.Words.Drawing.RelativeVerticalPosition.Page, topBarcodePosition,
    (image.Width * 72) / Resolution, (image.Height * 72) / Resolution, Aspose.Words.Drawing.WrapType.Square);
wordBuilder.Write("Second Sentence.");

//save the document
wordDoc.Save($"{path}AddBarcodeToWordDocumentFloatingEMF.docx", Aspose.Words.SaveFormat.Docx);
{{< /highlight >}}

[**Sample Output for Using Vector Images**](addbarcodetoworddocumentfloatingemf.docx)