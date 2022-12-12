---
title: Set Barcode Parameters
type: docs
weight: 40
description: "How to Manage Barcode Parameters in Aspose.BarCode for Python"
keywords: "Generate Barcodes, Customize Barcode Image, Barcode Size Units in Aspose.BarCode for Python, Work with Barcode Image in Aspose.BarCode for Python, Generate Barcodes in Aspose.BarCode, Convert Barcode Size in Aspose.Barcode"
url: /python-net/barcode-parameters/

---
This article describes how to manage settings provided by ***Aspose.BarCode for Python via .NET*** to adjust barcode measurement units (millimeters, inches, points, or pixels) and barcode image resolution.
  
## **Overview**
Cartesian coordinate systems use coordinates of pixels or drawable objects to represent image data for raster or vector images. To link these coordinates to real-world measurement units, such as millimeters or inches, ***Aspose.BarCode for Python via .NET*** includes a special class called [*Unit*](/barcode/python-net/api-reference/aspose.barcode.generation/unit/) and its properties called *resolution* that is intended to manage barcode resolution measured in dots per inch (dpi). Class [*Unit*](/barcode/python-net/api-reference/aspose.barcode.generation/unit/) provides various properties that serve to convert barcode size values defined in pixels, millimeters, inches, or points to any of the supported measurement units automatically. In this way, the size of elements in real-world measurement units can be converted into pixels to generate barcode images. 

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/python-dotnet/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Measuring Barcode Size in Various Units**
Class [*Unit*](/barcode/python-net/api-reference/aspose.barcode.generation/unit/) allows developers to manage measurement units for barcode parameters and can be modified using the properties of class [*BarcodeParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/barcodeparameters/), such as *bar_code_height*, *bar_code_width*, and *x_dimension*. Class [*Unit*](/barcode/python-net/api-reference/aspose.barcode.generation/unit/) can be used to convert measurement units into the desired ones: *Millimeters*, *Pixels*, *Inches*, *Point* (1/72 inch), or *Document* (1/300 inch). By default, *Millimeters* are used as size measurement units.  
  
Barcode labels created using various unit settings are shown below.
   
|Size Units|Pixels|Millimeters|
| :-: | :-: | :-: |
| |<image src="unitin3pixels.png">|<image src="unitin2millimeters.png">|

## **Image Resolution**
***Aspose.BarCode for Python via .NET*** allows developers to customize barcode image resolution settings using class [*Unit*](/barcode/python-net/api-reference/aspose.barcode.generation/unit/). This class includes the *resolution* properties to modify barcode image resolution and the *pixels* properties to convert all non-pixel size measurements into digital coordinates in pixels. To convert size values into requested supported units, the following properties can be used: *inches*, *millimeters*, *document*, *point*, and *pixels*. 
  
Barcode images with different resolution settings are given below.
  
|Resolution|Is Set to 96 dpi|Is Set to 300 dpi|
| :-: | :-: | :-: |
| |<image src="unitin1millimeterresolution96.png">|<image src="unitin1millimeterresolution300.png">|
  