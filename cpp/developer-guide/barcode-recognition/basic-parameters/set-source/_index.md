---
title: Set Barcode Source
type: docs
description: "This Article Describes How to Set Barcode Source for Recognition"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Barcode in WPF Project, Aspose.BarCode, Read Barcode C#"
ai_search_scope: "barcode_cpp_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 10
feedback: BARCODECOM
url: /cpp/set-barcode-source/
aliases:
- /cpp/working-with-barcode-images/

---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**

In ***Aspose.BarCode for C++***, a source for barcode recognition can be defined in three different ways: as an image file, as a stream, or as a bitmap. Reading barcodes from files can be done using five supported image formats: BMP, PNG, JPEG, GIF, or TIFF. The implementation details for three possible modes are provided further. 

## **Read Barcodes from File**
To set the barcode recognition source as an image file, it is necessary to specify the full or relative path to this file in the [*BarCodeReader*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.bar_code_recognition.bar_code_reader/) constructor or call the *SetBarCodeImage* method to pass the path to the already existing object of [*BarCodeReader*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.bar_code_recognition.bar_code_reader/).  
  

## **Read Barcodes from Bitmap**
In ***Aspose.BarCode for C++***, it is possible to get a barcode image for reading in the form of a graphical object, namely, a bitmap. Bitmap objects are used to process images composed of pixel data. To set the recognition source as a bitmap, it is necessary to pass the created bitmap object to the [*BarCodeReader*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.bar_code_recognition.bar_code_reader/) constructor or the *SetBarCodeImage* method similarly to the case of using a raster image file.
  


## **Read Barcodes from Stream**
***Aspose.BarCode for C++*** enables the possibility to load the source barcode image from a stream (in a binary format) that is viewed as an abstraction of a byte sequence. In many cases, it may be convenient to set a recognition source as a stream object that is universal and can be accessed without a file system. In ***Aspose.BarCode for C++***, the source stream for barcode recognition can be passed to the [*BarCodeReader*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.bar_code_recognition.bar_code_reader/) constructor or the *SetBarCodeImage* method.
  
