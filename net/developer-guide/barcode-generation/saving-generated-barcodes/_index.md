---
title: Save Generated Barcodes in C#
linktitle: Save Generated Barcodes
type: docs
ai_search_scope: "barcode_dotnet_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 50
feedback: BARCODECOM
description: Save Barcodes to File, Stream, Image Formats like BMP, PNG, GIF, JPEG, EMF, SVG using C# API
keywords: Generate Barcodes, Save Barcode in Aspose.BarCode for .NET, Download Barcode in Aspose.BarCode for .NET, Generate Barcodes in Aspose.BarCode, Save To File Aspose Barcode, Barcode Vector Format, Generate Vector Barcodes, Save Barcode as JPEG, Save Barcode as PNG, Save Barcode as BMP, Save Barcode as TIFF, Save Barcode as GIF
url: /net/save-barcode-image/
aliases:
- /net/saving-barcode-image/
---

This article describes different ways of saving generated barcode images to files, streams, or bitmaps, as well as outputting barcode labels in various raster (BMP, PNG, JPEG, GIF, and TIFF) and vector (EMF and SVG) image formats.

## **Overview**
In the process of barcode development, it may be necessary to save barcodes not only in standard raster image file formats but also to a stream or a vector file. ***Aspose.BarCode for .NET*** provides various options of outputting generated barcodes, such as saving in the five most widely used image formats, two vector formats, and other possibilities (loading barcode images to a file, a stream, or a bitmap). These options are described below along with corresponding code snippets that illustrate how to implement them.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Save Barcode to File**
***Aspose.BarCode for .NET*** allows saving the generated barcode label directly as a file of the desired format. The code snippet provided below shows how to implement this option.  
  
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
gen.Save($"{path}StoreImageAsFile.png", BarCodeImageFormat.Png);

```

## **Save Barcode to Stream**
In some cases, developers may need to save the generated barcode label in the form of a stream (as a binary format). In the .NET framework, a stream is an abstraction of a byte sequence, such as a file, an inter-process communication pipe, a TCP/IP socket, or an input/output device. The *Stream* class and its child classes represent a generic view of various input and output types and allow programmers to abstract away from the details of the operating system and particular devices. To enable this option, class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) calls the public method *Save* that takes *Stream* as an input parameter, as demonstrated in the code sample below.  

``` csharp

using (Stream str = new FileStream($"{path}StoreImageAsStream.png", FileMode.Create, FileAccess.Write))
{
    BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
    gen.Save(str, BarCodeImageFormat.Png);
}

```

## **Save Barcode as Bitmap**

***Aspose.BarCode for .NET*** allows outputting a barcode image in the form of a bitmap object and then saving it in the desired format or using it in further graphical transformations. Such objects can be obtained from instances of class *BarcodeGenerator* by calling the *GenerateBarCodeImage* method and then get processed as required. The following code snippet illustrates how to implement this option in ***Aspose.BarCode for .NET***.

``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
using (Bitmap bmp = gen.GenerateBarCodeImage())
    bmp.Save($"{path}StoreImageAsBitmap.png", ImageFormat.Png);

```

## **Output Barcodes in Raster Formats**

***Aspose.BarCode for .NET*** enables saving barcode images to most of the widely used raster image formats, namely, BMP, PNG, GIF, JPEG, and TIFF. You can pass the [BarCodeImageFormat](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeimageformat) enum as a second argument to the BarcodeGenerator.Save method to save a barcode in the desired format. The descriptions of all supported image formats along with corresponding code samples are provided below.

### **BMP Format**
Files with the .BMP extension correspond to bitmap files that are intended to store bitmap digital images and are independent of a graphics adapter. The BMP file format can store data as two-dimensional digital images in both monochrome and color formats with various color depths. The BMP format implies creating images without compression; accordingly, the generated barcode images will be of a large size, having 24-bit color depth, and without losses and artifacts. 
The code snippet provided below illustrates how to save barcode images in the BMP format.

``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as BMP
gen.Save($"{path}RasterImageBmp.bmp", BarCodeImageFormat.Bmp);

```
  
The example of a barcode image generated in the BMP format is demonstrated below.
  
<p align="center"><image src="rasterimagebmp.bmp"></p>

### **PNG Format**
Portable Network Graphics (PNG) is a raster file format that enables lossless data compression. PNG is the most preferred format to create barcode images. Barcode labels generated in this format will be of 32-bit color depth and without losses. The following code example can be used to save barcode images in the PNG format.
  
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as Png
gen.Save($"{path}RasterImagePng.png", BarCodeImageFormat.Png);

```
   
