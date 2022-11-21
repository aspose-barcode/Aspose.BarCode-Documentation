---
title: Overview of Barcode Types
type: docs
description: "Description of Various Barcode Types Supported in Aspose.BarCode for Node.js via Java"
keywords: "Generate Barcodes, Barcode Types, Barcode Symbology, How to Generate Barcodes in Node.js, Barcode types in Aspose.BarCode for Node.js, 2D Barcodes, Linear Barcodes, 1D Barcode, Postal Barcodes, Generate QR, QR Code, Generate Code 39, Generate PDF417, Generate Micro QR Code, Generate Data Matrix"
weight: 10
url: /nodejsjava/generate-barcode-types/

---
This article introduces general information about barcode types and describes their key properties along with providing sample barcode labels and code snippets to generate barcodes of different types. 

## **Overview**
A barcode is a graphical code composed of parallel lines and spaces of different widths or various figures combined in a visual pattern to encode data. After being generated and printed out, barcode labels get placed on scannable surfaces. Barcodes have been introduced as machine-readable tags to enable fast automatical information fetching from graphic data. A single barcode may correspond to approximately 25 characters for 1D types or 2,000 for 2D ones. The greater the number of characters to be encoded in a single barcode, the larger the generated barcode.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/nodejsjava/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
  
### **Supported Barcode Types**
All types supported in ***Aspose.BarCode for Node.js via Java*** are listed below.
  
<table> 
<tr> <th></th><th></th> 
<th><p align="center"><b>Supported Barcode Types</b></p></th> 
</tr> 
<tr> <th rowspan="2">1D</th> 
<th>Numerical Only</th> 
<td>Code 11, Code 32, Codabar, DataBar Omnidirectional, DataBar Stacked Omnidirectional, DataBar Limited, DataBar Truncated, DataBar Stacked, EAN 13, EAN 14, EAN 8,
IATA 2-of-5, Italian Post 25, Interleaved 2-of-5, ISBN, ISMN, ISSN, ITF 6, ITF 14, Matrix 2-of-5, MSI, OPC, Patch Code, Pharmacode, PZN, SSCC 14, SSCC 18, 
Standard 2-of-5, EAN 5, EAN 2, UPC-A, UPC-E, UpcaGs1DatabarCoupon
</td> 
</tr> 
<tr> <th>Alpha-Numeric</th> 
<td>Code 128, Code 39, Code 93, Code 16K, CodablockF, DataBar Expanded, DataBar Expanded Stacked, GS1 CodablockF, GS1 Code 128, VIN</td> 
 </tr> 
<tr> <th colspan ="2" >2D</th> 
<td>QR Code, Micro QR Code, PDF417, Compact PDF417, Macro PDF417, Micro PDF417, Aztec Code, Data Matrix, DotCode, GS1 Data Matrix, GS1 QR Code, MaxiCode</td> 
 </tr> 
 <tr> <th colspan ="2">Postal</th> 
<td>Australia Post, AustralianPostParcel, Deutsche Post Identcode, Deutsche Post Leticode, Planet, Postnet, RM4SCC, SingaporePost, Swiss Post Parcel, USPS OneCode</td> 
 </tr> 
</tr> 
</table>
    

## **Setting Barcode Type**
***Aspose.BarCode for Node.js via Java*** supports nearly all widely used barcode types. In general, to generate a barcode image, it is necessary to create an instance of class [*BarcodeGenerator*]() with two main parameters to be initialized: data contents to be encoded using the *setCodeText* method and the barcode type in the *setBarcodeType* method. The *setBarcodeType* method is used to define the type of generated barcodes. Developers can assign any options to the *setBarcodeType* property from the list of predefined barcode types supported by class [*BarcodeGenerator*](). However, not all types enable barcode generation with input text in a required format due to the limitations of a barcode type itself.  
  
Below, two barcode types, *Code 39* and *QR Code*, are considered as examples to demonstrate how to generate barcodes. 
  
**Code 39**    
*Code 39* is a barcode type with variable length. Its specification is limited to 43 characters, including uppercase letters (A-Z), numerical digits, and some special characters (-, ., $, /, +, %, and space). Each character is decoded by nine elements: five bars and four spaces. This type has low data density and does not allow ensuring recognition accuracy as it does not require setting an obligatory checksum by default. 

<p align="center"><image src="code39extended.png"></p>
  
  
**QR Code**  
*QR Code* is a 2D type that is used to encode long strings of alphanumeric data, typically text or URL. A *QR Code* label is composed of an array of black and white squares that can be recognized by smartphones and other readers. The *QR Code* type provides high data encoding density. Moreover, it supports the **Reed-Solomon** error correction that allows not only to restore corrupted data but also to ensure correct information decoding.  

<p align="center"><image src="qrcode.png"></p>
  

## **Data Encoding Formats**
<a name="dataencoding"></a>

Different types have different underlying data encoding approaches and capabilities. Accordingly, barcode label size and the amount of data to be encoded are predefined for each type. Some barcode types allow encoding only digits or a limited set of characters and digits, while others can accept any byte sequence without limitations.  
Further in the article, several barcode types (*EAN 13*, *Code 11*, *GS1 Code 128*, and *PDF417*) with different data densities are presented as examples.   

**EAN 13**  
*EAN 13* barcodes can encode only numerical digits. Specifically, the *EAN 13* data encoding format requires encoding precisely 12 digits with the 13th one used as a control sum calculated according to the specified algorithm. 
  
