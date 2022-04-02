---
title: MaxiCode Symbologies
type: docs
weight: 80
url: /java/maxicode-barcodes/
---
{{% alert color="primary" %}}[Generate MaxiCode Barcodes Online](https://products.aspose.app/barcode/generate/maxicode): You can test the quality of ***Aspose.BarCode*** generation for MaxiCode barcodes and view the results online.{{% /alert %}}

## **Overview**
*MaxiCode* is a 2D matrix barcode type that allows encoding both text information and byte streams. This symbology supports Reed-Solomon error correction. The amount of data required for error correction and barcode size are strictly specified in the *MaxiCode* standard. A *MaxiCode* barcode includes a round bullseye finder pattern composed of three concentric circles, six orientation patterns, and 33 rows with 29 or 30 hexagonal modules.  
  
The available size of information to be encoded (data capacity) depends on the input data characteristics due to encoding specificities and constitutes at most 60 bytes or 140 numerical (90 alphanumeric) digits. This symbology has been introduced for postal services; it is intended for industrial standard support and is not recommended for arbitrary use.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Encoding Mode Settings**
In ***Aspose.BarCode for Java***, developers can set different encoding modes for *MaxiCode* barcode generation using the [*MaxiCodeEncodeMode*]() property of class [*MaxiCodeParameters*](). The following encoding modes are supported: 
- *Encoding Modes 2 and 3* - special industrial standards that are used in the transportation industry and intended for storing the information about shipping along with additional data
- *Encoding Modes 4 and 5* - are intended to encode arbitrary text information or byte streams and differ from each other only by the number of codewords for error correction and potential data capacity
- *Encoding Mode 6* - is similar to *Encoding Mode 4*, but the information encoded in barcodes is intended for hardware reader programming only

These modes are described further in the article.   

### **Encoding Modes 2 and 3**
For correct barcode generation, *Encoding Modes 2 and 3* require specifying the input data in the predefined formats that can be summarized as follows:  
- <mark>Format1: “[)>(rs)01(gs)(Postal Code)(gs)(Country Code)(gs)(Service Category)(gs)(Secondary Message)(eot)”</mark>
- <mark>Format2: “(Postal Code 9 digits)(gs)(Country Code)(gs)(Service Category)(gs)(Secondary Message)(eot)”</mark>
  
The following special characters are used:
- Group separator Unicode character: (gs) - \u001d
- Record separator Unicode character: (rs) - \u001e
- End-of-transmision Unicode character: (eot) - \u0004
  
Sample *MaxiCode* barcodes demonstrated below have been created using Formats 1 and 2 of *Encoding Mode 2*.
   
|<p align="center">**Mode 2**</p>|<p align="center">**Format 1**</p>|<p align="center">**Format 2**</p>|
| :-: | :-: | :-: |
| |<img src="maxicodeencodemode2first.png" width="40%" height="40%">|<img src="maxicodeencodemode2second.png" width="40%" height="40%">|
  
The following code snippet explains how to work with encoding modes.

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MaxiCode, "");
gen.Parameters.Barcode.XDimension.Pixels = 15;
gen.Parameters.Barcode.CodeTextParameters.TwoDDisplayText = "MaxiCode Mode 2";

string gs = "\u001d";
string rs = "\u001e";
string eot = "\u0004";
//set MaxiCode encode mode to 2 and valid codetext
gen.Parameters.Barcode.MaxiCode.MaxiCodeEncodeMode = 2;
//[)>(rs)01(gs)(Postal Code)(gs)(Country Code)(gs)(Service Category)(gs)(Secondary Message)(eot)
gen.CodeText = $"[)>{rs}01{gs}B1050{gs}056{gs}001{gs}ADDITIONAL DATA{eot}";
gen.Save($"{path}MaxiCodeEncodeMode2First.png", BarCodeImageFormat.Png);

//set MaxiCode encode mode to 2 and valid codetext
gen.Parameters.Barcode.MaxiCode.MaxiCodeEncodeMode = 2;
//(Postal Code 9 digits)(gs)(Country Code)(gs)(Service Category)(gs)(Secondary Message)(eot)
gen.CodeText = $"123456789{gs}056{gs}001{gs}ADDITIONAL DATA{eot}";
gen.Save($"{path}MaxiCodeEncodeMode2Second.png", BarCodeImageFormat.Png);
{{< /highlight >}}  
  
### **Encoding Modes 4, 5, and 6**
These modes allow encoding the arbitrary text data and byte streams. The code sample given below shows how to perform byte stream encoding when *Encoding Mode 4* is enabled.

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MaxiCode, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 15;
//set MaxiCode encode mode to 4
gen.Parameters.Barcode.MaxiCode.MaxiCodeEncodeMode = 4;
gen.Save($"{path}MaxiCodeEncodeMode4.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
<p align="center"><img src="maxicodeencodemode4.png" width="20%" height="20%"></p>

## **Aspect Ratio**
*Aspect Ratio* is the ratio between the barcode width and height. In ***Aspose.BarCode for Java***, developers can use the [*AspectRatio*]() property of class [*MaxiCodeParameters*]() to adjust barcode proportions with respect to the X and Y coordinates. It is implemented as a relative coefficient to the [*XDimension*]() parameter. *MaxiCode* barcodes should be generated with the value of *AspectRatio* equal to 1. A sample *MaxiCode* barcode provided below has been generated using the *Aspect Ratio* set to 0.5.
  
<p align="center"><img src="maxicodeaspectratio0.5.png" width="20%" height="20%"></p>
  
The following code snippet illustrates how to manage *Aspect Ratio* settings for *MaxiCode* barcode generation.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MaxiCode, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 15;
//set aspect ratio 0.5
gen.Parameters.Barcode.MaxiCode.AspectRatio = 0.5f;
gen.Save($"{path}MaxiCodeAspectRatio0.5.png", BarCodeImageFormat.Png);
{{< /highlight >}}