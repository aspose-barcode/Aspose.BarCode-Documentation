---
title: Generate QR Code, Micro QR Code and Rectangular Micro QR Code in JavaScript
linktitle: QR, Micro QR and rMQR
type: docs
weight: 10
feedback: BARCODECOM
url: /javascript-cpp/qr-micro-qr-and-rmqr/
---
{{% alert color="primary" %}}[Generate QR Code Online](https://products.aspose.app/barcode/generate/qr): You can test the quality of ***Aspose.BarCode*** generation for QR Codes and get the results online.{{% /alert %}}

## **Overview**
The *QR Code* family corresponds to 2D matrix barcodes of square or rectangular shapes. *QR Code* and *Micro QR* Code barcodes require placement on a surface with a square space, while the *Rectangular Micro QR Code (rMQR)* barcode requires placement on a surface with a rectangular space. This group of symbologies has a high data density and allows for the encoding of both byte streams of data and arbitrary information represented as a set of Unicode symbols. In ***Aspose.BarCode for JavaScript via C++***, the data encoding in Unicode is performed using Extended Channel Interpretation (ECI) and supports various encoding modes, among which UTF8 is the most common.

At the minimal error correction level, the *QR Code* symbology can encode up to 7,089 numerical characters (or 4,296 alphanumeric characters) or 2,953 bytes. The *QR Code* standard supports all *QR Code* family features, including Extended Channel Interpretation (ECI), Structured Append Mode, and etc.

The *Micro QR Code* standard allows encoding at most 35 numerical (21 alphanumeric) or 15 bytes. *Micro QR Code* is used to generate barcodes of reasonably small size; at the same time, to enable such a possibility, it does not support Extended Channel Interpretation (ECI), does not support encoding Unicode symbols and does not support Structured Append Mode. Specifically, the M1 version allows encoding only 5 numerical digits, while M2 can encode 10 numerical or 6 alphanumeric symbols. This capacity may be sufficient to encode particular industrial markers.

The *Rectangular Micro QR Code (rMQR)* standard allows for the encoding of a maximum of 361 numerical characters (or 219 alphanumeric characters) or 150 bytes. The *rMQR Code* specifically designed for generating rectangular barcodes that can be applied to surfaces with limited height, such as test tubes. The *rMQR Code* standard does not support Structured Append Mode.

The key features of QR codes are summarized below:
- very high barcode recognition speed owing to geometrical specifics 
- barcode reading capability under severe 3D distortions 
- encoding byte streams of data
- encoding Unicode symbols using ECI (is not valid for *Micro QR Code*)
- high data encoding density
- customizable error correction that allows recovering up to 30% of the barcode data at the maximal level H 
  
However, *QR Code* barcodes are sensitive to substantial damages of a target pattern as they can hinder barcode detection in the scanned image.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out Aspose [Technical Support](/barcode/javascript-cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Layout Settings**

To define the size of the barcode, it is necessary to initialize the properties [*QrVersion*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/qrversion/), [*MicroQrVersion*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/microqrversion/), or [*RectMicroQrVersion*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/rectmicroqrversion/) of the [*QrParameters*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters) class for *QR Code*, *Micro QR Code*, and *Rectangular Micro QR Code* barcodes, respectively. The [*QrVersion*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/qrversion/) property can have values of *Auto* or from *Version01* to *Version40*, the [*MicroQrVersion*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/microqrversion/) property can have values of *Auto* or from *M1* to *M4*, and the [*RectMicroQrVersion*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/rectmicroqrversion/) property can have values of *Auto* or from *R7x43* to *R17x139*. When using the *Auto* option, the size of the barcode will be automatically selected based on the data size.

The code sample and barcode images below are provided to illustrate how to generate *QR Code* barcodes of various sizes.
  
|<p align="center">**Size Setting Mode**</p>|<p align="center">***Auto***</p>|<p align="center">***Version05***</p>|
| :-: | :-: | :-: |
| |<img src="qrversionauto.png">|<img src="qrversion05.png">|
  
{{< highlight csharp>}}
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "ASPOSE"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    
    //auto (by default)
    gen.Save($"{path}QRVersionAuto.png", BarCodeImageFormat.Png);

    //set QR version 05
    gen.Parameters.Barcode.QR.QrVersion = QRVersion.Version05;
    gen.Save($"{path}QRVersion05.png", BarCodeImageFormat.Png);
}
{{< /highlight >}}
   
The code sample and barcode images below are provided to illustrate how to generate *Micro QR Code* barcodes of various sizes.
  
|<p align="center">**Size Setting Mode**</p>|<p align="center">***Auto***</p>|<p align="center">***Version M4***</p>|
| :-: | :-: | :-: |
| |<img src="microqrversionauto.png">|<img src="microqrversionm4.png">|
  
{{< highlight csharp>}}
 using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MicroQR, "ASPOSE"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;

    //auto (by default)
    gen.Save($"{path}MicroQRVersionAuto.png", BarCodeImageFormat.Png);

    //set MicroQR M4 version
    gen.Parameters.Barcode.QR.MicroQRVersion = Generation.MicroQRVersion.M4;
    gen.Save($"{path}MicroQRVersionM4.png", BarCodeImageFormat.Png);
}
{{< /highlight >}}
   
