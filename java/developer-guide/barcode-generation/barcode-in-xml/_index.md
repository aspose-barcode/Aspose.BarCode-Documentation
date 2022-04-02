---
title: Working with Data in XML
type: docs
description: "This article explains how to import and export barcodes to XML using Aspose.BarCode for .NET."
keywords: "Export barcode to XML, Import barcode from XML, barcode in XML, Aspose.BarCode, Read Barcode C#"
weight: 80
url: /net/barcode-in-xml/
---

## **Overview**
In ***Aspose.BarCode for .NET***, it is possible to perform data serialization and import data from XML using the specific functionality of class [*BarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator). Data serialization can be done in two ways: saving data to an xml-file using the [*ExportToXml(String)*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation.barcodegenerator/exporttoxml/methods/1) or to a stream with the [*ExportToXml(Stream)*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/methods/exporttoxml) method.  
  
Similarly, loading data from XML can be performed from a file using the [*ImportFromXml(String)*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation.barcodegenerator/importfromxml/methods/1) method or a stream through the [*ImportFromXml(Stream)*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/methods/importfromxml) method.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Export Data to XML**
As previously mentioned, there are two ways to save the current state of class [*BarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator): to an XML file through the [*ExportToXml(String)*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation.barcodegenerator/exporttoxml/methods/1) function or to a stream using the [*ExportToXml(Stream)*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/methods/exporttoxml) function. The code snippet below illustrates how to implement data serialization to an XML file.   

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MacroPdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.Barcode.Pdf417.Columns = 4;
//set PDF417 metadata
gen.Parameters.Barcode.Pdf417.Pdf417MacroFileID = 12345678;
gen.Parameters.Barcode.Pdf417.Pdf417MacroSegmentID = 12;
gen.Parameters.Barcode.Pdf417.Pdf417MacroSegmentsCount = 20;
gen.Parameters.Barcode.Pdf417.Pdf417MacroFileName = "file01";
gen.Parameters.Barcode.Pdf417.Pdf417MacroChecksum = 1234;
gen.Parameters.Barcode.Pdf417.Pdf417MacroFileSize = 400000;
gen.Parameters.Barcode.Pdf417.Pdf417MacroTimeStamp = new DateTime(2019, 11, 1);
gen.Parameters.Barcode.Pdf417.Pdf417MacroAddressee = "street";
gen.Parameters.Barcode.Pdf417.Pdf417MacroSender = "aspose";
//serialize BarcodeGenerator to file
gen.ExportToXml($"{path}generatorMacroPdf417.xml");
//generate original
gen.Save($"{path}BarcodeGeneratorOriginal.png", BarCodeImageFormat.Png);
{{< /highlight >}}

<p align="center"><img src="barcodegeneratororiginal.png"></p>

## **Import Data from XML**
The current state of of class [*BarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) can be imported from an XML file using the [*ImportFromXml(String)*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation.barcodegenerator/importfromxml/methods/1) function or from a stream through the [*ImportFromXml(Stream)*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/methods/importfromxml) function. The code sample provided below explains how to load data from an XML file.   

{{< highlight csharp>}}
//load BarcodeGenerator from file
BarcodeGenerator gen = BarcodeGenerator.ImportFromXml($"{path}generatorMacroPdf417.xml");
//generate loaded
gen.Save($"{path}BarcodeGeneratorLoaded.png", BarCodeImageFormat.Png);
{{< /highlight >}}

<p align="center"><img src="barcodegeneratorloaded.png"></p>

## **Saving and Loading Data from Stream**
The code snippet given below demonstrates how to save and load data from streams using two methods, [*ExportToXml(Stream)*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/methods/exporttoxml) and [*ImportFromXml(Stream)*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/methods/importfromxml), respectively. 

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 4;

//save to Stream
MemoryStream ms = new MemoryStream();
gen.ExportToXml(ms);
ms.Position = 0;

//load from stream
gen = BarcodeGenerator.ImportFromXml(ms);
//generate loaded
gen.Save($"{path}BarcodeGeneratorFromStream.png", BarCodeImageFormat.Png);
{{< /highlight >}}

<p align="center"><img src="barcodegeneratorfromstream.png"></p>