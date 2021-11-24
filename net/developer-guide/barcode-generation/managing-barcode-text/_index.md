---
title: Managing Barcode Text
type: docs
weight: 40
url: /net/managing-barcode-text/
---
## Overview
  
<p align="center"><img src="Barcode_Text_Scheme.png"></p>
  
## Barcode Text

<p align="center"><img src="Codetext_Scheme.png"></p>
  
### Text Positioning
**Location**
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
//codetext Above
gen.Parameters.Barcode.CodeTextParameters.Location = CodeLocation.Above;
gen.Save($"{path}CodetextLocationAbove.png", BarCodeImageFormat.Png);
//codetext Below
gen.Parameters.Barcode.CodeTextParameters.Location = CodeLocation.Below;
gen.Save($"{path}CodetextLocationBelow.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

|Text Location|Above|Below|
|---|:---:|:---:|
|**Output**|<img src="CodetextLocationAbove.png">|<img src="CodetextLocationBelow.png">|

**Alignment**

{{< highlight csharp>}}
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
{{< /highlight >}} 
  
|Text Alignment|Left|Center|Right|
|---|:---:|:---:|:---:|
|**Output**|<img src="CodetextAligmentLeft.png">|<img src="CodetextAligmentCenter.png">|<img src="CodetextAligmentRight.png">|


### Text Visibility

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
//hide codetext
gen.Parameters.Barcode.CodeTextParameters.Location = CodeLocation.None;
gen.Save($"{path}CodetextHide.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
<p align="center"><img src="Codetext_Hide.png"></p>
  
### Space between Barcode and Text
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
//codetext space 5 pixels
gen.Parameters.Barcode.CodeTextParameters.Space.Pixels = 5;
gen.Save($"{path}CodetextSpace5Pixels.png", BarCodeImageFormat.Png);
//codetext space 40 pixels
gen.Parameters.Barcode.CodeTextParameters.Space.Pixels = 40;
gen.Save($"{path}CodetextSpace40Pixels.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
|Text Spacing|5 Pixels|40 Pixels|
|---|:---:|:---:|
|**Output**|<img src="CodetextSpace5Pixels.png">|<img src="CodetextSpace40Pixels.png">|
  
### Text Font Settings

|Font Setting Mode|Auto|Manual|
|---|:---:|:---:|
|**Output**|<img src="CodetextFontModeAuto.png">|<img src="CodetextFontModeManual.png">|
  
**Auto Mode**  
{{< highlight csharp>}}
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
{{< /highlight >}} 
  
**Manual Mode**

{{< highlight csharp>}}
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
{{< /highlight >}} 

### NoWrap Mode for Text

|Wrapping Mode|Long Text Wrap|Long Text No Wrap|
|---|:---:|:---:|
|**Output**|<img src="CodetextLongTextWrap.png">|<img src="CodetextLongTextNoWrap.png">|

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Extremly long codetext for one row");
gen.Parameters.Barcode.Pdf417.Rows = 12;
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.Barcode.CodeTextParameters.FontMode = FontMode.Manual;
gen.Parameters.Barcode.CodeTextParameters.Font.Size.Point = 12;
//text wrapapping mode on
gen.Parameters.Barcode.CodeTextParameters.NoWrap = false;
gen.Save($"{path}CodetextLongTextWrap.png", BarCodeImageFormat.Png);
//text wrapapping mode off
gen.Parameters.Barcode.CodeTextParameters.NoWrap = true;
gen.Save($"{path}CodetextLongTextNoWrap.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
## Caption

<p align="center"><img src="Caption_Scheme.png"></p>

### Text Positioning

### Caption Visibility

### Caption Padding

### Caption Font

### NoWrap Mode for Caption

<!--
## **Customize the appearance of Code text**
[Aspose.BarCode for .NET](https://apireference.aspose.com/barcode/net/) provides the ability to manage the appearance of code text underlying the generated barcode. To customize appearance-related parameters, various settings can be applied to code text using the properties of *CodeTextParameters* class. 
### **Location of Code text**
***Aspose.BarCode for .NET*** allows developers to decide whether code text needs to be displayed or not. Moreover, it is possible to customize the display location of code text (above or below the generated barcode), as shown in the figure below.

|**Possible Locations of Code Text**|
| :- |
|![todo:image_alt_text](working-with-barcode-text-appearance_1.jpg)|
All barcode generation classes have *CodeTextParameters.Location* property that can accept any pre-defined value stored in *CodeLocation* enumeration. The values in [*CodeLocation* ](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/location) enumeration are listed below.

|**Code Locations**|**Description** |
| :- | :- |
|Above|Code text on the top of a barcode|
|Below |Code text on the bottom of a barcode|
|None |Code text is hidden|

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarcodeImages-SetCodetextLocation-SetCodetextLocation.cs" >}}


### **Alignment of Code Text**
The horizontal alignment of code text can be configured using *CodeTextParameters.Alignment* property of *BarcodeGenerator* class. *CodeTextParameters.Alignment* property accepts any enumerated value stored in *Aspose.BarCode.Generation.TextAlignment* enumeration (that is a part of Microsoft .NET Framework). The pre-defined values in *StringAlignment* enumeration are listed below.

|**Alignment Types**|**Description** |
| :- | :- |
|Center |Text in the center of the layout rectangle|
|Left|Text is left-aligned from the original position of the layout rectangle|
|Right|Text is right-aligned on the right of the layout rectangle|

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarcodeImages-SetCodeAlignment-SetCodeAlignment.cs" >}}


### **Color of Code Text**
Besides customizing barcode color, the color of code text can be changed as well; it can be done by setting *CodeTextParameters.Color* property, as demonstrated below in the provided code snippet.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarcodeImages-SetForeColorText-SetForeColorText.cs" >}}


### **Set Code Text Font Family Name and Size**
Setting *CodeTextParameters.Font* property to any font family name and modifying the size of code text can be done as demonstrated below in the code snippet.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarcodeImages-SetCodeTextFontFamilyNameAndSize-SetCodeTextFontFamilyNameAndSize.cs" >}}


### **Space between Code text and Barcode**
By default, the default gap between a barcode and code text is rather small. Developers can increase/decrease the space (gap) between a barcode and code text by setting *CodeTextParameters.Space* property. The following code snippet illustrates how to space between code text and the barcode.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarcodeImages-AddSpaceInBarCodeAndText-AddSpaceInBarCodeAndText.cs" >}}

The example provided below illustrates all possible format settings that can be applied to code text.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarCodes-CodetextAppearance-CodetextAppearance.cs" >}}
-->