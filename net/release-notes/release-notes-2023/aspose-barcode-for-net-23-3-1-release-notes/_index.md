---
title: Aspose.BarCode for .NET 23.3.1 Release Notes
date: "2023-04-06"
author: "Konstantin Alkhimov"
type: docs
weight: 10
url: /net/aspose-barcode-for-net-23-3-1-release-notes/
description: A summary of recent changes, enhancements and bug fixes in Aspose.BarCode for .NET 23.3.1 (March 2023) release.
keywords:
- 2023
- March
- new
- release
- changelog
- NET 7
- Anti-aliasing
- Aspose.Drawing
- Linux
---

{{% alert color="primary" %}} 

This article contains release notes information for [**Aspose.BarCode for .NET 23.3.1 (March 2023)**](https://www.nuget.org/packages/Aspose.BarCode/23.3.1).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37820|Investigate replacing System.Drawing.Common to Aspose.Drawing for .NET|Enhancement|
|BARCODENET-37948|Investigate replacement of Reed-Solomon library|Enhancement|
|BARCODENET-38544|Add .Net 7 support to Aspose.Barcode|Enhancement|
|BARCODENET-38360|Add AntiAlias to barcode properties|Enhancement|
|BARCODENET-38322|Remove obsolete properties and warnings|Enhancement|
|BARCODENET-36917|Investigate multithreading addition to the Datamatrix region detection algorithms|Enhancement|

## Public API changes and backwards compatibility

### .NET 7.0 support

In this release .Net 7.0 support to Aspose.Barcode for .Net is added.

### AntiAlias mode

Added UseAntiAlias property to BarcodeGenerator, BarCodeGeneratorControl, BarcodeGeneratorElement and BarCode element for Reporting Services. Property UseAntiAlias indicates whether is used anti-aliasing mode to render image. Anti-aliasing mode is applied to barcode and text drawing.

The following API was added:
- Aspose.BarCode.Generation.BaseGenerationParameters.UseAntiAlias
- Aspose.BarCode.Windows.Forms.BarCodeGeneratorControl.UseAntiAlias
- Aspose.BarCode.WPF.BarcodeGeneratorElement.UseAntiAlias
- Aspose.BarCode.WPF.BarcodeGeneratorElement.UseAntiAliasProperty

### Obsolete API

The following obsolete API was removed:
- Aspose.BarCode.Generation.BarcodeParameters.AutoSizeMode
- Aspose.BarCode.Generation.BarcodeParameters.BarCodeHeight
- Aspose.BarCode.Generation.BarcodeParameters.BarCodeWidth
- Aspose.BarCode.Generation.BarcodeParameters.ForeColor
- Aspose.BarCode.BarCodeRecognition.BarCodeReader.ChecksumValidation
- Aspose.BarCode.BarCodeRecognition.BarCodeReader.StripFNC
- Aspose.BarCode.BarCodeRecognition.BarCodeReader.CustomerInformationInterpretingType
- Aspose.BarCode.BarCodeRecognition.BarCodeReader.DetectEncoding

### Aspose.Drawing for .NET Standard 2.0+ and NET 5.0+

In this release System.Drawing.Common in Aspose.Barcode for .Net (.Net Core) is replaced with Aspose.Drawing.Common

On some Linux systems you have to have "FreeSans" font family installed. Do this you can with the following commands:
```ps
sudo apt-get update
sudo apt-get install fonts-freefont-ttf
```

Changes for .NET Standard 2.0+ and NET 5.0+

- Removed method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(System.Drawing.Bitmap)
- Removed method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(System.Drawing.Bitmap,Aspose.BarCode.BarCodeRecognition.BaseDecodeType[])
- Removed method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(System.Drawing.Bitmap,Aspose.BarCode.BarCodeRecognition.BaseDecodeType)
- Removed method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(System.Drawing.Bitmap,System.Drawing.Rectangle,Aspose.BarCode.BarCodeRecognition.BaseDecodeType[])
- Removed method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(System.Drawing.Bitmap,System.Drawing.Rectangle,Aspose.BarCode.BarCodeRecognition.BaseDecodeType)
- Removed method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(System.Drawing.Bitmap,System.Drawing.Rectangle[],Aspose.BarCode.BarCodeRecognition.BaseDecodeType[])
- Removed method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(System.Drawing.Bitmap,System.Drawing.Rectangle[],Aspose.BarCode.BarCodeRecognition.BaseDecodeType)
- Removed method Aspose.BarCode.BarCodeRecognition.BarCodeReader.SetBarCodeImage(System.Drawing.Bitmap)
- Removed method Aspose.BarCode.BarCodeRecognition.BarCodeReader.SetBarCodeImage(System.Drawing.Bitmap,System.Drawing.Rectangle[])
- Removed method Aspose.BarCode.BarCodeRecognition.BarCodeReader.SetBarCodeImage(System.Drawing.Bitmap,System.Drawing.Rectangle)
- Removed method Aspose.BarCode.BarCodeRecognition.Quadrangle.#ctor(System.Drawing.Point,System.Drawing.Point,System.Drawing.Point,System.Drawing.Point)
- Removed method Aspose.BarCode.BarCodeRecognition.Quadrangle.Contains(System.Drawing.Point)
- Removed method Aspose.BarCode.BarCodeRecognition.Quadrangle.Contains(System.Drawing.Rectangle)

- Added method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(Aspose.Drawing.Bitmap)
- Added method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(Aspose.Drawing.Bitmap,Aspose.BarCode.BarCodeRecognition.BaseDecodeType[])
- Added method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(Aspose.Drawing.Bitmap,Aspose.BarCode.BarCodeRecognition.BaseDecodeType)
- Added method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(Aspose.Drawing.Bitmap,Aspose.Drawing.Rectangle,Aspose.BarCode.BarCodeRecognition.BaseDecodeType[])
- Added method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(Aspose.Drawing.Bitmap,Aspose.Drawing.Rectangle,Aspose.BarCode.BarCodeRecognition.BaseDecodeType)
- Added method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(Aspose.Drawing.Bitmap,Aspose.Drawing.Rectangle[],Aspose.BarCode.BarCodeRecognition.BaseDecodeType[])
- Added method Aspose.BarCode.BarCodeRecognition.BarCodeReader.#ctor(Aspose.Drawing.Bitmap,Aspose.Drawing.Rectangle[],Aspose.BarCode.BarCodeRecognition.BaseDecodeType)
- Added method Aspose.BarCode.BarCodeRecognition.BarCodeReader.SetBarCodeImage(Aspose.Drawing.Bitmap)
- Added method Aspose.BarCode.BarCodeRecognition.BarCodeReader.SetBarCodeImage(Aspose.Drawing.Bitmap,Aspose.Drawing.Rectangle[])
- Added method Aspose.BarCode.BarCodeRecognition.BarCodeReader.SetBarCodeImage(Aspose.Drawing.Bitmap,Aspose.Drawing.Rectangle)
- Added method Aspose.BarCode.BarCodeRecognition.Quadrangle.#ctor(Aspose.Drawing.Point,Aspose.Drawing.Point,Aspose.Drawing.Point,Aspose.Drawing.Point)
- Added method Aspose.BarCode.BarCodeRecognition.Quadrangle.Contains(Aspose.Drawing.Point)
- Added method Aspose.BarCode.BarCodeRecognition.Quadrangle.Contains(Aspose.Drawing.Rectangle)
