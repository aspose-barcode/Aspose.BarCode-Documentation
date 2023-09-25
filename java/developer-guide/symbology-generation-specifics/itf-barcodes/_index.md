---
title: ITF Barcode Generation in Java
linktitle: ITF Barcodes
type: docs
weight: 120
url: /java/itf-barcodes/
---
{{% alert color="primary" %}}[Generate ITF Barcodes Online](https://products.aspose.app/barcode/generate/itf): You can check the quality of ***Aspose.BarCode*** generation for ITF barcodes and view the results online.{{% /alert %}}

## **Overview**
The GS1 organization has proposed the *ITF 14* barcode standard as an extension of *Interleaved 2-of-5*. *ITF 14* is intended to work with trade identifiers in the form of Global Trade Item Numbers (GTIN). This symbology can be used to encode sets of 14 characters with the last one being the check digit. The *ITF 6* standard serves as a special extension of *ITF 14* that is used to encode such properties of trade items as weight. Generally, *ITF* barcodes are designed with frames of various styles with a quiet zone. Frame settings may require customization according to specific industrial requirements. ***Aspose.BarCode for Java*** allows developers to modify such appearance-related properties of *ITF* barcodes through class [*ITFParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/ITFParameters). In this article, it is explained how to manage these properties.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Frame Settings**
*ITF* barcodes usually are generated with frames with various styles depending on industrial specificities. ***Aspose.BarCode for Java*** enables adjusting appearance-related parameters of *ITF* barcodes, i.e. frame styles and thickness.
 
### **Frame Style Settings**
***Aspose.BarCode for Java*** supports five styles for *ITF* barcode frames. The required frame style including the one with no frames can be enabled using the [*ITF14BorderType*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/ITF14BorderType) enum. The following styles are available: *None*, *Frame*, *Bar*, *BarOut*, and *FrameOut*. *FrameOut* and *BarOut* imply displaying frames outside the barcode image itself so that the original height is not modified. 
  
Following barcodes have been generated with different frame settings. 
  
|Frame Style|No Borders (*None*)|Normal Frame (*Frame*)|Horizontal Lines (*Bar*)|Outside Frame (*FrameOut*)|Outside Lines (*BarOut*)|
| :-: | :-: | :-: | :-: | :-: | :-: |
| |<img src="itf14bordernone.png">|<img src="itf14borderframe.png">|<img src="itf14borderbar.png">|<img src="itf14borderframeout.png">|<img src="itf14borderbarout.png">|
  
<!--The following code sample shows how to manage the frame style for *ITF 14* barcodes.
  
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
{{< /highlight >}}-->
  
### **Frame Thickness Settings**
Developers can customize thickness settings for *ITF* barcodes according to particular industrial needs through the *setItfBorderThickness* method of class [*ITFParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/ITFParameters). The default settings for border thickness is equal to 12 pt.
  
Following *ITF 14* barcodes have been created setting different border thickness values.
  
|Border Thickness|Is Set to 5 Pixels|Is Set to 15 Pixels|
| :-: | :-: | :-: |
| |<img src="itf14bordersize5pixels.png">|<img src="itf14bordersize15pixels.png">|
  
<!--The following code snippet demonstrates to manage border thickness for *ITF 14* barcodes.
  
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
{{< /highlight >}}-->
  
## **Quiet Zone Settings**
***Aspose.BarCode for Java*** allows developers to modify the quiet zone size for *ITF* barcodes through the *setQuietZoneCoef* method of class [*ITFParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/ITFParameters). The quiet zone is determined as a relative coefficient to the value of *XDimension*.  
  
Following *ITF 14* barcodes have been created with different quiet zone settings. 
  
|Quiet Zone Coefficient|Is Set to 10|Is Set to 30|
| :-: | :-: | :-: |
| |<img src="itf14quietzone10.png">|<img src="itf14quietzone30.png">|
  
<!--The following code snippet shows how to manage the size of the quiet zone for *ITF 14* barcodes.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.ITF14, "12345678901231");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.Barcode.ITF.ItfBorderType = ITF14BorderType.Frame;
//ITF quiet zone 10 * XDimension
gen.Parameters.Barcode.ITF.QuietZoneCoef = 10;
gen.Save($"{path}ITF14QuietZone10.png", BarCodeImageFormat.Png);
//ITF quiet zone 30 * XDimension
gen.Parameters.Barcode.ITF.QuietZoneCoef = 30;
gen.Save($"{path}ITF14QuietZone30.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->