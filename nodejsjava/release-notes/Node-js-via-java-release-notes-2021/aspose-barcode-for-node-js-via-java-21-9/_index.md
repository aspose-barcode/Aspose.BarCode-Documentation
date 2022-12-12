---
title: Aspose.BarCode for Node.js via Java 21.9
type: docs
weight: 930
url: /nodejsjava/aspose-barcode-for-node-js-via-java-21-9/
aliases:
- /java/aspose-barcode-for-node-js-via-java-21-9/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Node.js via Java 21.9](https://downloads.aspose.com/barcode/nodejs/new-releases/aspose.barcode-for-node.js-via-java-21.9/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37826|Refactor BarcodeReader interface in data unpacking area|Enhancement|
|BARCODENET-37851|Throw Exception on timeout exceeding|Enhancement|

## **Public API and Backward Incompatible Changes**
The changes that were made in Recognition.js
- Added function BarCodeReader.getBarcodeSettings()
- Added class BarcodeSettings
- Added function BarcodeSettings.getChecksumValidation()
- Added function BarcodeSettings.setChecksumValidation(int)
- Added function BarcodeSettings.getStripFNC()
- Added function BarcodeSettings.setStripFNC(boolean)
- Added function BarcodeSettings.getDetectEncoding()
- Added function BarcodeSettings.setDetectEncoding(boolean)
- Added function BarcodeSettings.getAustraliaPost(): AustraliaPostSettings
- Added class AustraliaPostSettings
- Added function AustraliaPostSettings.getCustomerInformationInterpretingType()
- Added function AustraliaPostSettings.setCustomerInformationInterpretingType(int)
- Added function AustraliaPostSettings.getIgnoreEndingFillingPatternsForCTable()
- Added function AustraliaPostSettings.setIgnoreEndingFillingPatternsForCTable(boolean)
- Added class RecognitionAbortedException
- Added function RecognitionAbortedException.constructor(String, int)
- Added function RecognitionAbortedException.getExecutionTime()
- Added function RecognitionAbortedException.setExecutionTime(int)
