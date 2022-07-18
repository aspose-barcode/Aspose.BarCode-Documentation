---
title: PatchCode Barcodes
type: docs
description: "Aspose.BarCode for .NET enables PatchCode barcode generation."
keywords: "Generate Patch Code Barcode, Create PatchCode, How to Generate Patch Code barcodes, Aspose.BarCode for .NET, C#"
weight: 140
url: /net/how-to-generate-a-patch-code/
---
{{% alert color="primary" %}}[Generate PatchCode Barcodes Online](https://products.aspose.app/barcode/generate/patchcode): You can check the quality of ***Aspose.BarCode*** generation for PatchCode barcodes and view the results online.{{% /alert %}}

## **Overview**
The *PatchCode* symbology has been developed by Kodak to facilitate task management for automatic multi-page document scanning. Such barcodes do not encode any data; instead, a barcode pattern indicates an action to be performed. ***Aspose.BarCode for .NET*** supports six main *PatchCode* patterns and allows generating barcodes in two modes: as separate barcode images to be placed on a page manually; as a complete A4 or US Letter page with the required resolution. *PatchCode* barcode labels are printed on four sides of a document; however, it is sufficient to read only one of them to complete scanning. This feature allows reading barcodes successfully even if pages are rotated.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Supported Patterns**
***Aspose.BarCode for .NET*** enables generating the main *PatchCode* set that consists of six patterns. The extended set of patterns introduced by Kodak later on and not standardized yet is not supported by the library. The main pattern set includes the following options: *Patch I*, *Patch II*, *Patch III*, *Patch IV*, *Patch T*, and *Patch VI*.  
  
Sample barcode labels provided below illustrate six basic *PatchCode* barcode types.
  
|<p align="center">**PatchCode Standards**</p>|<p align="center">**Patch I**</p>|<p align="center">**Patch II**</p>|<p align="center">**Patch III**</p>|<p align="center">**Patch IV**</p>|<p align="center">**Patch T**</p>|<p align="center">**Patch VI**</p>|  
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| |<img src="patchcodei.png">|<img src="patchcodeii.png">|<img src="patchcodeiii.png">|<img src="patchcodeiv.png">|<img src="patchcodet.png">|<img src="patchcodevi.png">|
  
The following code snippet explains how to generate *PatchCode* barcodes using available patterns.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.PatchCode, "Patch I");
gen.Parameters.Barcode.CodeTextParameters.FontMode = FontMode.Manual;
gen.Parameters.Barcode.CodeTextParameters.Font.Size.Pixels = 20;
//Patch I
gen.CodeText = "Patch I";
gen.Save($"{path}PatchCodeI.png", BarCodeImageFormat.Png);
//Patch II
gen.CodeText = "Patch II";
gen.Save($"{path}PatchCodeII.png", BarCodeImageFormat.Png);
//Patch III
gen.CodeText = "Patch III";
gen.Save($"{path}PatchCodeIII.png", BarCodeImageFormat.Png);
//Patch IV
gen.CodeText = "Patch IV";
gen.Save($"{path}PatchCodeIV.png", BarCodeImageFormat.Png);
//Patch T
gen.CodeText = "Patch T";
gen.Save($"{path}PatchCodeT.png", BarCodeImageFormat.Png);
//Patch VI
gen.CodeText = "Patch VI";
gen.Save($"{path}PatchCodeVI.png", BarCodeImageFormat.Png);
{{< /highlight >}}


## **Generation Modes**
***Aspose.BarCode for .NET*** enables different modes of generating *PatchCode* barcodes: as separate images or as A4 or US Letter pages with portrait or landscape orientation. Moreover, the library allows adding an optional complementary *QR Code* as a source of supplement information that may be required to process scanning tasks. Setting other barcode types as complementary barcodes is not supported.  
  
**Setting Generation Format** 
  
To set the format of *PatchCode* barcodes to be generated, it is necessary to initialize the [*PatchFormat*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/patchcodeparameters/properties/patchformat) property of class [*PatchCodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/patchcodeparameters). This property can take the following values: 
- *PatchOnly* - basic *PatchCode* barcode images are generated. This value is used by default. 
- *A4* - A4 pages with portrait orientation are outputted having *PatchCode* barcodes on page borders and an optional QR code in the center.
- *A4_LANDSCAPE* - A4 pages with landscape orientation are created with *PatchCode* barcodes on page borders and an optional QR code in the center. 
- *US_Letter* - US Letter pages with portrait orientation are generated with *PatchCode* barcodes set on page borders and an optional QR code in the center.
- *US_Letter_LANDSCAPE* - US pages with landscape orientation are created with *PatchCode* barcodes placed on page borders and an optional QR code in the center.

**Adding Complementary QR Code**  
  
To add a complementary QR code to a *PatchCode* barcode page (A4 or US Letter), it is necessary to enter any text value into the [*ExtraBarcodeText*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/patchcodeparameters/properties/extrabarcodetext) property of class [*PatchCodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/patchcodeparameters) and then set the [*Location*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/location) property of class [*CodeTextParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters) to "*CodeLocation.None*".  
  
Images below illustrate the *PatchCode* barcode pages generated with and without adding complementary *QR Code* labels.
  
|<p align="center">**Complementary QR Code**</p>|<p align="center">**Is Disabled**</p>|<p align="center">**Is Enabled**</p>|
| :-: | :-: | :-: |
| |<a href="patchcodea4withoutqr.png"> <p align="center"><img src="patchcodea4withoutqr.png" width="40%" height="40%" alttext="PatchCode Barcode Without QR"></p></a>|<a href="patchcodea4withqr.png"> <p align="center"><img src="patchcodea4withqr.png" width="40%" height="40%" alttext="PatchCode Barcode With QR"></p></a>|
  
The following code snippet explains how to set the required format for a *PatchCode* barcode to be generated and how to add a complementary QR code.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.PatchCode, "Patch I");
//create a PatchCode barcode without complimentary QR
gen.Parameters.Barcode.PatchCode.PatchFormat = PatchFormat.A4;
gen.Save($"{path}PatchCodeA4WithoutQR.png", BarCodeImageFormat.Png);
//create a PatchCode barcode with complimentary QR
gen.Parameters.Barcode.PatchCode.PatchFormat = PatchFormat.A4;
gen.Parameters.Barcode.PatchCode.ExtraBarcodeText = "Aspose page extra info";
gen.Parameters.Barcode.CodeTextParameters.Location = CodeLocation.None;
gen.Save($"{path}PatchCodeA4WithQR.png", BarCodeImageFormat.Png);
{{< /highlight >}}