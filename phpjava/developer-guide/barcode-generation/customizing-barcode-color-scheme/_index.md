---
title: Modify Barcode Color Scheme
type: docs
ai_search_scope: "barcode_phpjava_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 60
description: "How to Adjust Color Schemes of Barcode Elements in Aspose.BarCode for PHP via Java"
keywords: "generate barcodes, customize barcode image, change barcode color, set barcode color, generate colored barcodes, barcode color in PHP, work with barcode image in Aspose.BarCode, generate barcodes in Aspose.BarCode"
url: /phpjava/modify-barcode-color/
---
In this article, the options available in ***Aspose.BarCode for PHP via Java*** to manage barcode color scheme and its key elements are descsribed.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/phpjava/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
Usually barcode images have the black-and-white color scheme. To provide the possibilty of modifying barcode colors, ***Aspose.BarCode for PHP via Java*** enables customizing system RGB colors for key barcode elements, including the following:
- Bars
- Background
- Text label
- Top and bottom captions
- Borders

## **Background Color**
Barcode background color can be modified through the *setBackColor (string $hexValue)* function of [*BaseGenerationParameters*](https://reference.aspose.com/barcode/php/classBaseGenerationParameters) class. The default value of background color is *White*.  
  
The barcode image with background color set to *Color.Green* is provided below.
   
<p align="center"><image src="colorbackground.png"></p>
  
## **Bar Color**
To manage the color of bars, the *setBarColor* function of [*BarcodeParameters*](https://reference.aspose.com/barcode/php/classBarcodeParameters) class needs to be used. By default, bar color is set to *Black*.  
  
The barcode image below has been generated with the bar color setting *Color.Green*.
  
<p align="center"><image src="colorbarcode.png"></p>
  
## **Border Color**
Barcode border color can be adjusted through the *setColor (string $hexValue)* function of class [*BorderParameters*](https://reference.aspose.com/barcode/php/classBorderParameters). The default border color is *Black*. The barcode image below has been generated with border color set to *Color.Green*.
  
<p align="center"><image src="colorborder.png"></p>
  
## **Main Text Color**
***Aspose.BarCode for PHP in Java*** provides the possibility to customize the color of main text label displayed on a barcode image. It can be done by calling the *setColor (string $hexValue)* function of class [*CodeTextParameters*](https://reference.aspose.com/barcode/php/classCodetextParameters). The default setting of main text color is *Black*. The sample barcode image shown below has been generated with the customized barcode text color setting (*Color.Green*).
  
<p align="center"><image src="colorcodetext.png"></p>
  
## **Caption Color**
In ***Aspose.BarCode for PHP in Java***, barcode images can be generated with top and bottom captions. Caption color can be customized using the *setTextColor (string $rgbValue)* function of class [*CaptionParameters*](https://reference.aspose.com/barcode/php/classCaptionParameters). Sample images below have been created with the color setting set to *Color.Green*.
  
|Caption Color|   |
|:--| :-: |
|<image src="colorcaptionabove.png">|<image src="colorcaptionbelow.png">|
  
