---
title: Aspose.BarCode for Python via Java 21.9
type: docs
weight: 910
url: /java/aspose-barcode-for-python-via-java-21-9/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Python via Java 21.9](https://downloads.aspose.com/barcode/pythonjava/new-releases/aspose.barcode-for-python-via-java-21.9/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37826|Refactor BarcodeReader interface in data unpacking area|Enhancement|
|BARCODENET-37851|Throw Exception on timeout exceeding|Enhancement|

## **Public API and Backward Incompatible Changes**
The changes that were made in Recognition.py
- Added function BarCodeReader.getBarcodeSettings()
- Added class BarcodeSettings
- Added function BarcodeSettings.getChecksumValidation():ChecksumValidation
- Added function BarcodeSettings.setChecksumValidation(ChecksumValidation)
- Added function BarcodeSettings.getStripFNC():boolean
- Added function BarcodeSettings.setStripFNC(boolean)
- Added function BarcodeSettings.getDetectEncoding():boolean
- Added function BarcodeSettings.setDetectEncoding(boolean)
- Added function BarcodeSettings.getAustraliaPost(): AustraliaPostSettings
- Added class AustraliaPostSettings
- Added function AustraliaPostSettings.getCustomerInformationInterpretingType():CustomerInformationInterpretingType
- Added function AustraliaPostSettings.setCustomerInformationInterpretingType(CustomerInformationInterpretingType)
- Added function AustraliaPostSettings.getIgnoreEndingFillingPatternsForCTable():boolean
- Added function AustraliaPostSettings.setIgnoreEndingFillingPatternsForCTable(boolean)
- Added class RecognitionAbortedException
- Added function RecognitionAbortedException.constructor(String, int)
- Added function RecognitionAbortedException.getExecutionTime()
- Added function RecognitionAbortedException.setExecutionTime(int)
