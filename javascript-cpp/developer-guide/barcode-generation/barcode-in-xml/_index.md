---
title: Export and Import Barcode Generation State via XML in JavaScript
linktitle: Barcode Generation State in XML
type: docs
feedback: BARCODECOM
description: This article explains how to import and export barcode the generation state to the XML format with JavaScript API or Library."
keywords: "Export barcode to XML, Import barcode from XML, Barcode in XML, Aspose.BarCode, Read Barcode JavaScript"
weight: 80
url: /javascript-cpp/barcode-generation-state-in-xml/
---
 
## **Overview**
In ***Aspose.BarCode for JavaScript via C++***, it is possible to perform the serialization of the barcode generation state and import it from XML using the specific functionality of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator). The serialization of a [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) instance can be executed in two ways: saving it to an XML-file using the [*ExportToXml(String)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation.barcodegenerator/exporttoxml/methods/1) or to a stream through the [*ExportToXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/methods/exporttoxml) method.  
  
Similarly, loading the barcode generation state from XML can be performed from a file using the [*ImportFromXml(String)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation.barcodegenerator/importfromxml/methods/1) method or a stream through the [*ImportFromXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/methods/importfromxml) method.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Export Barcode Generation State to XML**
As previously mentioned, there are two ways to save the current state of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator): to an XML file through the [*ExportToXml(String)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation.barcodegenerator/exporttoxml/methods/1) function or to a stream using the [*ExportToXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/methods/exporttoxml) function. The code snippet below illustrates how to implement the serialization of a [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) instance to an XML file.   

```javascript

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

```

<p align="center"><img src="barcodegeneratororiginal.png"></p>

## **Import Barcode Generation State from XML**
The current state of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) can be imported from an XML file using the [*ImportFromXml(String)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation.barcodegenerator/importfromxml/methods/1) function or from a stream through the [*ImportFromXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/methods/importfromxml) function. The code sample provided below explains how to import the barcode generation state from an XML file.   

```javascript

//load BarcodeGenerator from file
BarcodeGenerator gen = BarcodeGenerator.ImportFromXml($"{path}generatorMacroPdf417.xml");
//generate loaded
gen.Save($"{path}BarcodeGeneratorLoaded.png", BarCodeImageFormat.Png);

```

<p align="center"><img src="barcodegeneratorloaded.png"></p>

## **Save and Load Barcode Generation State from Stream**
The code snippet given below demonstrates how to save and load the barcode generation state from streams using two corresponding methods: [*ExportToXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/methods/exporttoxml) and [*ImportFromXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/methods/importfromxml). 

```javascript

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 4;

//save to stream
MemoryStream ms = new MemoryStream();
gen.ExportToXml(ms);
ms.Position = 0;

//load from stream
gen = BarcodeGenerator.ImportFromXml(ms);
//generate loaded
gen.Save($"{path}BarcodeGeneratorFromStream.png", BarCodeImageFormat.Png);

```

<p align="center"><img src="barcodegeneratorfromstream.png"></p>
