---
title: Barcode Parameters
type: docs
weight: 40
description: "How to Manage Barcode Parameters in Aspose.BarCode for Android"
keywords: "Generate Barcodes, Customize Barcode Image, Barcode Size Units in Aspose.BarCode for Android via Java, Work with Barcode Image in Aspose.BarCode for Android, Generate Barcodes in Aspose.BarCode, Convert Barcode Size in Aspose.Barcode"
url: /androidjava/barcode-generation-parameters/

---
This article describes how to manage settings provided by ***Aspose.BarCode for Android via Java*** to adjust barcode measurement units (millimeters, inches, points, or pixels) and barcode image resolution.
  
## **Overview**
Cartesian coordinate systems use coordinates of pixels or drawable objects to represent image data for raster or vector images. To link these coordinates to real-world measurement units, such as millimeters or inches, ***Aspose.BarCode for Android via Java*** includes a special class called [*Unit*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/Unit) and its method called *updateResolution* that is intended to manage barcode resolution measured in dots per inch (dpi). Class [*Unit*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/Unit) provides various methods that serve to convert barcode size values defined in pixels, millimeters, inches, or points to any of the supported measurement units automatically. In this way, the size of elements in real-world measurement units can be converted into pixels to generate barcode images.  

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Measuring Barcode Size in Various Units**
Class [*Unit*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/Unit) allows developers to manage measurement units for barcode parameters and can be modified using special methods of class [*BarcodeParameters*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/BarcodeParameters), such as *setBarCodeHeight*, *setBarCodeWidth*, and *setXDimension*. ***Aspose.BarCode for Android via Java*** determines measurement units in the [*GraphicsUnit*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/GraphicsUnit) enum that is defined as an internal representation of a Java interface called **java.lang.Comparable<GraphicsUnit>**. Class [*Unit*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/Unit) can be used to convert measurement units into the desired ones: *Millimeters*, *Pixels*, *Inches*, *Point* (1/72 inch), or *Document* (1/300 inch). By default, *Millimeters* are used as size measurement units.  
  
Barcode labels created using various unit settings are shown below.
   
|Size Units|Pixels|Millimeters|
| :-: | :-: | :-: |
| |<image src="unitin3pixels.png">|<image src="unitin2millimeters.png">|
  
<!--The following code sample explains how to manage various resolution settings.

{{< highlight java>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE");
//set unit size in 3 pixels
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}UnitIn3Pixels.png", BarCodeImageFormat.Png);
//set unit size in 2 millimeters
gen.Parameters.Barcode.XDimension.Millimeters = 2;
gen.Save($"{path}UnitIn2Millimeters.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->

## **Image Resolution**
***Aspose.BarCode for Android via Java*** allows developers to customize barcode image resolution settings using class [*Unit*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/Unit). This class includes the *updateResolution* method to modify barcode image resolution and the *setPixels* method to convert all non-pixel size measurements into digital coordinates in pixels. To convert size values into requested supported untis, special methods can be used: *setInches*, *setMillimeters*, *setDocument*, *setPoint*, and *setPixels*. 
  
Barcode images with different resolution settings are given below.
  
|Resolution|Is Set to 96 dpi|Is Set to 300 dpi|
| :-: | :-: | :-: |
| |<image src="unitin1millimeterresolution96.png">|<image src="unitin1millimeterresolution300.png">|
  
<!--The following code snippet demonstrates how to manage resolution settings.
  
{{< highlight java>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE");
//set unit size in 1 millimeter, resolution 96
gen.Parameters.Barcode.XDimension.Millimeters = 1;
gen.Parameters.Resolution = 96;
gen.Save($"{path}UnitIn1MillimeterResolution96.png", BarCodeImageFormat.Png);
//set unit size in 1 millimeter, resolution 300
gen.Parameters.Barcode.XDimension.Millimeters = 1;
gen.Parameters.Resolution = 300;
gen.Save($"{path}UnitIn1MillimeterResolution300.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
