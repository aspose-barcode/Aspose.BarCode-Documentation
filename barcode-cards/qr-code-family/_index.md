---
title: QR Code Family
description: ""
key words: ""
type: docs
weight: 10
url: /barcode/qr-code-cards/
---

{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/qr) and [Generate](https://products.aspose.app/barcode/generate/qr) QR Codes online. You can test the quality of ***Aspose.BarCode*** functionality and view the results.{{% /alert %}}

## **Overview**
QR (Quick Response) Codes are machine-readable labels with patterns composed of black and white squares that can be easily read by smartphones and other devices equipped with common digital image sensors. The idea of a QR Code has been proposed as an advance of conventional linear barcodes and can contain much more information. They are capable of encoding large portions of data and provide very high recognition speed. Conceptually, a QR code can be considered as a means to store information digitally, like flash drives that keep digital data physically. At present, QR Codes have multiple applications in various spheres, including E-Commerce, marketing, documentation management, item tracking, digital payments, and many others. The operations of scanning, reading, and decoding QR Codes can be executed using cameras and special QR code scanner applications on mobile phones (mobile tagging). QR Code scanners are generally embedded into various mobile devices, and third-party scanner applications can download for any smartphone. After capturing a QR code image, a special application converts it into readable text or more often, into an URL link. 

Apart from 40 basic variants, the QR Code standard supports a special option called Micro QR Code. Such barcodes can be used to save space for applications in which the data capacity of 35 characters or less is sufficient. See more information in the article about [Micro QR Codes](/barcode/net/micro-qr-card/).  

<p align="center"><img src="qrcodesample.png"></p>
  
The specification for this barcode type has been published in the [ISO/IEC 18004:2015](https://www.iso.org/standard/62021.html) standard.

{{% alert color="primary" %}}You can find the detailed description of classes and properties that are used in ***Aspose.BarCode for .NET*** for QR Code generation and recognition:
- [**QR Code in Aspose.BarCode for .NET**](/barcode/net/qr-and-micro-qr-barcode/)

{{% /alert %}} 

## **Features**
  
### **Encoding Character Set**
QR Codes can be used to encode various data types, including numeric and alphabetic characters, Unicode symbols, Kanji, and special characters.  
  
The QR Code standard allows encoding the following characters in four standard encoding modes:
- Numerical: all numerical digits (0-9)
- Alphanumeric: all numeric digits (0-9), uppercase English letters (A-Z), and special characters
- 8-bit byte/binary: data is encoded at 8 bits per character
- Kanji: Kanji characters are encoded as specified in the Japanese Industrial Standard (JIS), in accordance with the Shift JIS system 

<details>  
<summary>Read more</summary>
  
As an optional encoding feature, the QR Code standard supports the Extended Channel Interpretation (ECI) protocol that allows interpreting output data streams using character sets different from the default one. It also enables using alternative modes of data interpretation or supporting industry-specific encoding requirements. The ECI mode supports nearly 30 different encodings, including both standard and extended Unicode sets.

</details>

### **Structure**
Each QR Code label contains the following elements: square modules, finder patterns, timing patterns, alignment pattern, input data modules, error correction data modules, and quiet zone areas. QR Codes encode information as binary data in so-called modules (square dots). Black and while modules correspond to binaries 1 and 0, respectively.  

<details>
<summary>Read more</summary>

The key elements of QR Codes include the following:   
- Finder (position detection) patterns - square bull's eye signs in three corners of a QR Code label. These patterns facilitate accurate and fast scanning at any orientation
- Alignment pattern - added in QR versions only starting from Version 2 and higher and is intended to improve scanning in case of minor distortions of a QR Code label. It is a small square bull's eye sign placed among the input data modules
- Timing patterns - one row and one column of black and white modules that encode the symbol version and density
- Quiet zone space - an empty area around four QR Code label sides that is essential for scanning and facilitates symbol detection. Four or more empty cells are required to constitute the quiet zone
  
</details>

### **Size Dimentions**
The basic QR Code standard support QR Code versions that range from Version 1 to Version 40. The minimal size of a QR code is 21 x 21 modules (Version 1) or 5.25 mm x 5.25 mm excluding margins. The maximal size (Version 40) is 177 x 177 modules. Each higher version contains four additional modules per side and has its own module configuration (the number of modules). To ensure successful scanning by most smartphones, QR Code labels should have a size of at least 2 cm x 2 cm (0.8 x 0.8 inches).  
  
|<p align="center">**QR Code Version 5**</p>|
| :-: |
|<img src="qrcodeversion05.png">|
  
<details>  
<summary>Read more</summary>
  
Modules are black and white dots that constitute QR Code labels. Module configuration is determined by the number of modules presented in a QR Code label. The size of one module is 0.25 mm x 0.25 mm. Accordingly, the size of a QR Code image depends on the number of modules and the amount of information to be encoded. The greater is the portion of data to be stored, the larger is the size of a QR Code label.  

The actual minimal size of a QR Code image is 10 mm or 0.4 inches (as per the scanning standard compliant to ISO 18004). Generally, the size of QR Code labels is determined based on the intended scanning distance (the distance-to-size ratio of 10:1 is usually recommended), the resolution of a printer, scanning equipment (smartphones or industrial scanners), and the error correction level. 
   
</details>

### **Encoding Capacity and Data Density**
QR Code provides very high data density. Each QR Code version has its own maximum data capacity. The actual data capacity may vary according to the amount of information to be encoded, encoding type, and the error correction level. QR Codes can store up to 3 KB of data, namely, 2,953 bytes, 7,089 numerical digits, 4,296 letters, or 1,817 Japanese Kanji symbols. 

<details>  
<summary>Read more</summary>
  
For example, a 101 x 101 QR Code label with the high-level error correction can encode up to 406 bytes, while a QR Code with the 177 x 177 grid can store from 1,273 to 2,953 bytes depending on the selected error correction level.
</details>

### **Error Correction**
QR Code supports Reed-Solomon error correction capability to recover input information if an image is distorted, dirty, or damaged. The QR Code standard provides four error correction levels (L, M, Q, and H) that should be selected depending on the operating environment. These four error correction levels allow achieving the recovery capacity from 7% to 30% at most.

<details>  
<summary>Read more</summary>

The *QR Code* standard supports four error correction levels, as specified below.
  
|<p align="center">**Error Correction**</p>|<p align="center">**Recovery Capacity**</p>|
| :-: | :-: |
|Level L| 7% |
|Level M| 15% |
|Level Q| 25% |
|Level H| 30% |
    
Increasing the error correction level allows improving data recovery capability but also enlarges the size of the resulting QR Code image as more additional error correction data needs to be encoded together with input information. To select an error correction level, it is necessary to consider various factors, such as the operating environment and the desired QR Code label size.  
    
Levels Q or H may be selected in industrial environments where the probabilty of QR Code images getting distorted or dirty is high, while Level L may be suitable in cases when the large amount of data in rather safe environments. Typically, Level M (15%) is most frequently selected.  
  
</details>
  
## **Advantages and Weaknesses**
 
The key advantages of QR codes are summarized below:

- very high reading speed owing to geometrical specifics
- scanning capability through common mobile devices
- simple creation procedure
- readability from any angle
- reading capability under severe 3D distortions 
- encoding byte streams of data
- encoding Unicode symbols through ECI
- high data encoding density
- customizable error correction mechanism that allows recovering up to 30% of encoded information at the maximal level H 
  
However, QR Codes are sensitive to substantial damages of the target pattern as it can prevent from correct scanning and recognition.

## **Aspose Samples for QR Code Generation and Recognition**

### **QR Code Generation Sample**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//generate QR Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Aspose常に先を行く"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    //encode data as QR
    gen.Parameters.Barcode.QR.QrEncodeType = QREncodeType.ForceQR;
    //set error correction level 7%
    gen.Parameters.Barcode.QR.QrErrorLevel = QRErrorLevel.LevelL;
    //set ECI encoding UTF8
    gen.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.ECIEncoding;
    gen.Parameters.Barcode.QR.QrECIEncoding = ECIEncodings.UTF8;
    //set version 5 can be Auto
    gen.Parameters.Barcode.QR.QrVersion = QRVersion.Version05;
    gen.Save($"{path}QR.png", BarCodeImageFormat.Png);
}
{{< /highlight >}}


{{< /tab >}}

{{< tab tabNum="2" >}}

<!-->Insert Code<-->

{{< /tab >}}

{{< tab tabNum="3" >}}

<!-->Insert Code<-->

{{< /tab >}}

{{< /tabs >}}

### **QR Code Recognition Sample**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//Read QR Code
using (BarCodeReader read = new BarCodeReader($"{path}QR.png", DecodeType.QR))
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
{{< /highlight >}}


{{< /tab >}}

{{< tab tabNum="2" >}}

<!-->Insert Code<-->

{{< /tab >}}

{{< tab tabNum="3" >}}

<!-->Insert Code<-->

{{< /tab >}}

{{< /tabs >}}
