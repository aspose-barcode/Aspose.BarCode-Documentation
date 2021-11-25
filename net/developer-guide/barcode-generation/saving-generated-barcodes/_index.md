---
title: Saving Generated Barcodes
type: docs
weight: 60
url: /net/saving-generated-barcodes/
---

This article describes different ways of saving generated barcode images to files, streams, or bitmaps, as well as outputting barcode labels in various raster and vector image formats.

## Overview
In the process of barcode development, it may be necessary to save barcodes not only in standard raster image file formats but also to a stream or a vector file. ***Aspose.BarCode for .NET*** provides various options of outputting generated barcodes, such as saving in the five most widely used image formats, two vector formats, and other possibilities (loading barcode images to a file, a stream, or a bitmap). These options are described below along with corresponding code snippets that illustrate how to implement them.

## Saving to File
***Aspose.BarCode for .NET*** allows saving the generated barcode label directly as a file of the desired format. The code snippet provided below shows how to implement this option.  
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
gen.Save($"{path}StoreImageAsFile.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

## Saving to Stream
In some cases, developers may need to save the generated barcode label in the form of a stream (as a binary format). In the .NET framework, a stream is an abstraction of a byte sequence, such as a file, an inter-process communication pipe, a TCP/IP socket, or an input/output device. The *Stream* class and its child classes represent a generic view of various input and output types and allow programmers to abstract away from the details of the operating system and particular devices. To enable this option, barcode generating classes ([*BarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) and [*BarCodeGeneratorControl*](https://apireference.aspose.com/barcode/net/aspose.barcode.windows.forms/barcodegeneratorcontrol)) call the public method *Save* that takes *Stream* as an input parameter along with *BarCodeImageFormat*, as demonstrated in the code sample below.  

{{< highlight csharp>}}
using (Stream str = new FileStream($"{path}StoreImageAsStream.png", FileMode.Create, FileAccess.Write))
{
    BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
    gen.Save(str, BarCodeImageFormat.Png);
}
{{< /highlight >}} 

## Saving as Bitmap

***Aspose.BarCode for .NET*** allows outputting a barcode image in the form of a bitmap object and then saving it in the desired format or using it in further graphical transformations. A bitmap represents the pixel data for an image and its attributes. It is possible to generate images from files, streams, and other sources by calling one of the Bitmap constructors and then download them to a stream or the file system using the *Save* method. The following code snippet illustrates how to implement this option in ***Aspose.BarCode for .NET***.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
using (Bitmap bmp = gen.GenerateBarCodeImage())
    bmp.Save($"{path}StoreImageAsBitmap.png", ImageFormat.Png);
{{< /highlight >}} 

## Outputting in Raster Formats

***Aspose.BarCode for .NET*** enables saving barcode images to most of the widely used raster image formats, namely, BMP, PNG, GIF, GPEG, and TIFF. To realize this option, the *BarcodeGenerator.Save* method creates an instance of [*BarCodeImageFormat* ](https://apireference.aspose.com/barcode/net/aspose.barcode/barcodeimageformat) class passing the desired image format to the *Save method* of the barcode generating class as an argument. The descriptions of all supported image formats along with corresponding code samples are provided below.

### BMP Format
Files with the .BMP extension correspond to bitmap files that are intended to store bitmap digital images and are independent of a graphics adapter. The BMP file format can store data as two-dimensional digital images in both monochrome and color formats with various color depths. The BMP format implies creating images without compression; accordingly, the generated barcode images will be of a large size, having 24-bit color depth, and without losses and artifacts. 
The code snippet provided below illustrates how to save barcode images in BMP format.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as BMP
gen.Save($"{path}RasterImageBmp.bmp", BarCodeImageFormat.Bmp);
{{< /highlight >}}
The example of a barcode image generated in the BMP format is demonstrated below.
<p align="center"><image src="RasterImageBmp.bmp"></p>

### PNG Format
Portable Network Graphics (PNG) is a raster file format that enables lossless data compression. PNG is the most preferred format to create raster images. Barcode labels generated in this format will be of 32-bit color depth and without losses. The following code example can be used to save barcode images in PNG format.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as Png
gen.Save($"{path}RasterImagePng.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
The resulting barcode label generated in the PNG format is given below.
<p align="center"><image src="RasterImageBmp.bmp"></p>

### GIF Format
Graphics Interchange Format (GIF) is a lossless raster image format that contains only 256 colors and supports both static and animated images. In ***Aspose.BarCode for .NET***, it can be applied only to black and white raster images. The code sample shown below describes how to save barcode images in GIF format.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as Gif
gen.Save($"{path}RasterImageGif.gif", BarCodeImageFormat.Gif);
{{< /highlight >}} 
The barcode image example generated in the GIF format is demonstrated below.
<p align="center"><image src="RasterImageGif.gif"></p>

### JPEG Format
JPEG is a standard image format to store lossy and compress image data. Due to compression, the output image is a trade-off between storage size and image quality and usually contains artifacts and graphical noises. This format is the least recommended to save generated barcodes. The following code snippet can be used to generate barcode labels in the JPEG format.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as Jpeg
gen.Save($"{path}RasterImageJpeg.jpeg", BarCodeImageFormat.Jpeg);
{{< /highlight >}} 
The example of a barcode image generated in the JPEG format is represented below.
<p align="center"><image src="RasterImageJpeg.jpeg"></p>

### TIFF (TIFFInCMYK) Format
Tagged Image File Format (TIFF) is a lossless raster format that provides extremely high image quality and supports 32-bit color. It is the only output format that in its variation TIFFInCMYK), enables the CMYK color scheme. The code sample represented below describes how to create barcode images in TIFF format.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as Tiff
gen.Save($"{path}RasterImageTiff.tiff", BarCodeImageFormat.Tiff);
//save as TiffInCmyk
gen.Save($"{path}RasterImageTiffInCmyk.tiff", BarCodeImageFormat.TiffInCmyk);
{{< /highlight >}} 
The examples of barcode labels created in the TIFF and TIFFInCMYK formats are provided below.
<a href="RasterImageTiff.tiff"> <p align="center"><img src="RasterImagePng.png" alttext="Saving to TIFF format"> </p></a>
<a href="RasterImageTiffInCmyk.tiff"> <p align="center"><img src="RasterImagePng.png" alttext="Saving to TIFF format"> </p></a>

## Outputting in Vector Formats
Vector data formats allow representing an image as a set of graphical operations that are consequently executed on a user's graphics unit. Namely, vector images can be created using mathematical formulas that establish points on a grid. Vector images can be scaled without losing resolution; therefore, vector files are more preferable for some tasks compared with raster files. At present, ***Aspose.BarCode for .NET*** allows saving barcode labels in two vector formats: EMF and SVG.

### EMF Format
Enhanced Metafile (EMF) is a device-independent vector image format most used in Windows operating systems for printing purposes. An EMF image file contains the records of variable length in chronological order so that the stored image can be rendered after parsing on any output device. Such variable-length records can represent definitions of enclosed objects, commands for drawing, and graphics properties that are important to render the image accurately. When a device opens an EMF metafile using its own graphics environment, the dimension, proportions, colors, and other graphic properties of the original image remain unchanged regardless of the opening device platform. The code snippet below illustrates how to create barcode images in EMF format.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as Emf
gen.Save($"{path}VectorImageEmf.emf", BarCodeImageFormat.Emf);
{{< /highlight >}} 
<a href="VectorImageEmf.emf"> <p align="center"><img src="RasterImagePng.png" alttext="Saving to EMF format"> </p></a>


### SVG Format
Scalable Vector Graphics (SVG) is an XML-based vector image format used to render two-dimensional images in web applications. In SVG image files, XML-based text is used to describe how the image should appear; therefore, such a file can be scaled to different sizes without losing resolution. Accordingly, this format is often applied to develop websites and print graphics, as they may need to be resized to fit different designs. The following code sample describes how to generate barcode images in the SVG format.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "12345678");
//save as Svg
gen.Save($"{path}VectorImageSvg.svg", BarCodeImageFormat.Svg);
{{< /highlight >}} 
The example of a barcode label created in SVG format is provided below.
<p align="center"><image src="VectorImageSvg.svg"></p>