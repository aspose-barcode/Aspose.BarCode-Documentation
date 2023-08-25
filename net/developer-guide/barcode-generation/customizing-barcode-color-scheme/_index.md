---
title: Customize Barcode Color Scheme in C#
linktitle: Customize Barcode Color Scheme
type: docs
weight: 40
description: "How to Customize Color of Barcode Elements in C#"
keywords: "create barcode c#, barcode color ASP.NET, bar color c#, barcode text color c#, barcode caption c# .NET, Generate Barcodes, Customize Barcode Image, Change Barcode Color, Set Barcode Color, Generate Colored Barcodes, Barcode Color in Aspose.BarCode for .NET, Work with Barcode Image in Aspose.BarCode for .NET"
url: /net/customize-barcode-color/
aliases:
- /net/customizing-barcode-color-scheme/
---
This article describes the options provided by ***Aspose.BarCode for .NET*** to adjust the color scheme of a barcode image and its main elements.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
Generally, barcode images are created in black and white colors. To generate barcode labels of different colors, ***Aspose.BarCode for .NET*** enables customizing system RGB color for key barcode elements, such as:
- Background
- Bars
- Borders
- Barcode text
- Top and bottom captions

## **Set Barcode Background Color**
Setting color for barcode background can be done by initializing the [*BackColor*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/backcolor) property of [*BaseGenerationParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters) class. The default background color is set to *White*.  
  
The barcode image generated with adjusted background color settings (*Color.Green*) is demonstrated below.
   
<p align="center"><image src="colorbackground.png"></p>

The following code snippet illustrates how to set a barcode background color.
    
{{< gist "aspose-barcode-gists" "c57fb905001e8973548e1ee555a34e68" "barcode-background-color.cs" >}} 
  
## **Set Bar Color**
To customize the color of bars in a barcode image, it is necessary to set the value to the [*BarColor*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/barcolor) property of [*BarcodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters) class. The default bar color is *Black*.  
  
The following image represents the barcode label generated with the customized bar color settings (*Color.Green*).
  
<p align="center"><image src="colorbarcode.png"></p>
  
The code snippet provided below explains how to adjust bar color.  

{{< gist "aspose-barcode-gists" "2656aaf663f8f5d7217dca27f69d9515" "barcode-bar-color.cs" >}}  

## **Set Barcode Border Color**
It is possible to vary barcode border color by setting the [*Color*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/borderparameters/properties/color) property of class [*BorderParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/borderparameters). By default, the color of borders is set to *Black*. The barcode image provided below has been created setting border color to (*Color.Green*).
  
<p align="center"><image src="colorborder.png"></p>
  
The following code example is used to change the color of barcode borders.  

{{< gist "aspose-barcode-gists" "6c50f1bee0d5a51597ff1be3c27297dc" "barcode-border-color.cs" >}}  

## **Set Barcode Text Color**
The color of barcode text that may be placed on a barcode image can be adjusted as well. To do this, it is required to initialize the [*Color*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/color) property in property group [*CodeTextParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/codetextparameters). By default, the color of barcode text is set to *Black*. The sample barcode image shown below has been generated with the customized barcode text color setting (*Color.Green*).
  
<p align="center"><image src="colorcodetext.png"></p>
  
The following code snippet demonstrates how to change barcode text color.
  
{{< gist "aspose-barcode-gists" "701a80539ae8c01a0c959db324a902ad" "barcode-text-color.cs" >}}  

## **Set Barcode Caption Color**
Barcode images created using ***Aspose.BarCode for .NET*** may have top and/or bottom captions according to the will of a developer. The color of these elements can be adjusted by setting the value to the [*TextColor*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters/properties/textcolor) property in property group [*CaptionParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters). The following barcode images have been generated using the customized caption color settings (*Color.Green*).
  
|Adjusting Caption Color|   |
|:--| :-: |
|<image src="colorcaptionabove.png">|<image src="colorcaptionbelow.png">|
  
The code example given below explains how to adjust caption color for top and bottom captions.

{{< gist "aspose-barcode-gists" "48e360335b3a01ee89d4c135d8390eb9" "barcode-caption-color.cs" >}}  