The code sample and barcode images below are provided to illustrate how to generate *Rectangular Micro QR Code* barcodes of various sizes.
  
|<p align="center">**Size Setting Mode**</p>|<p align="center">***Auto***</p>|<p align="center">***Version R11x77***</p>|
| :-: | :-: | :-: |
| |<img src="rectmicroqrversionauto.png">|<img src="rectmicroqrversionr11x77.png">|
  
{{< highlight csharp>}}
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.RectMicroQR, "ASPOSE"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;

    //auto (by default)
    gen.Save($"{path}RectMicroQRVersionAuto.png", BarCodeImageFormat.Png);

    //set RectMicroQR R11x77 version
    gen.Parameters.Barcode.QR.RectMicroQrVersion = Generation.RectMicroQRVersion.R11x77;
    gen.Save($"{path}RectMicroQRVersionR11x77.png", BarCodeImageFormat.Png);
}
{{< /highlight >}}
   
## **Data Encoding Modes**
***Aspose.BarCode for JavaScript via C++*** supports several most widespread data encoding modes, including the Unicode standard. To set the required encoding mode, it is necessary to initialize the [*QrEncodeMode*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/properties/qrencodemode) property of class [*QrParameters*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters). This property can take the following values:
-	*Auto*. In Auto mode, the CodeText is encoded with maximum data compactness. This is the default value. 
-   *Binary*. The *Binary* mode is used to encode binary data with maximum data compactness. 
-   *ECI*. The Extended Channel Interpretation (ECI) mode indicates the encoded data is interpreted according to the ECI protocol defined by the AIM ECI Specifications.
-   *Extended*. The *Extended* mode provides flexible encoding controls and allows for manually specifying the required encoding for a part of Codetext.
  
### ***Auto* Mode**
In Auto mode, the CodeText is encoded with maximum data compactness. Unicode characters are encoded in kanji mode if possible, or they are re-encoded using the encoding specified in the [*QrECIEncoding*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/qreciencoding/) parameter, with an ECI identifier inserted. If a character is found that is not supported by the selected ECI encoding, an exception is thrown. By default, the [*QrECIEncoding*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/qreciencoding/) property is set to [*ECIEncodings*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/eciencodings/).UTF8 (ECI ID:"\000026"). The following code sample shows how to generate QR Code barcode in the *Auto* mode.    

{{< highlight csharp>}}
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Aspose常に先を行く"))
{
    gen.Save($"{path}QrEncodeModeAuto.png", BarCodeImageFormat.Png);

    //attempt to recognize it
    using (BarCodeReader read = new BarCodeReader(gen.GenerateBarCodeImage(), DecodeType.QR)){
        foreach (BarCodeResult result in read.ReadBarCodes())
            Console.WriteLine("QrEncodeModeAuto:" + result.CodeText);
    }
}
{{< /highlight >}}
  
