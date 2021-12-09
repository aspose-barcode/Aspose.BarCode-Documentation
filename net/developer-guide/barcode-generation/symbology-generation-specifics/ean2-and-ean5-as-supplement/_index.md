---
title: EAN2 and EAN5 as supplement barcodes
type: docs
weight: 40
url: /net/ean2-and-ean5-as-supplement/
---

## Overview
***Aspose.Barcode for .NET*** enables the generation of *EAN2* and *EAN5* barcode types but only as supplements for the following symbologies: *EAN13*, *EAN8*, *Interleaved 2 of 5*, *ISBN*, *ISMN*, *ISSN*, *Standard 2 of 5*, *UPC A*, and *UPC E*. Supplement barcodes may be used to encode two or five complementary digits in addition to the main barcode and have their own checksum. The use of such barcodes is reserved in various industries; however, in production, they can also be applied to encode additional information, for example, about an item or its price. 
  
## Setting Supplement Data
It is necessary to encode main information about a product in the primary barcode. To insert additional (supplement) information, ***Aspose.Barcode for .NET*** provides a specific property that is called [*SupplementData*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/supplementparameters/properties/supplementdata) and is defined in class [*SupplementParameters*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/supplementparameters) correspoding to the [*Supplement*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/supplement) property group. The *SupplementData* property needs to be initialized by adding 2 or 5 additional numerical digits for EAN2 or EAN5, respectively. Then, setting the required barcode type is performed automatically depending on the specified number of digits. The size of a supplement barcode is calculated automatically depending on the main barcode parameters.  
  
The barcode labels provided below have been generated with the enabled various supplement data settings for *EAN31* barcodes.

|Supplement Data|EAN2|EAN5|
|:---:|:---:|:---:|
| |<img src="SupplementEAN2.png">|<img src="SupplementEAN5.png">|
  
The following code sample explains how to generate supplement barcodes using the *EAN2* and *EAN5* symbologies.
    
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN13, "1234567890128");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.Barcode.Supplement.SupplementSpace.Pixels = 20;
//set EAN2 supplement
gen.Parameters.Barcode.Supplement.SupplementData = "12";
gen.Save($"{path}SupplementEAN2.png", BarCodeImageFormat.Png);
//set EAN5 supplement
gen.Parameters.Barcode.Supplement.SupplementData = "12345";
gen.Save($"{path}SupplementEAN5.png", BarCodeImageFormat.Png);
{{< /highlight >}}

## Setting Supplement Space
To set the size of a gap between the main and supplement barcodes, the library provides the [*SupplementSpace*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/supplementparameters/properties/supplementspace) property of class [*SupplementParameters*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/supplementparameters).  
  
The barcode samples demonstrated below have been generated with different gap settings.  
  
|Supplement Space|Is Set to 20 Pixels|Is Set to 40 Pixels|
|:---:|:---:|:---:|
| |<img src="SupplementSpace20Pixels.png">|<img src="SupplementSpace40Pixels.png">|
  
The following code snippet explains how to set the size of space between the main and supplement barcodes in case of using the *EAN13* symbology.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN13, "1234567890128");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.Barcode.Supplement.SupplementData = "12345";
//set supplement space 20 pixels
gen.Parameters.Barcode.Supplement.SupplementSpace.Pixels = 20;
gen.Save($"{path}SupplementSpace20Pixels.png", BarCodeImageFormat.Png);
//set supplement space 40 pixels
gen.Parameters.Barcode.Supplement.SupplementSpace.Pixels = 40;
gen.Save($"{path}SupplementSpace40Pixels.png", BarCodeImageFormat.Png);
{{< /highlight >}}