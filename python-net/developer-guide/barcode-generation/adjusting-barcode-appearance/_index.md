---
title: Customize Barcode Appearance in Python via.NET
linktitle: Customize Barcode Appearance
type: docs
ai_search_scope: "barcode_python-net_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 30
description: "How to Customize Barcode Appearance-Related Properties in Aspose.BarCode for Python"
keywords: "generate barcodes, customize barcode image, change barcode appearance, barcode appearance in Python, customize barcodes, work with barcode image, generate barcodes in Aspose.BarCode"
url: /python-net/customize-barcode-appearance/
aliases:
- /python-net/manage-barcode-appearance/
---
This article describes how to adjust barcode parameters, such as size, rotation angle, paddings, and image borders.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
***Aspose.BarCode for Python via .NET*** provides class [*BarcodeGenerator*](/barcode/python-net/api-reference/aspose.barcode.generation/barcodegenerator/) to generate barcodes according to the predefined settings so that each element of a barcode image gets its fixed position relative to other elements, as shown in the scheme below. A barcode label comprises the following parts: barcode text, bars, top and bottom captions, image borders, and paddings. All elements besides barcode bars are optional.
  
<p align="center"><img src="barcode_view_scheme.png"></p>


## **Barcode Image Sizing Modes**
In general, the library defines barcode image size in terms of height and width automatically. The library enables developers to manage image size settings manually by determining the height and width of barcode labels through *image_height* and *image_width* properties of class [*BaseGenerationParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/basegenerationparameters/).  
  
Barcode image size can be varied by using various sizing modes that can be enabled using the [*AutoSizeMode*](/barcode/python-net/api-reference/aspose.barcode.generation/autosizemode/) enum. *AutoSizeMode* provides the following options: *NONE*, *NEAREST*, and *INTERPOLATION*. In *INTERPOLATION* and *NEAREST* modes, barcode image size is managed based on the values of width and height, and other parameters are ignored. In turn, when the *NONE* mode is enabled, barcode image size is defined ignoring width and height; instead, other parameters, such as *XDimension*, are used. *AutoSizeMode* takes the *NONE* value by default.  

### **Sizing Mode *NONE*** 
As outlined above, setting the *NONE* mode implies that barcode image size is managed based on different parameters ignoring width and height. To specify barcode size, class [*BarcodeParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/barcodeparameters/) provides a special properties called *x_dimension*. It is used to define the minimum size of bars in 1D barcodes or cells in 2D barcodes. Other barcode sizing parameters are calculated based on the *XDimension* value.  
  
Various barcode standards often determine *XDimension* to provide compatibility between printing and scanning equipment units so that barcode images could be captured by scanners used in various companies. *XDimension* is related to the data density of a barcode type, meaning that it determines the amount of data that can be encoded in one barcode. Setting a small value of *XDimension* results in covering less space to place each encoded character in a barcode image. In contrast, setting a bigger value of *XDimension* leads to enlarging the area required to encode each character and decreasing the number of characters per inch.  
    
The barcode label shown below has been generated using the *NONE* mode.

<p align="center"><img src="autosizemodenone.png"></p>
  

### **Sizing Mode *INTERPOLATION***
Setting the *auto_size_mode* property to *AutoSizeMode.INTERPOLATION* means that only the values specified using *image_height* and *image_width* properties are used in barcode sizing. In this case, barcode image size is determined using the manually specified values of height and width even when it results in producing distorted barcode proportions and the deterioration of barcode readability. The *INTERPOLATION* mode is appropriate to create barcode images with a resolution of 300 dpi or higher. Such resolution settings will allow keeping barcode distortions negligible and avoiding the deterioration of barcode readability.  
  
The barcode label generated through the *INTERPOLATION* mode is demonstrated below.  

<p align="center"><img src="autosizemodeinterpolation.png"></p> 

