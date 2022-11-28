---
title: Aspose.BarCode for PHP via Java 21.12
type: docs
weight: 10
url: /java/aspose-barcode-for-php-via-java-21-12/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for PHP via Java 21.12](https://downloads.aspose.com/barcode/php/new-releases/aspose.barcode-for-php-via-java-21.12/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37656|Add support of Royal Mail Mailmark 4-state C and L barcodes decoding|Enhancement|
|BARCODENET-37655|Add support of Royal Mail Mailmark 4-state C and L barcodes encoding|Enhancement|
|BARCODENET-37842|Implement EMF encoder for BarcodeGenerator|Enhancement|

## **Public API and Backward Incompatible Changes**

- Added const Generation.EncodeTypes.MAILMARK
- Added function ComplexBarcode.ComplexCodetextReader::tryDecodeMailmark(String)
- Added class ComplexBarcode.MailmarkCodetext
- Added constructor ComplexBarcode.MailmarkCodetext.#ctor
- Added function ComplexBarcode.MailmarkCodetext.getFormat():number
- Added function ComplexBarcode.MailmarkCodetext.setFormat(number):void
- Added function ComplexBarcode.MailmarkCodetext.getVersionID():number
- Added function ComplexBarcode.MailmarkCodetext.setVersionID(number):void
- Added function ComplexBarcode.MailmarkCodetext.getClass_():String
- Added function ComplexBarcode.MailmarkCodetext.setClass(String):void
- Added function ComplexBarcode.MailmarkCodetext.getSupplychainID():number
- Added function ComplexBarcode.MailmarkCodetext.setSupplychainID(number):void
- Added function ComplexBarcode.MailmarkCodetext.getItemID():number
- Added function ComplexBarcode.MailmarkCodetext.setItemID(number):void
- Added function ComplexBarcode.MailmarkCodetext.getDestinationPostCodePlusDPS():String
- Added function ComplexBarcode.MailmarkCodetext.setDestinationPostCodePlusDPS(String):void
- Added function ComplexBarcode.MailmarkCodetext.getConstructedCodetext():String
- Added function ComplexBarcode.MailmarkCodetext.initFromString(String):void
- Added function ComplexBarcode.MailmarkCodetext.getBarcodeType():number
- Added enum's field DecodeType.MAILMARK
