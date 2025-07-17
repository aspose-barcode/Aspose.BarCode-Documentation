---
title: Export and Import Barcode Generation State via XML in C++
linktitle: Barcode Generation in XML
type: docs
description: This article explains how to import and export barcode the generation state to the XML format with C++ API or Library."
keywords: "Export barcode to XML, Import barcode from XML, Barcode in XML, Aspose.BarCode, Read Barcode C++"
ai_search_scope: "barcode_cpp_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 80
feedback: BARCODECOM
url: /cpp/barcode-generation-state-in-xml/
aliases:
- /cpp/managing-different-barcode-settings/

---
 
## **Overview**
In ***Aspose.BarCode for C++***, it is possible to perform the serialization of the barcode generation state and import it from XML using the specific functionality of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.barcode_generator/). The serialization of a [*BarcodeGenerator*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.barcode_generator/) instance can be executed in two ways: saving it to an XML-file using the *ExportToXml(String)* or to a stream through the *ExportToXml(Stream)* method.  
  
Similarly, loading the barcode generation state from XML can be performed from a file using the *ImportFromXml(String)* method or a stream through the *ImportFromXml(Stream)* method.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Export Barcode Generation State to XML**
As previously mentioned, there are two ways to save the current state of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.barcode_generator/): to an XML file through the *ExportToXml(String)* function or to a stream using the *ExportToXml(Stream)* function. The code snippet below illustrates how to implement the serialization of a [*BarcodeGenerator*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.barcode_generator/) instance to an XML file.   

<p align="center"><img src="barcodegeneratororiginal.png"></p>

## **Import Barcode Generation State from XML**
The current state of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.barcode_generator/) can be imported from an XML file using the *ImportFromXml(String)* function or from a stream through the *ImportFromXml(Stream)* function. The code sample provided below explains how to import the barcode generation state from an XML file.   

<p align="center"><img src="barcodegeneratorloaded.png"></p>

## **Save and Load Barcode Generation State from Stream**
The code snippet given below demonstrates how to save and load the barcode generation state from streams using two corresponding methods: *ExportToXml(Stream)* and *ImportFromXml(Stream)*. 

<p align="center"><img src="barcodegeneratorfromstream.png"></p>
