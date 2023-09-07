---
title: Generate and Read Mailmark 4-State Barcodes in C#
type: docs
description: "This article explains how to Generate and Read Royal Mail Mailmark 4-State Barcodes using Aspose.BarCode for .NET"
keywords: "Generate Mailmark Barcode, Royal Mail Mailmark Barcodes, Royal Mail Barcode, Aspose.BarCode, Generate Barcode C#"
weight: 30
url: /net/mailmark-4state-barcodes/
aliases:
- /net/mailmark-4state-barcode/
---

## **Overview**
The *Mailmark 4-state* postal symbology has been introduced by Royal Mail of the United Kingdom to encode information about postal and shipping operations. It has a specification similar to the *RM4SCC* standard but implies using a strictly fixed data format and does not provide extra space for customer-specific information. The *Mailmark 4-state* barcode type allows encoding numerical digits, uppercase English letters, and space. Moreover, *Mailmark 4-state* barcodes include a checksum and specific information for Reed-Solomon error correction.  
  
The Royal Mail *Mailmark 4-state* enables the following barcode types:
- Type L - encodes 26 characters and is intended for machine-readable Low Sort and Unsorted Retail and Access 70 services
- Type C - encodes 22 characters and is intended for consolidated machine-readable Low Sort and Unsorted Retail and Access 70 services

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
  
***Aspose.BarCode for .NET*** defines class [*MailmarkCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/mailmarkcodetext) to work with this symbology.

## **Generate Mailmark 4-State Barcode**
To generate a *Mailmark 4-state* barcode in ***Aspose.BarCode for .NET***, first, it is necessary to create an instance of class [*MailmarkCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/mailmarkcodetext) and enter the information to be encoded. Then, class [*ComplexBarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexbarcodegenerator) is used to complete barcode generation.    
  
<p align="center"><img src="mailmark4state.png"></p>
  
The following code snippet explains how to generate *Mailmark 4-state* barcodes.
  
{{< highlight csharp>}}
//create Mailmark 4-State Barcode
MailmarkCodetext mailmarkCode = new MailmarkCodetext();
mailmarkCode.Format = 4;
mailmarkCode.VersionID = 1;
mailmarkCode.Class = "0";
mailmarkCode.SupplychainID = 384224;
mailmarkCode.ItemID = 16563762;
mailmarkCode.DestinationPostCodePlusDPS = "EF61AH8T ";

//encode Mailmark 4-State Barcode
ComplexBarcodeGenerator generator = new ComplexBarcodeGenerator(mailmarkCode);
generator.Parameters.Barcode.XDimension.Pixels = 4;
generator.Save($"{path}Mailmark4State.png");
{{< /highlight >}}


## **Read Mailmark 4-State Barcode**
To read and parse Royal Mail *Mailmark 4-state* barcodes in ***Aspose.BarCode for .NET***, it is necessary to create an instance of class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) and set it to the value *DecodeType.Mailmark*. After that, the fetched data must be parsed further using class [*ComplexCodetextReader*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexcodetextreader) by calling the [*TryDecodeMailmark*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexcodetextreader/methods/trydecodemailmark) method that returns an instance of [*MailmarkCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/mailmarkcodetext) with the decoded barcode contents.  
  
The following code snippet is given to demonstrate how to read *Mailmark 4-state* barcodes.
  
{{< highlight csharp>}}
//create Mailmark 4-State Barcode
MailmarkCodetext mailmarkCode = new MailmarkCodetext();
mailmarkCode.Format = 4;
mailmarkCode.VersionID = 1;
mailmarkCode.Class = "0";
mailmarkCode.SupplychainID = 384224;
mailmarkCode.ItemID = 16563762;
mailmarkCode.DestinationPostCodePlusDPS = "EF61AH8T ";

//encode Mailmark 4-State Barcode
ComplexBarcodeGenerator generator = new ComplexBarcodeGenerator(mailmarkCode);
generator.Parameters.Barcode.XDimension.Pixels = 4;
generator.Save($"{path}Mailmark4State.png");
{{< /highlight >}}