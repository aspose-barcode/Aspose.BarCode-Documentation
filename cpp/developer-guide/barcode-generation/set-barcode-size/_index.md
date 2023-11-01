---
title: Set Barcode Size and Resolution in C++
linktitle: Set Barcode Size and Resolution
type: docs
weight: 10
feedback: BARCODECOM
description: "How to Set Size Units for Barcodes in Aspose.BarCode for C++"
keywords: Generate Barcodes, Customize Barcode Image, Barcode Size Units in Aspose.BarCode for C++, Work with Barcode Image in Aspose.BarCode for C++, Generate Barcodes in Aspose.BarCode, Convert Barcode Size in Aspose.Barcode
url: /cpp/set-barcode-size/
---

This article outlines the capabilities provided by ***Aspose.BarCode for C++*** to customize barcode measurement units (inches, millimeters, points, or pixels) and the resolution of generated barcode images.
  
## **Overview**
In Cartesian coordinate systems, image data are represented as the coordinates of pixels or drawable objects for raster or vector images, respectively.  
In ***Aspose.BarCode for C++***, to link the values of such coordinates to real-world measurement units, such as inches or millimeters, [*BarcodeGenerator*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.barcode_generator/) class includes class [*Unit*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.unit/) and its specific property called *Resolution* that is measured in dots per inch (dpi). Class *Unit* serves to convert barcode size values defined in pixels, millimeters, inches, or points into any of the supported measurement units automatically. In this way, the size of elements in real-world measurement units can be converted into pixels to perform barcode image generation.  

```cpp
// The path to the documents directory.
System::String dataDir = RunExamples::GetDataDir_ManageBarCodesImages();

// Instantiate barcode object and set CodeText & Barcode Symbology
System::SharedPtr<BarcodeGenerator> generator = [&] { auto tmp_0 = System::MakeObject<BarcodeGenerator>(EncodeTypes::Code39Standard, u"1234567890"); tmp_0->get_Parameters()->get_Barcode()->set_AutoSizeMode(AutoSizeMode::Nearest); tmp_0->get_Parameters()->get_Barcode()->get_BarCodeHeight()->set_Millimeters(50); tmp_0->get_Parameters()->get_Barcode()->get_BarCodeWidth()->set_Millimeters(120); return tmp_0; }();
generator->Save(dataDir + u"barcode-custom-size_out.jpg");
```

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Define Barcode Size in Different Units**
Class [*Unit*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.unit/) is used to set measurement units for various parameters of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.barcode_generator/), such as *BarCodeHeight*, *BarCodeWidth*, *XDimension*, *FontUnit*, and some others. Class *Unit* allows converting different measurement units into the desired ones: *Inches*, *Millimeters*, *Pixels*, *Point* (1/72 inch), or *Document* (1/300 inch). The default size measurement unit for barcode generation is *Millimeters*.  
  
Barcode images generated using different unit settings (three pixels and two millimeters) are demonstrated below.
   
|Size Units|Pixels|Millimeters|
| :-: | :-: | :-: |
| |<image src="unitin3pixels.png">|<image src="unitin2millimeters.png">|
  
```cpp
// The path to the documents directory.
System::String dataDir = RunExamples::GetDataDir_ManageBarCodesImages();

// Instantiate barcode object
System::SharedPtr<BarcodeGenerator> generator = System::MakeObject<BarcodeGenerator>(EncodeTypes::Code128, u"1234567"); 
generator->get_Parameters()->get_Barcode()->get_BarHeight()->set_Point(3.0f);
generator->Save(dataDir + u"barcode-size-unit_out.jpeg", BarCodeImageFormat::Jpeg);
System::Console::WriteLine(System::Environment::get_NewLine() + u"Barcode saved at " + dataDir);
```

## **Set Barcode Image Resolution**
***Aspose.BarCode for C++*** enables custom settings for barcode image resolution. To implement this, [*BarcodeGenerator*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.barcode_generator/) class provides the *Resolution* property that is used to get or set the resolution of a barcode image and is intended to convert all non-pixel barcode size values into digital coordinates measured in pixels. The *Resolution* property is defined uniformly for all dimensions of a barcode image and is measured in dpi. Its default value equals 96 dpi.  
  
Barcode labels created with different resolution settings (96 dpi and 300 dpi) are shown below.
  
|Resolution|Is Set to 96 dpi|Is Set to 300 dpi|
| :-: | :-: | :-: |
| |<image src="unitin1millimeterresolution96.png">|<image src="unitin1millimeterresolution300.png">|
  
```cpp
// The path to the documents directory.
System::String dataDir = RunExamples::GetDataDir_ManageBarCodesImages();

// Instantiate barcode object and set CodeText & Barcode Symbology
System::SharedPtr<BarcodeGenerator> generator = [&] { auto tmp_0 = System::MakeObject<BarcodeGenerator>(EncodeTypes::Code128, u"1234567"); tmp_0->get_Parameters()->set_Resolution(400.f); return tmp_0; }();

// Save the image to your system and set its image format to Jpeg
generator->Save(dataDir + u"barcode-image-resolution_out.jpeg", BarCodeImageFormat::Jpeg);
System::Console::WriteLine(System::Environment::get_NewLine() + u"Barcode saved at " + dataDir);
```  
