---
title: Bar Height Settings
type: docs
description: "How to Customize Bar Settings for 1D Barcodes in Aspose.BarCode for .NET"
keywords: "Generate Barcodes, Customize 1D Barcode Image, Adjust Bar Height in Aspose.BarCode for .NET, Work with Barcode Image in Aspose.BarCode for .NET, Generate Barcodes in Aspose.BarCode, Customized Linear Barcodes, Change Bar Height, Set Empty Bar Filling for 1D Barcodes, Barcode Wide-to-Narrow Ratio, Set Wide-to-Narrow Ratio in Aspose.BarCode"
weight: 20
url: /net/bar-height-settings/
---

## **Setting Bar Height**
***Aspose.BarCode for .NET*** allows adjusting the height of bars for 1D single-row barcodes. This can be done only when the barcode size property, [*AutoSizeMode*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/autosizemode), is set to *AutoSizeMode.None* (see more information about this property [here](/barcode/net/image-formatting-and-display-settings/)). In this case, regardless of the value specified in the [*XDimension*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/xdimension) property, the bar height can be regulated using the [*BarHeight*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/barheight) property of class [*BarcodeParameters*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters). This property cannot be set for multiple-row barcodes and 2D barcodes.
  
|Bar Height|Is Set to 40 Pixels|Is Set to 80 Pixels|
| :-: | :-: | :-: |
| |<img src="barheight40code128.png">|<img src="barheight80code128.png">|
  
The code snippet below explains how to set different values of bar height for *Code 128*.
     
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "ASPOSE");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//set BarHeight 40
gen.Parameters.Barcode.BarHeight.Pixels = 40;
gen.Save($"{path}BarHeight40Code128.png", BarCodeImageFormat.Png);
//set BarHeight 80
gen.Parameters.Barcode.BarHeight.Pixels = 80;
gen.Save($"{path}BarHeight80Code128.png", BarCodeImageFormat.Png);
{{< /highlight >}}
 