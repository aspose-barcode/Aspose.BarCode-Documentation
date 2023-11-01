---
title: Generate MaxiCode Barcodes in C#
linktitle: MaxiCode
type: docs
weight: 50
feedback: BARCODECOM
url: /net/maxicode-barcodes/
---
{{% alert color="primary" %}}[Generate MaxiCode Barcodes Online](https://products.aspose.app/barcode/generate/maxicode): You can test the quality of ***Aspose.BarCode*** generation for MaxiCode barcodes and view the results online.{{% /alert %}}

## **Overview**
*MaxiCode* is a 2D matrix barcode type that allows encoding both text information and byte streams. This symbology supports Reed-Solomon error correction. The amount of data required for error correction and barcode size are strictly specified in the *MaxiCode* standard. A *MaxiCode* barcode includes a round bullseye finder pattern composed of three concentric circles, six orientation patterns, and 33 rows with 29 or 30 hexagonal modules.  
  
The available size of information to be encoded (data capacity) depends on the input data characteristics and constitutes at most 60 bytes or 140 numerical (90 alphanumeric) digits. This symbology has been introduced for postal services; it is intended for industrial standard support and is not recommended for business-as-usual use.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **MaxiCode Mode Settings**
In ***Aspose.BarCode for .NET***, developers can set different generation modes to create *MaxiCode* barcodes using the [*MaxiCodeMode*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/maxicodeparameters/maxicodemode) property of class [*MaxiCodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/maxicodeparameters). The following data modes are supported: 
- *Modes 2 and 3* - special industrial standards that are used in the transportation industry to store the information about shipping along with additional data
- *Modes 4 and 5* - can store arbitrary text information or byte streams and differ from each other only by the number of codewords for error correction and potential data capacity
- *Mode 6* - is the same as *Mode 4*, but the barcode information is used to set up hardware readers

These modes are described further in the article. You can find more information and code samples for complex data modes [here](/net/complex-maxicode/).   

### **MaxiCode Modes 2 and 3**
For correct barcode generation, *MaxiCodeModes 2 and 3* require specifying the input data in the predefined formats that can be summarized as follows:  
- <mark>Format1: “[)>(rs)01(gs)(Postal Code)(gs)(Country Code)(gs)(Service Category)(gs)(Secondary Message)(eot)”</mark>
- <mark>Format2: “(Postal Code 9 digits)(gs)(Country Code)(gs)(Service Category)(gs)(Secondary Message)(eot)”</mark>
  
The following special characters are used:
- Group separator Unicode character: (gs) - \u001d
- Record separator Unicode character: (rs) - \u001e
- End-of-transmission Unicode character: (eot) - \u0004
  
Sample *MaxiCode* barcodes demonstrated below have been created using Formats 1 and 2 of *MaxiCode Mode 2*.
   
|Mode 2|Format 1|Format 2|
| :-: | :-: | :-: |
| |<img src="maxicodemode2first.png" width="40%" height="40%">|<img src="maxicodemode2second.png" width="40%" height="40%">|
  
The following code snippet explains how to work with MaxiCode modes.

``` csharp
string gs = "\u001d";
string rs = "\u001e";
string eot = "\u0004";
//[)>(rs)01(gs)(Postal Code)(gs)(Country Code)(gs)(Service Category)(gs)(Secondary Message)(eot)
string codetext = $"[)>{rs}01{gs}B1050{gs}056{gs}001{gs}ADDITIONAL DATA{eot}";

using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MaxiCode, codetext))
{
    //set MaxiCode mode to 2
    gen.Parameters.Barcode.MaxiCode.MaxiCodeMode = MaxiCodeMode.Mode2;

    gen.Parameters.Barcode.XDimension.Pixels = 15;
    gen.Parameters.Barcode.CodeTextParameters.TwoDDisplayText = "MaxiCode Mode 2";

    gen.Save($"{path}MaxiCodeMode2First.png", BarCodeImageFormat.Png);
}


//(Postal Code 9 digits)(gs)(Country Code)(gs)(Service Category)(gs)(Secondary Message)(eot)
codetext = $"123456789{gs}056{gs}001{gs}ADDITIONAL DATA{eot}";
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MaxiCode, codetext))
{
    //set MaxiCode mode to 2
    gen.Parameters.Barcode.MaxiCode.MaxiCodeMode = MaxiCodeMode.Mode2;

    gen.Parameters.Barcode.XDimension.Pixels = 15;
    gen.Parameters.Barcode.CodeTextParameters.TwoDDisplayText = "MaxiCode Mode 2";

    gen.Save($"{path}MaxiCodeMode2Second.png", BarCodeImageFormat.Png);
}

```
  
### **MaxiCode Modes 4, 5, and 6**
*MaxiCode* barcodes generated in these modes can store the arbitrary text data or byte streams. The code sample given below shows how to use the *MaxiCode Mode 4*.

``` csharp
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MaxiCode, "Åspóse.Barcóde©"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 15;
    //set MaxiCode encode mode to 4
    gen.Parameters.Barcode.MaxiCode.MaxiCodeMode = MaxiCodeMode.Mode4;
    gen.Save($"{path}MaxiCodeEncodeMode4.png", BarCodeImageFormat.Png);
}

```
  
<p align="center"><img src="maxicodemode4.png" width="20%" height="20%"></p>


## **Encoding Mode Settings**
The barcode library enables three data encoding modes for *MaxiCode* barcode generation. Developers can set the required encoding mode using the [*MaxiCodeEncodeMode*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/maxicodeparameters/maxicodeencodemode) property of class [*MaxiCodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/maxicodeparameters) and the corresponding enum [*MaxiCodeEncodeMode*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/maxicodeencodemode/). The following encoding modes are supported: 

- *Auto* - the barcode data is encoded using the value from the [*ECIEncoding*]( https://reference.aspose.com/barcode/net/aspose.barcode.generation/maxicodeparameters/eciencoding/) property
- *Bytes* - encodes byte streams
- *ExtendedCodetext* - uses special control words to enable the use of different encodings at once

### **Encoding Mode *Auto***
The data gets processed with the encoding specified in the [*ECIEncoding*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/maxicodeparameters/eciencoding/) property. By default, ISO-8859-1 is applied.

<p align="center"><img src="maxicodeencodemodeauto.png" width="20%" height="20%"></p>

``` csharp
using (var gen = new BarcodeGenerator(EncodeTypes.MaxiCode, "犬Right狗"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 15;

    //set MaxiCode ECI encoding to UTF8
    gen.Parameters.Barcode.MaxiCode.ECIEncoding = ECIEncodings.UTF8;
    gen.Save($"{path}MaxiCodeEncodyModeAuto.png", BarCodeImageFormat.Png);
}

```

### **Encoding Mode *Bytes***
The *Bytes* mode is used to encode streams of bytes. Any Unicode symbol presented in the input text will be encoded as 2 bytes with the first byte being the least significant one.

<p align="center"><img src="maxicodeencodemodebytes.png" width="20%" height="20%"></p>

``` csharp
byte[] encodedArr = { 0xFF, 0xFE, 0xFD, 0xFC, 0xFB, 0xFA, 0xF9 };

//encode array to string
StringBuilder strBld = new StringBuilder();
foreach (byte bval in encodedArr)
    strBld.Append((char)bval);
var codetext = strBld.ToString();

using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MaxiCode, codetext))
{
    gen.Parameters.Barcode.XDimension.Pixels = 15;
    //set MaxiCode encode mode to Bytes
    gen.Parameters.Barcode.MaxiCode.MaxiCodeEncodeMode = MaxiCodeEncodeMode.Bytes;
    gen.Save($"{path}MaxiCodeEncodeModeBytes.png", BarCodeImageFormat.Png);

}
```

### **Encoding Mode *ExtendedCodeText***
In this mode, the information passed to the [*CodeText*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/codetext/) property includes control words besides the main input data. Control words serve to enable extended control over the data encoding process and allow developers to store textual sequences with different encodings in one barcode. To generate *MaxiCode* barcodes in this format, it is recommended to use class [*MaxiCodeExtCodetextBuilder*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/maxicodeextcodetextbuilder/).

<p align="center"><img src="maxicodeencodemodeextendedcodetext.png" width="20%" height="20%"></p>

``` csharp
//create codetext
MaxiCodeExtCodetextBuilder textBuilder = new MaxiCodeExtCodetextBuilder();
textBuilder.AddECICodetext(ECIEncodings.Win1251, "Will");
textBuilder.AddECICodetext(ECIEncodings.UTF8, "犬Right狗");
textBuilder.AddECICodetext(ECIEncodings.UTF16BE, "犬Power狗");
textBuilder.AddPlainCodetext("Plain text");

//generate codetext
string codetext = textBuilder.GetExtendedCodetext();

//generate
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MaxiCode, codetext))
{
    gen.Parameters.Barcode.XDimension.Pixels = 15;
    //set encode mode to ExtendedCodetext
    gen.Parameters.Barcode.MaxiCode.MaxiCodeEncodeMode = MaxiCodeEncodeMode.ExtendedCodetext;
    gen.Parameters.Barcode.CodeTextParameters.TwoDDisplayText = "ExtendedCodetext mode";
    gen.Save($"{path}MaxiCodeEncodeModeExtendedCodetext.png", BarCodeImageFormat.Png);
}
```

## **Aspect Ratio**
*Aspect Ratio* is the ratio between the barcode width and height. In ***Aspose.BarCode for .NET***, developers can use the [*AspectRatio*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/maxicodeparameters/properties/aspectratio) property of class [*MaxiCodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/maxicodeparameters) to adjust barcode proportions with respect to the X and Y coordinates. It is implemented as a relative coefficient to the [*XDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/xdimension) parameter. *MaxiCode* barcodes should be generated with the value of *AspectRatio* equal to 1. A sample *MaxiCode* barcode provided below has been generated using the *Aspect Ratio* set to 0.5.
  
<p align="center"><img src="maxicodeaspectratio0.5.png" width="20%" height="20%"></p>
  
The following code snippet illustrates how to manage *Aspect Ratio* settings for *MaxiCode* barcode generation.
  
``` csharp
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MaxiCode, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 15;
//set aspect ratio 0.5
gen.Parameters.Barcode.MaxiCode.AspectRatio = 0.5f;
gen.Save($"{path}MaxiCodeAspectRatio0.5.png", BarCodeImageFormat.Png);

```

## **Structured Append**
The structured append mode is a special generation regime that allows combining up to eight MaxiCode barcodes. To use this mode, it is necessary to initialize the following properties:
-	[*MaxiCodeStructuredAppendModeBarcodesCount*]( https://reference.aspose.com/barcode/net/aspose.barcode.generation/maxicodeparameters/maxicodestructuredappendmodebarcodescount/) – is used to set the number of MaxiCode barcodes to be generated (from 2 to 8)
-	[*MaxiCodeStructuredAppendModeBarcodeId*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/maxicodeparameters/maxicodestructuredappendmodebarcodeid/) – sets the position of the barcode in the sequence


<p align="center"><img src="maxicodestructuredappendmode.png" width="20%" height="20%"></p>

``` csharp
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MaxiCode, "Åspóse.Barcóde©"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 15;
    //set MaxiCode strucutured append mode
    gen.Parameters.Barcode.MaxiCode.MaxiCodeStructuredAppendModeBarcodeId = 3;
    gen.Parameters.Barcode.MaxiCode.MaxiCodeStructuredAppendModeBarcodeId = 5;
    gen.Save($"{path}MaxiCodeStructuredAppendMode.png", BarCodeImageFormat.Png);
}
```