The resulting barcode label generated in the PNG format is given below.
  
<p align="center"><image src="rasterimagebmp.bmp"></p>

### **GIF Format**
Graphics Interchange Format (GIF) is a lossless raster image format that contains only 256 colors and supports both static and animated images. In ***Aspose.BarCode for .NET***, it can be applied only to black and white raster images. The code sample shown below describes how to save barcode images in the GIF format.
  
``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as Gif
gen.Save($"{path}RasterImageGif.gif", BarCodeImageFormat.Gif);

```
   
The barcode image example generated in the GIF format is demonstrated below.
  
<p align="center"><image src="rasterimagegif.gif"></p>

### **JPEG Format**
JPEG is a standard image format to store lossy and compressed image data. Due to compression, the output image is a trade-off between storage size and image quality and usually contains artifacts and graphical noises. This format is the least recommended to save generated barcodes. The following code snippet can be used to generate barcode labels in the JPEG format.

``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as Jpeg
gen.Save($"{path}RasterImageJpeg.jpeg", BarCodeImageFormat.Jpeg);

```
   
The example of a barcode image generated in the JPEG format is represented below.
  
<p align="center"><image src="rasterimagejpeg.jpeg"></p>

### **TIFF (TIFFInCMYK) Format**
Tagged Image File Format (TIFF) is a lossless raster format that provides extremely high image quality and supports 32-bit color. It is the only output format that in its variation TIFFInCMYK, enables the CMYK color scheme. The code sample represented below describes how to create barcode images in the TIFF format.

``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as Tiff
gen.Save($"{path}RasterImageTiff.tiff", BarCodeImageFormat.Tiff);
//save as TiffInCmyk
gen.Save($"{path}RasterImageTiffInCmyk.tiff", BarCodeImageFormat.TiffInCmyk);

```

The examples of barcode labels created in TIFF and TIFFInCMYK formats are provided below.
  
|Output Format|TIFF|TIFFInCMYK|
| :-: | :-: | :-: |
| |<a href="rasterimagetiff.tiff"><img src="rasterimagepng.png" alttext="Saving to TIFF format"></a>|<a href="rasterimagetiffincmyk.tiff"><img src="rasterimagepng.png" alttext="Saving to TIFFInCMYK format"></a>|
  
## **Output Barcodes in Vector Formats**
Vector data formats allow representing an image as a set of graphical operations that are consequently executed on a user's graphics unit. Namely, vector images can be created using mathematical formulas that establish points on a grid. Vector images can be scaled without losing resolution; therefore, vector files are more preferable for some tasks compared with raster files. At present, ***Aspose.BarCode for .NET*** allows saving barcode labels in two vector formats: EMF and SVG.

### **EMF Format**
Enhanced Metafile (EMF) is a device-independent vector image format most used in Windows operating systems for printing purposes. An EMF image file contains the records of variable length in chronological order so that the stored image can be rendered after parsing on any output device. Such variable-length records can represent definitions of enclosed objects, commands for drawing, and graphics properties that are important to render the image accurately. When a device opens an EMF metafile using its own graphics environment, the dimension, proportions, colors, and other graphic properties of the original image remain unchanged regardless of the opening device platform. The code snippet below illustrates how to create barcode images in the EMF format.

``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as Emf
gen.Save($"{path}VectorImageEmf.emf", BarCodeImageFormat.Emf);

``` 
  
<a href="vectorimageemf.emf"> <p align="center"><img src="rasterimagepng.png" alttext="Saving to EMF format"> </p></a>


### **SVG Format**
Scalable Vector Graphics (SVG) is an XML-based vector image format used to render two-dimensional images in web applications. In SVG image files, XML-based text is used to describe how the image should appear; therefore, such a file can be scaled to different sizes without losing resolution. Accordingly, this format is often applied to develop websites and print graphics, as they may need to be resized to fit different designs. 
  
The following code sample describes how to generate barcode images in the SVG format.  

``` csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as Svg
gen.Save($"{path}VectorImageSvg.svg", BarCodeImageFormat.Svg);

``` 
  
The example of a barcode label created in the SVG format is provided below.
  
<p align="center"><image src="vectorimagesvg.svg"></p>
