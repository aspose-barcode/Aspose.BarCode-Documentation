---
title: Bar Filling Settings
type: docs
description: "How to Set Different Filling Modes for 1D Barcodes in Aspose.BarCode for .NET"
keywords: "Generate Barcodes, Customize 1D Barcode Image, Adjust Bar Height in Aspose.BarCode for .NET, Work with Barcode Image in Aspose.BarCode for .NET, Generate Barcodes in Aspose.BarCode, Customized Linear Barcodes, Change Bar Height, Set Empty Bar Filling for 1D Barcodes, Barcode Wide-to-Narrow Ratio, Set Wide-to-Narrow Ratio in Aspose.BarCode"
weight: 20
url: /net/bar-filling/
---

## **Bar Filling Modes**
For 1D barcodes, ***Aspose.BarCode for .NET*** provides a specific mode to generate barcodes with empty bars instead of filled ones. Such a modification can be done using the [*FilledBars*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/filledbars) property of class [*BarcodeParameters*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters). This property is set to *True* by default and is valid only for 1D barcodes. 
  
|Bar Filling Modes|Filled|Empty|
| :-: | :-: | :-: |
| |<img src="barsfilledcode128.png">|<img src="barsemptycode128.png">|
  
The following code sample demonstrates how to adjust the bar filling mode for *Code 128*.

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "ASPOSE");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//set bars filled
gen.Parameters.Barcode.FilledBars = true;
gen.Save($"{path}BarsFilledCode128.png", BarCodeImageFormat.Png);
//set bars empty
gen.Parameters.Barcode.FilledBars = false;
gen.Save($"{path}BarsEmptyCode128.png", BarCodeImageFormat.Png);
{{< /highlight >}}
