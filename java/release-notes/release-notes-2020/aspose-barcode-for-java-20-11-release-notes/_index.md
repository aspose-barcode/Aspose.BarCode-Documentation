---
title: Aspose.BarCode for Java 20.11 Release Notes
type: docs
weight: 5
url: /java/aspose-barcode-for-java-20-11-release-notes/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Java 20.11](https://downloads.aspose.com/barcode/java/new-releases/aspose.barcode-for-java-20.11/).

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
- Added enum's field com.aspose.barcode.DataMatrixEncodeMode.EXTENDED_CODETEXT
- Added method com.aspose.barcode.generation.CaptionParameters.getNoWrap()
- Added method com.aspose.barcode.generation.CaptionParameters.setNoWrap(boolean)
- Added method com.aspose.barcode.generation.CodetextParameters.getNoWrap()
- Added method com.aspose.barcode.generation.CodetextParameters.setNoWrap(boolean)