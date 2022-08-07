---
title: Managing Barcode Text in C#
linktitle: Managing Barcode Text
type: docs
weight: 50
description: "How to Set Barcode Text and Captions in Aspose.BarCode for .NET"
keywords: "Generate Barcodes, Customize Barcode Image, Change Barcode Text, Barcode Appearance in Aspose.BarCode for .NET, Work with Barcode Image in Aspose.BarCode for .NET, Set Barcode Text in Aspose.BarCode, Generate Barcode with Caption, Generate Barcodes in Aspose.BarCode"
url: /net/working-with-barcode-text-appearance/
---

In the present article, you can find detailed information about how to manage text that can be placed onto barcode labels. To customize appearance-related parameters of barcode text in ***Aspose.BarCode for .NET***, developers can adjust various settings, such as visibility, location, font, spacings, and wrapping modes.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
Besides a barcode label itself, ***Aspose.BarCode for .NET*** enables the possibility to place human-readable text onto generated barcode images. This text information may include three fields as shown in the scheme below: main text, top caption, and bottom caption; any of these elements can be hidden.
    
<p align="center"><img src="barcode_text_scheme.png"></p>
   
## **Barcode Text**
Main barcode text represents short text information that is separated from the barcode label itself by some spacing. It can be placed on a barcode label in six different positions as shown in the scheme provided below: top left, top center, top right, bottom left, bottom center, or bottom right.
  
<p align="center"><img src="codetext_scheme.png"></p>
   
### **Text Visibility**

In ***Aspose.BarCode for .NET***, developers can decide whether barcode text needs to be displayed or not. In case, when there is no necessity to place additional text on a barcode image, it can be hidden as in the barcode sample image shown below.
  
<p align="center"><img src="codetexthide.png"></p>  
   
The following code snippet explains how to hide barcode text.
  
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
//hide codetext
gen.Parameters.Barcode.CodeTextParameters.Location = CodeLocation.None;
gen.Save($"{path}CodetextHide.png", BarCodeImageFormat.Png);

```
  
### **Text Positioning**
Barcode text can be adjusted on a barcode image in terms of its positioning, namely, location and alignment. To manage these parameters, it is necessary to initialize the [*Location*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/location) and [*Alignment*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/alignment) properties of class [CodetextParameters](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters).
  
**Location**
  
The [*Location*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/location) property is used to adjust the vertical position of barcode text: above or below the barcode label, as demonstrated in the figures below. By default, it is set to "Below". 
  
|Text Location|Above Barcode|Below Barcode|
| :-: | :-: | :-: |
| |<img src="codetextlocationabove.png">|<img src="codetextlocationbelow.png">|
  
The following code sample illustrates how to set the desired barcode text location.
    
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
//codetext Above
gen.Parameters.Barcode.CodeTextParameters.Location = CodeLocation.Above;
gen.Save($"{path}CodetextLocationAbove.png", BarCodeImageFormat.Png);
//codetext Below
gen.Parameters.Barcode.CodeTextParameters.Location = CodeLocation.Below;
gen.Save($"{path}CodetextLocationBelow.png", BarCodeImageFormat.Png);

``` 
  
**Alignment**
  
The [*Alignment*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/alignment) property allows modifying the horizontal position of barcode text: on the left, in the center, or on the right, as demonstrated in the figures below. By default, it is set to "Center". 
  
|Text Alignment|Left|Center|Right|
| :-: | :-: | :-: | :-: |
| |<img src="codetextaligmentleft.png">|<img src="codetextaligmentcenter.png">|<img src="codetextaligmentright.png">|
  
The following code example shows how to specify the required barcode text alignment.
     
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
//set Codetext Left alignment
gen.Parameters.Barcode.CodeTextParameters.Alignment = TextAlignment.Left;
gen.Save($"{path}CodetextAligmentLeft.png", BarCodeImageFormat.Png);
//set Codetext Center alignment
gen.Parameters.Barcode.CodeTextParameters.Alignment = TextAlignment.Center;
gen.Save($"{path}CodetextAligmentCenter.png", BarCodeImageFormat.Png);
//set Codetext Right alignment
gen.Parameters.Barcode.CodeTextParameters.Alignment = TextAlignment.Right;
gen.Save($"{path}CodetextAligmentRight.png", BarCodeImageFormat.Png);

