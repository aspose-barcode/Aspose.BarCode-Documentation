---
title: Setting Barcode Parameters
type: docs
weight: 40
description: "How to Set Size Units for Barcodes in Aspose.BarCode for .NET"
keywords: "Generate Barcodes, Customize Barcode Image, Barcode Size Units in Aspose.Barcode for .NET, Work with Barcode Image in Aspose.BarCode for .NET, Generate Barcodes in Aspose.BarCode, Convert Barcode Size in Aspose.Barcode"
url: /net/setting-barcode-parameters/
---
This article outlines the capabilities provided by ***Aspose.BarCode for .NET*** to customize barcode measurement units (inches, millimeters, points, or pixels) and the resolution of generated barcode images.
  
## Overview
In Cartesian coordinate systems, image data are represented as the coordinates of pixels or drawable objects for raster or vector images, respectively.  
In ***Aspose.BarCode for .NET***, to link the values of such coordinates to real-world measurement units, such as inches or millimeters, [*BarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) class includes class [*Unit*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/unit) and its specific property called [*Resolution*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/unit/properties/resolution) that is measured in dots per inch (dpi). Class *Unit* serves to convert barcode size values defined in pixels, millimeters, inches, or points into any of the supported measurement units automatically. In this way, the size of elements in real-world measurement units can be converted into pixels to perform barcode image generation.  

## Measuring Barcode Size in Different Units 
Class [*Unit*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/unit) is used to set measurement units for various parameters of class [*BarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator), such as *BarCodeHeight*, *BarCodeWidth*, *XDimension*, *FontUnit*, and some others. In ***Aspose.BarCode for .NET***, this class is implemented as an internal realization of .NET class [*GraphicsUnit Enum*](https://docs.microsoft.com/uk-ua/dotnet/api/system.drawing.graphicsunit?view=windowsdesktop-5.0). Class *Unit* allows converting different measurement units into the desired ones: *Inches*, *Millimeters*, *Pixels*, *Point* (1/72 inch), or *Document* (1/300 inch). The default size measurement unit for barcode generation is *Millimeters*.  
  
Barcode images generated using different unit settings (three pixels and two millimeters) are demonstrated below.
   
|Size Units|Pixels|Millimeters|
|---|:---:|:---:|
| |<image src="UnitIn3Pixels.png">|<image src="UnitIn2Millimeters.png">|
  
The following code snippet illustrates how to implement the settings as in the provided barcode labels.

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE");
//set unit size in 3 pixels
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}UnitIn3Pixels.png", BarCodeImageFormat.Png);
//set unit size in 2 millimeters
gen.Parameters.Barcode.XDimension.Millimeters = 2;
gen.Save($"{path}UnitIn2Millimeters.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

## Managing Image Resolution
***Aspose.BarCode for .NET*** enables custom settings for barcode image resolution. To implement this, [*BarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) class provides the [*Resolution*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/basegenerationparameters/properties/resolution) property that is used to get or set the resolution of a barcode image and is intended to convert all non-pixel barcode size values into digital coordinates measured in pixels. The *Resolution* property is defined uniformly for all dimensions of a barcode image and is measured in dpi. Its default value equals 96 dpi.  
  
Barcode labels created with different resolution settings (96 dpi and 300 dpi) are shown below.
  
|Resolution|96 dpi|300 dpi|
|---|:---:|:---:|
| |<image src="UnitIn1MillimeterResolution96.png">|<image src="UnitIn1MillimeterResolution300.png">|
  
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
