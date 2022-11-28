---
title: Manage Barcode Parameters
type: docs
weight: 40
description: "How to Manage Barcode Parameters in Aspose.BarCode for PHP"
keywords: "Generate Barcodes, Customize Barcode Image, Barcode Size Units in Aspose.BarCode for PHP via Java, Work with Barcode Image in Aspose.BarCode for PHP, Generate Barcodes in Aspose.BarCode, Convert Barcode Size in Aspose.Barcode"
url: /phpjava/set-barcode-parameters/

---
This article describes how to manage settings provided by ***Aspose.BarCode for PHP via Java*** to adjust barcode measurement units (millimeters, inches, points, or pixels) and barcode image resolution.
  
## **Overview**
Cartesian coordinate systems use coordinates of pixels or drawable objects to represent image data for raster or vector images. To link these coordinates to real-world measurement units, such as millimeters or inches, ***Aspose.BarCode for PHP via Java*** includes a special class called [*Unit*](https://reference.aspose.com/barcode/php/classUnit). Class [*Unit*](https://reference.aspose.com/barcode/php/classUnit) provides various functions that serve to convert barcode size values defined in pixels, millimeters, inches, or points to any of the supported measurement units automatically. In this way, the size of elements in real-world measurement units can be converted into pixels to generate barcode images.  

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/phpjava/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Measuring Barcode Size in Various Units**
Class [*Unit*](https://reference.aspose.com/barcode/php/classUnit) allows developers to set measurement units for barcode parameters and can be modified using functions of class [*BarcodeParameters*](https://reference.aspose.com/barcode/php/classBarcodeParameters), such as *setBarCodeHeight (Unit $value)*, *setBarCodeWidth (Unit $value)*, and *setXDimension (Unit $value)*. ***Aspose.BarCode for PHP via Java*** determines measurement units in the [*GraphicsUnit*](https://reference.aspose.com/barcode/php/classGraphicsUnit) enum. Class [*Unit*](https://reference.aspose.com/barcode/php/classUnit) can be used to convert measurement units into the desired ones: *Millimeters*, *Pixels*, *Inches*, *Point* (1/72 inch), or *Document* (1/300 inch). By default, *Millimeters* are used as size measurement units.  
  
Barcode labels created using various unit settings are shown below.
   
|Size Units|Pixels|Millimeters|
| :-: | :-: | :-: |
| |<image src="unitin3pixels.png">|<image src="unitin2millimeters.png">|
  
## **Image Resolution**
***Aspose.BarCode for PHP via Java*** allows developers to customize barcode image resolution settings using class [*Unit*](https://reference.aspose.com/barcode/php/classUnit). This class includes the *setPixels (float $value)* function to convert all non-pixel size measurements into digital coordinates in pixels. To convert size values into requested supported untis, the following functions need to be used: *setInches (float $value)*, *setMillimeters (float $value)*, *setDocument (float $value)*, *setPoint (float $value)*, and *setPixels (float $value)*. 
  
Barcode images with different resolution settings are given below.
  
|Resolution|Is Set to 96 dpi|Is Set to 300 dpi|
| :-: | :-: | :-: |
| |<image src="unitin1millimeterresolution96.png">|<image src="unitin1millimeterresolution300.png">|
  