``` 
  
### **Spacing between Barcode and Text**
By default, the spacing (gap) between a barcode label and text is rather small (2pt). Developers can increase or decrease this spacing by setting the [*Space*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/space) property of class [*CodetextParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters). This property is used to manage the spacing between barcode text and the barcode label from above or below depending on the barcode text position. It cannot be initialized for several symbologies, such as EAN8, EAN13, UPC E, UPC A, ISBN, ISMN, ISSN, and UpcaGs1DatabarCoupon.  
The images provided below illustrate the barcodes generated with different spacing settings, namely, five and forty pixels.
  
|Text Spacing|Is Set to 5 Pixels|Is Set to 40 Pixels|
| :-: | :-: | :-: |
| |<img src="codetextspace5pixels.png">|<img src="codetextspace40pixels.png">|
  
The following code snippet is provided to demonstrate how to adjust the spacing between the barcode label and text.
   
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
//codetext space 5 pixels
gen.Parameters.Barcode.CodeTextParameters.Space.Pixels = 5;
gen.Save($"{path}CodetextSpace5Pixels.png", BarCodeImageFormat.Png);
//codetext space 40 pixels
gen.Parameters.Barcode.CodeTextParameters.Space.Pixels = 40;
gen.Save($"{path}CodetextSpace40Pixels.png", BarCodeImageFormat.Png);

``` 
  
### **Text Font Settings**
To customize the font of barcode text, the [*Font*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/font) and [*FontMode*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/fontmode) properties of class [*CodetextParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters) need to be initialized. By default, the *Font* property is set to Arial 5pt regular; it is ignored in the case when the *Auto* mode is set in the *FontMode* property.  
The *FontMode* property allows adjusting the font size of barcode text. If *FontMode* is set to "*Auto*", font size is calculated automatically based on the value of *xDimension* so that the text should preferably fit into a single line. In contrast, the *Manual* mode implies setting font size by hand. It is recommended to use *FontMode.Auto* especially when the [*AutoSize*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/autosizemode) property is set to *AutoSizeMode.Nearest* or *AutoSizeMode.Interpolation*. Other parameters, such as font style, are initialized similarly in both *Auto* and *Manual* modes.  
  
The sample barcode images shown below have been generated using different font modes. 
    
|Font Setting Mode|Auto|Manual|
| :-: | :-: | :-: |
| |<img src="codetextfontmodeauto.png">|<img src="codetextfontmodemanual.png">|
  
**Auto Mode**
  
The following code sample illustrates how to set barcode text font in the *Auto* mode.
  
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
//automatic font set
gen.Parameters.Barcode.CodeTextParameters.FontMode = FontMode.Auto;
gen.Parameters.Barcode.CodeTextParameters.Font.FamilyName = "Lucida Handwriting";
gen.Parameters.Barcode.CodeTextParameters.Font.Style = FontStyle.Underline;
//font size is ignored
gen.Parameters.Barcode.CodeTextParameters.Font.Size.Point = 10;
gen.Save($"{path}CodetextFontModeAuto.png", BarCodeImageFormat.Png);

``` 
  
**Manual Mode**
  
The code snippet provided below explains how to set barcode text font in the *Manual* mode.
    
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
//manual font set
gen.Parameters.Barcode.CodeTextParameters.FontMode = FontMode.Manual;
gen.Parameters.Barcode.CodeTextParameters.Font.FamilyName = "Lucida Handwriting";
gen.Parameters.Barcode.CodeTextParameters.Font.Style = FontStyle.Underline;
//font size is set
gen.Parameters.Barcode.CodeTextParameters.Font.Size.Point = 10;
gen.Save($"{path}CodetextFontModeManual.png", BarCodeImageFormat.Png);

``` 

### **NoWrap Mode for Text**
The [*NoWrap*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/nowrap) property of class [*CodetextParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters) is used to disable line breaks within the text when it is too long for a single row. If *NoWrap* is set to "*True*", barcode text is always displayed in one row. By default, the property is set to "*False*". 
The figures below illustrate the difference in resulting barcode images in cases when the *NoWrap* property is set to *True* and *False*.

|Text Wrapping Mode|***Wrap*** Mode|***NoWrap*** Mode|
| :-: | :-: | :-: |
| |<img src="codetextlongtextwrap.png">|<img src="codetextlongtextnowrap.png">|
  
The following code sample illustrates how to enable and disable the *NoWrap* mode.
  
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Extremely long codetext for one row");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.Barcode.CodeTextParameters.FontMode = FontMode.Manual;
gen.Parameters.Barcode.CodeTextParameters.Font.Size.Point = 12;
//text wrapping mode on
gen.Parameters.Barcode.CodeTextParameters.NoWrap = false;
gen.Save($"{path}CodetextLongTextWrap.png", BarCodeImageFormat.Png);
//text wrapping mode off
gen.Parameters.Barcode.CodeTextParameters.NoWrap = true;
gen.Save($"{path}CodetextLongTextNoWrap.png", BarCodeImageFormat.Png);

