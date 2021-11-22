---
title: Managing Barcode Text
type: docs
weight: 20
url: /net/managing-barcode-text/
---

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
