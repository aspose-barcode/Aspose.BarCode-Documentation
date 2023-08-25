---
title: Specific Parameters of 1D Barcode Types
linktitle: 1D Barcode Types
type: docs
description: "How to Set Specific Display Parameters for 1D Barcodes in Aspose.BarCode for .NET"
keywords: "Generate Barcodes, Customize 1D Barcode Image, Adjust Bar Height in Aspose.BarCode for .NET, Work with Barcode Image in Aspose.BarCode for .NET, Generate Barcodes in Aspose.BarCode, Customized Linear Barcodes, Change Bar Height, Set Empty Bar Filling for 1D Barcodes, Barcode Wide-to-Narrow Ratio, Set Wide-to-Narrow Ratio in Aspose.BarCode"
weight: 20
url: /net/1d-barcode-types/
aliases: 
- /net/managing-different-barcode-settings/
---

## **Overview**
**One-dimensional (1D)**, or linear, barcodes represent data by varying the width and spacing of parallel lines. In general, a linear barcode is composed of a leading margin, start character, message characters, check character (if any), stop character, and a trailing margin. Based on this framework, all known symbologies define their own encoding principles. In 1D barcodes, bars represent the binary digits, 0 and 1, that may constitute various sequences to encode numbers and then get processed by a digital unit.  

***Aspose.BarCode for .NET*** enables customizing various parameters that are specific for 1D barcode generation. Particularly for 1D barcode standards, developers can adjust the following display properties: the height of bars, the mode of bar filling, the wide-to-narrow ratio, and the automatic correction of invalid barcode text.  
This article describes how to manage these properties using specified classes and properties of the library.  

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Bar Height Settings**
***Aspose.BarCode for .NET*** allows adjusting the height of bars for 1D single-row barcodes. This can be done only when the barcode size property, [*AutoSizeMode*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/autosizemode), is set to *AutoSizeMode.None* (see more information about this property [here](/barcode/net/image-formatting-and-display-settings/)). In this case, regardless of the value specified in the [*XDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/xdimension) property, the bar height can be regulated using the [*BarHeight*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/barheight) property of class [*BarcodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters). This property cannot be set for multiple-row barcodes and 2D barcodes.
  
|<p align="center">**Bar Height**</p>|<p align="center">**Is Set to 40 Pixels**</p>|<p align="center">**Is Set to 80 Pixels**</p>|
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
  
## **Bar Filling Modes**
For 1D barcodes, ***Aspose.BarCode for .NET*** provides a specific mode to generate barcodes with empty bars instead of filled ones. Such a modification can be done using the [*FilledBars*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/filledbars) property of class [*BarcodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters). This property is set to *True* by default and is valid only for 1D barcodes. 
  
|<p align="center">**Bar Filling**</p>|<p align="center">**Filled**</p>|<p align="center">**Empty**</p>|
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

## **Wide-to-Narrow Ratio**
Two-width 1D barcodes are based on the binary code principle, meaning that information is encoded using bars and spaces with two options of width: wide and narrow. Two-width barcode symbologies include the following: *Codabar*, *Code 11*, *Code 32*, *Code 39*, *DataLogic 2-of-5*, *IATA 2-of-5*, *Interleaved 2-of-5*, *ITF 6*, *ITF 14*, *Matrix 2-of-5*, *MSI*, *OPC*, *PZN*, *Standard 2-of-5*, and *VIN*.  
  
In ***Aspose.BarCode for .NET***, the **wide-to-narrow ratio** defines the relation between the width of wide and narrow elements. It can be set in the [*WideNarrowRatio*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/widenarrowratio) property of class [*BarcodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters). The larger if the value of the wide-to-narrow ratio, the larger is the width of the generated barcode. However, the readability also improves with an increase in this parameter. By default, *WideNarrowRatio* is set to 3.  
  
|<p align="center">**Wide-to-Narrow Ratio**</p>|<p align="center">**Is Set to 2**</p>|<p align="center">**Is Set to 5**</p>|
| :-: | :-: | :-: |
| |<img src="widenarrow2code39.png">|<img src="widenarrow5code39.png">|
  
The code snippet provided below illustrates how to adjust the setting of the wide-to-narrow ratio for *Code 39*.  

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code39Extended, "ASPOSE");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//set Wide-to-Narrow Ratio to 2
gen.Parameters.Barcode.WideNarrowRatio = 2;
gen.Save($"{path}WideNarrow2Code39.png", BarCodeImageFormat.Png);
//set Wide-to-Narrow Ratio to 5
gen.Parameters.Barcode.WideNarrowRatio = 5;
gen.Save($"{path}WideNarrow5Code39.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
## **Handle Exceptions on Incorrect Barcode Text**
In case when a barcode has not been created correctly due to invalid barcode text, by default, the library can generate additional dummy data to bring the barcode into line with the standard or delete conflicting characters. Thereafter barcode generation is considered successful.  
  
Developers can change this behaviour by setting the [*ThrowExceptionWhenCodeTextIncorrect*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/throwexceptionwhencodetextincorrect) property of [*BarcodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters) class. When this property is enabled, an exception is thrown if the barcode text has been found incorrect or incomplete.
  
|<p align="center">**Barcode Text Correctness**</p>|<p align="center">**Correct with Valid Barcode Text**</p>|<p align="center">**Adjusted with Invalid Barcode Text**</p>|
| :-: | :-: | :-: |
| |<img src="itf6correct.png">|<img src="itf6filled.png">|
  
The code sample given below illustrates how to set the [*ThrowExceptionWhenCodeTextIncorrect*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/throwexceptionwhencodetextincorrect) property. In this example, the following exception will be thrown: "*Symbology ITF 6 - codetext is invalid*". 
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.ITF6, "123457");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//correct codetext with correction check
gen.CodeText = "12345";
gen.Parameters.Barcode.ThrowExceptionWhenCodeTextIncorrect = true;
gen.Save($"{path}ITF6Correct.png", BarCodeImageFormat.Png);
//incorrect codetext without correction check
gen.CodeText = "12";
gen.Parameters.Barcode.ThrowExceptionWhenCodeTextIncorrect = false;
gen.Save($"{path}ITF6Filled.png", BarCodeImageFormat.Png);
//incorrect codetext without correction check
try
{
    gen.CodeText = "12";
    gen.Parameters.Barcode.ThrowExceptionWhenCodeTextIncorrect = true;
    gen.GenerateBarCodeImage();
}
catch (Exception e)
{
    Console.WriteLine(e.Message);
}
{{< /highlight >}}