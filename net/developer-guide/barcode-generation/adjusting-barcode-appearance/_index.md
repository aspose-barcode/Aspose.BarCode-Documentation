---
title: Adjusting Barcode Appearance using C# Library
linktitle: Adjusting Barcode Appearance
type: docs
weight: 30
description: "How to Adjust Barcode Appearance-Related Properties in Aspose.BarCode for .NET"
keywords: "Generate Barcodes, Customize Barcode Image, Change Barcode Appearance, Barcode Appearance in Aspose.BarCode for .NET, Work with Barcode Image in Aspose.BarCode for .NET, Generate Barcodes in Aspose.BarCode"
url: /net/image-formatting-and-display-settings/
---
This article provides all necessary information about adjusting barcode appearance-related properties, including image size, rotation angle, paddings, and borders.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
In ***Aspose.BarCode for .NET***, class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) allows creating barcode labels according to the specified scenario where each element has the fixed position relative to other elements in a barcode image, as shown in the scheme below. A barcode image may include the following elements: barcode bars, borders, paddings, top and bottom captions, and barcode text. All elements besides the barcode label itself are optional.
  
<p align="center"><img src="barcode_view_scheme.png"></p>
 
## **Barcode Image Sizing Modes**

In the general case, ***Aspose.BarCode for .NET*** adjusts the size of a barcode image (width and height) automatically. However, it is possible to customize the image size settings manually by specifying the height and width of a barcode image using [*ImageHeight*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/imageheight) and [*ImageWidth*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/imagewidth) properties of class [*BaseGenerationParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters).  
  
The size of a barcode image can be managed according to different sizing modes that can be set by initializing the [*AutoSizeMode*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/autosizemode) property of class *BaseGenerationParameters*. This parameter can take the following values: *Interpolation*, *Nearest*, and *None*. The *Interpolation* and *Nearest* modes imply that barcode image size gets adjusted according to the required values of width and height while most of the other parameters are ignored. In contrast, the *None* mode defines the size of a barcode image ignoring width and height but considers other parameters, for example, such as [*XDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/xdimension). By default, *AutoSizeMode* is set to "*None"*.  
   
Below, the available barcode sizing modes are described in detail along with sample barcode labels and code snippets.

### **AutoSizeMode.None** 
As mentioned previously, when the *None* mode is set, the size of the generated barcode image is based on various parameters while the values of width and height are not taken into consideration. The main parameter used to define barcode size is the [*XDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/xdimension) property. It specifies the minimum size value of bars for 1D barcodes or cells for 2D ones. Then, this value is used to calculate most of the other barcode parameters.  
  
Barcode symbologies usually specify the minimum value (*XDimension*) to ensure compatibility between scanning and printing equipment used in open systems (barcode labels need to be readable by scanners utilized in different companies). *X-Dimension* determines the density of a symbology, in other words, defines the amount of information that can be stored in a barcode. When *X-Dimension* is small, the area required to display each character in a barcode label is less compared with the case when *X-Dimension* is large; thus a barcode can store more information per linear inch and is considered to be of higher density. Otherwise, increasing the width of the narrowest element (*X-Dimension*) enlarges the space required for each character and reduces the number of characters per inch.  
    
The barcode image provided below has been created in the *None* mode.

<p align="center"><img src="autosizemodenone.png"></p>
  
The following code snippet illustrates how to set the *AutoSizeMode* property to *None*.  

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE");
gen.Parameters.AutoSizeMode = AutoSizeMode.None;
gen.Parameters.ImageWidth.Pixels = 300;
gen.Parameters.ImageHeight.Pixels = 300;
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}AutoSizeModeNone.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  

### **AutoSizeMode.Interpolation**
When the [*AutoSizeMode*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/autosizemode) property is set to "*Interpolation*", only the values of [*ImageHeight*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/imageheight) and [*ImageWidth*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/imagewidth) are taken into account. This sizing mode prescribes to adjust barcode image size to the specified height and width precisely even though it may lead to the distortion of barcode proportions and accordingly, to the loss of barcode readability for side scanners. The *Interpolation* mode is suitable to generate barcode images with the resolution of 300 dpi or higher as in this case proportion distortion will be negligible and will not affect barcode readability.  
  
The sample barcode image created using the *Interpolation* mode is shown below.  

<p align="center"><img src="autosizemodeinterpolation.png"></p> 

The following code sample explains how to initialize the *AutoSizeMode* property with the *Interpolation* value.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE");
gen.Parameters.AutoSizeMode = AutoSizeMode.Interpolation;
gen.Parameters.ImageWidth.Pixels = 300;
gen.Parameters.ImageHeight.Pixels = 300;
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}AutoSizeModeInterpolation.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
### **AutoSizeMode.Nearest** 
The *Nearest* mode uses only the values of [*ImageHeight*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/imageheight) and [*ImageWidth*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/autosizemode) to set the size of the resulting barcode image similarly to *Interpolation*. However, in this case, *BarcodeGenerator* seeks to specify the most appropriate image size to avoid distorting barcode proportions and deteriorating its readability.  
  
