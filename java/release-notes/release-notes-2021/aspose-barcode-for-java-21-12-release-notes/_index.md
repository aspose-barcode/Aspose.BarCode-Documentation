---
title: Aspose.BarCode for Java 21.12 Release Notes
type: docs
weight: 890
url: /java/aspose-barcode-for-java-21-12-release-notes/
---

{{% alert color="primary" %}}

This page contains release notes information for [Aspose.BarCode for Java 21.12](https://downloads.aspose.com/barcode/java/new-releases/aspose.barcode-for-java-21.12/).

{{% /alert %}}
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37656|[Epic] Add support of Royal Mail Mailmark 4-state C and L barcodes decoding|Enhancement|
|BARCODENET-37655|[Epic] Add support of Royal Mail Mailmark 4-state C and L barcodes encoding|Enhancement|
|BARCODENET-37842|[Epic] Implement EMF encoder for BarcodeGenerator|Enhancement|

## **Public API and Backward Incompatible Changes**

- Added field com.aspose.barcode.generation.EncodeTypes.Mailmark
- Added method com.aspose.barcode.complexbarcode.ComplexCodetextReader.tryDecodeMailmark(String)
- Added class com.aspose.barcode.complexbarcode.MailmarkCodetext
- Added constructor com.aspose.barcode.complexbarcode.MailmarkCodetext.#ctor
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.getFormat():int
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.setFormat(int):void
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.getVersionID():int
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.setVersionID(int):void
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.getClass():String
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.setClass(String):void
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.getSupplychainID():int
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.setSupplychainID(int):void
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.getItemID():int
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.setItemID(int):void
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.getDestinationPostCodePlusDPS():String
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.setDestinationPostCodePlusDPS(String):void
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.getConstructedCodetext():String
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.initFromString(String):void
- Added method com.aspose.barcode.complexbarcode.MailmarkCodetext.getBarcodeType():BaseEncodeType
- Added field com.aspose.barcode.barcoderecognition.DecodeType.MAILMARK

