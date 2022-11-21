---
title: Generate QR Code and Micro QR Code
type: docs
description: "Use Aspose.BarCode for Node.js via Java to generate QR Codes"
weight: 40
url: /nodejsjava/generate-qr-code/
---
{{% alert color="primary" %}}[Generate QR Code Online](https://products.aspose.app/barcode/generate/qr): You can test the quality of ***Aspose.BarCode*** generation for QR Codes and get results.{{% /alert %}}

## **Overview**
*QR Code* corresponds to a group of 2D square types that benefits from high data density and allows encoding streams of bytes and textual data composed of using Unicode symbols. ***Aspose.BarCode for Node.js via Java*** supports Extended Channel Interpretation (ECI) to encode Unicode data and provides various encoding modes; UTF8 is one of the most widely used encoding mode.  
  
Reserving the minimum possible amount of data for error correction, the *QR Code* standard can be used to encode at most 7,089 numerical digits or 4,296 alphanumeric characters or 2,953 bytes. The other standard, *Micro QR Code*, allows encoding up to 35 numerical digits or 21 alphanumeric characters or 15 bytes. *Micro QR Code* serves to create considerably small *QR Code* images. However, it does not enable Extended Channel Interpretation (ECI) and does not allow encoding Unicode characters. In particular, *Micro Qr Code* barcodes corresponding to the *M1* version can encode at most five numerical digits; the *M2* version allows encoding up to ten numericals or six alphanumeric characters. This encoding capacity is usually suitable to work with industrial markers.  

Main advantages of the *QR Code* symbology can be outlined as follows:
- large data density
- the capability to perform scanning and reading even for severely distorted barcode images 
- the possibility of encoding streams of bytes
- high scanning and decoding speed 
- the possibility to encode Unicode characters through ECI (not supported in *Micro QR Code*)
- several error correction modes; the maximal error correction level H allows restoring up to 30% of encoded information 
  
It should be noted that considerable damages of target patterns in *QR Code* images can results in deteriorating barcode scanning and reading efficiency.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out Aspose [Technical Support](/barcode/nodejsjava/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Generation Modes**
***Aspose.BarCode for Node.js via Java*** allows generating *QR Code* or *Micro QR Code* images corresponding to different versions. This can done through two methods of class [*QrParameters*](), i.e. *setQrEncodeType* using values from the [*QREncodeType*]() enum and *setQrVersion* with values from the [*QRVersion*]() enum. By default, the *AUTO* setting is enabled.  
  
The first way to set the required version of *QR Code* or *Micro QR Code* is to use the *setQrVersion* method. If data inputted for encoding does not occupy the entire capacity of the target version, padding characters are used to fill the leftover space. If barcode information exceeds the available capacity, barcode images cannot be generated, and the corresponding exception is thrown.  
  
The second way to determine the desired *QR Code* generation mode is applicable when [*QRVersion*]() remains set to *AUTO*. In this case, the *setQrEncodeType* method can be used to select the barcode type according to the input data size. The [*QREncodeType*]() enum can take the following values:

- *AUTO*: firstly, the library aims to identify the most appropriate *Micro QR Code* version from M1 to M4. If no suitable version is found, the library iterates over supported *QR Code* versions from *Version 01* to *Version 40*. If the data to be encoded does not fit to the data capacity of *Version 40*, an exception is thrown.
- *FORSE_QR*: the most appropriate *QR Code* version is automatically selected among options from *Version 01* to *Version 40*.
- *FORSE_MICRO_QR*: the library aims at selecting the most applicable *Micro QR Code* version from M1 to M4. If the input data exceeds the data capacity of the M4 verion, an exception is thrown. 
  
### **Automatic Version Setting**
The following sample barcodes images are given to explain how to create different types of *QR Code* using varios automatic version setting modes.
  
|Generation Mode|*AUTO*|*FORSE_QR*|*FORSE_MICRO_QR*|
| :-: | :-: | :-: | :-: |
| |<img src="qrencodetypeauto.png">|<img src="qrencodetypeforceqr.png">|<img src="qrencodetypeforcemicroqr.png">|
  
 
### **Manual Version Selection**
It is possible to manually select the desired *QR Code* version for barcode generation. In this case, it is required to call the *setQRVersion* method of class [*QrParameters*]() passing a value from the [*QRVersion*]() enum, i.e. from *VERSION_01* to *VERSION_40* for *QR Code* or from *VERSION_M1* to *VERSION_M4* for *Micro QR Code*. The following barcode images are intended to explain how to create *QR Code* barcodes using manual settings to define the requested version.
  
|Version|QR Code VERSION_05|Micro QR VERSION_M4|
| :-: | :-: | :-: |
| |<img src="qrversion05.png">|<img src="qrversionm4.png">|
  
## **Encoding Modes**
***Aspose.BarCode for Node.js via Java*** enables the variety of widely used data encoding specifications, including Unicode. Developers can select the desired encoding mode through the *setQrEncodeMode* method of class [*QrParameters*]() passing a value from the [*QrEncodeMode*]() enum that includes the following options:
-	*AUTO*: information inputted through the *setCodeText* method gets encoded using the value set through the *setCodeTextEncoding* method (UTF8 is applied by default).
-	*BYTES*: is intended to encode byte streams and allows encoding digits from 0 to 255. In cases when a byte stream includes digits larger than 255, the library applies the *UTF16LE*. 
-	*UTF_8_BOM* and *UTF_16_BEBOM*: allow encoding barcode data in UTF8 and UTF16BE encodings. The first character is encoded as a byte order mark (BOM) character to denote the enabled encoding. However, the *ECI_ENCODING* mode is recommended for use because it is more suitable to set the encodings suitable for the *QR Code* standard.  
-	*ECI_ENCODING*: applies encodings from the list defined in the [*ECIEncodings*]() class.
-	*EXTENDED_CODETEXT*: in addition to main information, barcode data must include special control words that are required to establish improved controls over the data encoding process; in this mode, textual parts with various encodings can be stored in one *QR Code* barcode.
  
### ***AUTO* Mode**
To encode input data when the *AUTO* encoding mode is enabled, the library applies the encoding defined through the *setCodeTextEncoding* method. If the required encoding is not specified explicitly, UTF8 is applied. 
  
<p align="center"><img src="qrencodemodeauto.png"></p>

### ***BYTES* Mode**
When the *BYTES* encoding mode is used, input information presented in a form of a plain byte stream is trasnformed to an array of symbols and then to a string. Digits from 0 to 255 can be encoded. If a byte stream contains digits larger than 255, this symbol gets encoded as two bytes in the UTF16LE encoding (the lower byte is put first). 
  
<p align="center"><img src="qrencodemodebytes.png"></p>
  
### ***UTF_8_BOM* and *UTF_16_BEBOM* Modes**
The library provides two special encoding modes called *UTF_8_BOM* and *UTF_16_BEBOM* that serve to encode information according to *UTF8* and *UTF16BE* specifications. A byte order mark (BOM) symbol is added as the first digit. 
<!--The following code sample shows how to enable with the *UTF_16_BEBOM* encoding mode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Aspose常に先を行く");
gen.Parameters.Barcode.XDimension.Pixels = 4;
Console.OutputEncoding = Encoding.Unicode;
//set the encode mode to UTF16BE with BOM
gen.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.Utf16BEBOM;
gen.Save($"{path}QrEncodeModeUtfBOM.png", BarCodeImageFormat.Png);
//attempt to read the barcode
BarCodeReader read = new BarCodeReader(gen.GenerateBarCodeImage(), DecodeType.QR);
read.BarcodeSettings.DetectEncoding = true;
foreach (BarCodeResult result in read.ReadBarCodes())
    Console.WriteLine("QrEncodeModeUtfBOM:" + result.CodeText);
{{< /highlight >}}-->
  
<p align="center"><img src="qrencodemodeutfbom.png"></p>
  
### ***ECI_ENCODING* Mode**

The *ECI_ENCODING* encoding mode suggests applying one of the encodings listed in the [*ECIEncodings*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/ECIEncodings) class. ***Aspose.BarCode for Android via Java*** supports the variety of widely used encodings. In this mode, the extended channel interpretation (ECI) identifier is added to denote the enabled encoding to transfer the information about it to decoders. It is recommended to use the UTF8 value. 
<!--The following code snippet explains how to use the *ECI_ENCODING* mode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Aspose常に先を行く");
gen.Parameters.Barcode.XDimension.Pixels = 4;
Console.OutputEncoding = Encoding.Unicode;
//set the encoding mode to ECI_Encoding and ECI to UTF8
gen.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.ECIEncoding;
gen.Parameters.Barcode.QR.QrECIEncoding = ECIEncodings.UTF8;
gen.Save($"{path}QrEncodeModeECIEncoding.png", BarCodeImageFormat.Png);
//attempt to read the barcode
BarCodeReader read = new BarCodeReader(gen.GenerateBarCodeImage(), DecodeType.QR);
foreach (BarCodeResult result in read.ReadBarCodes())
    Console.WriteLine("QrEncodeModeECIEncoding:" + result.CodeText);
{{< /highlight >}}-->
  
<p align="center"><img src="qrencodemodeeciencoding.png"></p>
  
### ***EXTENDED_CODETEXT* Mode**
***Aspose.BarCode for Android via Java*** supports the *EXTENDED_CODETEXT* mode that allows customizing settings for the *QR Code* generation process manually. This mode enables activating the multi-ECI mode and adding FNC characters (special symbols to differentiate between fields in variable-length identifiers) to work with extended textual information. The library provides a special class called [*QrExtCodetextBuilder*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/QrExtCodetextBuilder) that facilitate using with this encoding mode. When the multi-ECI mode is enabled, barcode information gets processed for all predefined encodings automatically. In all other cases, the encoding defined through the *setCodeTextEncoding* method is applied.    

<!--The following code sample shows how to enable the multi-encoding ECI regime when the *EXTENDED_CODETEXT* mode is enabled. 
  
{{< highlight csharp>}}
//create the extended barcode text
QrExtCodetextBuilder lTextBuilder = new QrExtCodetextBuilder();
lTextBuilder.AddECICodetext(ECIEncodings.Win1251, "Aspose");
lTextBuilder.AddECICodetext(ECIEncodings.UTF8, "常に先");
lTextBuilder.AddECICodetext(ECIEncodings.UTF16BE, "を行く");
lTextBuilder.AddPlainCodetext(@"!!!");
//generate a QR Code
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, lTextBuilder.GetExtendedCodetext());
gen.Parameters.Barcode.XDimension.Pixels = 4;
Console.OutputEncoding = Encoding.Unicode;
//set the encoding mode to EXTENDED_CODETEXT
gen.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.ExtendedCodetext;
gen.Parameters.Barcode.CodeTextParameters.TwoDDisplayText = "ExtendedCodetext mode";
gen.Save($"{path}QrEncodeModeExtendedCodetext.png", BarCodeImageFormat.Png);
//attempt to read the barcode
BarCodeReader read = new BarCodeReader(gen.GenerateBarCodeImage(), DecodeType.QR);
foreach (BarCodeResult result in read.ReadBarCodes())
    Console.WriteLine("QrEncodeModeExtendedCodetext:" + result.CodeText);
{{< /highlight >}}-->
  
<p align="center"><img src="qrencodemodeextendedcodetext.png"></p>
  
## **Error Correction Level**
The *QR Code* group of barcode standards provides four types of Reed-Solomon error correction (EC). The error correction mechanism prescribes storing redundant data to facilitate automatic error detectiion and correctiion in the case of barcode image distortions or damages. Basically, to recover 1% of corrupted data, 2% redundancy is required.  
  
Following error correction levels are supported for *QR Code* symbologies.
  
|Error Correction Level|Data Recovery Capacity|
| :-: | :-: |
|Level L| 7% |
|Level M| 15% |
|Level Q| 25% |
|Level H| 30% |
  
For all *QR Code* subtypes with the exception of *Micro QR*, developers can use any error correction level. For *Micro QR*, different subtypes are compatible with specific EC levels only, i.e. *M1* enables EC level L; *M2* - levels L and M; *M3* and *M4* - levels L, M, and Q. 
  
|Error Correction Level|Level L|Level M|Level Q|Level H|
| :-: | :-: | :-: | :-: | :-: |
| |<img src="qrerrorlevell.png">|<img src="qrerrorlevelm.png">|<img src="qrerrorlevelq.png">|<img src="qrerrorlevelh.png">|
  
<!--The following code snippet demonstrates how to enable various error correction levels for *QR Code* barcodes.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "A QR code is a type of matrix barcode invented in 1994");
gen.Parameters.Barcode.XDimension.Pixels = 4;
//set error correction level to L
gen.Parameters.Barcode.QR.QrErrorLevel = QRErrorLevel.LevelL;
gen.Save($"{path}QrErrorLevelL.png", BarCodeImageFormat.Png);
//set error correction level to M
gen.Parameters.Barcode.QR.QrErrorLevel = QRErrorLevel.LevelM;
gen.Save($"{path}QrErrorLevelM.png", BarCodeImageFormat.Png);
//set error correction level to Q
gen.Parameters.Barcode.QR.QrErrorLevel = QRErrorLevel.LevelQ;
gen.Save($"{path}QrErrorLevelQ.png", BarCodeImageFormat.Png);
//set error correction level to H
gen.Parameters.Barcode.QR.QrErrorLevel = QRErrorLevel.LevelH;
gen.Save($"{path}QrErrorLevelH.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->

## **Structured Append Mechanism**
*QR Code* types (except *Micro QR*) support the possibility to generate composite barcodes using the structured append mechanism. In this mode, the input data can be divided among different *QR Code* barcodes and then composed into a single image. ***Aspose.BarCode for Android via Java*** does not enable distributing input barcode data across several *QR Code* barcodes; however, it allows creating a composite *QR Code* label manually. This can be done through the *setStructuredAppend* method passing an object of lass [*QrStructuredAppendParameters*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/QrStructuredAppendParameters) class. This class provides the following methods: 
- *setTotalCount* - the number of barcodes in a composite *QR Code* image (can take values from 2 to 16)
- *setSequenceIndicator* - the sequence number of the current barcode (starting from 0)
- *setParityByte* - a byte that serves as a checksum identifier. In the general case, it is calculated as *XOR* of all bytes in which UTF16BE symbols are encoded using two bytes   
  
Sample barcode images provided below have been created using the structured append mechanism.
  
|Structured Append Type|First Type|Second Type|
| :-: | :-: | :-: |
| |<img src="qrstructuredappendfirst.png">|<img src="qrstructuredappendsecond.png">|
  

## **Aspect Ratio Settings**
*Aspect Ratio* is the ratio between the height and the width of a barcode. To adjust barcode proportions using the X and Y coordinates, it is required to use the *setAspectRatio* method of class [*QrParameters*](). This property is defined as a relative coefficient to the value of *XDimension* parameter. Generally, the value of *AspectRatio* should be set to 1. When it is necessary to adjust the proportions of generated *QR Code* barcodes, the *setAspectRatio* method can be used. Sample barcode labels shown below have been generated using different aspect ratio settings.  
  
|Aspect Ratio|Is Set to 1|Is Set to 2|
| :-: | :-: | :-: |
| |<img src="qraspectratio1.png">|<img src="qraspectratio2.png">|
  