<p align="center"><img src="qrencodemodeauto.png" width="10%"></p>

### ***Binary* Mode**
The *Binary* mode serves to encode byte streams. If a Unicode character is encountered, an exception is thrown. The code sample below explains how to work with this encoding mode.

{{< highlight csharp>}}
byte[] encodedArr = { 0xFF, 0xFE, 0xFD, 0xFC, 0xFB, 0xFA, 0xF9 };
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR))
{
    gen.SetCodeText(encodedArr);
    //set QR Code encode mode to Binary
    gen.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.Binary;
    gen.Save($"{path}QrEncodeModeBinary.png", BarCodeImageFormat.Png);
}
{{< /highlight >}}
  
<p align="center"><img src="qrencodemodebinary.png" width="10%"></p>


### ***ECI* Mode**
The Extended Channel Interpretation (ECI) mode indicates that the encoded data is interpreted according to the ECI protocol defined by the AIM ECI Specifications. When the ECI mode is selected, the entire CodeText is re-encoded using the encoding specified in the [*QrECIEncoding*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/qreciencoding/) parameter, with an ECI identifier inserted. If a character is found that is not supported by the selected ECI encoding, an exception is thrown. By default, the [*QrECIEncoding*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/qreciencoding/) property is set to [*ECIEncodings*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/eciencodings/).UTF8 (ECI ID:"\000026").

The following code sample demonstrates how to use the *ECI* mode.

{{< highlight csharp>}}
// ECI mode, Latin/Greek alphabet encoding. ECI ID:"\000009"
var str = "ΑΒΓΔΕ";

using (var gen = new BarcodeGenerator(EncodeTypes.QR, str))
{
    gen.Parameters.Barcode.QR.QrEncodeMode = QrEncodeMode.ECI;
    gen.Parameters.Barcode.QR.ECIEncoding = ECIEncodings.ISO_8859_7;
    var img = gen.GenerateBarCodeImage();
}
{{< /highlight >}}
  
<p align="center"><img src="qrencodemodeeci.png" width="10%"></p>
  
### ***Extended* Mode**
***Aspose.BarCode for JavaScript via C++*** provides an advanced data encoding mode called *Extended* that enables flexible manual settings for *QR Code* barcode generation. Particularly, this mode includes specific encoding capabilities, such as using the multi-ECI mode and setting FNC symbols (characters used to detect and distinguish fields in variable-length application identifiers). Developers can facilitate the generation of barcodes with extended barcode text using class [*QrExtCodetextBuilder*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrextcodetextbuilder). To replace the text displayed under the generated barcode, it is necessary to initialize the [*TwoDDisplayText*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/codetextparameters/properties/twoddisplaytext) property.
The following code snippet illustrates how to use the multi-encoding ECI regime when the *Extended* mode is applied. 
  
{{< highlight csharp>}}
//generate extended codetext
QrExtCodetextBuilder textBuilder = new QrExtCodetextBuilder();
textBuilder.AddECICodetext(ECIEncodings.Win1251, "Aspose");
textBuilder.AddECICodetext(ECIEncodings.UTF8, "常に先");
textBuilder.AddECICodetext(ECIEncodings.UTF16BE, "を行く");
textBuilder.AddPlainCodetext(@"!!!");

//generate barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, textBuilder.GetExtendedCodetext())){
    //set the encoding mode to Extended
    gen.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.Extended;
    gen.Parameters.Barcode.CodeTextParameters.TwoDDisplayText = "Extended mode";
    gen.Save($"{path}QrEncodeModeExtended.png", BarCodeImageFormat.Png);
    //attempt to recognize it
    using (BarCodeReader read = new BarCodeReader(gen.GenerateBarCodeImage(), DecodeType.QR)){
        foreach (BarCodeResult result in read.ReadBarCodes())
            Console.WriteLine("QrEncodeModeExtended:" + result.CodeText);
    }
}
{{< /highlight >}}
  
<p align="center"><img src="qrencodemodeextended.png" width="10%"></p>
  
