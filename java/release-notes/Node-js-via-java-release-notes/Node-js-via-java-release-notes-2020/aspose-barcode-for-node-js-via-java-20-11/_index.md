---
title: Aspose.BarCode for Node.js via Java 20.11
type: docs
weight: 49
url: /java/aspose-barcode-for-node-js-via-java-20-11/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Node.js via Java 20.11](https://downloads.aspose.com/barcode/nodejs/new-releases/aspose.barcode-for-node.js-via-java-20.11/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37636 |Investigate addition of NoWrap mode to BarcodeGenerator text fields|Enhancement|
|BARCODENET-37653 |Add encodation scheme selector to DataMatrix codetext|Enhancement|
|BARCODENET-37615 |Investigate and fix Databar Expanded recognition|Bug|
|BARCODENET-37659 |PDF417 barcode cannot be generated with text having apostrophe|Bug|
|BARCODENET-37658 |Incorrect CodeText size interpolation with low height images|Bug|


## **Public API and Backward Incompatible Changes**
- Added enum's field Generator.DataMatrixEncodeMode.EXTENDED_CODETEXT
- Added function Generator.CaptionParameters.getNoWrap():boolean
- Added function Generator.CaptionParameters.setNoWrap(boolean)
- Added function Generator.CodetextParameters.getNoWrap():boolean
- Added function Generator.CodetextParameters.setNoWrap(boolean)
