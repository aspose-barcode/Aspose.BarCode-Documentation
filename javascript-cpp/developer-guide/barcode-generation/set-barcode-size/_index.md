---
title: Set Barcode Size and Resolution in JavaScript
linktitle: Set Barcode Size and Resolution
type: docs
weight: 10
feedback: BARCODECOM
description: "How to Set Size Units for Barcodes in Aspose.BarCode for JavaScript via C++"
keywords: Generate Barcodes, Customize Barcode Image, Barcode Size Units in Aspose.BarCode for JavaScript via C++, Work with Barcode Image in Aspose.BarCode for JavaScript via C++, Generate Barcodes in Aspose.BarCode, Convert Barcode Size in Aspose.Barcode
url: /javascript-cpp/set-barcode-size/
---
This article outlines the capabilities provided by ***Aspose.BarCode for JavaScript via C++*** to customize barcode measurement units (inches, millimeters, points, or pixels) and the resolution of generated barcode images.

## **Overview**
In Cartesian coordinate systems, image data are represented as the coordinates of pixels or drawable objects for raster or vector images, respectively.  
In ***Aspose.BarCode for JavaScript via C++***, to link these coordinates to real-world measurement units, such as inches or millimeters, the [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) class uses common notation like "1px", "2mm", "3in", "4pt". 

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/javascript-cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Define Barcode Size in Different Units**
The [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) class provides several parameters to configure the size of a barcode. These include:

- **BarCodeHeight**  
- **BarCodeWidth**  
- **XDimension**  
- **FontUnit**  

You can adjust these parameters to customize the barcode dimensions according to your requirements.


Barcode images generated with different unit settings (three pixels and two millimeters) are shown below.

|Size Units|Pixels|Millimeters|
| :-: | :-: | :-: |
| |<image src="unitin3pixels.png">|<image src="unitin2millimeters.png">|

The following code snippet shows how to set up these configurations as in the provided barcode images.


[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript

// Create a DataMatrix barcode generator with unit size settings
var gen = new BarCodeInstance.BarcodeGenerator("DataMatrix", "ASPOSE");

// Set unit size in 3 pixels
gen.Parameters.Barcode.XDimension = "3px";
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image with unit in 3 pixels

// Set unit size in 2 millimeters
gen.Parameters.Barcode.XDimension = "2mm";
document.getElementById("img2").src = gen.GenerateBarCodeImage(); // Display barcode image with unit in 2 millimeters

// Cleanup
gen.delete();


``` 
## **Set Barcode Image Resolution**
***Aspose.BarCode for JavaScript via C++*** allows you to customize the resolution of a barcode image. The [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) class has a [*Resolution*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/basegenerationparameters/properties/resolution) property that can be used to get or set the barcode image resolution. This property converts all non-pixel size values into digital coordinates measured in pixels and is uniform for all barcode image dimensions. The resolution is measured in dpi, with the default value set to 96 dpi.

The barcode images below show examples created with different resolution settings (96 dpi and 300 dpi).

|Resolution|96 dpi|300 dpi|
| :-: | :-: | :-: |
| |<image src="unitin1millimeterresolution96.png">|<image src="unitin1millimeterresolution300.png">|

The following code example illustrates how to set the resolution for a barcode image.

  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript

// Generate a DataMatrix barcode with unit size settings in millimeters and different resolutions
var gen = new BarCodeInstance.BarcodeGenerator("DataMatrix", "ASPOSE");

// Set unit size to 1 millimeter and resolution to 96 DPI
gen.Parameters.Barcode.XDimension = "1mm";
gen.Parameters.Resolution = 96;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

// Set unit size to 1 millimeter and resolution to 300 DPI
gen.Parameters.Barcode.XDimension = "1mm";
gen.Parameters.Resolution = 300;
document.getElementById("img2").src = gen.GenerateBarCodeImage(); // Display barcode image

gen.delete();


``` 
