---
title: Generation of EAN-2 and EAN-5 as Supplement Barcodes in Java
linktitle: EAN-2 and EAN-5 as Supplement
type: docs
weight: 160
url: /java/use-checksum-and-supplement-data-for-barcodes/
---
{{% alert color="primary" %}}[Generate Barcodes Online](https://products.aspose.app/barcode/generate): You can check the quality of ***Aspose.BarCode*** barcode generation and view the results online.{{% /alert %}}

## **Overview**
***Aspose.BarCode for Java*** supports *EAN-2* and *EAN-5* types but only as a supplement for some barcode types, i.e. *EAN-8*, *EAN-13*, *Interleaved 2-of-5*, *Standard 2-of-5*, *ISMN*, *ISBN*, *ISSN*, *UPC-E*, or *UPC-A*. Supplement barcodes are used to encode two or five additional characters with their own checksum controls. Supplement barcodes have applications that are limited to specific industrial tasks. They can also be used in production to store additional information about products or their price. 
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
  
## **Supplement Barcode Settings**
Conventional barcodes serve to encode the most important information about items or products. To store additional (supplement) data besides primary barcodes, developers can use a special method called *setSupplementData* of class [*SupplementParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/SupplementParameters). The *setSupplementData* method needs to be called passing 2 or 5 additional numerical digits for *EAN-2* or *EAN-5*, respectively. Thereafter, the library identifies the suitable barcode type automatically based on the entered number of digits. Supplement barcode size is computed automatically according to the parameters of the primary barcode.  
  
The following barcodes have been created enabling *EAN-2* and *EAN-5* supplements for *EAN-13* barcodes.

|Supplement Barcode|EAN-2|EAN-5|
| :-: | :-: | :-: |
| |<img src="supplementean2.png">|<img src="supplementean5.png">|
  
<!--The following code snippet explains how to generate supplement barcodes using *EAN-2* and *EAN-5*.
    
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
{{< /highlight >}}-->

## **Adjusting Supplement Spacing**
To define the size of a gap between the main and supplement barcodes, the library provides the *getSupplementSpace* method of class [*SupplementParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/SupplementParameters).  
  
The barcode samples demonstrated below have been generated with different gap settings.  
  
|Supplement Spacing|Is Set to 20 Pixels|Is Set to 40 Pixels|
| :-: | :-: | :-: |
| |<img src="supplementspace20pixels.png">|<img src="supplementspace40pixels.png">|
  
<!--The following code sample shows how to modify the spacing between main and supplement barcodes for a *EAN 13* barcode.
  
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
{{< /highlight >}}-->