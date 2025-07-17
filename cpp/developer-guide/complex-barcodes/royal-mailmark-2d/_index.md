---
title: Generate and Read Mailmark 2D Barcodes in C++
linktitle: Mailmark 2D
type: docs
description: "This article explains how to Generate and Read Royal Mail Mailmark 2D Barcodes using Aspose.BarCode for C++"
keywords: "Generate Mailmark Barcode, Royal Mail Mailmark Barcodes, Royal Mail Barcode, Aspose.BarCode, Generate Barcode C++"
ai_search_scope: "barcode_cpp_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 20
feedback: BARCODECOM
url: /cpp/mailmark-2D-barcodes/
---

## **Overview**
The Royal Mail *Mailmark* symbology has been developed to encode postal and shipping information in the format defined in the *DataMatrix* standard. The *Mailmark 2D* symbology includes three types denoted as 7, 9, and 29; they differ from each other in terms of customer data capacity. Customer information is encoded in addition to the main barcode data in special predefined barcode fields. The amount of space to store customer data depends on the barcode type and the used encoding. This information can serve to describe print and scanning operations, identify items, or enable barcode scanning with smartphones.  

To perform data encoding, the *Mailmark 2D* standard uses the basic C40 character set (numerical digits, uppercase English letters, and the space character). All fields of information to be encoded in a *Mailmark 2D* barcode except customer data must be entered in the format compatible with the mentioned encoding standard. The customer information field does not require to comply with this encoding; however, using alternative encodings may affect the overall barcode data capacity.  
  
To work with *Mailmark 2D* barcodes in ***Aspose.BarCode for C++***, it is necessary to use class *Mailmark2DCodetext*.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Generate Mailmark 2D Barcodes**
To generate *Mailmark 2D* barcodes, ***Aspose.BarCode for C++*** provides class *Mailmark2DCodetext* to specify barcode fields and class [*ComplexBarcodeGenerator*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.complex_barcode.complex_barcode_generator/) to generate barcodes. The *Mailmark2DType* enumeration is used to select the type of a *Mailmark 2D* barcode to be generated.  
  
Sample *Mailmark 2D* barcodes demonstrated below have been created setting different *Mailmark 2D* types.
  
|<p align="center">**Mailmark 2D**</p>|<p align="center">**Type 7**</p>|<p align="center">**Type 9**</p>|<p align="center">**Type 29**</p>|
| :-: | :-: | :-: | :-: |
| |<img src="mailmark2dtype7.png">|<img src="mailmark2dtype9.png">|<img src="mailmark2dtype29.png">|
  

  
## **Read Mailmark 2D Barcodes**
To read and parse Royal Mail *Mailmark 2D* barcodes in ***Aspose.BarCode for C++***, first, it is required to create an instance of class *BarCodeReader* and set it to the value *DecodeType.DataMatrix*. Then, the obtained information can be parsed further in class [*ComplexCodetextReader*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.complex_barcode.complex_codetext_reader/) by calling the *TryDecodeMailmark2D* method that returns an instance of *Mailmark2DCodetext* with the decoded barcode data.  
  