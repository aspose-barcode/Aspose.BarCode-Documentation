---
title: Customize Barcode Text and Captions in Python via .NET
linktitle: Customize Barcode Text
type: docs
ai_search_scope: "barcode_python-net_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 50
description: "How to Set Barcode Text and Captions in Aspose.BarCode for Python via .NET"
keywords: "Generate Barcodes, Customize Barcode Image, Change Barcode Text, Barcode Appearance in Aspose.BarCode for Python, Work with Barcode Image in Aspose.BarCode for Python, Set Barcode Text in Aspose.BarCode, Generate Barcode with Caption, Generate Barcodes in Aspose.BarCode"
url: /python-net/set-barcode-text/
aliases:
- /python-net/barcode-text-settings/
---

This article describes how to work with text placed on barcode images. ***Aspose.BarCode for Python via .NET*** enables customizing various parameters of barcode text: visibility, font, spacings, text location, and wrapping modes.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
***Aspose.BarCode for Python via .NET*** allows developers to add human-readable text on barcode images in three different forms shown in the scheme below: main text label, top caption, and bottom caption. Any of these elements can be placed optionally or hidden.
    
<p align="center"><img src="barcode_text_scheme.png"></p>

## **Barcode Text**
The main barcode text label contains short text information detached from bars by spacings. This text label can take six positions, as explained in the figure below: top center, top left, top right, bottom center, bottom left, or bottom right.
  
<p align="center"><img src="codetext_scheme.png"></p>
   
### **Text Visibility**
***Aspose.BarCode for Python via .NET*** allows developers to visualize or hide barcode text. If there is no need to put human-readable text on a barcode image, barcode images can be generated without text labels, as shown in the example below.
  
<p align="center"><img src="codetexthide.png"></p>  

  
### **Text Positioning**
The position of a barcode text label can be modified by customizing two parameters: alignment and location. These parameters can be adjusted through *location* and *alignment* properties of class [*CodetextParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/codetextparameters/).
  
#### **Alignment**
  
The *alignment* property is used to set the horizontal position of a text label in a barcode image: right-side, left-side, or center, as illustrated in the figures below. The default setting of barcode text alignment is *Center*. 
  
|Text Alignment|Left|Center|Right|
| :-: | :-: | :-: | :-: |
| |<img src="codetextaligmentleft.png">|<img src="codetextaligmentcenter.png">|<img src="codetextaligmentright.png">|
  

#### **Location**
  
The *location* property allows setting the vertical position of a text label, namely, placing it above or below bars, as shown in the figures below. The default setting is *Below*. 

  
|Text Location|Above Barcode|Below Barcode|
| :-: | :-: | :-: |
| |<img src="codetextlocationabove.png">|<img src="codetextlocationbelow.png">|
  
### **Spacing between Bars and Text Label**
The default spacing (gap) between bars and a text label is equal to 2pt. It is possible to modify this spacing using the *space* property of class [*CodetextParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/codetextparameters/). This property is not applicable to specific barcode types, including EAN-13, EAN-8, UPC-E, UPC-A, ISMN, ISBN, ISSN, and UpcaGs1DatabarCoupon.  
  
Sample barcode images shown below have been created with various spacing settings (five and forty pixels).
  
|Text Spacing|Is Set to 5 Pixels|Is Set to 40 Pixels|
| :-: | :-: | :-: |
| |<img src="codetextspace5pixels.png">|<img src="codetextspace40pixels.png">|
  
  
### **Font Settings**
To manage barcode text font, ***Aspose.BarCode for Python via .NET*** provides *font* and *font_mode* properties of class [*CodetextParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/codetextparameters/). The default font setting is Arial 5pt regular. This setting is ignored if the *Auto* mode is enabled using the *font_mode* property. This property is used to manage font size settings automatically. If it is called passing the *Auto* value, font size is determined automatically based on *x_dimension* in such a way that the text label should take only one text line. *FontMode.Auto* is recommended when *AutoSizeMode.Nearest* or *AutoSizeMode.Interpolation* settings are enabled. Alternatilvely, setting *FontMode.Manual* allows managing font size manually. Other font parameters, including font style, are set similarly in both *Auto* and *Manual* modes.  
  
Barcode images shown below have been created with these two font modes. 
    
|Font Setting Mode|Auto|Manual|
| :-: | :-: | :-: |
| |<img src="codetextfontmodeauto.png">|<img src="codetextfontmodemanual.png">|
  

