---
title: Add Barcodes to PDF Documents
description: "How to Insert Barcodes to PDF Files"
keywords:
type: docs
ai_search_scope: "barcode_java_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 10
feedback: BARCODECOM
url: /java/add-barcode-to-pdf-document/
---

## **Overview**

Adding one or more barcodes to a PDF document is a widely requested feature. This operation requires first generating a barcode image in a raster format (Raster Graphics) and then inserting this barcode into a PDF document. PDF supports vector graphics in general but it has its own vector format and does not allow embedding vector images in a document. Instead, they get converted to a raster format.  
  
This article briefly describes the technique to integrate these two products together for adding high-quality barcode images to PDF documents. We will discuss creating a barcode image using Aspose.BarCode and then embed that barcode image to a PDF document generated by Aspose.PDF.  

## **Create a PDF Document using Aspose.PDF**
After the barcode image is saved to a MemoryStream, we are done with the barcode image. The only thing now needed is to add this barcode image (saved in the MemoryStream) to the PDF document. So, now it's time to create a PDF document using Aspose.PDF so that we can add this newly generated barcode image to it. Let's start by creating an instance of Aspose.Pdf.Document class and then add a page to this document instance as shown below.

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" 
"Examples-src-main-java-com-aspose-barcode-examples-technical_articles-AddBarcodeToPDFDocument-CreatePdfDocument.java" >}}

## **Add Barcode Image to the PDF Document**
Aspose.Pdf provides a Document class that represents a PDF document. We can create an instance of the Document class by calling its empty constructor. After creating an empty document, we will add a page by calling Document.Pages.Add method. The Barcode image shall be generated in the Memorystream using BarcodeGenerator.Save method with Memorystream as a parameter and BMP as BarCodeImageFormat. The PdfFileMend class object shall be initiated provided by Aspose.PDF to add Barcode image to PDF as shown below.

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" 
"Examples-src-main-java-com-aspose-barcode-examples-technical_articles-AddBarcodeToPDFDocument-AddBarcodeImageToPDFDocument.java" >}}