```
  
## **Replacing Barcode Text in 2D Barcodes**
In case when it is necessary to replace the barcode text for 2D barcodes with some other text with better readability without changing the barcode itself, developers can initialize the [*TwoDDisplayText*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/twoddisplaytext) property of class [*CodetextParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters) by inserting new text to be displayed. This solution applies to the following 2D symbologies: Aztec, Pdf417, DataMatrix, QR, MaxiCode, and DotCode.  
  
The following barcode image has been generated with barcode text replaced by initializing the *TwoDDisplayText* property.
  
<p align="center"><img src="codetexttwoddisplaytext.png"></p>
  
The following code snippet explains how to replace barcode text for 2D barcodes.
    
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
//replace visible codetext for 2D barcodes: Aztec, Pdf417, DataMatrix, QR, MaxiCode, DotCode
gen.Parameters.Barcode.CodeTextParameters.TwoDDisplayText = "Replace Codetext";
gen.Save($"{path}CodetextTwoDDisplayText.png", BarCodeImageFormat.Png);

```
  
## **Caption**  
In some cases, it may be necessary to display additional text information on a barcode image. To address such a need, ***Aspose.BarCode for .NET*** enables the possibility to place captions above and below the barcode label. As shown in the scheme below, captions have a property called *Padding* that is used to specify the size of spacings for all sides between a caption and the nearest element (barcode label itself, barcode text, or border). By default, both captions are hidden; they can be displayed by one or both at the same time.
     
<p align="center"><img src="caption_scheme.png"></p>
  
### **Caption Visibility**

As previously mentioned, both captions, [*CaptionAbove*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/captionabove) and [*CaptionBelow*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/captionbelow) contained in class [*BaseGenerationParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters), are hidden by default. To display any of them or both, it is required to initialize the [*Visible*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters/properties/visible) property of class [*CaptionParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters) and enter some text information in the [*Text*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters/properties/text) property of the same class. Top and bottom captions can be placed on a barcode image independently from each other and barcode elements. If required, a caption can replace barcode text for 1D barcodes by setting the former visible and hiding the latter. The figures provided below illustrate how captions can be placed on generated barcode images.
  
|Caption Visibility|Above|Below|
| :-: | :-: | :-: |
| |<img src="captionvisibleabove.png">|<img src="captionvisiblebelow.png">|
  
The following code snippet explains how to set captions visible.
  
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
//set Top Caption visible
gen.Parameters.CaptionAbove.Visible = true;
gen.Parameters.CaptionAbove.Text = "Caption Above";
gen.Parameters.CaptionAbove.Font.Size.Point = 14;
gen.Save($"{path}CaptionVisibleAbove.png", BarCodeImageFormat.Png);
gen.Parameters.CaptionAbove.Visible = false;
//set Bottom Caption visible
gen.Parameters.CaptionBelow.Visible = true;
gen.Parameters.CaptionBelow.Text = "Caption Below";
gen.Parameters.CaptionBelow.Font.Size.Point = 14;
gen.Save($"{path}CaptionVisibleBelow.png", BarCodeImageFormat.Png);

```
    
### **Text Positioning**
The [*Alignment*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters/properties/alignment) is used to adjust the horizontal positioning of captions in three ways: on the left, in the center, or on the right. By default, captions are placed in the center position. The figures below represent the barcode images generated with the top caption aligned in three ways.
  
|Caption Alignment|Left|Center|Right|
| :-: | :-: | :-: | :-: |
| |<img src="captionalignmentleft.png">|<img src="captionalignmentcenter.png">|<img src="captionalignmentright.png">|
  
The following code sample shows how to adjust caption alignment.

``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.CaptionAbove.Visible = true;
gen.Parameters.CaptionAbove.Text = "Caption Above";
gen.Parameters.CaptionAbove.Font.Size.Point = 14;
//set Caption Above Left alignment
gen.Parameters.CaptionAbove.Alignment = TextAlignment.Left;
gen.Save($"{path}CaptionAlignmentLeft.png", BarCodeImageFormat.Png);
//set Caption Above Center alignment
gen.Parameters.CaptionAbove.Alignment = TextAlignment.Center;
gen.Save($"{path}CaptionAlignmentCenter.png", BarCodeImageFormat.Png);
//set Caption Above Right alignment
gen.Parameters.CaptionAbove.Alignment = TextAlignment.Right;
gen.Save($"{path}CaptionAlignmentRight.png", BarCodeImageFormat.Png);

``` 
   
