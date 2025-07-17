---
title: Generate Codablock-F Barcodes in Java
linktitle: Codablock-F
feedback: BARCODECOM
type: docs
ai_search_scope: "barcode_java_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 20
url: /java/codablockf-barcodes/
---
{{% alert color="primary" %}}[Generate Codablock-F Barcodes Online](https://products.aspose.app/barcode/generate/codablock?type=codablockf): You can check the quality of ***Aspose.BarCode*** generation for Codablock-F barcodes and view results online.{{% /alert %}}

## **Overview**
*Codablock-F* is a stacked multiple-row barcode type that enables creating barcodes that include many *Code 128* barcodes. This symbology allows encoding at most 2,725 digits and contains from 2 to 44 rows with from 4 to 62 characters. *Codablock-F* benefits from two principle differences compared with the basic *Code 128* symbology. It provides flexible settings of barcode layout in terms of the number of rows and columns and thus allows organizing vertical and horizontal space more efficiently. Moreover, it contains two additional check digits (calculated using the modulo 86 algorithm) for a *Codablock-F* barcode besides obligatory checksum controls that are included in each row of *Code 128* barcodes. Finally, *Codablock-F* can be detected using laser scanners.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
  
## **Barcode Height Settings**

***Aspose.BarCode for Java*** allows developers to modify the height of each row in a stacked barcode through the *setAspectRatio* method of class [*CodablockParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/CodablockParameters). *AspectRatio* is determined as a relative coefficient to *XDimension*. For *Codablock-F* barcodes, the value of *AspectRatio* should be set greater than 10.  
  
Following barcode images have been created using various aspect ratio settings. 
  
|Aspect Ratio|Is Set to 15|Is Set to 30|
| :-: | :-: | :-: |
| |<img src="codablockfaspectratio15.png">|<img src="codablockfaspectratio30.png">|
  
<!--The following code sample shows how to modify the height of a *Codablock-F* barcode.
  
{{< highlight java>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CodablockF, "Aspose");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//set CodablockF aspect ratio 15
gen.Parameters.Barcode.Codablock.AspectRatio = 15;
gen.Save($"{path}CodablockFAspectRatio15.png", BarCodeImageFormat.Png);
//set CodablockF aspect ratio 30
gen.Parameters.Barcode.Codablock.AspectRatio = 30;
gen.Save($"{path}CodablockFAspectRatio30.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
  

## **Layout Settings**
To adjust the layout of a *Codablock-F* barcode in terms of the number of columns and rows, *setColumns* and *setRows* methods of class [*CodablockParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/CodablockParameters) can be used. The maximum values of columns and rows can be 62 and 44, respectively.  
  
Barcode images provided below have been generated using different layout settings.
  
|Layout Settings|4 Columns|4 Rows|6 Rows and 4 Columns|
| :-: | :-: | :-: | :-: | :-: |
| |<img src="codablockfcol4.png">|<img src="codablockfrow4.png">|<img src="codablockfrow6col4.png">|
  
<!--The following code snippet illustrates how to customize layout settings for *Codablock-F* barcodes.
  
{{< highlight java>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CodablockF, "Aspose.Barcode");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//set CodablockF columns 4
gen.Parameters.Barcode.Codablock.Columns = 4;
gen.Parameters.Barcode.Codablock.Rows = 0;
gen.Save($"{path}CodablockFCol4.png", BarCodeImageFormat.Png);
//set CodablockF rows 4
gen.Parameters.Barcode.Codablock.Columns = 0;
gen.Parameters.Barcode.Codablock.Rows = 4;
gen.Save($"{path}CodablockFRow4.png", BarCodeImageFormat.Png);
//set CodablockF columns 4 rows 6
gen.Parameters.Barcode.Codablock.Columns = 4;
gen.Parameters.Barcode.Codablock.Rows = 6;
gen.Save($"{path}CodablockFRow6Col4.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->