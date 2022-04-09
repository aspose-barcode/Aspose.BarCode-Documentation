---
title: Barcode Color Scheme
type: docs
weight: 60
description: "How to Adjust Color Schemes of Barcode Elements in Aspose.BarCode for Java"
keywords: "Generate Barcodes, Customize Barcode Image, Change Barcode Color, Set Barcode Color, Generate Colored Barcodes, Barcode Color in Aspose.BarCode for Java, Work with Barcode Image in Aspose.BarCode for Java, Generate Barcodes in Aspose.BarCode"
url: /java/customizing-barcode-color-scheme/
---
This article describes the options provided by ***Aspose.BarCode for Java*** to adjust the color scheme of a barcode image and its main elements.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
Generally, barcode images are created in black and white colors. However, to address the necessity to generate barcode labels of different colors, ***Aspose.BarCode for Java*** enables customizing system RGB color for key barcode elements, such as:
- Background
- Bars
- Borders
- Barcode text
- Top and bottom captions

## **Barcode Background Color**
Setting color for barcode background can be done by using the *setBackColor* method of [*BaseGenerationParameters*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/BaseGenerationParameters) class. The default background color is set to *White*.  
  
The barcode image generated with adjusted background color settings (*Color.Green*) is demonstrated below.
   
<p align="center"><image src="colorbackground.png"></p>

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
  
## **Bar Color**
To customize the bar color in a barcode image, it is necessary to call the *setBarColor* method of [*BarcodeParameters*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeParameters) class. The default bar color is *Black*.  
  
The following image represents the barcode label generated with the customized bar color settings (*Color.Green*).
  
<p align="center"><image src="colorbarcode.png"></p>
  
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

## **Border Color**
It is possible to vary barcode border color by setting the *setColor* property of class [*BorderParameters*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/BorderParameters). By default, the color of borders is set to *Black*. The barcode image provided below has been created setting border color to (*Color.Green*).
  
<p align="center"><image src="colorborder.png"></p>
  
The following code example is used to change the color of barcode borders.  

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
gen.Parameters.Border.Visible = true;
gen.Parameters.Border.Width.Pixels = 5;
//set color of border
gen.Parameters.Border.Color = Color.Green;
gen.Save($"{path}ColorBorder.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

## **Barcode Text Color**
The color of barcode text that may be placed on a barcode image can be adjusted as well. To do this, it is required to call the *setColor* method of class [*CodeTextParameters*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/CodetextParameters). By default, the color of barcode text is set to *Black*. The sample barcode image shown below has been generated with the customized barcode text color setting (*Color.Green*).
  
<p align="center"><image src="colorcodetext.png"></p>
  
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

## **Caption Color**
Barcode images created using ***Aspose.BarCode for Java*** may have top and/or bottom captions according to the will of a developer. The color of these elements can be adjusted through the *SetTextColor* method of class [*CaptionParameters*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/CaptionParameters). The following barcode images have been generated using the customized caption color settings (*Color.Green*).
  
|Adjusting Caption Color|   |
|:--| :-: |
|<image src="colorcaptionabove.png">|<image src="colorcaptionbelow.png">|
  
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