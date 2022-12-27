---
title: Mailmark 2D Barcodes
type: docs
description: "This article explains how to Generate and Read Royal Mail Mailmark 2D Barcodes using Aspose.BarCode for Python via .NET."
keywords: "Generate Mailmark Barcode, Royal Mail Mailmark Barcodes, Royal Mail Barcode, Aspose.BarCode, Generate Barcode in Python"
weight: 20
url: /python-net/mailmark-2D-barcode/
---

## **Overview**
Royal Mail *Mailmark* has been developed to encode postal and shipping information in the format defined in the *DataMatrix* standard. *Mailmark 2D* includes three types denoted as 7, 9, and 29; they differ from each other in terms of customer data capacity. Customer information is encoded in addition to the main barcode data in special predefined barcode fields. The amount of space to store customer data depends on the barcode type and the used encoding. This information can serve to describe print and scanning operations, identify items, or enable barcode scanning with smartphones.  

To perform data encoding, the *Mailmark 2D* standard uses the basic C40 character set (numerical digits, uppercase English letters, and the space character). All fields of information to be encoded in a *Mailmark 2D* barcode except customer data must be entered in the format compatible with the mentioned encoding standard. The customer information field does not require to comply with this encoding; however, using alternative encodings may affect the overall barcode data capacity.  
  
To work with *Mailmark 2D* barcodes in ***Aspose.BarCode for Python via .NET***, it is necessary to use class [*Mailmark2DCodetext*](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/mailmark2dcodetext).
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Generate Mailmark 2D Barcodes**
To generate *Mailmark 2D* barcodes, the barcode library provides class [*Mailmark2DCodetext*](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/mailmark2dcodetext) to specify barcode fields and class [*ComplexBarcodeGenerator*](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/complexbarcodegenerator) to generate barcodes. The [*Mailmark2DType*](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/mailmark2dtype) enumeration is used to select the type of a *Mailmark 2D* barcode to be generated.  
  
Sample *Mailmark 2D* barcodes demonstrated below have been created setting different *Mailmark 2D* types.
  
|Mailmark 2D|Type 7|Type 9|Type 29|
| :-: | :-: | :-: | :-: |
| |<img src="mailmark2dtype7.png">|<img src="mailmark2dtype9.png">|<img src="mailmark2dtype29.png">|
  
  
## **Read Mailmark 2D Barcodes**
To read and parse Royal Mail *Mailmark 2D* barcodes, first, it is required to create an instance of class [*BarCodeReader*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader) and set it to the value *DecodeType.DataMatrix*. Then, the obtained information can be parsed further in class [*ComplexCodetextReader*](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/complexcodetextreader) by calling the *try_decode_mailmark_2d(encoded_codetext)* method that returns an instance of [*Mailmark2DCodetext*](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/mailmark2dcodetext) with the decoded barcode data.  

  