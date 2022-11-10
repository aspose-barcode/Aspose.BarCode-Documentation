---
title: Mailmark 4-State Barcodes
type: docs
description: "This article explains how to Generate and Read Royal Mail Mailmark 4-State Barcodes using Aspose.BarCode for Python via .NET"
keywords: "Generate Mailmark Barcode, Royal Mail Mailmark Barcodes, Royal Mail Barcode, Aspose.BarCode, Generate Barcode in Python"
weight: 30
url: /python-net/mailmark-4state-barcode/
---

## **Overview**
Royal Mail of the United Kingdom has created the *Mailmark 4-state* postal type to store data about postal and shipping transactions. Its specification is similar to the *RM4SCC* standard but uses a fixed data format and does not support customer-specific information. *Mailmark 4-state* encodes numerical digits, uppercase English letters, and space. It enables checksum controls and Reed-Solomon error correction.  
  
*Mailmark 4-state* has the following subtypes:
- Type L - encodes 26 characters and is intended for machine-readable Low Sort and Unsorted Retail and Access 70 services
- Type C - encodes 22 characters and is intended for consolidated machine-readable Low Sort and Unsorted Retail and Access 70 services

The barcode library provides class [*MailmarkCodetext*](https://reference.aspose.com/barcode/python-net/aspose.barcode.complexbarcode/mailmarkcodetext) to work with this type.


{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
  
## **Generate Mailmark 4-State Barcodes**
To generate a *Mailmark 4-state* barcode in ***Aspose.BarCode for .NET***, first, it is necessary to create an instance of class [*MailmarkCodetext*](https://reference.aspose.com/barcode/python-net/aspose.barcode.complexbarcode/mailmarkcodetext) and enter the information to be encoded. Then, class [*ComplexBarcodeGenerator*](https://reference.aspose.com/barcode/python-net/aspose.barcode.complexbarcode/complexbarcodegenerator) is used to complete barcode generation.    
  
<p align="center"><img src="mailmark4state.png"></p>

## **Read Mailmark 4-State Barcodes**
To read and parse Royal Mail *Mailmark 4-state* barcodes in ***Aspose.BarCode for .NET***, it is necessary to create an instance of class [*BarCodeReader*](https://reference.aspose.com/barcode/python-net/aspose.barcode.barcoderecognition/barcodereader) and set it to the value *DecodeType.Mailmark*. After that, the fetched data must be parsed further using class [*ComplexCodetextReader*](https://reference.aspose.com/barcode/python-net/aspose.barcode.complexbarcode/complexcodetextreader) by calling the *try_decode_mailmark(encoded_codetext)* method that returns an instance of [*MailmarkCodetext*](https://reference.aspose.com/barcode/python-net/aspose.barcode.complexbarcode/mailmarkcodetext) with the decoded barcode contents.  
  