The resulting barcode image generated using the *Nearest* mode is demonstrated below.
  
<p align="center"><img src="autosizemodenearest.png"></p>
  
The following code snippet shows how to set the *Nearest* mode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE");
gen.Parameters.AutoSizeMode = AutoSizeMode.Nearest;
gen.Parameters.ImageWidth.Pixels = 300;
gen.Parameters.ImageHeight.Pixels = 300;
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}AutoSizeModeNearest.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
## **Barcode Rotation**
***Aspose.BarCode for .NET*** enables barcode image rotation that can be performed by initializing the [*RotationAngle*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/rotationangle) property of class [*BaseGenerationParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters). Setting this property to a value in degrees results in generating a barcode image rotated according to the required angle clockwise or counterclockwise.  
  
The sample barcode images rotated by different angles are represented below.
  
|<p align="center">**Rotation Angle**</p>|<p align="center">**Is Set to +90°**</p>|<p align="center">**Is Set to -90°**</p>|<p align="center">**Is Set to +45°**</p>|<p align="center">**Is Set to -45°**</p>|<p align="center">**Is Set to 180°**</p>| 
| :-: | :-: | :-: | :-: | :-: | :-: | 
| |<img src="rotationangle+90.png">|<img src="rotationangle-90.png">|<img src="rotationangle+45.png">|<img src="rotationangle-45.png">|<img src="rotationangle180.png">|
  
