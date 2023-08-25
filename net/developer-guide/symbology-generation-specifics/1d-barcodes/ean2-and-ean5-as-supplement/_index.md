---
title: Generate EAN-2 and EAN-5 Barcodes as Supplement in C#
type: docs
weight: 60
url: /net/ean2-and-ean5-as-supplement/
---
{{% alert color="primary" %}}[Generate Barcodes Online](https://products.aspose.app/barcode/generate): You can check the quality of ***Aspose.BarCode*** barcode generation and view the results online.{{% /alert %}}

## **Overview**
***Aspose.BarCode for .NET*** enables the generation of *EAN 2* and *EAN 5* barcode types but only as supplements for the following symbologies: *EAN 13*, *EAN 8*, *Interleaved 2-of-5*, *ISBN*, *ISMN*, *ISSN*, *Standard 2-of-5*, *UPC-A*, and *UPC-E*. Supplement barcodes may be used to encode two or five complementary digits in addition to the main barcode and have their own checksum. The use of such barcodes is reserved in various industries; however, in production, they can also be applied to encode additional information, for example, about an item or its price. 
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
  
## **Supplement Barcode Settings**
The main information about a product or an item needs to be encoded in the primary barcode. To insert additional (supplement) information, ***Aspose.BarCode for .NET*** provides a specific property that is called [*SupplementData*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/supplementparameters/properties/supplementdata) and is defined in class [*SupplementParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/supplementparameters) corresponding to the [*Supplement*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/supplement) property group. The [*SupplementData*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/supplementparameters/properties/supplementdata) property is initialized by inputting 2 or 5 additional numerical digits for *EAN 2* or *EAN 5*, respectively. Then, the required barcode type is defined automatically according to the specified number of digits. Then, the size of a supplement barcode is calculated automatically depending on the main barcode parameters.  
  
Barcode labels provided below have been generated with *EAN 2* and *EAN 5* supplement data settings enabled for *EAN 13* barcodes.

|<p align="center">**Supplement Barcode**</p>|<p align="center">**EAN 2**</p>|<p align="center">**EAN 5**</p>|
| :-: | :-: | :-: |
| |<img src="supplementean2.png">|<img src="supplementean5.png">|
  
The following code sample explains how to generate supplement barcodes using *EAN 2* and *EAN 5* symbologies.
    
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN13, "1234567890128");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.Barcode.Supplement.SupplementSpace.Pixels = 20;
//set EAN 2 supplement
gen.Parameters.Barcode.Supplement.SupplementData = "12";
gen.Save($"{path}SupplementEAN2.png", BarCodeImageFormat.Png);
//set EAN 5 supplement
gen.Parameters.Barcode.Supplement.SupplementData = "12345";
gen.Save($"{path}SupplementEAN5.png", BarCodeImageFormat.Png);
{{< /highlight >}}

## **Adjust Spacing Between Main and Supplement Barcodes**
To define the size of a gap between the main and supplement barcodes, the library provides the [*SupplementSpace*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/supplementparameters/properties/supplementspace) property of class [*SupplementParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/supplementparameters).  
  
Barcode samples demonstrated below have been generated with different gap settings.  
  
|<p align="center">**Supplement Spacing**</p>|<p align="center">**Is Set to 20 Pixels**</p>|<p align="center">**Is Set to 40 Pixels**</p>|
| :-: | :-: | :-: |
| |<img src="supplementspace20pixels.png">|<img src="supplementspace40pixels.png">|
  
The following code snippet explains how to set the size of the spacing between the main and supplement barcodes in case of using the *EAN 13* symbology.
  
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