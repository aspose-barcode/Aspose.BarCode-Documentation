---
title: Manage Barcode Parameters
type: docs
ai_search_scope: "barcode_nodejsjava_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 40
description: "How to Manage Barcode Parameters in Aspose.BarCode for Node.js"
keywords: "Generate Barcodes, Customize Barcode Image, Barcode Size Units in Aspose.BarCode for Node.js via Java, Work with Barcode Image in Aspose.BarCode for Node.js, Generate Barcodes in Aspose.BarCode, Convert Barcode Size in Aspose.Barcode"
url: /nodejsjava/set-barcode-parameters/
---

This article describes how to manage settings provided by ***Aspose.BarCode for Node.js via Java*** to adjust barcode measurement units (millimeters, inches, points, or pixels) and barcode image resolution.
  
## **Overview**
Cartesian coordinate systems use coordinates of pixels or drawable objects to represent image data for raster or vector images. To link these coordinates to real-world measurement units, such as millimeters or inches, ***Aspose.BarCode for Node.js via Java*** includes a special class called [*Unit*](https://reference.aspose.com/barcode/nodejs/Unit) and its method called *updateResolution* that is intended to manage barcode resolution measured in dots per inch (dpi). Class [*Unit*](https://reference.aspose.com/barcode/nodejs/Unit) provides various methods that serve to convert barcode size values defined in pixels, millimeters, inches, or points to any of the supported measurement units automatically. In this way, the size of elements in real-world measurement units can be converted into pixels to generate barcode images.  

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/nodejsjava/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Measuring Barcode Size in Various Units**
Class [*Unit*](https://reference.aspose.com/barcode/nodejs/Unit) allows developers to manage measurement units for barcode parameters and can be modified using special methods of class [*BarcodeParameters*](https://reference.aspose.com/barcode/nodejs/BarcodeParameters), such as *setBarCodeHeight*, *setBarCodeWidth*, and *setXDimension*. ***Aspose.BarCode for Node.js via Java*** determines measurement units in the [*GraphicsUnit*](https://reference.aspose.com/barcode/nodejs/global#GraphicsUnit) global property. Class [*Unit*](https://reference.aspose.com/barcode/nodejs/Unit) can be used to convert measurement units into the desired ones: *Millimeters*, *Pixels*, *Inches*, *Point* (1/72 inch), or *Document* (1/300 inch). By default, *Millimeters* are used as size measurement units.  
  
Barcode labels created using various unit settings are shown below.
   
|Size Units|Pixels|Millimeters|
| :-: | :-: | :-: |
| |<image src="unitin3pixels.png">|<image src="unitin2millimeters.png">|
  
## **Image Resolution**
***Aspose.BarCode for Node.js via Java*** allows developers to customize barcode image resolution settings using class [*Unit*](https://reference.aspose.com/barcode/nodejs/Unit). This class includes the *updateResolution* method to modify barcode image resolution and the *setPixels* method to convert all non-pixel size measurements into digital coordinates in pixels. To convert size values into requested supported untis, special methods can be used: *setInches*, *setMillimeters*, *setDocument*, *setPoint*, and *setPixels*. 
  
Barcode images with different resolution settings are given below.
  
|Resolution|Is Set to 96 dpi|Is Set to 300 dpi|
| :-: | :-: | :-: |
| |<image src="unitin1millimeterresolution96.png">|<image src="unitin1millimeterresolution300.png">|
  
