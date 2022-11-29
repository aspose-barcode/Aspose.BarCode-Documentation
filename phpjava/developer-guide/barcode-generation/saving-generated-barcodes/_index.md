---
title: Save Generated Barcodes
type: docs
weight: 70
description: "How to Save Generated Barcodes in Aspose.BarCode for PHP"
keywords: "Generate Barcodes, Save Barcode in PHP, Download Barcode in Aspose.BarCode for PHP, Generate Barcodes in Aspose.BarCode, Save To File Aspose Barcode, Barcode Vector Format, Generate Vector Barcodes, Save Barcode as JPEG, Save Barcode as PNG, Save Barcode as BMP, Save Barcode as TIFF, Save Barcode as GIF"
url: /phpjava/save-barcodes/
---

This article outlines the ways of outputting generated barcode images as files, streams, or bitmaps, as well as various raster (PNG, JPEG, BMP, GIF, and TIFF) and vector (SVG and EMF) image file formats.

## **Overview**
During barcode generation, it may be required to save barcode images not only in common raster image formats but also as streams or vector files. ***Aspose.BarCode for PHP via Java*** enables different options of saving generated barcodes: five common image formats, two vector formats, and some other ways, such as outputting barcode labels to a file, stream, or a bitmap). These options are discussed further.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/phpjava/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Saving to File**
***Aspose.BarCode for PHP via Java*** enables saving generated barcode images as files in the desired format. 

## **Saving to Stream**
It may be necessary to output generated barcode images in the form of a stream, in other words, in a binary format. A stream can be viewed as a byte sequence abstraction. To save barcode images as streams, class [*BarcodeGenerator*](https://reference.aspose.com/barcode/php/classBarcodeGenerator) provides the public function *save (string $filePath, int $format)*.  


## **Saving as Bitmap**
***Aspose.BarCode for PHP via Java*** enables saving barcode images in the form of bitmap objects and then converting it to the required format or using it in graphical transformations. These objects can be fetched from instances of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/php/classBarcodeGenerator) using the *generateBarCodeImage (int $format)* function and then processed further. 

## **Raster Image Formats**

In ***Aspose.BarCode for PHP via Java***, barcode images can be saved to common raster image formats, namely, PNG, GIF, BMP, JPEG, and TIFF. The value of the [*BarCodeImageFormat*](https://reference.aspose.com/barcode/php/classBarCodeImageFormat) class can be passed as the second argument to the *save (string $filePath, int $format)* function of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/php/classBarcodeGenerator) to download barcode images in the specified format. The description of all supported image formats is given further.

### **BMP Format**
BMP images are bitmap files that store bitmap digital images regardless of a graphics adapter. The BMP file format enables storing information as two-dimensional digital images in monochrome and color formats with different color depths. Using the BMP format for image generation results in producing images without compression. In this case, barcode images will have large size and 24-bit color depth. Moreover, they will not contain losses and artifacts. 
  
The sample BMP barcode image is given below.
  
<p align="center"><image src="rasterimagebmp.bmp"></p>

### **PNG Format**
Portable Network Graphics (PNG) is a raster image format that is used for lossless data compression. This format is the most preferable to generate barcode labels. Images created using this format have 32-bit color depth and no losses. 
   
The sample barcode image in the PNG format is provided below.
  
<p align="center"><image src="rasterimagebmp.bmp"></p>

### **GIF Format**
Graphics Interchange Format (GIF) is a lossless raster file format that supports only 256 colors and enables creating both static and animated images. ***Aspose.BarCode for PHP via Java*** allows using this format only for black and white raster images. The code following code snippet explains how to generate barcodes in the GIF format.
   
The GIF barcode image generated using this code is shown below.
  
<p align="center"><image src="rasterimagegif.gif"></p>

### **JPEG Format**
JPEG is a common image file format used for lossy and compressed image data. As a result of compression, generating JPEG images require finding a trade-off between  image quality and storage size and therefore often have artifacts and graphical noises. This file format is not recommended for barcode generation. The following code sample shows how to create JPEG barcode images.
   
The example of a JPEG barcode image is given below.
  
<p align="center"><image src="rasterimagejpeg.jpeg"></p>

### **TIFF (TIFFInCMYK) Format**
Tagged Image File Format (TIFF) is a lossless raster image format that allows creating images of very high quality and 32-bit color. Only a variation of this format, TIFFInCMYK, supports the CMYK color scheme. The code snippet provided below explains how to generate barcode images in the TIFF format.

TIFF and TIFFInCMYK barcode images are given below.
  
|Output Format|TIFF|TIFFInCMYK|
| :-: | :-: | :-: |
| |<a href="rasterimagetiff.tiff"><img src="rasterimagepng.png" alttext="Saving to TIFF format"></a>|<a href="rasterimagetiffincmyk.tiff"><img src="rasterimagepng.png" alttext="Saving to TIFFInCMYK format"></a>|
  
## **Vector Image Formats**
Vector image formats represent images as a set of graphical operations executed consequently on a graphics unit. Vector images can be generated through mathematical formulas that specify points on a grid. This format allows scaling without resolution losses. Accordingly, vector image formats may be more suitable than raster ones in some cases. ***Aspose.BarCode for PHP via Java*** supports outputting barcode images in two vector formats: EMF and SVG.

### **EMF Format**
Enhanced Metafile (EMF) is a vector image format that is device-independent and is commonly used in Windows operating systems for printing tasks. An EMF image file comprise variable-length records in chronological order. Then, a vector image can be rendered on any output device. Such records can serve to represent objects, drawing commands, and graphics parameters that are critical to render vector images. When a digital device opens an EMF metafile through its graphics environment, dimension paraneters, proportions, color scheme, and other graphics properties of the source image do not get altered on any platform. 

  
<a href="vectorimageemf.emf"> <p align="center"><img src="rasterimagepng.png" alttext="Saving to EMF format"> </p></a>


### **SVG Format**
Scalable Vector Graphics (SVG) corresponds to an vector image format based on XML. It is used to create two-dimensional images in web applications. In SVG images, the image appearance is described in XML text. Such files can be scaled to various size measures keeping resolution quality. Accordingly, this vector image format is suitable for websites and graphics printing owing to its capability to resize images in line with various design requirements. 

  
<p align="center"><image src="vectorimagesvg.svg"></p>