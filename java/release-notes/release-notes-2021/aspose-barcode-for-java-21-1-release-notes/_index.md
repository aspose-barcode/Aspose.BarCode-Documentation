---
title: Aspose.BarCode for Java 21.1 Release Notes
type: docs
weight: 1000
url: /java/aspose-barcode-for-java-21-1-release-notes/
---

{{% alert color="primary" %}}

This page contains release notes information for [Aspose.BarCode for Java 21.1](https://downloads.aspose.com/barcode/java/new-releases/aspose.barcode-for-java-21.1/).

{{% /alert %}}
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37469|Add Structured Append support to QR encoder|Enhancement|
|BARCODENET-37470|Add Kanji encoding to QR encoder|Enhancement|
|BARCODENET-37713|BarCodeResult.Region.Angle direction not returned properly|Bug|
|BARCODENET-37702|Zero byte EMF file created in Linux|Bug|
|BARCODENET-37719|MicroPDF417 hungs in Auto mode|Bug|



## **Public API and Backward Incompatible Changes**
- Added method com.aspose.barcode.generation.QrParameters.getStructuredAppend():QrStructuredAppendParameters
- Added method com.aspose.barcode.generation.QrParameters.setStructuredAppend(QrStructuredAppendParameters):void
- Added class com.aspose.barcode.generation.QrStructuredAppendParameters
- Added method com.aspose.barcode.generation.QrStructuredAppendParameters.getParityByte():byte
- Added method com.aspose.barcode.generation.QrStructuredAppendParameters.setParityByte(byte):void
- Added method com.aspose.barcode.generation.QrStructuredAppendParameters.getSequenceIndicator():int
- Added method com.aspose.barcode.generation.QrStructuredAppendParameters.setSequenceIndicator(int):void
- Added method com.aspose.barcode.generation.QrStructuredAppendParameters.getTotalCount():int
- Added method com.aspose.barcode.generation.QrStructuredAppendParameters.setTotalCount(int):void