### **NoWrap Mode for Text**
It is possible to avoid line breaks in a text that is too long for a single row using the *no_wrap* property of class [*CodetextParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/codetextparameters/). When the *True* setting is enabled, the text label is displayed in a single row regardless of the text length. The default setting is *False*. Barcode images shown below have been created with different *no_wrap* settings.

|Text Wrapping Mode|Wrap|No Wrap|
| :-: | :-: | :-: |
| |<img src="codetextlongtextwrap.png">|<img src="codetextlongtextnowrap.png">|
  
  
## **Replacing Barcode Text in 2D Barcodes**
To replace barcode text in 2D barcodes with some other text label with improved readability without modifications to the barcode image itself, it is possible to call the *two_d_display_text* property of class [*CodetextParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/codetextparameters/) and pass new text to be placed. This is applicable to selected 2D type, including QR Code, Aztec Code, Data Matrix, MaxiCode, PDF417, and DotCode.  
  
The sample barcode image shown below has been created using the *two_d_display_text* setting.
  
<p align="center"><img src="codetexttwoddisplaytext.png"></p>
  
## **Caption**  
***Aspose.BarCode for Python via .NET*** allows developers to place additional text labels in a barcode image in form of captions above and below barcodes. As demonstrated in the figure below, such text captions have a parameter called *Padding* that allows modifying spacing size between captions and the nearest element (barcodes, main text label, or borders). Both text captions are disabled by default. If required, they can be shown by one or both simultaneously.
     
<p align="center"><img src="caption_scheme.png"></p>

### **Caption Visibility**

As stated above, additional text captions *Caption_Above* and *Caption_Below* are disabled by default. When required, top and bottom caption labels can be shown independently from each other or enabled simultaneously. The *visible* property of class [*CaptionParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/captionparameters/) can be used to display one or two captions. Then, caption text can be inserted through the *text* property. If required, caption labels can replace main text in 1D barcodes by enabling the former and disabling the latter. The figures given below demonstrate how to caption positioning options.
  
|Caption Visibility|Above|Below|
| :-: | :-: | :-: |
| |<img src="captionvisibleabove.png">|<img src="captionvisiblebelow.png">|

### **Text Positioning**
The *alignment* property of class [*CaptionParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/captionparameters/) allows modifying horizontal positions of caption labels in three directions: right, left, and center. The default position of captions is center. The figures shown below demonstrate barcode images with the top caption label with different alignment positions.
  
|Caption Alignment|Left|Center|Right|
| :-: | :-: | :-: | :-: |
| |<img src="captionalignmentleft.png">|<img src="captionalignmentcenter.png">|<img src="captionalignmentright.png">|
  
   
### **Caption Padding**
The *padding* property of class [*CaptionParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/captionparameters/) can be used to manage spacings for text captions. By default, the spacing value is set to {5pt; 5pt; 0; 5pt} for the top caption and {0; 5pt; 5pt; 5pt} for the bottom one according to the standard Rectangle setting {Top, Left, Bottom, Right}. This property is inapplicable when captions are disabled. Barcode images shown below have been generated with different padding settings.
  
|Caption Padding|Is Set to 5 Pixels|Is Set to 40 Pixels|
| :-: | :-: | :-: |
| |<img src="captionpadding5pixels.png">|<img src="captionpadding40pixels.png">|
  

### **Caption Font**
***Aspose.BarCode for Python via .NET*** does not enable automatic font size settings based on barcode size. Accordingly, caption font size requires manual setting. For top and bottom captions, various parameters, including font style and size can be set independently. Caption font can be customized using the properties of class [*FontUnit*](/barcode/python-net/api-reference/aspose.barcode.generation/fontunit/). The default setting for caption font is Arial 8pt regular. 
The barcode image shown below explains different caption font settings.
   
<p align="center"><img src="captionfont.png"></p>
  

### **NoWrap Mode for Caption**
The *no_wrap* property of class [*CaptionParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/captionparameters/) allows disabling text line breaks when a text string is too large to fit in one line. When this property is initiated using the *True* value, caption text is always displayed as a single line. Barcode images below show the difference between *true* and *false* settings.
  
|Caption Wrapping|*no_wrap* Is Set to *False*|*no_wrap* Is Set to *True*|
| :-: | :-: | :-: |
| |<img src="captiontextwrap.png">|<img src="captiontextnowrap.png">|
  
