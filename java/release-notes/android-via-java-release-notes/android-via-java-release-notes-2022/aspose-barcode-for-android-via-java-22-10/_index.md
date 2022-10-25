---
title: Aspose.BarCode for Android via Java 22.10
type: docs
weight: 920
url: /java/aspose-barcode-for-android-via-java-22-10/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Android via Java 22.10](https://downloads.aspose.com/barcode/androidjava/new-releases/aspose.barcode-for-android-via-java-22.10/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-38034|Incorrect File ID field encoding in MacroPdf417|Bug|
|BARCODENET-38344|QR/GS1QR generation throws exception in AutoSizeMode.Nearest|Bug|

## **Public API and Backward Incompatible Changes**

- Added enum com.aspose.barcode.generation.Pdf417MacroTerminator
- Added field com.aspose.barcode.generation.Pdf417MacroTerminator.AUTO
- Added field com.aspose.barcode.generation.Pdf417MacroTerminator.NONE
- Added field com.aspose.barcode.generation.Pdf417MacroTerminator.SET
- Added method com.aspose.barcode.generation.Pdf417Parameters.getPdf417MacroTerminator():Pdf417MacroTerminator
- Added method com.aspose.barcode.generation.Pdf417Parameters.setPdf417MacroTerminator(Pdf417MacroTerminator):void
- Added method com.aspose.barcode.barcoderecognition.Pdf417ExtendedParameters.getMacroPdf417Terminator():boolean

- Default value for property com.aspose.barcode.generation.CodetextParameters.Location has been changed to CodeLocation.NONE for all **2D** barcode symbologies.
