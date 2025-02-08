---
title: Generate and Read Mailmark 4-State Barcodes in Java
linktitle: Mailmark 4-State Type
type: docs
description: "This article explains how to Generate and Read Royal Mail Mailmark 4-State Barcodes using Aspose.BarCode for Java"
keywords: Generate Mailmark Barcode, Royal Mail Mailmark Barcodes, Royal Mail Barcode, Aspose.BarCode, Generate Barcode Java
weight: 30
feedback: BARCODECOM
url: /java/mailmark-4state-barcodes/
aliases:
- /java/mailmark-4state-barcode/

---

## **Overview**
Royal Mail of the United Kingdom has introduced the *Mailmark 4-state* postal barcode standard to store postal and shipping data. Its specification is alike the *RM4SCC* symbology but requires using the specific data format and does not allow adding customer-specific data. The *Mailmark 4-state* symbology can be used to encode numerical characters, uppercase letters of the English alphabet, and space. To ensure data integrity and correct barcode recognition, *Mailmark 4-state* barcodes contain checksum controls and supports Reed-Solomon error correction.  
  
The Royal Mail *Mailmark 4-state* standard includes the following subtypes:
- Type L - allows encoding up to 26 digits; is applied to machine-readable Low Sort and Unsorted Retail and Access 70 services
- Type C - allows enconding up to 22 digits; is used for consolidated machine-readable Low Sort and Unsorted Retail and Access 70 services

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
  
To read and generate *Mailmark 4-state* barcode images, ***Aspose.BarCode for Java*** provides special class [*MailmarkCodetext*](https://reference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/MailmarkCodetext).

## **Generate Mailmark 4-State Barcodes**
Developers can create *Mailmark 4-state* barcodes in ***Aspose.BarCode for Java*** executing the following steps. First, an instance of class [*MailmarkCodetext*](https://reference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/MailmarkCodetext) needs to be created passing the data for encoding. Thereafter, the *generateBarCodeImage()* method of class [*ComplexBarcodeGenerator*](https://reference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/ComplexBarcodeGenerator) needs to be called to finalize barcode generation.    
  
<p align="center"><img src="mailmark4state.png"></p>
  
<!--The following code sample shows how to create *Mailmark 4-state* barcode images.
  
{{< highlight java>}}
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
{{< /highlight >}}-->


## **Read Mailmark 4-State Barcodes**
To recognize *Mailmark 4-state* barcode images through ***Aspose.BarCode for Java***, first, it is needed to generate an instance of class [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) setting it to *DecodeType.Mailmark*. Thereafter, barcode data has to be parsed using the *TryDecodeMailmark(java.lang.String encodedCodetext)* method of class [*ComplexCodetextReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/ComplexCodetextReader). This method returns an instance of class [*MailmarkCodetext*](https://reference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/MailmarkCodetext) with the decoded barcode data.  
  
<!--The following code sample explains how to decode *Mailmark 4-state* barcode images.
  
{{< highlight java>}}
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
{{< /highlight >}}-->