### **Caption Padding**
The [*Padding*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters/properties/padding) property allows setting spacings for top and bottom captions. The default value is set to {5pt; 5pt; 0; 5pt} for *CaptionAbove* and to {0; 5pt; 5pt; 5pt} for *CaptionBelow* accoroding to the standard Windows Rectangle properties {Top, Left, Bottom, Right}. In the case of setting captions invisible this property is ignored. The sample barcode images provided below have been created adjusting the value of the *Padding* property for captions to five and forty pixels.
  
|Caption Padding|Is Set to 5 Pixels|Is Set to 40 Pixels|
| :-: | :-: | :-: |
| |<img src="captionpadding5pixels.png">|<img src="captionpadding40pixels.png">|
  
The following code snippet demonstrates how to set caption paddings.
  
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.CaptionAbove.Visible = true;
gen.Parameters.CaptionAbove.Text = "Caption Above";
gen.Parameters.CaptionAbove.Font.Size.Point = 14;
//Set all padding values around the Caption to 5 pixels
gen.Parameters.CaptionAbove.Padding.Left.Pixels = 5;
gen.Parameters.CaptionAbove.Padding.Top.Pixels = 5;
gen.Parameters.CaptionAbove.Padding.Right.Pixels = 5;
gen.Parameters.CaptionAbove.Padding.Bottom.Pixels = 5;
gen.Save($"{path}CaptionPadding5Pixels.png", BarCodeImageFormat.Png);
//Set all padding values around the Caption to 40 pixels
gen.Parameters.CaptionAbove.Padding.Left.Pixels = 40;
gen.Parameters.CaptionAbove.Padding.Top.Pixels = 40;
gen.Parameters.CaptionAbove.Padding.Right.Pixels = 40;
gen.Parameters.CaptionAbove.Padding.Bottom.Pixels = 40;
gen.Save($"{path}CaptionPadding40Pixels.png", BarCodeImageFormat.Png);

``` 

### **Caption Font**
***Aspose.BarCode for .NET*** does not provide the possibility to enable automatic font size adjustment depending on the size of a barcode label. Therefore, this parameter needs to be set manually. For top and bottom captions, it is possible to set the font, its style, and size independently. Caption font parameters can be adjusted using the [*Font*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters/properties/font) property of class [CaptionParameters](https://reference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters). By default, this property is set to Arial 8pt regular. 
The barcode image below illustrates how the caption font can be displayed according to the desired settings.
   
<p align="center"><img src="captionfont.png"></p>
  
The following code sample explains how to adjust caption font settings.
   
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.CaptionAbove.Visible = true;
gen.Parameters.CaptionAbove.Text = "Caption Above";
//set Caption font
gen.Parameters.CaptionAbove.Font.FamilyName = "Lucida Handwriting";
gen.Parameters.CaptionAbove.Font.Style = FontStyle.Underline;
gen.Parameters.CaptionAbove.Font.Size.Point = 10;
gen.Save($"{path}CaptionFont.png", BarCodeImageFormat.Png);

```

### **NoWrap Mode for Caption**

The [*NoWrap*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters/properties/nowrap) property of class [*CaptionParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/captionparameters) is intended to disable text line breaks in the case when a text string is too long to fit in a single line. When this property is set to "*True*", caption text is always displayed in a single line. The following barcode images show the difference in resulting barcode images in cases when the *NoWrap* property is initialized as *True* and *False*.
  
|Caption Wrapping|Is Set to *Wrap*|Is Set to *No Wrap*|
| :-: | :-: | :-: |
| |<img src="captiontextwrap.png">|<img src="captiontextnowrap.png">|
  
The code snippet provided below explains how to set the *NoWrap* mode for a barcode caption.
  
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.CaptionAbove.Visible = true;
gen.Parameters.CaptionAbove.Text = "Caption Above";
gen.Parameters.CaptionAbove.Font.Size.Point = 28;
//set wrapping Caption text mode
gen.Parameters.CaptionAbove.NoWrap = false;
gen.Save($"{path}CaptionTextWrap.png", BarCodeImageFormat.Png);
//set no wrapping Caption text mode
gen.Parameters.CaptionAbove.NoWrap = true;
gen.Save($"{path}CaptionTextNoWrap.png", BarCodeImageFormat.Png);

``` 
