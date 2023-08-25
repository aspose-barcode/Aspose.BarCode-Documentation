---
title: Customize Barcode Color Scheme in C++
linktitle: Customize Barcode Color Scheme
type: docs
weight: 40
description: "How to Customize Color of Barcode Elements in C++"
keywords: "create barcode c#, barcode color, bar color c#, barcode text color c#, barcode caption C++, Generate Barcodes, Customize Barcode Image, Change Barcode Color, Set Barcode Color, Generate Colored Barcodes, Barcode Color in Aspose.BarCode for C++, Work with Barcode Image in Aspose.BarCode for C++"
url: /cpp/customize-barcode-color/
---
This article describes the options provided by ***Aspose.BarCode for C++*** to adjust the color scheme of a barcode image and its main elements.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
Generally, barcode images are created in black and white colors. To generate barcode labels of different colors, ***Aspose.BarCode for C++*** enables customizing system RGB color for key barcode elements, such as:
- Background
- Bars
- Borders
- Barcode text
- Top and bottom captions

## **Set Barcode Background Color**
Setting color for barcode background can be done by initializing the [*BackColor*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/backcolor) property of [*BaseGenerationParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters) class. The default background color is set to *White*.  
  
The barcode image generated with adjusted background color settings (*Color.Green*) is demonstrated below.
   
<p align="center"><image src="colorbackground.png"></p>

## **Set Bar Color**
To customize the color of bars in a barcode image, it is necessary to set the value to the [*BarColor*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/barcolor) property of [*BarcodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters) class. The default bar color is *Black*.  
  
The following image represents the barcode label generated with the customized bar color settings (*Color.Green*).
  
<p align="center"><image src="colorbarcode.png"></p>
  

## **Set Barcode Border Color**
It is possible to vary barcode border color by setting the [*Color*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/borderparameters/properties/color) property of class [*BorderParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/borderparameters). By default, the color of borders is set to *Black*. The barcode image provided below has been created setting border color to (*Color.Green*).
  
<p align="center"><image src="colorborder.png"></p>
  
## **Set Barcode Text Color**
The color of barcode text that may be placed on a barcode image can be adjusted as well. To do this, it is required to initialize the [*Color*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/color) property in property group [*CodeTextParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/codetextparameters). By default, the color of barcode text is set to *Black*. The sample barcode image shown below has been generated with the customized barcode text color setting (*Color.Green*).
  
<p align="center"><image src="colorcodetext.png"></p>
   
## **Set Barcode Caption Color**
Barcode images created using ***Aspose.BarCode for C++*** may have top and/or bottom captions according to the will of a developer. The color of these elements can be adjusted by setting the value to the [*TextColor*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters/properties/textcolor) property in property group [*CaptionParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters). The following barcode images have been generated using the customized caption color settings (*Color.Green*).
  
|Adjusting Caption Color|   |
|:--| :-: |
|<image src="colorcaptionabove.png">|<image src="colorcaptionbelow.png">|
  