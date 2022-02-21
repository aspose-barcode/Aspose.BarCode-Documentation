---
title: Export PDF Pages to Images and Recognize Barcodes
type: docs
weight: 60
url: /net/export-pdf-pages-to-images-and-recognize-barcode/
---

In this article, we will explain how to read barcodes from a PDF document using Aspose.BarCode for .NET and Aspose.PDF for .NET. We will execute the below steps to recognize all barcodes presented in a PDF document:

1. Export the source PDF page to an image using Aspose.PDF for .NET
1. Save the extracted image as a stream
1. Pass the image in the form of a stream to Aspose.BarCode for .NET
1. Read barcodes from the image
1. Repeat the above steps until the end of the PDF document

To implement these steps, you can use class [PdfConverter](https://apireference.aspose.com/pdf/net/aspose.pdf.facades/pdfconverter) and bind it to a PDF document using the PdfConverter.BindPdf() method. It is necessary to specify start and end page numbers and then call the PdfConverter.DoConvert() method to convert the selected page to an image. Then, you need to call the PdfConverter.GetNextImage() method and save the image to a stream. Finally, it is required to create an instance of class Aspose.BarCodeRecognition.BarCodeReader passing the stream and setting the target symbology type and then call the BarCodeReader.Read() method to read barcodes from the stream (image). The sample code snippet is given below:

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-ExportPDFPagesToImagesAndRecognizeBarCode-ExportPDFPagesToImagesAndRecognizeBarCode.cs" >}}

The evaluation version of Aspose.BarCode for .NET can only be used to read Code 39 barcodes. If an image contains barcodes of different symbology types, a valid license must be set. To get information about a temporary license for 30 days, please visit <http://www.aspose.com/corporate/purchase/temporary-license.aspx>.
