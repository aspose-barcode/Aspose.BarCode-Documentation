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
In ***Aspose.BarCode for JavaScript via C++***, you can serialize the state of barcode generation and import it from XML using the [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) class. Serialization of a [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) instance can be done in two ways: exporting it to an XML file using the [*ExportToXml(String)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation.barcodegenerator/exporttoxml/methods/1) method or exporting to a stream with the [*ExportToXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/methods/exporttoxml) method.

Similarly, you can load the barcode generation state from an XML source using the [*ImportFromXml(String)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation.barcodegenerator/importfromxml/methods/1) method for files or the [*ImportFromXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/methods/importfromxml) method for streams.

{{% alert color="primary" %}}*For any questions, reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/). Join the [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Export Barcode Generation State to XML**
You can save the state of a [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) instance to an XML file using the [*ExportToXml(String)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation.barcodegenerator/exporttoxml/methods/1) method or to a stream with the [*ExportToXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/methods/exporttoxml) method. The following code example demonstrates how to serialize a [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) instance to an XML file.
  

[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript

// Generate a Macro PDF417 barcode with metadata and export settings
var gen = new BarCodeInstance.BarcodeGenerator("MacroPdf417", "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension = "2px";
gen.Parameters.Barcode.Pdf417.Columns = 4;

// Set PDF417 metadata
gen.Parameters.Barcode.Pdf417.Pdf417MacroFileID = 12345678;
gen.Parameters.Barcode.Pdf417.Pdf417MacroSegmentID = 12;
gen.Parameters.Barcode.Pdf417.Pdf417MacroSegmentsCount = 20;
gen.Parameters.Barcode.Pdf417.Pdf417MacroFileName = "file01";
gen.Parameters.Barcode.Pdf417.Pdf417MacroChecksum = 1234;
gen.Parameters.Barcode.Pdf417.Pdf417MacroFileSize = 400000;
gen.Parameters.Barcode.Pdf417.Pdf417MacroTimeStamp = "1970-10-20T15:20:35.123Z";
gen.Parameters.Barcode.Pdf417.Pdf417MacroAddressee = "street";
gen.Parameters.Barcode.Pdf417.Pdf417MacroSender = "aspose";

// Export BarcodeGenerator settings to XML file
var xmlFile = gen.ExportToXml();
console.log(xmlFile);
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

gen.delete();


```

<p align="center"><img src="barcodegeneratororiginal.png"></p>

## **Import Barcode Generation State from XML**
You can import the state of a [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) instance from an XML file using the [*ImportFromXml(String)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation.barcodegenerator/importfromxml/methods/1) method or from a stream using the [*ImportFromXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/methods/importfromxml) method. The code example below shows how to import the barcode generation state from an XML file.
  

[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript

// Load BarcodeGenerator from XML file
var gen = BarCodeInstance.BarcodeGenerator.ImportFromXml(xmlFile);
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

gen.delete();


```

<p align="center"><img src="barcodegeneratorloaded.png"></p>

