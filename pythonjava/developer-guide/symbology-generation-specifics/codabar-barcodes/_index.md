---
title: Codabar Barcodes
type: docs
description: "Use Aspose.BarCode for Python to generate Codabar barcodes"
ai_search_scope: "barcode_python-java_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 110
url: /python-java/generate-codabar/
---
{{% alert color="primary" %}}[Generate Codabar Barcodes Online](https://products.aspose.app/barcode/generate/codabar): You can test the quality of ***Aspose.BarCode*** generation for Codabar barcodes and get results online.{{% /alert %}}

## **Overview**
***Aspose.BarCode for Python via Java*** supports the *Codabar* type that allows encoding numerical characters and a set of six punctuation signs. *Codabar* barcodes may include four optional alphabet symbols (generally, A, B, C, or D) serving as start and stop characters. As such, this symbology supports four sets of start digits and four sets of stop ones. In this way, using the same input data, it is possible to create 16 barcodes with service sets of start and stop symbols.  
  
Input text in *Codabar* barcodes has the following format:  
<p align="center"><mark>[Start Character "A/B/C/D"] [Data Digits from the charset: "0-9" and "–$./:+"] [Stop Character "A/B/C/D"]</mark></p>
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
  
## **Start and Stop Symbols**
Start and stop digits can be encoded separately using any of four formats (A, B, C, or D). To specify the preferred format, it is possible to use *setCodabarStartSymbol* and *setCodabarStopSymbol* methods from class [*CodabarParameters*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.generation.codabar_parameters/). The default set of start and stop digits is "A".  
  
Following barcode images have been created using various sets of start and stop characters.
  
|Start and Stop Characters|A+A|B+B|C+C|D+D|
| :-: | :-: | :-: | :-: | :-: |
| |<img src="codabarstartastopa.png">|<img src="codabarstartbstopb.png">|<img src="codabarstartcstopc.png">|<img src="codabarstartdstopd.png">|
  
<!--The following code sample shows how to use various start and stop digits in *Codabar* barcodes. 
    
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Codabar, "-12345-");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//set start A and stop A
gen.Parameters.Barcode.Codabar.CodabarStartSymbol = CodabarSymbol.A;
gen.Parameters.Barcode.Codabar.CodabarStopSymbol = CodabarSymbol.A;
gen.Save($"{path}CodabarStartAStopA.png", BarCodeImageFormat.Png);
//set start B and stop B
gen.Parameters.Barcode.Codabar.CodabarStartSymbol = CodabarSymbol.B;
gen.Parameters.Barcode.Codabar.CodabarStopSymbol = CodabarSymbol.B;
gen.Save($"{path}CodabarStartBStopB.png", BarCodeImageFormat.Png);
//set start C and stop C
gen.Parameters.Barcode.Codabar.CodabarStartSymbol = CodabarSymbol.C;
gen.Parameters.Barcode.Codabar.CodabarStopSymbol = CodabarSymbol.C;
gen.Save($"{path}CodabarStartCStopC.png", BarCodeImageFormat.Png);
//set start D and stop D
gen.Parameters.Barcode.Codabar.CodabarStartSymbol = CodabarSymbol.D;
gen.Parameters.Barcode.Codabar.CodabarStopSymbol = CodabarSymbol.D;
gen.Save($"{path}CodabarStartDStopD.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
  
## **Checksum Settings**
By default, the *Codabar* standard does not require obligatory checksum controls. If checksum controls are needed, *Codabar* provides two checksum algorithms: Mod10 and Mod16. The pseudocode given below shows how these two checksum algorithms can be used.  

```java

//Mod10
foreach (var value in encodedCodetext)
    checkSum = (checkSum + value) % 10;
//Mod16
foreach (var value in encodedCodetext)
    checkSum = (checkSum + value) % 16;

```
  
Checksum controls for *Codabar* can be enabled using the [*EnableChecksum*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.generation.enable_checksum/) enum. The required checksum algorithm can be allocated through the [*CodabarChecksumMode*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.generation.codabar_checksum_mode/) enum. By default, the *Mod16* checksum is applied.  
  
*Codabar* barcode images below have been generated using different checksum control settings.

|Checksum Calculation|Is Set to *None*|Is Set to *Mod10*|Is Set to *Mod16*|
| :-: | :-: | :-: | :-: |
| |<img src="codabarchecksumnone.png">|<img src="codabarchecksummod10.png">|<img src="codabarchecksummod16.png">|
  
<!--The following code snippet shows how to set different checksum control modes (Mod10 and Mod16) for *Codabar* barcodes. 

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Codabar, "-12345-");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//set None checksum
gen.Parameters.Barcode.IsChecksumEnabled = EnableChecksum.Default;
gen.Save($"{path}CodabarChecksumNone.png", BarCodeImageFormat.Png);
//set Mod10 checksum
gen.Parameters.Barcode.IsChecksumEnabled = EnableChecksum.Yes;
gen.Parameters.Barcode.Codabar.CodabarChecksumMode = CodabarChecksumMode.Mod10;
gen.Save($"{path}CodabarChecksumMod10.png", BarCodeImageFormat.Png);
//set Mod16 checksum
gen.Parameters.Barcode.IsChecksumEnabled = EnableChecksum.Yes;
gen.Parameters.Barcode.Codabar.CodabarChecksumMode = CodabarChecksumMode.Mod16;
gen.Save($"{path}CodabarChecksumMod16.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->