The following code snippet illustrates how to set various rotation angles.
   
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "ASPOSE");
gen.Parameters.RotationAngle = 90;
gen.Save($"{path}RotationAngle+90.png", BarCodeImageFormat.Png);
gen.Parameters.RotationAngle = -90;
gen.Save($"{path}RotationAngle-90.png", BarCodeImageFormat.Png);
gen.Parameters.RotationAngle = 45;
gen.Save($"{path}RotationAngle+45.png", BarCodeImageFormat.Png);
gen.Parameters.RotationAngle = -45;
gen.Save($"{path}RotationAngle-45.png", BarCodeImageFormat.Png);
gen.Parameters.RotationAngle = 180;
gen.Save($"{path}RotationAngle180.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
## **Customizing Barcode Borders and Padding**
***Aspose.BarCode for .NET*** enables adjusting barcode borders and paddings during barcode generation. By default, borders are placed tightly to image edges; then, corresponding paddings may be specified.
  
### **Border Settings**
According to the default settings, a barcode image is generated without borders; however, they can be specified explicitly according to five different styles: solid, dashed, dotted, dash-dot, and dash dot dot. Border appearance can be adjusted using the [*Border*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/border) property of class [*BaseGenerationParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters). In turn, this property gets an instance of class [*BorderParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/borderparameters) that contains all barcode configuration settings. In addition, this class enables adjusting border thickness (that can be defined in any supported [**units**](http://localhost:1313/barcode/net/setting-barcode-parameters/#measuring-barcode-size-in-different-units)) and color by initializing the [*Width*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/borderparameters/properties/width) and [*Color*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/borderparameters/properties/color) properties, respectively.  
  
Barcode images provided below are the sample barcode labels generated using different border styles. The border style can be customized by initializing the [*DashStyle*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/borderparameters/properties/dashstyle) of class *BorderParameters*.
  
|<p align="center">**Border Style**</p>|<p align="center">**Solid**</p>|<p align="center">**Dashed**</p>|<p align="center">**Dotted**</p>|<p align="center">**Dash Dot**</p>|<p align="center">**Dash Dot Dot**</p>| 
| :-: | :-: | :-: | :-: | :-: | :-: | 
| |<img src="bordersolid.png">|<img src="borderdash.png">|<img src="borderdot.png">|<img src="borderdashdot.png">|<img src="borderdashdotdot.png">|
  
The following code sample explains how to set the required barcode border style.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "ASPOSE");
//set border visible
gen.Parameters.Border.Visible = true;
//set border size to 5 pixels
gen.Parameters.Border.Width.Pixels = 5;
gen.Parameters.Border.DashStyle = BorderDashStyle.Solid;
gen.Save($"{path}BorderSolid.png", BarCodeImageFormat.Png);
gen.Parameters.Border.DashStyle = BorderDashStyle.Dash;
gen.Save($"{path}BorderDash.png", BarCodeImageFormat.Png);
gen.Parameters.Border.DashStyle = BorderDashStyle.Dot;
gen.Save($"{path}BorderDot.png", BarCodeImageFormat.Png);
gen.Parameters.Border.DashStyle = BorderDashStyle.DashDot;
gen.Save($"{path}BorderDashDot.png", BarCodeImageFormat.Png);
gen.Parameters.Border.DashStyle = BorderDashStyle.DashDotDot;
gen.Save($"{path}BorderDashDotDot.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

### **Paddings**
The border paddings from the edges of a barcode image or its borders can be set in four directions by initializing the [Padding](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/padding) property of class [*BarcodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters). The *Padding* property creates an instance of class [Aspose.BarCode.Generation.Padding](https://reference.aspose.com/barcode/net/aspose.barcode.generation/padding) that specifies the *Left*, *Right*, *Top*, and *Bottom* padding settings. The default values are set to 5 points in all directions.
  
|<p align="center">**Padding**</p>|<p align="center">**Millimeters**</p>|<p align="center">**Pixels**</p>|  
| :-: | :-: | :-: |  
| |<img src="padding10millimeters.png">|<img src="padding10pixels.png">| 

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "ASPOSE");
//set border
gen.Parameters.Border.Visible = true;
gen.Parameters.Border.Width.Pixels = 5;
gen.Parameters.Border.DashStyle = BorderDashStyle.Solid;
//set padding to 10 pixels
gen.Parameters.Barcode.Padding.Left.Pixels = 10;
gen.Parameters.Barcode.Padding.Top.Pixels = 10;
gen.Parameters.Barcode.Padding.Right.Pixels = 10;
gen.Parameters.Barcode.Padding.Bottom.Pixels = 10;
gen.Save($"{path}Padding10Pixels.png", BarCodeImageFormat.Png);
//set padding to 10 millimeters
gen.Parameters.Barcode.Padding.Left.Millimeters = 10;
gen.Parameters.Barcode.Padding.Top.Millimeters = 10;
gen.Parameters.Barcode.Padding.Right.Millimeters = 10;
gen.Parameters.Barcode.Padding.Bottom.Millimeters = 10;
gen.Save($"{path}Padding10Millimeters.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
## **Bar Width Reduction**
The width of bars in a barcode is an important parameter that requires to be set with high precision to ensure proper barcode scanning. Depending on the way of barcode printing, the initially specified width of bars may increase after printing out barcode labels due to ink floating. This effect is common in commercial printing where conventional printing presses are widely used. Therefore, to ensure that printed barcode labels have acceptable bar width, it may be necessary to set an appropriate bar width reduction value.  
  
Bar width reduction (BWR) is a method to adjust a graphic design file of a barcode aiming to compensate for ink floating. ***Aspose.BarCode for .NET*** allows adjusting the width of bars in generated barcodes by setting the [*BarWidthReduction*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/barwidthreduction) property of class [*BarcodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters). Initializing this property with the required value results in decreasing the width of bars or the size of cells in 1D and 2D barcodes, respectively. The BWR value for a particular printer is defined by printer manufacturers and can be found in dedicated tables. Note that adjusting this parameter does not have any impact in the case of laser printers.  
  
The sample barcodes shown below have been generated with and without applying bar width reduction.
  
|<p align="center">**Symbology**</p>|<p align="center">**Bar Width Reduction 0**</p>|<p align="center">**Bar Width Reduction 3**</p>|  
| :-: | :-: | :-: |  
|**Code 128**|<img src="code128barwidthreduction0.png" width="50%" height="50%">|<img src="code128barwidthreduction3.png" width="50%" height="50%">| 
|**Data Matrix**|<img src="datamatrixbarwidthreduction0.png" width="50%" height="50%">|<img src="datamatrixbarwidthreduction4.png" width="50%" height="50%">|
  
The following code example describes how to set bar width reduction.
   
{{< highlight csharp>}}
//Code 128
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "ASPOSE");
gen.Parameters.Barcode.XDimension.Pixels = 10;
//Code 128 without barwidth rediction
gen.Parameters.Barcode.BarWidthReduction.Pixels = 0;
gen.Save($"{path}Code128BarWidthReduction0.png", BarCodeImageFormat.Png);
//Code 128 with 4 pix barwidth rediction
gen.Parameters.Barcode.BarWidthReduction.Pixels = 4;
gen.Save($"{path}Code128BarWidthReduction4.png", BarCodeImageFormat.Png);

//DataMatrix
gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE");
gen.Parameters.Barcode.XDimension.Pixels = 10;
//DataMatrix without barwidth rediction
gen.Parameters.Barcode.BarWidthReduction.Pixels = 0;
gen.Save($"{path}DataMatrixBarWidthReduction0.png", BarCodeImageFormat.Png);
//DataMatrix with 4 pix barwidth rediction
gen.Parameters.Barcode.BarWidthReduction.Pixels = 4;
gen.Save($"{path}DataMatrixBarWidthReduction4.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