<p align="center"><image src="ean13.png"></p>
  
**Code 11**  
*Code 11* allows encoding a string of any length (theoretically, unlimited), including numerical digits and the dash sign (-).
  
<p align="center"><image src="code11.png"></p>
  
  
**GS1 Code 128**  
*GS1 Code 128* can encode any of ASCII alphanumeric characters similarly to the basic *Code 128* type. However, in *GS1 Code 128*, the data encoding format is defined strictly according to the GS1 standards.  
  
<p align="center"><image src="gs1code128.png"></p>
  

**PDF417**  
The *PDF417* barcode is a 2D high-density type that is capable of encoding any sequence of bytes, including text, numbers, files, and actual data bytes. It supports the Reed-Solomon error correction and thus provides high recognition accuracy.
  
<p align="center"><image src="pdf417.png"></p>
  

## **Data Density**
<a name="datadensity"></a>
Data density is one of the most important properties of barcode types. It defines how much information can be encoded in a single barcode. It is low for 1D barcodes and considerably high for 2D matrix barcode types. The difference in data density for 2D and 1D types can exceed 10 times.
The barcode types discussed below, *Code93* and *Data Matrix*, are provided as examples of barcode types with different density values.  

**Code 93**  
*Code 93* is a more secure and compact version of *Code 39* that can encode both alphabet characters and numerical digits. *Code 93* has quite low data density; therefore, with respect to other types, it requires generating larger barcodes to encode the same amounts of information.  
  
<p align="center"><image src="code93extended.png"></p>
  

**Data Matrix**  
*Data Matrix* is a 2D code that allows encoding large amounts of data in a compact space. A single *Data Matrix* can contain up to 2,335 alphanumeric or 3,116 numerical characters. This is 10 times greater than the standard data density of 1D barcodes.
  
<p align="center"><image src="datamatrix.png"></p>


## **Barcode Shapes**
<a name="shape"></a>
In general, the surfaces to place printed barcodes can have various shapes. At the same time, barcodes can be of rectangular or square forms only. Accordingly, if there is a large space to put a rectangular barcode, the generation of a square-shaped barcode is unacceptable from the viewpoint of space usage.  
Further, two barcode types, *Micro QR Code* and *Compact PDF417*, are considered as examples of barcodes with different shapes. 

**Micro QR Code**  
*Micro QR Code* provides large data density; however, it has a square shape and thus needs square space to be placed. A major feature of *MicroQR* is that it has only one position detection pattern instead of three ones for regular *QR Code* and requires a more compact placement area.
  
<p align="center"><image src="microqr.png"></p>
  
  
**Compact PDF417**    
*Compact PDF417* can be used when space limitations are the main concern and barcode damage is unlikely. It has less data density compared with other 2D barcodes; however, owing to its property to have a length 64 times larger than height, it is more suitable for narrow rectangular areas with size limitations.
  
<p align="center"><image src="compactpdf417.png"></p>
  

## **Barcode Recognition Precision**
<a name="precision"></a>
In some cases, the data fetched after barcode recognition may be incorrect. Generally, 1D barcodes do not include a checksum or contain only simple controls; accordingly, this may result in reading erroneous data from barcodes. In turn, the majority of 2D barcodes rely on the Reed-Solomon error correction, which allows ensuring correct barcode recognition and partially recovering the data from damaged barcodes.  
The types outlined below, *Interleaved 2-of-5* and *Aztec Code*, are considered as examples of barcode types with different recognition accuracy.
  
**Interleaved 2-of-5**  
*Interleaved 2-of-5* can encode sequences of digits of any length as long as such a sequence contains an even number of digits. By default, it does not require setting a checksum and thus can be read with errors.
  
<p align="center"><image src="interleaved2of5.png"></p>
  
  
**Aztec Code**  
*Aztec Code* is a highly efficient 2D type that uses square modules with a unique finder pattern in the middle of a barcode, which allows barcode scanners to identify cell locations required for barcode reading. This barcode type not only enables encoding any sequence of bytes but also ensures correct data recognition.
  
<p align="center"><image src="aztecfull.png"></p>
  
  
## **Postal Barcodes** 
Postal symbologies correspond to the specific industrial barcode types that are used only for the needs of postal services. They have much lower data density compared with 2D barcodes and are capable of encoding limited sets of characters, mainly, only numerical ones. Unlike traditional barcodes, postal types usually vary the height of bars to encode information. At present, postal services tend to replace specified postal types with widely used 2D barcodes. However, this transition process cannot be completed immediately; ***Aspose.Barcode for Node.js via Java*** supports the most widely used postal types in addition to 1D and 2D ones.

**Postnet**  
*Postnet* allows encoding only digits corresponding to ZIP or ZIP+4 codes in half- and full-height bars; its parameters are similar to those of 1D barcodes. In this barcode type, each digit is encoded by a set of five bars, two of which are of full height.
Two type considered below, *Postnet* and *RM4SCC*, are provided as examples of postal barcodes. 
<p align="center"><image src="postnet.png"></p>
  
**RM4SCC**  
*RM4SCC* is capable of encoding only digits and English alphabet capital characters. Its parameters are similar to those of 1D barcodes. In this barcode type, each character corresponds to four bars so that two of them are extended upwards and the other two - downwards. The combination of such bars with variable height provides combinations to encode 36 possible characters: 10 numerical and 26 alphabetical ones.
  
<p align="center"><image src="rm4scc.png"></p>



