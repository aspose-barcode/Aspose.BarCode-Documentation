---
title: Work with Barcode Recognition State in XML
linktitle: Barcode Reading in XML
type: docs
description: "This Article Describes How to Save or Load Barcode Recognition State in the XML format"
keywords: "Read barcode in XML, Barcode XML Serialization, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcode JavaScript"
weight: 50
feedback: BARCODECOM
url: /javascript-cpp/barcode-reading-in-xml/
---

## **Overview**
In addition to barcode recognition, the [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) class supports serializing the barcode recognition state and exporting it to XML format. The recognition state can be saved to a file using the [*ExportToXml(String)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition.barcodereader/exporttoxml/methods/1) method or to a stream with the [*ExportToXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/exporttoxml) method. Additionally, the recognition state can be imported from XML format using [*ImportFromXml(String)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition.barcodereader/importfromxml/methods/1) and [*ImportFromXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/importfromxml).

It is important to note that automatic serialization of barcode image information, source image file links, or the image itself is not supported. To include this data, use the [*SetBarCodeImage*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/setbarcodeimage/index) methods.

{{% alert color="primary" %}}*For any clarifications, please reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/), ask questions at the [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13), or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Save Barcode Recognition State to XML**
***Aspose.BarCode for JavaScript via C++*** offers two methods to export the current state of the [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) class to XML: the [*ExportToXml(String)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition.barcodereader/exporttoxml/methods/1) method for file export and [*ExportToXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/exporttoxml) for stream export. The code snippet below demonstrates how to serialize the barcode recognition state to an XML file.

```javascript
// Create a BarCodeReader instance and configure settings
var read = new BarCodeInstance.BarCodeReader();
read.BarcodeSettings.StripFNC = true;
read.QualitySettings.XDimension = BarCodeInstance.XDimensionMode.Small;

// Serialize the BarCodeReader
var xmlString = read.ExportToXml();
console.log(xmlString);

read.delete();

```

## **Load Barcode Recognition State from XML**
The [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) class allows the current recognition state to be loaded from an XML file using the [*ImportFromXml(String)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition.barcodereader/importfromxml/methods/1) method or from a stream using the [*ImportFromXml(Stream)*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/importfromxml) method. The barcode image must be specified using the [*SetBarCodeImage*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/setbarcodeimage/index) properties. The following code snippet shows how to load the state of a [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) object from an XML file.


```javascript
// Load BarCodeReader 
var read = BarCodeInstance.BarCodeReader.ImportFromXml(xmlString);

// Initialized data
console.log(`StripFNC: ${read.BarcodeSettings.StripFNC}`);

read.delete();

```

