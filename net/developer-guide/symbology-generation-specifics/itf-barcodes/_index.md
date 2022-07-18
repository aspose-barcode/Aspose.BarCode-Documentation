---
title: ITF Barcodes
type: docs
weight: 120
url: /net/itf-barcodes/
---
{{% alert color="primary" %}}[Generate ITF Barcodes Online](https://products.aspose.app/barcode/generate/itf): You can check the quality of ***Aspose.BarCode*** generation for ITF barcodes and view the results online.{{% /alert %}}

## **Overview**
The *ITF 14* symbology has been introduced by GS1 based on the *Interleaved 2-of-5* standard to encode trade identifiers defined as Global Trade Item Numbers (GTIN). This barcode type allows encoding a set of 14 digits where the last one is a check digit. The *ITF 6* symbology is mainly used as an addition to *ITF 14* to encode the quantity or weight of a trade item. *ITF* barcode labels usually have borders or frames of different types with a quiet zone. Such appearance-related settings may vary depending on particular industrial needs. In ***Aspose.BarCode for .NET***, parameters of generated *ITF* barcodes can be adjusted using the [*ITF*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/itf) property group of class [*BarcodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters). Further in the article, these properties are discussed in detail along with the instructions on their use and corresponding code samples.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Frame Settings**
As mentioned above, *ITF* barcode labels may have frames of different types depending on industrial needs. ***Aspose.BarCode for .NET*** allows customizing the appearance of *ITF* barcode frames according to specific requirements. Namely, it is possible to adjust frame style and thickness, as explained below.
 
### **Frame Style for ITF 14 and ITF 6**
In ***Aspose.BarCode for .NET***, developers can set five different styles for *ITF* barcode frames, including the absence of such. It can be done by using the [*ItfBorderType*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/itf14bordertype) enumeration that provides the following options: *None*, *Frame*, *Bar*, *FrameOut*, and *BarOut*. Note that *FrameOut* and *BarOut* allow placing the frame outside a barcode image without affecting its original height. 
  
Sample barcode labels provided below illustrate how the appearance of barcode frames will change depending on particular settings. 
  
|<p align="center">**Frame Style**</p>|<p align="center">**No Borders (*None*)**</p>|<p align="center">**Normal Frame (*Frame*)**</p>|<p align="center">**Horizontal Lines (*Bar*)**</p>|<p align="center">**Outside Frame (*FrameOut*)**</p>|<p align="center">**Outside Lines (*BarOut*)**</p>|
| :-: | :-: | :-: | :-: | :-: | :-: |
| |<img src="itf14bordernone.png">|<img src="itf14borderframe.png">|<img src="itf14borderbar.png">|<img src="itf14borderframeout.png">|<img src="itf14borderbarout.png">|
  
The following code snippet explains how to adjust the frame style considering the *ITF 14* symbology as an example.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.ITF14, "12345678901231");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//ITF border type None
gen.Parameters.Barcode.ITF.ItfBorderType = ITF14BorderType.None;
gen.Save($"{path}ITF14BorderNone.png", BarCodeImageFormat.Png);
//ITF border type Bar
gen.Parameters.Barcode.ITF.ItfBorderType = ITF14BorderType.Bar;
gen.Save($"{path}ITF14BorderBar.png", BarCodeImageFormat.Png);
//ITF border type BarOut
gen.Parameters.Barcode.ITF.ItfBorderType = ITF14BorderType.BarOut;
gen.Save($"{path}ITF14BorderBarOut.png", BarCodeImageFormat.Png);
//ITF border type Frame
gen.Parameters.Barcode.ITF.ItfBorderType = ITF14BorderType.Frame;
gen.Save($"{path}ITF14BorderFrame.png", BarCodeImageFormat.Png);
//ITF border type FrameOut
gen.Parameters.Barcode.ITF.ItfBorderType = ITF14BorderType.FrameOut;
gen.Save($"{path}ITF14BorderFrameOut.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
### **Border Thickness**
Depending on specific industrial requirements, the library enables adjusting border thickness for *ITF* barcodes by initializing the [*ItfBorderThickness*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/itfparameters/properties/itfborderthickness) property of class [*ITFParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/itfparameters). By default, this property is set to 12 pt.
  
*ITF 14* barcode labels shown below have been generated with different border thickness settings.
  
|<p align="center">**Border Thickness**</p>|<p align="center">**Is Set to 5 Pixels**</p>|<p align="center">**Is Set to 15 Pixels**</p>|
| :-: | :-: | :-: |
| |<img src="itf14bordersize5pixels.png">|<img src="itf14bordersize15pixels.png">|
  
The following code sample shows how to set different border thickness values using the *ITF 14* symbology as an example.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.ITF14, "12345678901231");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.Barcode.ITF.ItfBorderType = ITF14BorderType.Frame;
//ITF border size 5 Pixels
gen.Parameters.Barcode.ITF.ItfBorderThickness.Pixels = 5;
gen.Save($"{path}ITF14BorderSize5Pixels.png", BarCodeImageFormat.Png);
//ITF border size 15 Pixels
gen.Parameters.Barcode.ITF.ItfBorderThickness.Pixels = 15;
gen.Save($"{path}ITF14BorderSize15Pixels.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
## **Quiet Zone Settings**
In ***Aspose.BarCode for .NET***, developers can customize the size of the quiet zone in *ITF* barcodes by setting the [*QuietZoneCoef*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/itfparameters/properties/quietzonecoef) property of class [*ITFParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/itfparameters). This property is defined as a relative coefficient to the [*XDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/xdimension) parameter.  
  
*ITF 14* barcode images demonstrated below as examples have been generated using different settings for the quiet zone. 
  
|<p align="center">**Quiet Zone Coefficient**</p>|<p align="center">**Is Set to 10**</p>|<p align="center">**Is Set to 30**</p>|
| :-: | :-: | :-: |
| |<img src="itf14quietzone10.png">|<img src="itf14quietzone30.png">|
  
The following code sample illustrates how to adjust the appearance of the quiet zone for *ITF 14* barcodes.
  
{{< highlight csharp>}}
arcodeGenerator gen = new BarcodeGenerator(EncodeTypes.ITF14, "12345678901231");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.Barcode.ITF.ItfBorderType = ITF14BorderType.Frame;
//ITF quiet zone 10 * XDimension
gen.Parameters.Barcode.ITF.QuietZoneCoef = 10;
gen.Save($"{path}ITF14QuietZone10.png", BarCodeImageFormat.Png);
//ITF quiet zone 30 * XDimension
gen.Parameters.Barcode.ITF.QuietZoneCoef = 30;
gen.Save($"{path}ITF14QuietZone30.png", BarCodeImageFormat.Png);
{{< /highlight >}}