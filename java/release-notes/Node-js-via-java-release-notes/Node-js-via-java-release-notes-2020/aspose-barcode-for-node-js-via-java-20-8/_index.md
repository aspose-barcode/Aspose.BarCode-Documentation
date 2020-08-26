---
title: Aspose.BarCode for Node.js via Java 20.8
type: docs
weight: 70
url: /java/aspose-barcode-for-node-js-via-java-20-8/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Node.js via Java 20.8](https://downloads.aspose.com/barcode/nodejs/new-releases/aspose.barcode-for-node.js-via-java-20.8/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37560|Implement Reader Initialization mode for Pdf417 and MacroPdf417|Enhancement|
|BARCODENET-37489|Barcode values were not read correctly|Bug|
|BARCODENET-37554|Unable to read barcodes in the image|Bug|

## **Public API and Backward Incompatible Changes**
- added function Reader.QualitySettings.getReadTinyBarcodes:boolean
- added function Reader.QualitySettings.setReadTinyBarcodes(boolean)
- added function Generator.Pdf417Parameters.isReaderInitialization:boolean
- added function Generator.Pdf417Parameters.setReaderInitialization(boolean)