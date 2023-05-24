---
title: Aspose.BarCode for PHP via Java 23.4
type: docs
weight: 9700
url: /phpjava/aspose-barcode-for-php-via-java-23-4/
aliases:
- /java/aspose-barcode-for-php-via-java-23-4/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for PHP via Java 23.4](https://downloads.aspose.com/barcode/php/new-releases/aspose.barcode-for-php-via-java-23.4/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-38360|Add AntiAlias to barcode properties|Enhancement|
|BARCODENET-38322|Remove obsolete properties and warnings|Enhancement|
|BARCODENET-36917|Investigate multithreading addition to the Datamatrix region detection algorithms|Enhancement|


## **Public API and Backward Incompatible Changes**
The following API was added:
- Generation->BaseGenerationParameters->setUseAntiAlias(bool)
- Generation->BaseGenerationParameters->getUseAntiAlias():bool

The following obsolete API was removed:
- Generation->BarcodeParameters->setAutoSizeMode(AutoSizeMode)
- Generation->BarcodeParameters->getAutoSizeMode():AutoSizeMode
- Generation->BarcodeParameters->setBarCodeHeight(Unit)
- Generation->BarcodeParameters->getBarCodeHeight():Unit
- Generation->BarcodeParameters->setBarCodeWidth(Unit)
- Generation->BarcodeParameters->getBarCodeWidth():Unit
- Generation->BarcodeParameters->setForeColor(Color)
- Generation->BarcodeParameters->getForeColor():Color
- Recognition->BarCodeReader->setChecksumValidation(ChecksumValidation)
- Recognition->BarCodeReader->setChecksumValidation(int)
- Recognition->BarCodeReader->getChecksumValidation():ChecksumValidation
- Recognition->BarCodeReader->setStripFNC(bool)
- Recognition->BarCodeReader->getStripFNC():bool
- Recognition->BarCodeReader->setCustomerInformationInterpretingType(CustomerInformationInterpretingType)
- Recognition->BarCodeReader->setCustomerInformationInterpretingType(int)
- Recognition->BarCodeReader->getCustomerInformationInterpretingType():CustomerInformationInterpretingType
- Recognition->BarCodeReader->getDetectEncoding():bool
- Recognition->BarCodeReader->setDetectEncoding(bool)