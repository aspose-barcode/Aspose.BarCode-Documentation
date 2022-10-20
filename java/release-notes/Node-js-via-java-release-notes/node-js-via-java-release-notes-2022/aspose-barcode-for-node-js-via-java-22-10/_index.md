---
title: Aspose.BarCode for Node.js via Java 22.10
type: docs
weight: 920
url: /java/aspose-barcode-for-node-js-via-java-22-10/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Node.js via Java 22.10](https://downloads.aspose.com/barcode/nodejs/new-releases/aspose.barcode-for-node.js-via-java-22.10/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-38034|Incorrect File ID field encoding in MacroPdf417|Bug|
|BARCODENET-38344|QR/GS1QR generation throws exception in AutoSizeMode.Nearest|Bug|

## **Public API and Backward Incompatible Changes**

- Added class Generation.Pdf417MacroTerminator
- Added const Generation.Pdf417MacroTerminator.AUTO
- Added const Generation.Pdf417MacroTerminator.NONE
- Added const Generation.Pdf417MacroTerminator.SET
- Added function Generation.Pdf417Parameters.getPdf417MacroTerminator():int
- Added function Generation.Pdf417Parameters.setPdf417MacroTerminator(int):void
- Added function Recognition.Pdf417ExtendedParameters.getMacroPdf417Terminator():boolean
- Added function Recognition.Pdf417ExtendedParameters.setMacroPdf417Terminator(boolean):void

- Default value for Generation.CodetextParameters.setLocation has been changed to CodeLocation.NONE for all **2D** barcode symbologies.
