---
title: Generate QR Code and Micro QR Code in C++
linktitle: QR Code and Micro QR Code
type: docs
feedback: BARCODECOM
weight: 40
url: /cpp/qr-code-and-micro-qr-code/
aliases:
- /cpp/qr-and-micro-qr-barcode/
---
{{% alert color="primary" %}}[Generate QR Code Online](https://products.aspose.app/barcode/generate/qr): You can test the quality of ***Aspose.BarCode*** generation for QR Codes and get the results online.{{% /alert %}}

## **Overview**
The *QR Code* family corresponds to 2D matrix barcodes of square shape (except *Rectangular Micro QR Code* (rMQR) that will be added to ***Aspose.BarCode*** in the nearest future). Accordingly, *QR Code* and *Micro QR Code* barcodes require square space to be placed on a surface. This group of symbologies has large data density and enables encoding both byte streams of data and arbitrary information represented as a set of Unicode symbols. In ***Aspose.BarCode for C++***, the data encoding in Unicode is performed using Extended Channel Interpretation (ECI) and enables different encoding modes among which UTF8 is the most widespread one.  
  
At the minimal error correction level, the *QR Code* symbology can encode up to 7,089 numerical (4,296 alphanumeric) digits or 2,953 bytes, while the *Micro QR Code* standard allows encoding at most 35 numerical (21 alphanumeric) or 15 bytes. *Micro QR Code* is used to generate barcodes of reasonably small size; at the same time, to enable such a possibility, it does not support Extended Channel Interpretation (ECI) and does not support encoding Unicode symbols. Specifically, the *M1* version allows encoding only 5 numerical digits, while *M2* can encode 10 numerical or 6 alphanumeric symbols. This capacity may be sufficient to encode particular industrial markers.  

The key features of QR codes are summarized below:
- very high barcode recognition speed owing to geometrical specifics 
- barcode reading capability under severe 3D distortions 
- encoding byte streams of data
- encoding Unicode symbols using ECI (is not valid for *Micro QR Code*)
- high data encoding density
- customizable error correction that allows recovering up to 30% of the barcode data at the maximal level H 
  
However, *QR Code* barcodes are sensitive to substantial damages of a target pattern as they can hinder barcode detection in the scanned image.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out Aspose [Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **QR and Micro QR Code Generation Modes**
In ***Aspose.BarCode for C++***, it is possible to select *QR Code* or *Micro QR Code* barcodes and its versions to be generated using two properties of class *QrParameters*: *QrEncodeType* and *QrVersion* that are set to *Auto* by default.  
  
The first option is to initialize the *QrVersion* field that allows setting the required version of *QR Code* or *Micro QR Code*. If the inputted information is less than the capacity of the selected version, the remaining space is filled with padding symbols; if it is surplus, an exception is thrown.  
  
The second option can be used when *QrVersion* is set to *Auto*. In this case, the *QrEncodeType* field can be initialized to select the barcode type according to the input data size. This property can take the following values:

- *Auto*. First, the most suitable *Micro QR Code* version (from M1 to M4) is searched; then, *QR Code* versions (from *Version01* to *Version40*) are iterated over to find the most appropriate one. If the capacity of *Version40* is not sufficient for the input information, an exception is thrown.
- *ForceQR*. The most suitable *QR Code* version (from *Version01* to *Version40*) is set.
- *ForceMicroQR*. The most suitable *Micro QR Code* version (from *M1* to *M4*) is selected. If the capacity of *M4* is not sufficient to encode the inputted data, an exception is thrown. 
  
### **Automatic Sizing**
Barcode images below are provided to illustrate how to generate *QR Code* barcodes of various types using automatic size settings.
  
|<p align="center">**Size Setting Mode**</p>|<p align="center">***Auto***</p>|<p align="center">***ForceQR***</p>|<p align="center">***ForceMicroQR***</p>|
| :-: | :-: | :-: | :-: |
| |<img src="qrencodetypeauto.png">|<img src="qrencodetypeforceqr.png">|<img src="qrencodetypeforcemicroqr.png">|
  
  
### **Manual Version Selection**
***Aspose.BarCode for C++*** enables manual settings for the required version of *QR Code* barcodes to be generated. To do this, it is necessary to initialize the *QRVersion* property of class *QrParameters*. This property can take the values from *Version 01* to *Version 40* for *QR Code* and from *M1* to *M4* for *Micro QR Code*. Sample barcode labels demonstrated below are given to explain how to generate *QR Code* barcodes by setting the required version manually.
  
|<p align="center">**QR Version**</p>|<p align="center">**Is Set to *QR Version 05***</p>|<p align="center">**Is Set to *Micro QR Version M4***</p>|
| :-: | :-: | :-: |
| |<img src="qrversion05.png">|<img src="qrversionm4.png">|
  

## **Data Encoding Modes**
***Aspose.BarCode for C++*** supports several most widespread data encoding modes, including the Unicode standard. To set the required encoding mode, it is necessary to initialize the *QrEncodeMode* property of class *QrParameters*. This property can take the following values:
-	*Auto*. This encoding mode implies that the data passed to *CodeText* is encoded according to the value of the *CodeTextEncoding* property that gets the encoding of the inputted symbols (by default, it is set to *UTF8*).
-	*Bytes*. This mode is used to work with streams of bytes and can encode values from 0 to 255. If a byte stream contains digits greater than 255, the *UTF16LE* encoding is applied. 
-	*Utf8BOM* and *Utf16BEBOM*. These modes are applied to encode the input data using UTF8 and UTF16BE encodings, respectively; a byte order mark (BOM) character is added to indicate the used encoding. Note that it is preferable to use the *ECIEncoding* mode as it allows setting the encodings that are explicitly specified in the *QR Code* standard.  
-	*ECIEncoding*. This data encoding mode implies using the encoding listed in *QrECIEncoding*.
-	*ExtendedCodetext*. In this mode, information passed to the *CodeText* property contains control words besides the main text to be encoded. These control words are intended to set advanced control over data encoding and allow including text with different encodings into a single *QR Code* barcode.
  
### ***Auto* Mode**
The *Auto* data encoding mode utilizes the information from the *CodeTextEncoding* property to encode the input data. In case the text encoding is not defined explicitly in *CodeTextEncoding*, the binary encoding mode is applied. 
  
<p align="center"><img src="qrencodemodeauto.png"></p>

### ***Bytes* Mode**
The *Bytes* data encoding mode implies representing an input byte stream as an array of characters and then as a string. It allows encoding values from 0 to 255. In the case when a byte stream includes digits greater than 255, such a character is encoded as two bytes using the UTF16LE encoding (the lower byte first). To visualize the text under a *QR Code* barcode, the *TwoDDisplayText* property needs to be initialized.  
  
  
<p align="center"><img src="qrencodemodebytes.png"></p>
  
### ***Utf8BOM* and *Utf16BEBOM* Modes**
The *Utf8BOM* and *Utf16BEBOM* data encoding modes are used to encode the input data using *UTF8* and *UTF16BE* standards, respectively, using a byte order mark (BOM) character that is placed before the first data symbol. 
  
<p align="center"><img src="qrencodemodeutfbom.png"></p>
  
### ***ECIEncoding* Mode**
In the *ECIEncoding* data encoding mode, the input data is processed using one of the encodings specified in *QrECIEncoding*. The present library implementation includes all well-known charset encodings. In addition, the extended channel interpretation identifier that corresponds to the current encoding is set. In this way, information about the way of decoding the barcode data is passed to decoders. The *QrECIEncoding.UTF8* mode is the most preferable. 
  
<p align="center"><img src="qrencodemodeeciencoding.png"></p>
  
### ***ExtendedCodetext* Mode**
***Aspose.BarCode for C++*** provides an advanced data encoding mode called *ExtendedCodetext* that enables flexible manual settings for *QR Code* barcode generation. Particularly, this mode includes specific encoding capabilities, such as using the multi-ECI mode and setting FNC symbols (characters used to detect and distinguish fields in variable-length application identifiers). Developers can facilitate the generation of barcodes with extended barcode text using class *QrExtCodetextBuilder*. To replace the text displayed under the generated barcode, it is necessary to initialize the *TwoDDisplayText* property. In the case of setting the multi-ECI mode, data processing is performed for each predefined encoding automatically. Otherwise, the information inputted into *CodeText* is encoded according to the value of *CodeTextEncoding*.    

  
<p align="center"><img src="qrencodemodeextendedcodetext.png"></p>
  
## **Error Correction Level Settings**
The *QR Code* family supports four levels of Reed-Solomon error correction. This mechanism requires adding redundant information to a barcode so as to enable detecting and correcting errors automatically in the case of barcode label damages. In general, to restore 1% of errors, 2% redundancy is needed.  
  
*QR Code* standards provide the following error correction levels.
  
|<p align="center">**Error Correction**</p>|<p align="center">**Recovery Capacity**</p>|
| :-: | :-: |
|Level L| 7% |
|Level M| 15% |
|Level Q| 25% |
|Level H| 30% |
  
*QR Code* symbologies except *Micro QR* can set any of the supported error correction levels. In turn, *Micro QR* enables different error correction levels for different barcodes types: *M1* supports level L; *M2* - levels L and M; *M3* and *M4* - levels L, M, and Q. 
  
|<p align="center">**Error Correction Level**</p>|<p align="center">**Is Set to L**</p>|<p align="center">**Is Set to M**</p>|<p align="center">**Is Set to Q**</p>|<p align="center">**Is Set to H**</p>|
| :-: | :-: | :-: | :-: | :-: |
| |<img src="qrerrorlevell.png">|<img src="qrerrorlevelm.png">|<img src="qrerrorlevelq.png">|<img src="qrerrorlevelh.png">|
  

## **Structured Append Mechanism**
*QR Code* symbologies (except *Micro QR*) support the possibility to generate composite barcodes using the so-called **Structured Append** mechanism. In this mode, the input data can be divided among different *QR Code* barcodes and then composed into a single image. ***Aspose.BarCode for C++*** does not enable distributing information inputted into *CodeText* across several *QR Code* barcodes; however, it allows creating a composite *QR Code* label manually. This can be done by initializing the *StructuredAppend* property using the following fields: 
- *TotalCount* - the number of barcodes in a composite *QR Code* image (can take values from 2 to 16)
- *SequenceIndicator* - the sequence number of the current barcode (starting from 0)
- *ParityByte* - a byte that serves as a checksum identifier. In the general case, it is calculated as *XOR* of all bytes in which UTF16BE symbols are encoded using two bytes  
  
Sample barcode images provided below have been created using the structured append mechanism.
  
|<p align="center">**Structured Append QR Code**</p>|<p align="center">**First Type**</p>|<p align="center">**Second Type**</p>|
| :-: | :-: | :-: |
| |<img src="qrstructuredappendfirst.png">|<img src="qrstructuredappendsecond.png">|
  

## **Aspect Ratio Settings**
*Aspect Ratio* is the ratio between the height and the width of a barcode. To adjust barcode proportions using the X and Y coordinates in ***Aspose.BarCode for C++***, it is required to set the *AspectRatio* property of class *QrParameters*. This property is defined as a relative coefficient to the value of the *XDimension* parameter. Generally, the value of *AspectRatio* should be set to 1. When it is necessary to adjust the proportions of generated *QR Code* barcodes, the *AspectRatio* property can be used. Sample barcode labels shown below have been generated using different aspect ratio settings.  
  
|<p align="center">**Aspect Ratio**</p>|<p align="center">**Is Set to 1**</p>|<p align="center">**Is Set to 2**</p>|
| :-: | :-: | :-: |
| |<img src="qraspectratio1.png">|<img src="qraspectratio2.png">|
  
