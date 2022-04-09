---
title: Barcode Parameters
type: docs
weight: 40
description: "How to Manage Barcode Parameters in Aspose.BarCode for Java"
keywords: "Generate Barcodes, Customize Barcode Image, Barcode Size Units in Aspose.BarCode for Java, Work with Barcode Image in Aspose.BarCode for Java, Generate Barcodes in Aspose.BarCode, Convert Barcode Size in Aspose.Barcode"
url: /java/setting-barcode-parameters/
---
This article outlines the capabilities provided by ***Aspose.BarCode for Java*** to customize barcode measurement units (inches, millimeters, points, or pixels) and the resolution of generated barcode images.
  
## **Overview**
In Cartesian coordinate systems, image data are represented as the coordinates of pixels or drawable objects for raster or vector images, respectively.  
To link the values of such coordinates to real-world measurement units, such as inches or millimeters, ***Aspose.BarCode for Java*** provides class [*Unit*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/Unit) and its specific method called *updateResolution* that is used to adjust the barcode resolution measured in dots per inch (dpi). Class [*Unit*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/Unit) provides several methods that serve to convert barcode size values defined in pixels, millimeters, inches, or points into any of the supported measurement units automatically. In this way, the size of elements in real-world measurement units can be converted into pixels to perform barcode image generation.  

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Measuring Barcode Size in Different Units**
Class [*Unit*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/Unit) is intended to set measurement units for various barcode parameters that can be adjusted through dedicated methods of class [*BarcodeParameters*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeParameters), such as *setBarCodeHeight*, *setBarCodeWidth*, *setXDimension*, and some others. In ***Aspose.BarCode for Java***, measurement units are defined in the [*GraphicsUnit*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/GraphicsUnit) enum that is defined as an internal representation of Java  interface **java.lang.Comparable<GraphicsUnit>**. Class *Unit* allows converting different measurement units into the desired ones: *Inches*, *Millimeters*, *Pixels*, *Point* (1/72 inch), or *Document* (1/300 inch). The default size measurement unit for barcode generation is *Millimeters*.  
  
Barcode images generated using different unit settings (three pixels and two millimeters) are demonstrated below.
   
|<p align="center">**Size Units**</p>|<p align="center">**Pixels**</p>|<p align="center">**Millimeters**</p>|
| :-: | :-: | :-: |
| |<image src="unitin3pixels.png">|<image src="unitin2millimeters.png">|
  
The following code snippet illustrates how to implement resolution settings as in the provided barcode labels.

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE");
//set unit size in 3 pixels
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}UnitIn3Pixels.png", BarCodeImageFormat.Png);
//set unit size in 2 millimeters
gen.Parameters.Barcode.XDimension.Millimeters = 2;
gen.Save($"{path}UnitIn2Millimeters.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

## **Managing Image Resolution**
***Aspose.BarCode for Java*** enables custom settings for barcode image resolution. To implement this, class [*Unit*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.generation/Unit) provides the *updateResolution* method to adjust the resolution of a barcode image and the *setPixels* method that is intended to convert all non-pixel barcode size values into digital coordinates measured in pixels. To convert barcode size values into desired supported untis, this class suggests using special methods, such as *setMillimeters*, *setInches*, *setPoint*, *setDocument*, and *setPixels*. 
  
Barcode labels created with different resolution settings (96 dpi and 300 dpi) are shown below.
  
|<p align="center">**Resolution**</p>|<p align="center">**Is Set to 96 dpi**</p>|<p align="center">**Is Set to 300 dpi**</p>|
| :-: | :-: | :-: |
| |<image src="unitin1millimeterresolution96.png">|<image src="unitin1millimeterresolution300.png">|
  
The following code example is provided to demonstrate how to customize resolution settings.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE");
//set unit size in 1 millimeter, resolution 96
gen.Parameters.Barcode.XDimension.Millimeters = 1;
gen.Parameters.Resolution = 96;
gen.Save($"{path}UnitIn1MillimeterResolution96.png", BarCodeImageFormat.Png);
//set unit size in 1 millimeter, resolution 300
gen.Parameters.Barcode.XDimension.Millimeters = 1;
gen.Parameters.Resolution = 300;
gen.Save($"{path}UnitIn1MillimeterResolution300.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