## **Error Correction Level Settings**
The *QR Code* family supports four levels of Reed-Solomon error correction. This mechanism requires adding redundant information to a barcode so as to enable detecting and correcting errors automatically in the case of barcode label damages. In general, to restore 1% of errors, 2% redundancy is needed.  
  
*QR Code* standards provide the following error correction levels.
  
|<p align="center">**Error Correction**</p>|<p align="center">**Recovery Capacity**</p>|<p align="center">**Supported barcode types**</p>|
| :-: | :-: | :-- |
|Level L| 7% |*QR*<br>*Micro QR*|
|Level M| 15% |*QR*<br>*Rectangular Micro QR*<br>*Micro QR* (for versions from *M2* to *M4*)|
|Level Q| 25% |*QR*<br>*Micro QR* (for *M4* version)|
|Level H| 30% |*QR*<br>*Rectangular Micro QR*|
  
|<p align="center">**Error Correction Level**</p>|<p align="center">**Is Set to L**</p>|<p align="center">**Is Set to M**</p>|<p align="center">**Is Set to Q**</p>|<p align="center">**Is Set to H**</p>|
| :-: | :-: | :-: | :-: | :-: |
| |<img src="qrerrorlevell.png">|<img src="qrerrorlevelm.png">|<img src="qrerrorlevelq.png">|<img src="qrerrorlevelh.png">|
  
The following code sample illustrates how to set error correction level for *QR Code* generation.
  
{{< highlight csharp>}}
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "A QR code is a type of matrix barcode invented in 1994"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    //set error level L
    gen.Parameters.Barcode.QR.QrErrorLevel = QRErrorLevel.LevelL;
    gen.Save($"{path}QrErrorLevelL.png", BarCodeImageFormat.Png);
    //set error level M
    gen.Parameters.Barcode.QR.QrErrorLevel = QRErrorLevel.LevelM;
    gen.Save($"{path}QrErrorLevelM.png", BarCodeImageFormat.Png);
    //set error level Q
    gen.Parameters.Barcode.QR.QrErrorLevel = QRErrorLevel.LevelQ;
    gen.Save($"{path}QrErrorLevelQ.png", BarCodeImageFormat.Png);
    //set error level H
    gen.Parameters.Barcode.QR.QrErrorLevel = QRErrorLevel.LevelH;
    gen.Save($"{path}QrErrorLevelH.png", BarCodeImageFormat.Png);
}
{{< /highlight >}}

## **Structured Append Mechanism**
*QR Code* symbologies (except *Micro QR* and *Rectangular Micro QR*) support the possibility to generate composite barcodes using the so-called **Structured Append** mechanism. In this mode, the input data can be divided among different *QR Code* barcodes and then composed into a single image. ***Aspose.BarCode for JavaScript via C++*** does not enable distributing information inputted into [*CodeText*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/properties/codetext) across several *QR Code* barcodes; however, it allows creating a composite *QR Code* label manually. This can be done by initializing the [*StructuredAppend*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/properties/structuredappend) property using the following fields: 
- *TotalCount* - the number of barcodes in a composite *QR Code* image (can take values from 2 to 16)
- *SequenceIndicator* - the sequence number of the current barcode (starting from 0)
- *ParityByte* - a byte that serves as a checksum identifier. In the general case, it is calculated as *XOR* of all bytes in which UTF16BE symbols are encoded using two bytes  
  
Sample barcode images provided below have been created using the structured append mechanism implemented in the following code snippet.
  
|<p align="center">**Structured Append QR Code**</p>|<p align="center">**First Type**</p>|<p align="center">**Second Type**</p>|
| :-: | :-: | :-: |
| |<img src="qrstructuredappendfirst.png">|<img src="qrstructuredappendsecond.png">|
  
{{< highlight csharp>}}
Console.OutputEncoding = Encoding.Unicode;
//messages
string firstMessage = "Aspose";
string secondMessage = "常に先を行く";
//calculate parity byte
byte parity = 0;
foreach (char val in firstMessage.ToCharArray())
    parity ^= (val <= 255) ? (byte)val : (byte)((byte)val ^ (byte)((int)val >> 8));
