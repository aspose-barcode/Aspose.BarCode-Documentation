---
title: Aspose.BarCode for Node.js via Java 21.12
type: docs
weight: 890
url: /java/aspose-barcode-for-node-js-via-java-21-12/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Node.js via Java 21.12](https://downloads.aspose.com/barcode/nodejs/new-releases/aspose.barcode-for-node.js-via-java-21.12/).

{{% /alert %}}
|BARCODENET-37656|[Epic] Add support of Royal Mail Mailmark 4-state C and L barcodes decoding|Enhancement|
|BARCODENET-37655|[Epic] Add support of Royal Mail Mailmark 4-state C and L barcodes encoding|Enhancement|
|BARCODENET-37842|[Epic] Implement EMF encoder for BarcodeGenerator|Enhancement|

## **Public API and Backward Incompatible Changes**

- Added enum's field EncodeTypes.MAILMARK
- Added function ComplexBarcode.ComplexCodetextReader.tryDecodeMailmark2D(String)
- Added class ComplexBarcode.MailmarkCodetext
- Added constructor ComplexBarcode.MailmarkCodetext.#ctor
- Added function ComplexBarcode.MailmarkCodetext.getFormat():int
- Added function ComplexBarcode.MailmarkCodetext.setFormat(int):void
- Added function ComplexBarcode.MailmarkCodetext.getVersionID():int
- Added function ComplexBarcode.MailmarkCodetext.setVersionID(int):void
- Added function ComplexBarcode.MailmarkCodetext.getClass_():String
- Added function ComplexBarcode.MailmarkCodetext.setClass(String):void
- Added function ComplexBarcode.MailmarkCodetext.getSupplychainID():int
- Added function ComplexBarcode.MailmarkCodetext.setSupplychainID(int):void
- Added function ComplexBarcode.MailmarkCodetext.getItemID():int
- Added function ComplexBarcode.MailmarkCodetext.setItemID(int):void
- Added function ComplexBarcode.MailmarkCodetext.getDestinationPostCodePlusDPS():String
- Added function ComplexBarcode.MailmarkCodetext.setDestinationPostCodePlusDPS(String):void
- Added function ComplexBarcode.MailmarkCodetext.getConstructedCodetext():String
- Added function ComplexBarcode.MailmarkCodetext.initFromString(String):void
- Added function ComplexBarcode.MailmarkCodetext.getBarcodeType():number
- Added enum's field DecodeType.MAILMARK
