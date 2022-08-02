---
title: Barcode Appearance Customization
type: docs
weight: 30
description: "How to Customize Barcode Appearance-Related Properties in Aspose.BarCode for Android"
keywords: "generate barcodes, customize barcode image, change barcode appearance, barcode appearance in Android, customize barcodes, work with barcode image, generate barcodes in Aspose.BarCode"
url: /androidjava/barcode-appearance-customization/
---
In the present article, you can find details about customizing various parameters of barcodes to be generated, such as barcode label size, rotation angle, barcode paddings, and barcode image borders.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
***Aspose.BarCode for Android via Java*** provides class [*BarcodeGenerator*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/BarcodeGenerator) to generate barcodes in line with the predefined settings so that each element of a barcode image gets its fixed position relatively to other elements, as shown in the scheme below. A barcode label comprises the following parts: barcode text, bars, top and bottom captions, image borders, and paddings. All elements besides barcode bars are optional.
  
<p align="center"><img src="barcode_view_scheme.png"></p>
 
## **Barcode Image Sizing Modes**

In general, ***Aspose.BarCode for Android via Java*** defines barcode image size in terms of height and width automatically. The library enables developers to manage image size settings manually by determining the height and width of barcode labels through *setImageHeight(Unit value)* and *setImageWidth(Unit value)* methods of class [*BaseGenerationParameters*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/BaseGenerationParameters).  
  
Barcode image size can be varied by using varios sizing modes that can be enabled using the [*AutoSizeMode*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/AutoSizeMode) enum of class [*BaseGenerationParameters*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/BaseGenerationParameters). *AutoSizeMode* provides the following options: *NONE*, *NEAREST*, and *INTERPOLATION*. In *Interpolation* and *Nearest* modes, barcode image size is managed based on the values of width and height, and other parameters are ignored. In turn, when the *None* mode is enabled, barcode image size is defined ignoring width and height; instead, other parameters, such as *XDimension*, are used. *AutoSizeMode* takes the *NONE* value by default.  
   
Further in the article, different barcode sizing modes are discussed.

### **AutoSizeMode.None** 
As outlined above, setting the *None* mode implies that barcode image size is managed based on different parameters ignoring width and height. To specify barcode size, class [*BarcodeParameters*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/BarcodeParameters) provides a special method called *setXDimension*. It is used to define the minimum size of bars in 1D barcodes or cells in 2D barcodes. Other barcode sizing parameters are calculated based on the *XDimension* value.  
  
Various barcode standards often determine *XDimension* to provide compatibility between printing and scanning equipment units so that barcode images could be captured by scanners used in various companies. *XDimension* is related to the data density of a barcode type, meaning that it determines the amount of data that can be encoded in one barcode. Setting a small value of *XDimension* results in covering less space to place each encoded character in a barcode image. In contrast, setting a bigger value of *XDimension* leads to enlarging the area required to encode each character and decreasing the number of characters per inch.  
    
The barcode label shown below has been generated using the *None* mode.

<p align="center"><img src="autosizemodenone.png"></p>
  
<!--The following code sample explains how to set the *AutoSizeMode* property to *None*.  

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE");
gen.Parameters.AutoSizeMode = AutoSizeMode.None;
gen.Parameters.ImageWidth.Pixels = 300;
gen.Parameters.ImageHeight.Pixels = 300;
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}AutoSizeModeNone.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
  

### **AutoSizeMode.Interpolation**
Setting *AutoSizeMode.INTERPOLATION* means that only the values specified using *setImageHeight* and *setImageWidth* methods are used to set the barcode size. In this case, barcode image size is determined using the manually specified values of height and width even when it results in producing distorted barcode proportions and the deterioration of barcode readability. The *Interpolation* mode is appropriate to create barcode images with the resolution of 300 dpi or higher. Using such resolution will allow keeping barcode distortions negligible and avoiding the descrease of barcode readability.  
  
The barcode label generated through the *Interpolation* mode is demonstrated below.  

<p align="center"><img src="autosizemodeinterpolation.png"></p> 

<!--The following code snippet shows how to enable *AutoSizeMode.INTERPOLATION*.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE");
gen.Parameters.AutoSizeMode = AutoSizeMode.Interpolation;
gen.Parameters.ImageWidth.Pixels = 300;
gen.Parameters.ImageHeight.Pixels = 300;
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}AutoSizeModeInterpolation.png", BarCodeImageFormat.Png);
{{< /highlight >}}--> 
  
### **AutoSizeMode.Nearest** 
To set barcode image size, the *Nearest* mode uses only the values specified using *setImageHeight* and *setImageWidth* methods similarly to the *Interpolation* mode. In this mode, [*BarcodeGenerator*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/BarcodeGenerator) aims at finding the most suitable image size to avoid barcode proportion distortion and readability deterioration.  
  
