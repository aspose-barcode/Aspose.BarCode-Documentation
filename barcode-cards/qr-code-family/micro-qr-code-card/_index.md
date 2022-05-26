---
title: Micro QR Code Symbology
description: 
key words:
type: docs
weight: 20
url: /micro-qr-card/
---

{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/qr) and [Generate](https://products.aspose.app/barcode/generate/qr) QR Code barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view the results online.{{% /alert %}}

## Description
Micro QR (Quick Response) code is a variant of the QR Code standard that has been introduced to save printing space by further reducing the size of a QR Code label.

<p align="center"><img src="microqrcodesample.png"></p>

## Features
  
### Encoding Character Set
Micro QR Codes allow encoding same data types as [QR Codes](/barcode/net/qr-card/): numeric and alphabetic characters, Unicode symbols, Kanji, and special characters.  
  
Hence, the Micro QR Code specification also supports encoding the following standard encoding modes:
- Numerical: all numerical digits (0-9)
- Alphanumeric: all numeric digits (0-9), uppercase English letters (A-Z), and special characters
- 8-bit byte/binary: data is encoded at 8 bits per character
- Kanji: Kanji characters according to the Japanese Industrial Standard (JIS) 
  
### Barcode Structure
A Micro QR Code barcode has the structure similar to that of basic QR Code labels; namely, it includes square modules, timing patterns, input data, error correction data, and quiet zones. However, it has only one orientation (finder) pattern and does not contain the alignment pattern to reduce the lable size so that it can be printed on minute components such as printed circuit boards. The least numbers of modules are 11 x 11. Micro QR Code barcodes encode input information as binary data in "modules" (square dots) in the same way as defined in the QR Code specification.  

<details>
<summary>Read more</summary>

The key elements of QR Codes are:   
- One finder (position detection) pattern - a square bull's eye sign in a corner of a QR Code image. It serves for accurate and fast scanning at any orientation.
- Timing patterns are composed of one row and one column of alternating black and white modules. They are used to encode symbol version and density
- A margin space essential for scanning the QR Code. This quiet zone gets it easier for symbol detection from among the image which is the record by the CCD sensor. Four or more cells are essential for the quiet area


### Size Dimentions
Micro QR Code versions range from M1 to M4 for Micro QR Code. Each version has its own module configuration or the number of modules. Micro QR codes can range from 11 x 11 modules or 2.75mm x 2.75mm excluding margins to 17 x 17 modules.
<details>  
<summary>Read more</summary>
  
|<p align="center">**Micro QR Code Version M1**</p>|<p align="center">**Micro QR Code Version M4**</p>|
| :-: | :-: |
|<img src="qrcodeversionm1.png">|<img src="qrcodeversionm4.png">|
  
</details>

### Encoding Capacity and Data Density
A Micro QR code can encode up to 35 numerical digits (21 alpabetical symbols) or 15 bytes. 


### Error Correction
QR Code has error correction capability to restore data if the code is dirty or damaged. Four error correction levels (L, M, Q, and H) are available for users to choose according to the operating environment. The QR Code standard supports Reed-Solomon error correction and provides four error correction levels with the recovery capacity from 7% to 30% at most. For Micro QR Code symbols, error correction level H is not available. For Version M1 Micro QR Code
symbols, the RS capacity is limited to error detection only.

<details>  
<summary>Read more</summary>

The *QR Code* standard supports four error correction levels as listed below.
  
|<p align="center">**Error Correction**</p>|<p align="center">**Recovery Capacity**</p>|
| :-: | :-: |
|Level L| 7% |
|Level M| 15% |
|Level Q| 25% |
|Level H| 30% |
     
</details>

## Advantanges and Weaknesses
<details>  
<summary>Read more</summary>
  
The key advantages of QR codes are summarized below:
- very high barcode recognition speed owing to geometrical specifics
- readability from any angle 
- barcode reading capability under severe 3D distortions 
- encoding byte streams of data
- encoding Unicode symbols using ECI (is not valid for *Micro QR Code*)
- high data encoding density
- customizable error correction that allows recovering up to 30% of barcode data at the maximal level H 
- structured append feature
  
However, *QR Code* barcodes are sensitive to substantial damages of a target pattern as they can hinder barcode detection in the scanned image.

Concerning personal vaccination passports/certificates, in some cases, QR codes may contain personal data that you might want to keep private. In general, such QR codes simply store links to external pages, and data on such pages are usually anonymized. To verify this, you may check information on the official website of your local authorities or control what exactly is encoded in your QR code using the Aspose.Barcode QR Code scanner.

</details>

## **Aspose Code Samples for Micro QR Code Generation and Recognition**
### **Micro QR Code Generation Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

Insert Code

{{< /tab >}}

{{< tab tabNum="2" >}}

<!-->Insert Code<-->

{{< /tab >}}

{{< tab tabNum="3" >}}

<!-->Insert Code<-->

{{< /tab >}}

{{< /tabs >}}

### **Micro QR Code Recognition Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

Insert Code

{{< /tab >}}

{{< tab tabNum="2" >}}

Insert Code

{{< /tab >}}

{{< tab tabNum="3" >}}

Insert Code

{{< /tab >}}

{{< /tabs >}}

<details>  
<summary>**Code Sample for Micro QR Code Generation**</summary>

{{< highlight csharp>}}
//generate Micro QR Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Aspose"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    //encode data as MicroQR
    gen.Parameters.Barcode.QR.QrEncodeType = QREncodeType.ForceMicroQR;
    //set error correction level 7%
    gen.Parameters.Barcode.QR.QrErrorLevel = QRErrorLevel.LevelL;
    //set version M4 can be Auto
    gen.Parameters.Barcode.QR.QrVersion = QRVersion.VersionM4;
    gen.Save($"{path}MicroQR.png", BarCodeImageFormat.Png);
}
{{< /highlight >}}

</details>
  
<details>  
<summary>**Code Sample for Micro QR Recognition**</summary>

{{< highlight csharp>}}
//read Micro QR Barcode
using (BarCodeReader read = new BarCodeReader($"{path}MicroQR.png", DecodeType.MicroQR))
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
{{< /highlight >}}

</details>  
  
### Aspose.BarCode for Java

<details>  
<summary>Code Sample for Micro QR Code Generation</summary>
</details>
  
<details>  
<summary>Code Sample for Micro QR Code Recognition</summary>
</details>  

### Aspose.BarCode for C++

<details>  
<summary>Code Sample for Micro QR Code Generation</summary>
</details>
  
<details>  
<summary>Code Sample for Micro QR Code Recognition</summary>
</details>  
