---
title: Aspose.BarCode for PHP via Java 21.2
type: docs
weight: 28
url: /java/aspose-barcode-for-php-via-java-21-2/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for PHP via Java 21.2](https://downloads.aspose.com/barcode/php/new-releases/aspose.barcode-for-php-via-java-21.2/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37487|Investigate extending of Macro PDF417 encoder with optional fields|Enhancement|
|BARCODENET-37730|Barcode is not recognized|Bug|

# **Public API and Backward Incompatible Changes**
- Added function Generator->Pdf417Parameters->setPdf417MacroECIEncoding(int):void
- Added function Generator->Pdf417Parameters->getPdf417MacroECIEncoding():int
- Added function Generator->Pdf417Parameters->setPdf417MacroFileName(string):void
- Added function Generator->Pdf417Parameters->getPdf417MacroFileName():string
- Added function Generator->Pdf417Parameters->setPdf417MacroTimeStamp(DateTime):void
- Added function Generator->Pdf417Parameters->getPdf417MacroTimeStamp():DateTime
- Added function Generator->Pdf417Parameters->setPdf417MacroSender(string):void
- Added function Generator->Pdf417Parameters->getPdf417MacroSender():string
- Added function Generator->Pdf417Parameters->setPdf417MacroAddressee(string):void
- Added function Generator->Pdf417Parameters->getPdf417MacroAddressee():string
- Added function Generator->Pdf417Parameters->setPdf417MacroFileSize(int):void
- Added function Generator->Pdf417Parameters->getPdf417MacroFileSize():int
- Added function Generator->Pdf417Parameters->setPdf417MacroChecksum(int):void
- Added function Generator->Pdf417Parameters->getPdf417MacroChecksum():int
- Added function Reader->Pdf417ExtendedParameters->getMacroPdf417FileName():string
- Added function Reader->Pdf417ExtendedParameters->getMacroPdf417FileSize():int
- Added function Reader->Pdf417ExtendedParameters->getMacroPdf417Sender():string
- Added function Reader->Pdf417ExtendedParameters->getMacroPdf417Addressee():string
- Added function Reader->Pdf417ExtendedParameters->getMacroPdf417TimeStamp():DateTime
- Added function Reader->Pdf417ExtendedParameters->getMacroPdf417Checksum():int
- Added function Reader->QualitySettings->setCheckMore1DVariants(bool):void
- Added function Reader->QualitySettings->getCheckMore1DVariants():bool