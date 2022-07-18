---
title: Barcode Generation Data in XML
type: docs
description: "This article explains how to import and export barcodes to XML using Aspose.BarCode for Java."
keywords: "Export barcode to XML, Import barcode from XML, barcode in XML, Aspose.BarCode, Read Barcode Java"
weight: 80
url: /java/barcode-generation-in-xml/
aliases:
- /java/barcode-in-xml/
---

## **Overview**
***Aspose.BarCode for Java*** enables data serialization and data import from XML through special methods of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeGenerator). There are two ways of implementing data serialization: outputting data to an XML-file through the *exportToXml(java.lang.String xmlFile)* method or a stream through the *exportToXml(java.io.OutputStream xml)* method. Uploading data from XML can be done from a file through the *importFromXml(java.lang.String xmlFile)* method or a stream through the *importFromXml(java.io.InputStream xml)* method.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Export Barcode Generation Data to XML**
As stated above, ***Aspose.BarCode for Java*** provides two ways of outputting the current state of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeGenerator): to an XML file using the *exportToXml(java.io.String xmlFile)* method or a stream through the *exportToXml(java.lang.OutputStream xml)* method. 
<!--The following code sample shows how to perform data serialization to an XML file.   

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

<p align="center"><img src="barcodegeneratororiginal.png"></p>-->

## **Import Barcode Generation Data from XML**
It is possible to import the current state of of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeGenerator) from an XML file through the *importFromXml(java.lang.String xmlFile)* method or a stream using the *importFromXml(java.io.InputStream xml)* function. 
<!--The following code snippet shows how to import data from an XML file.   

{{< highlight csharp>}}
//load BarcodeGenerator from file
BarcodeGenerator gen = BarcodeGenerator.ImportFromXml($"{path}generatorMacroPdf417.xml");
//generate loaded
gen.Save($"{path}BarcodeGeneratorLoaded.png", BarCodeImageFormat.Png);
{{< /highlight >}}
-->

<p align="center"><img src="barcodegeneratorloaded.png"></p>

## **Saving and Loading Barcode Data from Stream**
To export and import information from streams, two special methods need to be called: *exportToXml(java.lang.OutputStream xml)* and *importFromXml(java.io.InputStream xml)*. 

<!--{{< highlight csharp>}}
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
{{< /highlight >}}-->

<p align="center"><img src="barcodegeneratorfromstream.png"></p>