### **Sizing Mode *NEAREST*** 
To set barcode image size, the *NEAREST* mode uses only the values specified using *image_height* and *image_width* properties similarly to the *INTERPOLATION* mode. In this mode, [*BarcodeGenerator*](/barcode/python-net/api-reference/aspose.barcode.generation/barcodegenerator/) aims at finding the most suitable image size to avoid barcode proportion distortion and readability deterioration.  
  
The barcode label created through the *NEAREST* mode is provided below.
  
<p align="center"><img src="autosizemodenearest.png"></p>
  
## **Bar Width Reduction**
The other important property that needs to be determined accurately is bar width. Setting an appropriate value of this parameter is critical to assure successful barcode scanning. Due to the so-called ink floating phenomenon, some barcode printing techniques may result in increasing actual bar width after printing out barcode images. This happens often in commercial printing in cases when conventional printing presses are used. To ensure that printed barcode images will be printed out with appropriate bar width, setting a bar width reduction value may be required.  
  
Bar width reduction (BWR) is a way to mitigate the effect of ink floating in a graphic design file of a barcode. The barcode library allows modifying bar width through the *bar_width_reduction* property of class [*BarcodeParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/barcodeparameters/). Passing the required value while setting this property allows decreasing bar width in 1D barcodes or cell size in 2D barcodes. To find out the suitable BWR value for a printer, it is necessary to check special tables provided by printer manufacturers. Modifying this parameter is not applicable to laser printers.  
  
The sample barcodes shown below have been generated with and without applying bar width reduction.
  
|Barcode Type|Bar Width Reduction 0|Bar Width Reduction 3|  
| :-: | :-: | :-: |  
|**Code 128**|<img src="code128barwidthreduction0.png" width="50%" height="50%">|<img src="code128barwidthreduction3.png" width="50%" height="50%">| 
|**Data Matrix**|<img src="datamatrixbarwidthreduction0.png" width="50%" height="50%">|<img src="datamatrixbarwidthreduction4.png" width="50%" height="50%">|


## **Customizing Barcode Borders and Padding**
The barcode library allows customizing barcode image borders and paddings. Corresponding properties are described further.
  
### **Border Settings**
Applying default border settings results in generating barcode images without borders. Alternatively, they can be defined manually using five styles: solid, dotted, dashed, dash-dot, and dash-dot-dot. The border style can be modified using class [*BorderParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/borderparameters/). In addition, this class allows setting border thickness in any available units and colors using *width* and *color* properties. Border styles can be changed using the *dash_style* property of this class. 
  
Barcode labels demonstrated below have been generated using different border styles. 
  
|Border Style|Solid|Dashed|Dotted|Dash-Dot|Dash-Dot-Dot| 
| :-: | :-: | :-: | :-: | :-: | :-: | 
| |<img src="bordersolid.png">|<img src="borderdash.png">|<img src="borderdot.png">|<img src="borderdashdot.png">|<img src="borderdashdotdot.png">|


### **Paddings**
Paddings from the edges of a barcode image or its borders can be set in four directions using a special class called [*Padding*](/barcode/python-net/api-reference/aspose.barcode.generation/padding/) and its properties: *left*, *right*, *top*, and *bottom*. By default, the padding values are set to 5 points in all directions.
  
|Padding|Millimeters|Pixels|  
| :-: | :-: | :-: |  
| |<img src="padding10millimeters.png">|<img src="padding10pixels.png">| 
  
## **Barcode Rotation**
Barcode image rotation can be set using the *rotation_angle* property of class [*BaseGenerationParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/basegenerationparameters/). Setting this property to a value in degrees allows generating a barcode image rotated at the desired angle clockwise or counterclockwise.  
  
The sample barcode labels rotated by various angles are shown below.
  
|Rotation Angle|Is Set to +90°|Is Set to -90°|Is Set to +45°|Is Set to -45°|Is Set to 180°| 
| :-: | :-: | :-: | :-: | :-: | :-: | 
| |<img src="rotationangle+90.png">|<img src="rotationangle-90.png">|<img src="rotationangle+45.png">|<img src="rotationangle-45.png">|<img src="rotationangle180.png">|
 