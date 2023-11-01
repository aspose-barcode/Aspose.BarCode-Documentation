---
title: Customize Barcode Color Scheme in Java
linktitle: Customize Barcode Color Scheme
type: docs
weight: 40
feedback: BARCODECOM
description: "How to Adjust Color Schemes of Barcode Elements in Aspose.BarCode for Java"
keywords: "Generate Barcodes, Customize Barcode Image, Change Barcode Color, Set Barcode Color, Generate Colored Barcodes, Barcode Color in Aspose.BarCode for Java, Work with Barcode Image in Aspose.BarCode for Java, Generate Barcodes in Aspose.BarCode"
url: /java/customize-barcode-color/
aliases:
- /java/colorize-any-part-of-the-barcode-image/
---
In this article, the options available in ***Aspose.BarCode for Java*** to manage barcode color scheme and its key elements are described.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
Usually, barcode images have a black-and-white color scheme. To provide the possibility of modifying barcode colors, ***Aspose.BarCode for Java*** enables customizing system RGB colors for key barcode elements, including the following:
- Bars
- Background
- Text label
- Top and bottom captions
- Borders

## **Set Barcode Background Color**
Barcode background color can be modified through the *setBackColor* method of [*BaseGenerationParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/BaseGenerationParameters) class. The default value of background color is *White*.  
  
The barcode image with background color set to *Color.Green* is provided below.
   
<p align="center"><image src="colorbackground.png"></p>

<!--The following code sample explains how to adjust the barcode background color.
    
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
{{< /highlight >}}--> 
  
## **Set Bar Color**
To manage the color of bars, the *setBarColor* method of [*BarcodeParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeParameters) class needs to be used. By default, the bar color is set to *Black*.  
  
The barcode image below has been generated with the bar color setting *Color.Green*.
  
<p align="center"><image src="colorbarcode.png"></p>
  
<!--The code snippet provided below explains how to modify the bar color.  
  
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
{{< /highlight >}}--> 

## **Set Barcode Border Color**
Barcode border color can be adjusted through the *setColor* method of class [*BorderParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/BorderParameters). The default border color is *Black*. The barcode image below has been generated with border color set to *Color.Green*.
  
<p align="center"><image src="colorborder.png"></p>
  
<!--The following code snippet shows how to customize border color in a barcode image.  

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
{{< /highlight >}}--> 

## **Set Barcode Text Color**
***Aspose.BarCode for Java*** provides the possibility to customize the color of the main text label displayed on a barcode image. It can be done by calling the *setColor* method of class [*CodeTextParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/CodetextParameters). The default setting of the main text color is *Black*. The sample barcode image shown below has been generated with the customized barcode text color setting (*Color.Green*).
  
<p align="center"><image src="colorcodetext.png"></p>
  
<!--The following code snippet demonstrates how to change barcode text color.
  
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
{{< /highlight >}}-->

## **Set Barcode Caption Color**
In ***Aspose.BarCode for Java***, barcode images can be generated with top and bottom captions. Caption color can be customized using the *setTextColor* method of class [*CaptionParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/CaptionParameters). Sample images below have been created with the color setting set to *Color.Green*.
  
|Caption Color|   |
|:--| :-: |
|<image src="colorcaptionabove.png">|<image src="colorcaptionbelow.png">|
  
<!--The following code snippet demonstrates how to modify color for top and bottom captions.
  
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
{{< /highlight >}}--> 