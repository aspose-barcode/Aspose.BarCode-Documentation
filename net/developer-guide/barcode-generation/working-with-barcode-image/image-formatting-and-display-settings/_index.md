---
title: Image Formatting and Display Settings
type: docs
weight: 10
url: /net/image-formatting-and-display-settings/
---

## **Working with Image Borders**
[Aspose.BarCode](https://apireference.aspose.com/barcode/net/) allows its users to handle everything about barcode image borders, which include setting border style, margins, and its width. Let's experience these features one by one.
### **Border Style**
Developers can customize the border style of the barcode image using BarcodeGenerator.[Border.DashStyle](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/borderparameters/properties/dashstyle) property that is included in all barcode generating classes in Aspose.BarCode. The Aspose.BarCode offers some built-in border styles which are contained in an enumeration also named as [BorderDashStyle](https://apireference.aspose.com/barcode/net/aspose.barcode/borderdashstyle). Developers can select the desired border style from this enumeration and then assign that selected border style to the [Border.DashStyle](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/borderparameters/properties/dashstyle) property of the BarcodeGenerator class. The pre-defined border styles in BorderDashStyle enumeration are as follows:

|**Border Styles**|**Description**|
| :- | :- |
|Dash|Specifies a line consisting of dashes|
|DashDot|Specifies a line consisting of a repeating pattern of dash-dot|
|DashDotDot|Specifies a line consisting of a repeating pattern of dash-dot-dot|
|Dot|Specifies a line consisting of dots|
|Solid|Specifies a solid line|
The border styles described above are demonstrated graphically in the figure below:

|**Pre-defined border styles**|
| :- |
|![todo:image_alt_text](image-formatting-and-display-settings_1.jpg)|

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarCodes-SetBorderStyle-SetBorderStyle.cs" >}}

{{% alert color="primary" %}} 

Aspose.BarCode for Java does not support Border features.

{{% /alert %}} 
### **Border Width**
A very simple but handy feature is to set the border width of the barcode image. The border can be made thick or thin by setting [Width](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/borderparameters/properties/width) property of the Border class.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarCodes-BorderWidth-BorderWidth.cs" >}}


### **Enable Image Border**
Developers may also decide whether to show or hide an image border by setting the [Visible](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/borderparameters/properties/visible) property of the Border class to true or false.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarCodeImages-EnableImageBorder-EnableImageBorder.cs" >}}

A complete example to handle the borders of the barcode image is given below.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarcodeImages-BarcodeImageBorders-BarcodeImageBorders.cs" >}}


## **Colorize portion of Barcode Image**
Normally, barcodes are generated and printed in black and white colors. But, what if it is required to generate a colored barcode?. Keeping this possible requirement in mind, [Aspose.BarCode](https://apireference.aspose.com/barcode/net/) gives free hand to developers to change the colors of:

- Barcode
- Code text
- Barcode Background
- Barcode Border
- Caption

All barcode classes ( [BarcodeGenerator](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) and [BarCodeGeneratorControl](https://apireference.aspose.com/barcode/net/aspose.barcode.windows.forms/barcodegeneratorcontrol)) provided by Aspose.BarCode have some common properties that are used to colorize different parts of a barcode as follows:

- BarColor property to assign any color to the Barcode
- CodeTextStyle.Color property to assign any color to the Code text of the barcode
- BackColor property to set the background color of the barcode
- Border.Color property to set the Border color of the barcode

Developers can select any desired color using System.Drawing.Color structure (part of Microsoft .NET Framework) and then assign that selected color to any of the properties (BarColor, CodeTextColor, BackColor or BorderColor) according to their custom requirements. The following code snippet shows you how to colorize a portion of the barcode Image.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarcodeImages-ColorizeAnyPartoftheBarcodeImage-ColorizeAnyPartoftheBarcodeImage.cs" >}}


## **Control Bars Filling of 1D Barcodes**
[Aspose.BarCode](https://apireference.aspose.com/barcode/net/) supports the new property [FilledBars](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/filledbars) for BarcodeGenerator for generating filled or not filled bars. This property works only with 1D barcodes. The default value is true (filled).

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarcodeImages-ControlBarsFillingofOneDBarcodes-ControlBarsFillingofOneDBarcodes.cs" >}}
## **Set Barcode Image Padding**
Developers can set the border paddings of the barcode image by setting the padding property found in any BarcodeGenerator class provided by Aspose.BarCode. The Padding property takes an instance of Aspose.BarCode.Generation.Padding class that specifies Left, Right, Top and Bottom padding settings.

|**BarCode Image Padding**|
| :- |
|![todo:image_alt_text](image-formatting-and-display-settings_2.png)|

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarcodeImages-BarcodeImageMargins-BarcodeImageMargins.cs" >}}
## **Rotate Barcode Image**
[Aspose.BarCode](https://apireference.aspose.com/net/barcode) allows developers to rotate the barcode image by setting the [RotationAngle ](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/rotationangle)property of the BarcodeGenerator class.

|**Demonstration of common rotation angles**|
| :- |
|![todo:image_alt_text](image-formatting-and-display-settings_3.jpg)|

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarcodeImages-RotateBarcode-RotateBarcode.cs" >}}


## **Customize Barcode Image Resolution**
What if developers need to set the resolution of their barcode images according to their custom settings? Well, [Aspose.BarCode](https://apireference.aspose.com/barcode/net/) also addresses this issue and provides [Resolution](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/resolution) class that serves developers to customize the resolution of their barcode images in any way they want. Resolution property gets or sets the resolution of the BarCode image. One value for both dimensions.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarcodeImages-BarcodeImageResolution-BarcodeImageResolution.cs" >}}

## **Set Size Unit for the Barcode Image**
To change the measuring unit of the barcode image, developers can make use of [Unit ](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/unit)class properties of any barcode class ([BarcodeGenerator](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator), or [BarCodeControl](https://apireference.aspose.com/barcode/net/aspose.barcode.windows.forms/barcodegeneratorcontrol)) provided by [Aspose.BarCode](https://apireference.aspose.com/barcode/net/). Unit specifies the size value in different units as follows:

|**Measuring Units**|**Description**|
| :- | :- |
|Document|Specifies the document unit (1/300 inch) as the unit of measure|
|Inch|Specifies the inch as the unit of measure|
|Millimeter|Specifies the millimeter as the unit of measure|
|Pixel|Specifies a device pixel as the unit of measure|
|Point|Specifies a printer's point (1/72 inch) as the unit of measure|
The default size measurement unit for the barcode image is Millimeter. An example is given below that changes the bar height of the barcode but the measuring unit being used for the bar height is Point.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarcodeImages-SetSizeUnitForBarcodeImage-SetSizeUnitForBarcodeImage.cs" >}}
## **Generate Barcode by Specifying Custom Image Size**
Aspose.BarCode for .NET automatically adjusts the image size (width and height) according to the generated barcode’s size. But, you can also control the image size by specifying the height and width of the image using BarcodeGenerator.BarCodeHeight and BarCodeWidth properties. [BarcodeGenerator.AutoSizeMode](https://apireference.aspose.com/barcode/net/aspose.barcode.windows.forms/barcodegeneratorcontrol/properties/autosizemode) should be set to none in order to customize the image size. In the below example, we will generate a Code39Standard barcode with customized height and width.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarcodeImages-BarcodeCustomSize-BarcodeCustomSize.cs" >}}