foreach (char val in secondMessage.ToCharArray())
    parity ^= (val <= 255) ? (byte)val : (byte)((byte)val ^ (byte)((int)val >> 8));

//generate first barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, firstMessage))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.ECIEncoding;
    gen.Parameters.Barcode.QR.QrECIEncoding = ECIEncodings.UTF8;
    gen.Parameters.Barcode.QR.StructuredAppend.ParityByte = parity;
    gen.Parameters.Barcode.QR.StructuredAppend.TotalCount = 2;
    gen.Parameters.Barcode.QR.StructuredAppend.SequenceIndicator = 0;
    gen.Save($"{path}QrStructuredAppendFirst.png", BarCodeImageFormat.Png);
    //try to recognize it
    using (BarCodeReader read = new BarCodeReader(gen.GenerateBarCodeImage(), DecodeType.QR))
    {
        foreach (BarCodeResult result in read.ReadBarCodes())
            Console.WriteLine($"QrStructuredAppend: Count:{result.Extended.QR.QRStructuredAppendModeBarCodesQuantity} " +
                $"Index: {result.Extended.QR.QRStructuredAppendModeBarCodeIndex} Parity:{result.Extended.QR.QRStructuredAppendModeParityData.ToString()} " +
                $"Codetext: {result.CodeText}");
    }
}

//generate second barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, secondMessage)) { 
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.ECIEncoding;
    gen.Parameters.Barcode.QR.QrECIEncoding = ECIEncodings.UTF8;
    gen.Parameters.Barcode.QR.StructuredAppend.ParityByte = parity;
    gen.Parameters.Barcode.QR.StructuredAppend.TotalCount = 2;
    gen.Parameters.Barcode.QR.StructuredAppend.SequenceIndicator = 1;
    gen.Save($"{path}QrStructuredAppendSecond.png", BarCodeImageFormat.Png);
    //try to recognize it
    using (BarCodeReader read = new BarCodeReader(gen.GenerateBarCodeImage(), DecodeType.QR))
    {
        foreach (BarCodeResult result in read.ReadBarCodes())
            Console.WriteLine($"QrStructuredAppend: Count:{result.Extended.QR.QRStructuredAppendModeBarCodesQuantity} " +
                $"Index: {result.Extended.QR.QRStructuredAppendModeBarCodeIndex} Parity:{result.Extended.QR.QRStructuredAppendModeParityData.ToString()} " +
                $"Codetext: {result.CodeText}");
    }
}
{{< /highlight >}}

## **Aspect Ratio Settings**
*Aspect Ratio* is the ratio between the height and the width of a barcode. To adjust barcode proportions using the X and Y coordinates in ***Aspose.BarCode for JavaScript via C++***, it is required to set the [*AspectRatio*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/properties/aspectratio) property of class [*QrParameters*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters). This property is defined as a relative coefficient to the value of the [*XDimension*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodeparameters/properties/xdimension) parameter. Generally, the value of *AspectRatio* should be set to 1. When it is necessary to adjust the proportions of generated *QR Code* barcodes, the [*AspectRatio*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/qrparameters/properties/aspectratio) property can be used. Sample barcode labels shown below have been generated using different aspect ratio settings.  
  
|<p align="center">**Aspect Ratio**</p>|<p align="center">**Is Set to 1**</p>|<p align="center">**Is Set to 2**</p>|
| :-: | :-: | :-: |
| |<img src="qraspectratio1.png">|<img src="qraspectratio2.png">|
  
The following code snippet explains how to set the required value of *AspectRatio* for *QR Code* barcodes.
  
{{< highlight csharp>}}
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "ASPOSE"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    //set Aspect Ratio to 1
    gen.Parameters.Barcode.QR.AspectRatio = 1;
    gen.Save($"{path}QrAspectRatio1.png", BarCodeImageFormat.Png);
    //set Aspect Ratio to 2
    gen.Parameters.Barcode.QR.AspectRatio = 2;
    gen.Save($"{path}QrAspectRatio2.png", BarCodeImageFormat.Png);
}
{{< /highlight >}}