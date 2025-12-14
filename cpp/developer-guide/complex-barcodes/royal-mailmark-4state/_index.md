---
title: Generate and Read Mailmark 4-State Barcodes in C++
linktitle: Mailmark 4-State
type: docs
description: "This article explains how to Generate and Read Royal Mail Mailmark 4-State Barcodes using Aspose.BarCode for C++"
keywords: "Generate Mailmark Barcode, Royal Mail Mailmark Barcodes, Royal Mail Barcode, Aspose.BarCode, Generate Barcode C++"
ai_search_scope: "barcode_cpp_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 30
feedback: BARCODECOM
url: /cpp/mailmark-4state-barcodes/
---

## **Overview**
The *Mailmark 4-state* postal symbology has been introduced by Royal Mail of the United Kingdom to encode information about postal and shipping operations. It has a specification similar to the *RM4SCC* standard but implies using a strictly fixed data format and does not provide extra space for customer-specific information. The *Mailmark 4-state* barcode type allows encoding numerical digits, uppercase English letters, and space. Moreover, *Mailmark 4-state* barcodes include a checksum and specific information for Reed-Solomon error correction.  
  
The Royal Mail *Mailmark 4-state* enables the following barcode types:
- Type L - encodes 26 characters and is intended for machine-readable Low Sort and Unsorted Retail and Access 70 services
- Type C - encodes 22 characters and is intended for consolidated machine-readable Low Sort and Unsorted Retail and Access 70 services

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
  
***Aspose.BarCode for C++*** defines class *MailmarkCodetext* to work with this symbology.

## **Generate Mailmark 4-State Barcode**
To generate a *Mailmark 4-state* barcode in ***Aspose.BarCode for C++***, first, it is necessary to create an instance of class *MailmarkCodetext* and enter the information to be encoded. Then, class [*ComplexBarcodeGenerator*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.complex_barcode.complex_barcode_generator/) is used to complete barcode generation.    
  
<p align="center"><img src="mailmark4state.png"></p>
  
## **Read Mailmark 4-State Barcode**
To read and parse Royal Mail *Mailmark 4-state* barcodes in ***Aspose.BarCode for C++***, it is necessary to create an instance of class *BarCodeReader* and set it to the value *DecodeType.Mailmark*. After that, the fetched data must be parsed further using class [*ComplexCodetextReader*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.complex_barcode.complex_codetext_reader/) by calling the *TryDecodeMailmark* method that returns an instance of *MailmarkCodetext* with the decoded barcode contents.  
  