---
title: Work with Barcode Recognition State in XML
linktitle: Barcode Reading in XML
type: docs
description: "This Article Describes How to Save or Load Barcode Recognition State in the XML format"
keywords: "Read barcode in XML, Barcode XML Serialization, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Barcode in WPF Project, Aspose.BarCode, Read Barcode C++"
ai_search_scope: "barcode_cpp_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 50
feedback: BARCODECOM
url: /cpp/barcode-reading-in-xml/
---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can check the quality of Aspose.BarCode recognition and view the results online.{{% /alert %}}

## **Overview**
In addition to barcode recognition functionality, class [*BarCodeReader*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.bar_code_recognition.bar_code_reader/) allows performing the serialization of the barcode recognition state and uploading it in the XML format. The recognition state can be saved both to a file *ExportToXml(String)* or a stream *ExportToXml(Stream)*. Moreover, it can be imported in the XML format from a file or a stream using functions *ImportFromXml(String)* and *ImportFromXml(Stream)*. 
  
It should be noted that the serialization of the information about a barcode image, the link to a source image file, or the image itself cannot be performed automatically. In the case of such a need, this functionality has to be set explicitly using the family of functions called *SetBarCodeImage*.    

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Save Barcode Recognition State to XML**
***Aspose.BarCode for C++*** provides two ways to obtain the current state of class [*BarCodeReader*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.bar_code_recognition.bar_code_reader/): to an XML file through the *ImportToXml(String)* function or a stream using the *ImportToXml(Stream)* function. 

## **Load Barcode Recognition State from XML**
The current state of class [*BarCodeReader*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.bar_code_recognition.bar_code_reader/) can be loaded from an XML file through the *ImportFromXml(String)* function or from a stream through the *ImportFromXml(Stream)* function. The target barcode image needs to be specified using the group of properties called *SetBarCodeImage*. 


## **Load and Save Barcode Recognition State from Stream**
***Aspose.BarCode for C++*** enables saving the barcode recognition state or loading it from streams using special functions *ExportToXml(Stream)* and *ImportFromXml(Stream)*, respectively. The target barcode image needs to be set explicitly using the group of properties called *SetBarCodeImage*. 