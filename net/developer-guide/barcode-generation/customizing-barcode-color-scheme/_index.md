---
title: Customizing Barcode Color Scheme
type: docs
weight: 50
url: /net/customizing-barcode-color-scheme/
---
This article describes the options provided by ***Aspose.BarCode for .NET*** to adjust the color scheme of a barcode image and its main elements.

## Overview
Generally, barcode images are created in black and white colors. However, to address the necessity to generate barcode labels of different colors, ***Aspose.BarCode for .NET*** enables customizing system RGB color for key barcode elements, such as:
- Barcode background
- Barcode bars
- Barcode text
- Top and bottom captions

## Barcode Background Color
Setting color for barcode background can be done by initializing the [*BackColor*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/backcolor) property of [*BaseGenerationParameters*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters) class. The default background color is set to *White*.  
The barcode image generated with adjusted background color settings (*Color.Green*) is demonstrated below.
   
<p align="center"><image src="ColorBackground.png"></p>

The following code snippet illustrates how to set a barcode background color.
    
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Parameters.CaptionAbove.Visible = true;
gen.Parameters.CaptionAbove.Font.Size.Point = 20;
gen.Parameters.CaptionAbove.Text = "Caption Above";
gen.Parameters.CaptionBelow.Visible = true;
gen.Parameters.CaptionBelow.Font.Size.Point = 20;
gen.Parameters.CaptionBelow.Text = "Caption Below";
//set background color
gen.Parameters.BackColor = Color.Green;
gen.Save($"{path}ColorBackground.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
## Bar Color
To customize the bar color in a barcode image, it is necessary to set the value to the [*BarColor*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/barcolor) property of [*BarcodeParameters*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters) class. The default bar color is *Black*.  
The following image represents the barcode label generated with the customized bar color settings (*Color.Green*).
  
<p align="center"><image src="ColorBarcode.png"></p>
  
The code snippet provided below explains how to adjust bar color.  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Parameters.CaptionAbove.Visible = true;
gen.Parameters.CaptionAbove.Font.Size.Point = 20;
gen.Parameters.CaptionAbove.Text = "Caption Above";
gen.Parameters.CaptionBelow.Visible = true;
gen.Parameters.CaptionBelow.Font.Size.Point = 20;
gen.Parameters.CaptionBelow.Text = "Caption Below";
//set barcode color
gen.Parameters.Barcode.BarColor = Color.Green;
gen.Save($"{path}ColorBarcode.png", BarCodeImageFormat.Png);
{{< /highlight >}} 


## Barcode Text Color

The color of barcode text that may be placed on a barcode image can be adjusted as well. To do this, it is required to initialize the [*Color*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/color) property in property group [*CodeTextParameters*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/codetextparameters). By default, the color of barcode text is set to *Black*.  
The sample barcode image shown below has been generated with customized barcode text color setting (*Color.Green*).
  
<p align="center"><image src="ColorCodetext.png"></p>
  
The following code snippet demonstrates how to change barcode text color.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Parameters.CaptionAbove.Visible = true;
gen.Parameters.CaptionAbove.Font.Size.Point = 20;
gen.Parameters.CaptionAbove.Text = "Caption Above";
gen.Parameters.CaptionBelow.Visible = true;
gen.Parameters.CaptionBelow.Font.Size.Point = 20;
gen.Parameters.CaptionBelow.Text = "Caption Below";
//set codetext color
gen.Parameters.Barcode.CodeTextParameters.Color = Color.Green;
gen.Save($"{path}ColorCodetext.png", BarCodeImageFormat.Png);
{{< /highlight >}}

## Caption Color
Barcode images created using ***Aspose.BarCode for .NET*** may have top and/or bottom captions according to the will of a developer. The color of these elements can be adjusted by setting the value to the [*TextColor*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters/properties/textcolor) property in property group [*CaptionParameters*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters).  
The following barcode images have been generated using the customized caption color settings ((*Color.Green*)).
  
|Adjusting Caption Color | |
|:---|:---:|
|<p align="center"><image src="ColorCaptionAbove.png"></p>|<p align="center"><image src="ColorCaptionBelow.png"></p>|
  
The code example given below explains how to adjust caption color for top and bottom captions.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Parameters.CaptionAbove.Visible = true;
gen.Parameters.CaptionAbove.Font.Size.Point = 20;
gen.Parameters.CaptionAbove.Text = "Caption Above";
gen.Parameters.CaptionBelow.Visible = true;
gen.Parameters.CaptionBelow.Font.Size.Point = 20;
gen.Parameters.CaptionBelow.Text = "Caption Below";
//set Top Caption color
gen.Parameters.CaptionAbove.TextColor = Color.Green;
gen.Save($"{path}ColorCaptionAbove.png", BarCodeImageFormat.Png);
//set Bottom Caption color
gen.Parameters.CaptionAbove.TextColor = Color.Black;
gen.Parameters.CaptionBelow.TextColor = Color.Green;
gen.Save($"{path}ColorCaptionBelow.png", BarCodeImageFormat.Png);
{{< /highlight >}} 