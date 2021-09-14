---
title: Aspose.BarCode for PHP via Java 21.9
type: docs
weight: 18
url: /java/aspose-barcode-for-php-via-java-21-9/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for PHP via Java 21.9](https://downloads.aspose.com/barcode/phpjava/new-releases/aspose.barcode-for-php-via-java-21.9/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37826|Refactor BarcodeReader interface in data unpacking area|Enhancement|
|BARCODENET-37851|Throw Exception on timeout exceeding|Enhancement|

## **Public API and Backward Incompatible Changes**
The changes that were made in Recognition.php
- Added function BarCodeReader->getBarcodeSettings():BarcodeSettings
- Added class BarcodeSettings
- Added function BarcodeSettings->getChecksumValidation(): int
- Added function BarcodeSettings->setChecksumValidation(int):void
- Added function BarcodeSettings->getStripFNC():bool
- Added function BarcodeSettings->setStripFNC(bool):void
- Added function BarcodeSettings->getDetectEncoding(): bool
- Added function BarcodeSettings->setDetectEncoding(bool):void
- Added function BarcodeSettings->getAustraliaPost(): AustraliaPostSettings
- Added class AustraliaPostSettings
- Added function AustraliaPostSettings->getCustomerInformationInterpretingType():int
- Added function AustraliaPostSettings->setCustomerInformationInterpretingType(int):void
- Added function AustraliaPostSettings->getIgnoreEndingFillingPatternsForCTable():bool
- Added function AustraliaPostSettings->setIgnoreEndingFillingPatternsForCTable(bool):void
- Added class RecognitionAbortedException
- Added function RecognitionAbortedException->__construct(string, int)
- Added function RecognitionAbortedException->getExecutionTime():int
- Added function RecognitionAbortedException->setExecutionTime(int):void
