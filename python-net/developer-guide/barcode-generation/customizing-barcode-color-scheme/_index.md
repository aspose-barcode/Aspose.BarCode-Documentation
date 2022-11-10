---
title: Customize Barcode Color Scheme
type: docs
weight: 60
description: "How to Adjust Color Schemes of Barcode Elements in Aspose.BarCode for Python"
keywords: "generate barcodes, customize barcode image, change barcode color, set barcode color, generate colored barcodes, barcode color in Python, work with barcode image in Aspose.BarCode, generate barcodes in Aspose.BarCode"
url: /python-net/s
---
This article explains how to adjust color of barcode key elements in ***Aspose.BarCode for Python via .NET***.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
Barcode images have a black-and-white color scheme. To provide the possibility of modifying barcode colors, ***Aspose.BarCode for Python via .NET*** enables customizing system RGB colors for key barcode elements, including the following:
- Bars
- Background
- Text label
- Top and bottom captions
- Borders

## **Bar Color**
To manage the color of bars, the *bar_color* property of [*BarcodeParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/barcodeparameters/) class needs to be used. By default, the bar color is set to *Black*.  
  
The barcode image below has been generated with the bar color setting *Color.Green*.
  
<p align="center"><image src="colorbarcode.png"></p>

## **Background Color**
Barcode background color can be modified through the *back_color* property of [*BaseGenerationParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/basegenerationparameters/) class. The default value of background color is *White*.  
  
The barcode image with background color set to *Color.Green* is provided below.
   
<p align="center"><image src="colorbackground.png"></p>

## **Main Text Color**
The barcide library provides the possibility to customize the color of the main text label displayed on a barcode image. It can be done by calling the *color* property of class [*CodeTextParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/codetextparameters/). The default setting of the main text color is *Black*. The sample barcode image shown below has been generated with the customized barcode text color setting (*Color.Green*).
  
<p align="center"><image src="colorcodetext.png"></p>

## **Caption Color**
Barcode images can be generated with top and bottom captions. Caption color can be customized using the *text_color* property of class [*CaptionParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/captionparameters/). Sample images below have been created with the color setting set to *Color.Green*.
  
|Caption Color|   |
|:--| :-: |
|<image src="colorcaptionabove.png">|<image src="colorcaptionbelow.png">|

## **Border Color**
Barcode border color can be adjusted through the *color* property of class [*BorderParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/borderparameters/). The default border color is *Black*. The barcode image below has been generated with border color set to *Color.Green*.
  
<p align="center"><image src="colorborder.png"></p>
