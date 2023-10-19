---
title: Add Barcodes to PDF Documents
description: "How to Insert Barcodes to PDF Files"
keywords:
type: docs
feedback: BARCODECOM
weight: 10
url: /net/add-barcode-to-pdf-document/
---

## **Overview**

Adding one or more barcodes to a PDF document is a widely requested feature. This operation requires first generating a barcode image in a raster format (Raster Graphics) and then inserting this barcode into a PDF document.

PDF supports vector graphics in general but it has its own vector format and does not allow embedding vector images in a document. Instead, they get converted to a raster format.

It is recommended to work with PDF documents using [**Aspose.PDF**](https://products.aspose.com/pdf/net/) as shown in the examples provided in this article. Before starting to work with this library, developers must consider several specificities explained further. The axis of coordinates used to place objects in [**Aspose.PDF**](https://reference.aspose.com/pdf/net/) increases upwards similarly as in the standard Cartesian coordinate system. However, object coordinates are defined as [**lower-left; lower-bottom; upper-right; upper-top**] instead of using the standard way to set computer coordinates with the start in the [left, top] area. This peculiarity needs to be taken into account if you are going to use the standard coordinate system, see examples given further.  
[*Resolution*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/resolution) of an embedded barcode image is not related to its placement on a page of a PDF document. The standard resolution of a raster imager equals 96 dpi, which is insufficient for high-quality printing. It is recommended to set a resolution to 300 or 600 dpi for barcode images. This will allow printing high-quality documents through increase the size of the resulting PDF file. Note that PDF uses points instead of pixels (one pixel equals 72 points per inch). This is also explained in the given examples.  
  
[**Aspose.PDF**](https://reference.aspose.com/pdf/net/) provides many options to add barcode images to PDF documents that differ from each other in terms of simplicity or flexibility in managing document contents. In most cases, this operation includes the following steps:
1.	Create or open a PDF document using [*Aspose.Pdf.Document*](https://reference.aspose.com/pdf/net/aspose.pdf/document)
2.	Generate a barcode image setting desired resolution through class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) and save it to an object of [*MemoryStream*](https://docs.microsoft.com/dotnet/api/system.io.memorystream)
3.	Using [**Aspose.PDF**](https://reference.aspose.com/pdf/net/), place the created barcode image onto one or many pages of the PDF document setting its position on a page
4.	Save the updated PDF document  
    
## **How to Add Barcodes to PDF Document**

### **Standard Way**
This example shows how to insert barcode images created through [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) using the standard procedure. First, we generate a barcode image with a resolution of 300 dpi. Then, it is added to the selected page [*Aspose.Pdf.Page*](https://reference.aspose.com/pdf/net/aspose.pdf/page) of a document [*Aspose.Pdf.Document*](https://reference.aspose.com/pdf/net/aspose.pdf/document) and convert standard coordinates to an object of [*Aspose.Pdf.Rectangle*](https://reference.aspose.com/pdf/net/aspose.pdf/rectangle). The barcode image is inserted without compression and losses in quality, thus the size of the document increases.  
  
The following code sample explains how to do this. The resulting PDF file is provided below. 
    
{{< highlight csharp>}}
int Resolution = 300;//300 dpi high resolution of the barcode image
int leftBarcodePosition = 10;//left position of the barcode image
int topBarcodePosition = 20;//top position of the barcode image

//create a PDF document with a new page
Aspose.Pdf.Document pdfDoc = new Aspose.Pdf.Document();
Aspose.Pdf.Page pdfPage = pdfDoc.Pages.Add();

//convert the barcode image to a PNG stream
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Pdf417, "Aspose.Barcode Example");
generator.Parameters.Resolution = Resolution;//set the barcode image resolution
Bitmap image = generator.GenerateBarCodeImage();
MemoryStream imageStream = new MemoryStream();
generator.Save(imageStream, BarCodeImageFormat.Png);
imageStream.Position = 0;

//Rectangle where the image will be placed in the top/left corner
Rectangle imageRect = new Rectangle(leftBarcodePosition, topBarcodePosition, (image.Width * 72) / Resolution, (image.Height * 72) / Resolution);
Aspose.Pdf.Rectangle pdfRect = new Aspose.Pdf.Rectangle(imageRect.Left, pdfPage.Rect.Height - imageRect.Bottom, imageRect.Right, pdfPage.Rect.Height - imageRect.Top);
//add the image to the created PDF page
pdfPage.AddImage(imageStream, pdfRect);

//save the PDF document
pdfDoc.Save($"{path}AddBarcodeToPDFDocumentDirectly.pdf");
{{< /highlight >}}

[**Sample Output for Standard Way**](addbarcodetopdfdocumentdirectly.pdf)
  
### **Using PDF Facades**
This example explains how to add barcodes to PDF documents using [*PdfFileMend*](https://reference.aspose.com/pdf/net/aspose.pdf.facades/pdffilemend) from the [Aspose.Pdf.Facades](https://reference.aspose.com/pdf/net/aspose.pdf.facades/) namespace. It includes similar steps as described above. [*PdfFileMend*](https://reference.aspose.com/pdf/net/aspose.pdf.facades/pdffilemend) provides additional functions, such as inserting an image to several pages simultaneously, using a special insertion mode [*BlendMode*](https://reference.aspose.com/pdf/net/aspose.pdf/compositingparameters), and some other tools to facilitate image processing.  
  
The following code snippet demonstrates how to implement this option. The resulting PDF file is shown below. 
  
{{< highlight csharp>}}
int Resolution = 300;//300 dpi high resolution of the barcode image
int leftBarcodePosition = 10;//left position of the barcode image
int topBarcodePosition = 20;//top pistion of the barcode image

//create a PDF document and add a page
Aspose.Pdf.Document pdfDoc = new Aspose.Pdf.Document();
pdfDoc.Pages.Add();

//covert the barcode image to a PNG stream
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Pdf417, "Aspose.Barcode Example");
generator.Parameters.Resolution = Resolution;//set the barcode image resolution
Bitmap image = generator.GenerateBarCodeImage();
MemoryStream imageStream = new MemoryStream();
generator.Save(imageStream, BarCodeImageFormat.Png);
imageStream.Position = 0;

//create a mender and bind it to the PDF document
Aspose.Pdf.Facades.PdfFileMend mender = new Aspose.Pdf.Facades.PdfFileMend();
mender.BindPdf(pdfDoc);

//Place the image on page 1 in the top/left corner
Rectangle imageRect = new Rectangle(leftBarcodePosition, topBarcodePosition, (image.Width * 72) / Resolution, (image.Height * 72) / Resolution);
//page to acquire the box to calculate top/left corner
Aspose.Pdf.Page pdfPage = pdfDoc.Pages[1];
mender.AddImage(imageStream, 1, imageRect.Left, (float)pdfPage.Rect.Height - imageRect.Bottom, imageRect.Right, (float)pdfPage.Rect.Height - imageRect.Top);

//save the PDF document with the mender
mender.Save($"{path}AddBarcodeToPDFDocumentWithFacades.pdf");
{{< /highlight >}}
  
[**Sample Output for Using PDF Facades**](addbarcodetopdfdocumentwithfacades.pdf)
  
### **Using Operators**

This example demonstrates how to insert barcode images into PDF documents using [*Aspose.Pdf.Operator*](https://reference.aspose.com/pdf/net/aspose.pdf/operator) and its feature [*ConcatenateMatrix*](https://reference.aspose.com/pdf/net/aspose.pdf.operators/concatenatematrix). This way is more complicated than the others explained above and allows advanced users to flexibly manage barcode image properties.  
  
The following code sample shows how to work with this option. The resulting PDF file is given below. 
   
{{< highlight csharp>}}
int Resolution = 300;//300 dpi high resolution of the barcode image
int leftBarcodePosition = 10;//left position of the barcode image
int topBarcodePosition = 20;//top pistion of the barcode image

//create a PDF document with a new page
Aspose.Pdf.Document pdfDoc = new Aspose.Pdf.Document();
Aspose.Pdf.Page pdfPage = pdfDoc.Pages.Add();

//convert the barcode image to a PNG stream
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Pdf417, "Aspose.Barcode Example");
generator.Parameters.Resolution = Resolution;//set the barcode image resolution
Bitmap image = generator.GenerateBarCodeImage();
MemoryStream imageStream = new MemoryStream();
generator.Save(imageStream, BarCodeImageFormat.Png);
imageStream.Position = 0;

//Rectangle where the image will be placed in the top/left corner
Rectangle imageRect = new Rectangle(leftBarcodePosition, topBarcodePosition, (image.Width * 72) / Resolution, (image.Height * 72) / Resolution);
Aspose.Pdf.Rectangle pdfRect = new Aspose.Pdf.Rectangle(imageRect.Left, pdfPage.Rect.Height - imageRect.Bottom, imageRect.Right, pdfPage.Rect.Height - imageRect.Top);

//Add the image to the PDF document using operators
//add the image to resources and create a placement matrix
string pdfImageName = pdfPage.Resources.Images.Add(imageStream);
Aspose.Pdf.Matrix matrix = new Aspose.Pdf.Matrix(new double[] { pdfRect.URX - pdfRect.LLX, 0, 0, pdfRect.URY - pdfRect.LLY, pdfRect.LLX, pdfRect.LLY });

//save the graphics state
pdfPage.Contents.Add(new Aspose.Pdf.Operators.GSave());

//set the position of the next added image with ConcatenateMatrix
pdfPage.Contents.Add(new Aspose.Pdf.Operators.ConcatenateMatrix(matrix));

//draws an image in the previous placement
pdfPage.Contents.Add(new Aspose.Pdf.Operators.Do(pdfImageName));

//restore the graphics state
pdfPage.Contents.Add(new Aspose.Pdf.Operators.GRestore());

//save the PDF document
pdfDoc.Save($"{path}AddBarcodeToPDFDocumentWithOperators.pdf");
{{< /highlight >}}
  
[**Sample Output for Using Operators**](addbarcodetopdfdocumentwithoperators.pdf)
  