The barcode label created through the *Nearest* mode is provided below.
  
<p align="center"><img src="autosizemodenearest.png"></p>
  
<!--The following code snippet shows how to set the *Nearest* mode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE");
gen.Parameters.AutoSizeMode = AutoSizeMode.Nearest;
gen.Parameters.ImageWidth.Pixels = 300;
gen.Parameters.ImageHeight.Pixels = 300;
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}AutoSizeModeNearest.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
  
## **Barcode Rotation**
In ***Aspose.BarCode for Android via Java***, barcode image rotation can be set through the *setRotationAngle* method of class [*BaseGenerationParameters*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/BaseGenerationParameters). Passing a value in degrees to this method allows generating a barcode image rotated at the desired angle clockwise or counterclockwise.  
  
The sample barcode labels rotated by various angles are shown below.
  
|Rotation Angle|Is Set to +90°|Is Set to -90°|Is Set to +45°|Is Set to -45°|Is Set to 180°| 
| :-: | :-: | :-: | :-: | :-: | :-: | 
| |<img src="rotationangle+90.png">|<img src="rotationangle-90.png">|<img src="rotationangle+45.png">|<img src="rotationangle-45.png">|<img src="rotationangle180.png">|
  
<!--The following code sample explains how to rotate barcode images at different angles.
   
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
{{< /highlight >}}--> 
  
## **Customizing Barcode Borders and Padding**
***Aspose.BarCode for Android via Java*** allows customizing barcode image borders and paddings. Corresponding methods are described further.
  
### **Border Settings**
Applying default border settings results in generating barcode images without borders. Alternatively, they can be defined manually using five styles: solid, dotted, dashed, dash-dot, and dash dot dot. The border style can be modified using special class [*BorderParameters*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/BorderParameters). In addition, this class allows setting border thickness in any available units and colors through *setWidth* and *setColor* methods. Border styles can be changed using the *setDashStyle* method of the same class. 
  
Barcode labels demonstrated below have been generated using different border styles. 
  
|Border Style|Solid|Dashed|Dotted|Dash Dot|Dash Dot Dot| 
| :-: | :-: | :-: | :-: | :-: | :-: | 
| |<img src="bordersolid.png">|<img src="borderdash.png">|<img src="borderdot.png">|<img src="borderdashdot.png">|<img src="borderdashdotdot.png">|
  
<!--The following code snippet demonstrates how to set different border styles.
  
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
{{< /highlight >}}--> 

### **Paddings**
Paddings from the edges of a barcode image or its borders can be set in four directions using a special class called [*Padding*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/Padding) and its methods: *setLeft*, *setRight*, *setTop*, and *setBottom*. By default, the padding value is set to 5 points in all directions.
  
|Padding|Millimeters|Pixels|  
| :-: | :-: | :-: |  
| |<img src="padding10millimeters.png">|<img src="padding10pixels.png">| 

<!--{{< highlight csharp>}}
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
{{< /highlight >}}--> 
  
## **Bar Width Reduction**
The other important property that needs to be determined accurately is bar width. Setting an approriate value of this parameter is critical to assure successful barcode scanning. Due to the so-called ink floating phenomenon, some barcode printing techniques may result in increasing actual bar width after printing out barcode images. This happens often in commercial printing in cases when conventional printing presses are used. To ensure that printed barcode images will be printed out with appropriate bar width, setting a bar width reduction value may be required.  
  
Bar width reduction (BWR) is a way to mitigate the effecet of ink floating in a graphic design file of a barcode. ***Aspose.BarCode for Android via Java*** allows modifying bar width through the *setBarWidthReduction* method of class [*BarcodeParameters*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/BarcodeParameters). Passing the required value while calling this method allows decreasing bar width in 1D barcodes or cell size in 2D barcodes. To find out the suitable BWR value for a printer, it is necessary to check special tables provided by printer manufacturers. Modifying this parameter is not applicable to laser printers.  
  
The sample barcodes shown below have been generated with and without applying bar width reduction.
  
|Barcode Type|Bar Width Reduction 0|Bar Width Reduction 3|  
| :-: | :-: | :-: |  
|**Code 128**|<img src="code128barwidthreduction0.png" width="50%" height="50%">|<img src="code128barwidthreduction3.png" width="50%" height="50%">| 
|**Data Matrix**|<img src="datamatrixbarwidthreduction0.png" width="50%" height="50%">|<img src="datamatrixbarwidthreduction4.png" width="50%" height="50%">|
  
<!--The following code snippet explains how to implement bar width reduction.
   
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
{{< /highlight >}}--> 
  