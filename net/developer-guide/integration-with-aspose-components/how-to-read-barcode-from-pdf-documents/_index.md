---
title: How to Read Barcode from PDF Documents
type: docs
weight: 20
url: /net/how-to-read-barcode-from-pdf-documents/
---

## **Recognize Barcode from PDF Documents**
In this article, we will explain how to read barcodes from a PDF document through integrating Aspose.BarCode for .NET and Aspose.PDF for .NET. We will take the below steps to read barcodes from a PDF document:

1. Extract an image from a PDF document using Aspose.PDF for .NET using PdfExtractor or PdfConverter classes
1. Save the extracted image as a stream
1. Pass the image in the form of a stream to Aspose.BarCode for .NET
1. Read barcodes from the image

Developers can use class [PdfExtractor](https://apireference.aspose.com/pdf/net/aspose.pdf.facades/pdfextractor) and bind an object of this class to a PDF document using the PdfExtractor.BindPdf() method. Then, it is necessary to specify start and end page numbers and then call the PdfExtractor.ExtractImage() method to get images for the mentioned pages. Using the while loop, it is required to call the PdfExtractor.GetNextImage() method and save the image to a stream. Thereafter, it is necessary to initialize an object of class BarCodeReader passing the stream and the target symbology type and then call the BarCodeReader.Read() method to read barcodes from the stream (image). The sample code snippet is given below:

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-RecognizeBarcodeFromPDFDocuments-RecognizeBarcodeFromPDFDocuments.cs" >}}

Class [PdfConverter](https://apireference.aspose.com/pdf/net/aspose.pdf.facades/pdfconverter) can be used to convert entire pages of a PDF document into images instead of extracting images from pages. This class can be useful in the cases when it is necessary to reade barcodes that occupy whole pages (for example, PatchCode letters) and also if PdfExtractor fails to extract barcode images from a PDF document. First, an instance of class PdfConverter needs to be created and binded to a PDF document using the PdfConverter.BindPdf() method. Then, it is required to specify start and end page numbers, set the PdfConverter.RenderingOptions.BarcodeOptimization parameter, and call the PdfConverter.DoConvert() method to initialize the converter. Using the while loop, it is necessary to call the PdfConverter.GetNextImage() method and save the page image to a stream. Thereafter, an instance of class BarCodeReader needs to be initialized setting the source stream and the target symbology type; then, it is required to call the BarCodeReader.Read() method to read barcodes from the source stream (image). The sample code snippet is given below:

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-RecognizeBarcodeFromPDFDocumentsUsingPdfConverter-RecognizeBarcodeFromPDFDocumentsUsingPdfConverter.cs" >}}

The evaluation version of Aspose.BarCode for .NET provides limited functionality. To get information about requesting a temporary license for 30 days, please visit <http://www.aspose.com/corporate/purchase/temporary-license.aspx>.
