---
title: Recognize Barcodes from Word Document
type: docs
weight: 40
url: /net/recognize-barcode-from-word-document/
---

## **Recognize Barcode from Word Document**
In this article, we will explain how to read barcodes from a Word document using [Aspose.BarCode](https://products.aspose.com/barcode/net) and [Aspose.Words](https://products.aspose.com/words/net). We will execute the following steps to recognize all barcodes from a Word document:

1. Extract an image from a Word document using Aspose.Words for .NET
1. Save the extracted image as a stream
1. Pass the image in the form of a stream to Aspose.BarCode for .NET
1. Read barcodes from the image

First, it is necessary to use class Aspose.Words.Document to open the source Word document. Then, the Document.GetChildNodes() method must be called to get a collection of all shapes (including images) from the Word document. Through applying the for-each loop to this collection, it is required to check if a shape has an image using the Shape.HasImage property and then call the Shape.ImageData.Save() method to save the target image to a stream. Then, an object of class BarCodeReader needs to be initialized using the stream and setting DecodeType; then, it is required to call the BarCodeReader.Read() method to read barcodes from the stream (image). The sample code snippet is given below:

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-RecognizeBarcodeFromWordDocument-RecognizeBarcodeFromWordDocument.cs" >}}


The evaluation version of Aspose.BarCode for .NET can only recognize Code 39 barcodes. If the image contains barcodes of other symbology types, a valid license must be set. To get more details about requesting a temporary license for 30 days, please visit <http://www.aspose.com/corporate/purchase/temporary-license.aspx>.
