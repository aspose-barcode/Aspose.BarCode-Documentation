---
title: Aspose.BarCode for Python via Java 21.2
type: docs
weight: 990
url: /java/aspose-barcode-for-python-via-java-21-2/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Python via Java 21.2](https://downloads.aspose.com/barcode/pythonjava/new-releases/aspose.barcode-for-python-via-java-21.2/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37487|Investigate extending of Macro PDF417 encoder with optional fields|Enhancement|
|BARCODENET-37730|Barcode is not recognized|Bug|

## **Public API and Backward Incompatible Changes**
- Added function Generation.Pdf417Parameters.setPdf417MacroECIEncoding(int)
- Added function Generation.Pdf417Parameters.getPdf417MacroECIEncoding():int
- Added function Generation.Pdf417Parameters.setPdf417MacroFileName(str)
- Added function Generation.Pdf417Parameters.getPdf417MacroFileName():str
- Added function Generation.Pdf417Parameters.setPdf417MacroTimeStamp(datetime)
- Added function Generation.Pdf417Parameters.getPdf417MacroTimeStamp():datetime
- Added function Generation.Pdf417Parameters.setPdf417MacroSender(str)
- Added function Generation.Pdf417Parameters.getPdf417MacroSender():str
- Added function Generation.Pdf417Parameters.setPdf417MacroAddressee(str)
- Added function Generation.Pdf417Parameters.getPdf417MacroAddressee():str
- Added function Generation.Pdf417Parameters.setPdf417MacroFileSize(int)
- Added function Generation.Pdf417Parameters.getPdf417MacroFileSize():int
- Added function Generation.Pdf417Parameters.setPdf417MacroChecksum(int)
- Added function Generation.Pdf417Parameters.getPdf417MacroChecksum():int
- Added function Recognition.Pdf417ExtendedParameters.getMacroPdf417FileName():str
- Added function Recognition.Pdf417ExtendedParameters.getMacroPdf417FileSize():int
- Added function Recognition.Pdf417ExtendedParameters.getMacroPdf417Sender():str
- Added function Recognition.Pdf417ExtendedParameters.getMacroPdf417Addressee():str
- Added function Recognition.Pdf417ExtendedParameters.getMacroPdf417TimeStamp():datetime
- Added function Recognition.Pdf417ExtendedParameters.getMacroPdf417Checksum():int
- Added function Recognition.QualitySettings.setCheckMore1DVariants(bool)
- Added function Recognition.QualitySettings.getCheckMore1DVariants():bool