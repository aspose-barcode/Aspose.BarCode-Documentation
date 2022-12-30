---
title: Aspose.BarCode for PHP via Java 22.11
type: docs
weight: 15
url: /phpjava/aspose-barcode-for-php-via-java-22-11/
aliases:
- /java/aspose-barcode-for-php-via-java-22-11/
---

{{% alert color="primary" %}}
This page contains release notes information for [Aspose.BarCode for PHP via Java 22.11](https://downloads.aspose.com/barcode/php/new-releases/aspose.barcode-for-php-via-java-22.11/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-38034|Incorrect File ID field encoding in MacroPdf417|Bug|
|BARCODENET-38344|QR/GS1QR generation throws exception in AutoSizeMode.Nearest|Bug|
|BARCODEPHP-459|Configure the launching embedded Java server|Enhancement|

## **Public API and Backward Incompatible Changes**

- Added class Generation->Pdf417MacroTerminator
- Added const Generation->Pdf417MacroTerminator::AUTO
- Added const Generation->Pdf417MacroTerminator::NONE
- Added const Generation->Pdf417MacroTerminator::SET
- Added function Generation->Pdf417Parameters->getPdf417MacroTerminator():int
- Added function Generation->Pdf417Parameters->setPdf417MacroTerminator(int):void
- Added function Recognition->Pdf417ExtendedParameters->getMacroPdf417Terminator():boolean

- Default value for Generation->CodetextParameters->setLocation has been changed to CodeLocation::NONE for all **2D** barcode symbologies.