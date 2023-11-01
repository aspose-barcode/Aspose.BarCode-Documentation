---
title: Data Matrix Barcodes
type: docs
description: "How to use Aspose.BarCode for Android to generate Data Matrix barcodes"
weight: 60
url: /androidjava/datamatrix-generation/
---
{{% alert color="primary" %}}[Generate Data Matrix Barcodes Online](https://products.aspose.app/barcode/generate/datamatrix): You can test the quality of ***Aspose.BarCode*** generation for Data Matrix barcodes and get results online.{{% /alert %}}

## **Overview**
*Data Matrix* is a 2D matrix symbology used to generate barcodes of rectangular and square shapes. It is a widespread industrial standard that can be used to encode characters and streams of bytes. Maximum configuration of *Data Matrix* contains up to 144 rows and columns and allows encoding at most 3,116 numerical digits or 2,335 ASCII symbols or 1,555 bytes. The *Data Matrix* barcode data includes special information for integrity verification and error correction. The error correction mechanism allows reading barcodes with severe damages. *Data Matrix* includes two standards described in the table below.  
   
|Data Matrix Standard|Description|
|---|---|
|*ECC 000-140*|Several obsolete standards that enable square barcode configuration only, use outdated encoding algorithms and support convolutional error correction. It is recommended not to apply these standards to business-as-usual goals as they currently serve only to execute industrial tasks that are compatible with outdated instructions|
|*ECC 200*|Modern standard that enables both square and rectangular barcode configurations, utilizes up-to-date encoding methods and supports Reed-Solomon error correction. It is applicable to any up-to-date application|
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Data Matrix ECC Standards**
To enable the required *Data Matrix* standard, developers can use the *setDataMatrixEcc* method of class [*DataMatrixParameters*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/DataMatrixParameters). This method allows setting one of the supported standards: *ECC 000-140* (outdated standards) or *ECC 200* (recent universal standard) using the values available in the [*DataMatrixEccType*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/DataMatrixEccType) enum. The value of *DataMatrixEccType.ECC_200* is set by default.
  
### ***ECC 200***
***Aspose.BarCode for Android*** allows explicitly setting the *ECC 200* standard by calling the *setDataMatrixEcc* method and passing values *ECC_AUTO* or *ECC_200*. *ECC 200* is conpatible with all encoding modes specified in the [*DataMatrixEncodeMode*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/DataMatrixEncodeMode) enum. Moreover, it allows encoding Unicode characters through the *setCodeTextEncoding* method. The capacity of additional recovery information required for error correction is precisely limited for barcodes according to their size.  
  
<!--The following code sample shows how to enable the *ECC 200* encoding standard.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 4;
//set DataMatrix ECC to 140
gen.Parameters.Barcode.DataMatrix.DataMatrixEcc = DataMatrixEccType.Ecc200;
gen.Save($"{path}DatamatrixEcc200Basic.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
  
<p align="center"><img src="datamatrixecc200basic.png"></p>  
  
### ***ECC 000-140***  
*ECC 000-140* standards can be applied only to a few encoding modes included in the [*DataMatrixEncodeMode*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/DataMatrixEncodeMode) enum, i.e. *AUTO*, *FULL*, and *ASCII*. All other encoding modes are processed as *FULL* by default. The *setCodeTextEncoding* method  is not applicable to these standards and therefore, encoding Unicode characters is not supported. Barcode layout confirgurations of *ECC 000-140* differ significantly from *ECC 200*. At the same time, different standards corresponding to *ECC 000-140* are quite similar between each other and only have different data recovery capacity, as explained below. 
  
|ECC Standard|Data Recovery Capacity|
| :-: | :-: |
|**ECC_000**|Only error detection|
|**ECC_050**|2.8%|
|**ECC_080**|5.5%|
|**ECC_100**|12.6%|
|**ECC_140**|25%| 
  
<!--The following code snippet explains how to work with the *ECC 140* standard.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 4;
//set DataMatrix ECC to 140
gen.Parameters.Barcode.DataMatrix.DataMatrixEcc = DataMatrixEccType.Ecc140;
gen.Save($"{path}DatamatrixEcc000140Basic.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
  
<p align="center"><img src="datamatrixecc000140basic.png"></p>
  
## **Encoding Modes**
***Aspose.BarCode for Android via Java*** supports various encoding modes that are defined in the [*DataMatrixEncodeMode*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/DataMatrixEncodeMode) enum of class [*DataMatrixParameters*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/DataMatrixParameters). This enum provides nine encoding modes, as described below. The *AUTO* encoding mode is used by default.
  
|Encoding Mode|Description|
|---|---|
|*AUTO*|Similar to *ASCII*|
|*ASCII*|Encodes both ASCII characters and streams of bytes; characters from 128 to 255 are encoded with two bytes. The *FULL* mode is recommended to encode streams of bytes|
|*FULL*|Encodes any symbol in 8 bits. This mode is recommended to encode byte streams|
|*CUSTOM*|Uses the encoding determined in *BarCodeBuilder.CodeTextEncoding*; thereafter, the generated stream of bytes is further processed through the *FULL* mode|
|*C40*, *TEXT*, *EDIFACT*, and *ANSIX12*|Encode predefined sets of symbols through special industrial encodings, i.e. C40, Text, EDIFACT, and ANSI X12|
|*EXTENDED_CODETEXT*|Gives flexible control over encodings and allows setting the required encoding for a part of the input message manually|
  
For all encoding modes except *CUSTOM*, the encoding determined in *BarCodeBuilder.CodeTextEncoding* is used to process input information that includes a Unicode symbol (any character with the value over 255). The *CUSTOM* mode is enabled in the *ECC 200* standard only. Further in the article, it is explained how to manage different encoding modes.
  
### ***AUTO* and *ASCII* Encoding Modes**
*AUTO* and *ASCII* encoding modes allow encoding ASCII symbols and byte streams. However, encoding characters from 128 to 255 takes two bytes for each character. In cases when input text includes Unicode symbols, information needs to be re-encoded with the use of the encoding determined in *BarCodeBuilder.CodeTextEncoding*.  
  
<!--The following code snippet explains how to enable the *AUTO* encoding mode.

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 4;
//set encode mode to Auto
gen.Parameters.Barcode.DataMatrix.DataMatrixEncodeMode = DataMatrixEncodeMode.Auto;
gen.Save($"{path}DatamatrixEncodeModeAuto.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
  
<p align="center"><img src="datamatrixencodemodeauto.png"></p> 

### **Encoding Streams of Bytes in *FULL* Mode**
The *FULL* mode is used to encode streams of bytes. In this mode, each byte is encoded with 8 bits. If input barcode data contains Unicode characters, information gets re-encoded with the encoding set in *BarCodeBuilder.CodeTextEncoding*. It is possible to represent text lines by calling the *setTwoDDisplayText* method. 
  
<!--The following code snippet shows how to work with the *FULL* encoding mode.
  
{{< highlight csharp>}}
byte[] encodedArr = { 0xFF, 0xFE, 0xFD, 0xFC, 0xFB, 0xFA, 0xF9 };

//encode array to string
StringBuilder strBld = new StringBuilder();
foreach (byte bval in encodedArr)
    strBld.Append((char)bval);

//encode in a DataMatrix barcode
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, strBld.ToString());
gen.Parameters.Barcode.XDimension.Pixels = 4;
//set encode mode to Full
gen.Parameters.Barcode.DataMatrix.DataMatrixEncodeMode = DataMatrixEncodeMode.Full;
gen.Parameters.Barcode.CodeTextParameters.TwoDDisplayText = "Bytes mode";
gen.Save($"{path}DatamatrixEncodeModeFullBytes.png", BarCodeImageFormat.Png);

//attempt to recognize
BarCodeReader read = new BarCodeReader(gen.GenerateBarCodeImage(), DecodeType.DataMatrix);
foreach (BarCodeResult result in read.ReadBarCodes())
    Console.WriteLine("DatamatrixEncodeModeFullBytes:" + BitConverter.ToString(result.CodeBytes));
{{< /highlight >}}-->

<p align="center"><img src="datamatrixencodemodefullbytes.png"></p> 

### **Encoding Unicode Text in *CUSTOM* Mode**
In all cases, the *CUSTOM* encoding mode implies first re-encoding barcode information into a stream of bytes. Thereafter, the generated stream gets processed in the *FULL* mode; here, each byte is encoded using 8 bits.  
  
<!--The following code sample explains how to manage the *Custom* mode. 

{{< highlight csharp>}}
Console.OutputEncoding = Encoding.Unicode;
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "Aspose常に先を行く");
gen.Parameters.Barcode.XDimension.Pixels = 4;
//set encode mode to Full
gen.Parameters.Barcode.DataMatrix.DataMatrixEncodeMode = DataMatrixEncodeMode.Custom;
gen.Parameters.Barcode.DataMatrix.CodeTextEncoding = Encoding.UTF8;
gen.Save($"{path}DatamatrixEncodeModeCustom.png", BarCodeImageFormat.Png);

//attempt to recognize it
BarCodeReader read = new BarCodeReader(gen.GenerateBarCodeImage(), DecodeType.DataMatrix);
foreach (BarCodeResult result in read.ReadBarCodes())
    Console.WriteLine("DatamatrixEncodeModeCustom:" + result.GetCodeText(Encoding.UTF8));
{{< /highlight >}}-->

<p align="center"><img src="datamatrixencodemodecustom.png"></p> 

### **Extended Encoding Controls in *EXTENDED_CODETEXT* Mode**
The *EXTENDED_CODETEXT* mode allows encoding input data applying various encodings to different parts of barcode text if requested by specific industrial standards. It is possible to combine different supported encodings, i.e. *AUTO*, *ASCII*, *C40*, *TEXT*, *ANSIX12*, and *EDIFACT*.  
  
It is necessary to formulate a barcode text message using the following form: <mark>"\Encoding_mode_name:text\Encoding_mode_name:text"</mark>. It is necessary to double all backslashes in text. To display the text message under a barcode, it is required to call the *setTwoDDisplayText* method.  
  
<!--The following code sample demonstrates how to enable the *EXTENDED_CODETEXT* mode.  
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "");
gen.Parameters.Barcode.XDimension.Pixels = 4;
//set encode mode to ExtendedCodetext
gen.Parameters.Barcode.DataMatrix.DataMatrixEncodeMode = DataMatrixEncodeMode.ExtendedCodetext;
//set codetext with multiple encodings (ansix12 encoding)(Text)(ascii encoding)(Text)(edifact encoding)(Text)
gen.CodeText = @"\ansix12:ANSIX12TEXT\ascii:backslash must be \\ doubled\edifact:EDIFACT-ENCODED-TEXT";
gen.Parameters.Barcode.CodeTextParameters.TwoDDisplayText = "Extended Codetext";
gen.Save($"{path}DatamatrixExtendedCodetext.png", BarCodeImageFormat.Png);

//attempt to recognize
BarCodeReader read = new BarCodeReader(gen.GenerateBarCodeImage(), DecodeType.DataMatrix);
foreach (BarCodeResult result in read.ReadBarCodes())
    Console.WriteLine("DatamatrixExtendedCodetext:" + result.CodeText);
{{< /highlight >}}-->
  
<p align="center"><img src="datamatrixextendedcodetext.png"></p> 
  
### **Special Industrial Encoding Modes: *C40*, *TEXT*, *EDIFACT*, and *ANSIX12***
Various special encoding modes, such as *TEXT*, *C40*, *EDIFACT*, and *ANSIX12*, can be used to encode barcode information in forms compatible with specific industrial requirements. These modes are applicable to industrial tasks only.  
  
<!--The following code snippet shows how to enable the *C40* encoding mode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE.BARCODE");
gen.Parameters.Barcode.XDimension.Pixels = 6;
//set encode mode to C40
gen.Parameters.Barcode.DataMatrix.DataMatrixEncodeMode = DataMatrixEncodeMode.C40;
gen.Save($"{path}DatamatrixEncodeModeC40.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
  
<p align="center"><img src="datamatrixencodemodec40.png"></p> 
  
## **Layout Settings**
The layout for *Data Matrix* barcode generation can be determined through *setRows* and *setColumns* methods of class [*DataMatrixParameters*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/DataMatrixParameters). If these methods have not been called explicitly, ***Aspose.BarCode for Android via Java*** identifies a layout that is optimal for the size of input data. Barcode layout configurations are different in *ECC 000-140* and *ECC 200* standards. Only *ECC 200* allows modifying the number of rows and columns. In *ECC 000-140* standards, the suitable barcode layout configuration is determined automatically. The *ECC 200* standard prescribes setting even numbers of rows and columns. In other words, it supports the following layout configurations: 8 x 18; 16 x 48; 10 x 10; 144 x 144.

|<p align="center">**Layout Settings**</p>|<p align="center">**22 Rows and 22 Columns**</p>|<p align="center">**12 Rows and 36 Columns**</p>|
| :-: | :-: | :-: |
| |<img src="datamatrixrows22columns22ecc200.png">|<img src="datamatrixrows12columns36ecc200.png">|
  
<!--{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 4;
//set ECC type to Ecc200
gen.Parameters.Barcode.DataMatrix.DataMatrixEcc = DataMatrixEccType.Ecc200;
//set rows 22 columns 22
gen.Parameters.Barcode.DataMatrix.DataMatrixVersion = DataMatrixVersion.ECC200_22x22;
gen.Save($"{path}DatamatrixRows22Columns22Ecc200.png", BarCodeImageFormat.Png);
//set rows 12 columns 36
gen.Parameters.Barcode.DataMatrix.DataMatrixVersion = DataMatrixVersion.ECC200_12x36;
gen.Save($"{path}DatamatrixRows12Columns36Ecc200.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->

## **Working with Macro Characters**
***Aspose.BarCode for Android via Java*** supports the use of macro characters in *Data Matrix* barcodes. The *Data Matrix* standard allows encoding industry-specific headers and trailers in a single character. This feature leads to the reduction of the number of symbols for data encoding owing to the use of dedicated structured formats. Macro characters can be useful to implement particular industrial needs. It is necessary to put a macro character in the first digit position.

<!--The following code sample shows how to manage macro characters in *Data Matrix* barcodes.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "ASPOSE");
gen.Parameters.Barcode.XDimension.Pixels = 4;
//set macro character to 05
gen.Parameters.Barcode.DataMatrix.MacroCharacters = MacroCharacter.Macro05;
gen.Save($"{path}DatamatrixMacro.png", BarCodeImageFormat.Png);

//attempt to recognize it
BarCodeReader read = new BarCodeReader(gen.GenerateBarCodeImage(), DecodeType.DataMatrix);
foreach (BarCodeResult result in read.ReadBarCodes())
    Console.WriteLine("DatamatrixMacro:" + result.CodeText);
{{< /highlight >}}-->
  
<p align="center"><img src="datamatrixmacro.png"></p> 
  
## **Aspect Ratio Settings**
*Aspect Ratio* is one of the most important parameters defined as the ratio between barcode height and width. ***Aspose.BarCode for Android via Java*** provides the *setAspectRatio* method of class [*DataMatrixParameters*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/DataMatrixParameters) that allows managing barcode proportions based on the X and Y coordinates. *Aspect Ratio* is determined as a relative coefficient to *XDimension*. Usually, it is recommended to set the value of *Aspect Ratio* equal to 1.
  
|Aspect Ratio|Is Set to 1|Is Set to 0.5|
| :-: | :-: | :-: |
| |<img src="datamatrixaspectratio1.png">|<img src="datamatrixaspectratio0.5.png">|
  
<!--{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 4;
//set aspect ratio 1
gen.Parameters.Barcode.DataMatrix.AspectRatio = 1;
gen.Save($"{path}DatamatrixAspectRatio1.png", BarCodeImageFormat.Png);
//set aspect ratio 0.5
gen.Parameters.Barcode.DataMatrix.AspectRatio = 0.5f;
gen.Save($"{path}DatamatrixAspectRatio0.5.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->