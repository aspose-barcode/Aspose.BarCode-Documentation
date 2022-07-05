---
title: Working with Barcode Types
type: docs
description: "Description of Various Barcode Types Supported in Aspose.BarCode for .NET"
keywords: "Generate Barcodes, Barcode Types, Barcode Symbology, How to Generate Barcodes in C# .NET, Barcode types in Aspose.BarCode for .NET, 2D Barcodes, Linear Barcodes, 1D Barcode, Postal Barcodes, Generate QR, QR Code, Generate Code 39, Generate PDF 417, Generate MicroQR, Generate Data Matrix"
weight: 10
url: /net/symbologies-for-barcodes/
aliases:
- /net/managing-2d-barcodes/
-
---
This article introduces general information about barcode symbologies and describes their key properties along with providing sample barcode labels and code snippets to generate barcodes of different types. 

## **Overview**
A barcode is a graphical code composed of parallel lines and spaces of different widths or various figures combined in a visual pattern to encode data. After being generated and printed out, barcode labels get placed on scannable surfaces. Barcodes have been introduced as machine-readable tags to enable fast automatical information fetching from graphic data. A single barcode may correspond to approximately 25 characters for 1D types or 2,000 for 2D ones. The greater is the number of characters to be encoded in a single barcode, the larger is the generated barcode.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
  
### **Barcodes vs RFID**
Barcode reading requires using a light beam to identify black and white lines in a barcode label. Barcode scanners contain sensors that emit light signals and decoders that convert signals into text. Such scanners require line-of-sight visibility and can scan only one barcode at a time to read data successfully.  
Radio-frequency identification (RFID) may be considered as an alternative to barcode systems. This technology suggests employing radio waves to transmit the data fetched from RFID tags to RFID readers for further processing and interpretation. RFID tags enable data transmission to readers using sensors fixed on antennas. Such sensors usually have a unique ID so that one reader can scan multiple tags simultaneously without requesting line-of-sight visibility.  
  
Summing up, RFID systems are more efficient when there is a need to scan a large number of items at once, but they are more expensive and require more sophisticated setups compared with barcode ones. Moreover, RFID has physical limitations in terms of use, such as, for example, working with metals or liquids. In turn, barcode systems are known to be more accurate than RFID. Although they do not allow scanning multiple items simultaneously, they provide better recognition accuracy and reliability as barcode scanners can precisely read only required items.

### **Barcode Usage**
Barcodes have multiple applications in various spheres, such as retail, industry, healthcare, pharmacy, post and delivery, documentation management, and many others. Some examples of barcode system business applications are mentioned below:
- **Inventory tracking**. A simple inventory tracking system includes barcode scanners or mobile computers and specialized software to process barcodes. Each inventory item is assigned with a unique barcode label so that all operations with this item can be tracked by scanning its barcode.
- **Asset tracking**. Any business possesses various assets. Barcode asset tags can be placed onto each asset and then scanned to manage items using asset tracking software. Such an approach allows improving accountability and facilitating audit processes.
- **Billing and invoice management**. A barcode can be associated with a customer number or an individual invoice number so that the corresponding customer account or invoice number can be easily identified.
- **Managing admission desks**. Cinema tickets, event passes, travel itineraries, and other similar documents may have unique barcodes to get verified, in this way, facilitating and speeding up various admission processes. Moreover, this technology allows reducing printing costs.
- **Storing business and personal data**. Nowadays, barcodes and specifically, QR codes, are widely used to store information about organizations and persons. In many cases, such barcode labels can be read simply by a smartphone and provide quick and simple access to information for any user.  

## **Barcode Type Definition**
Barcode types define the way of encoding information in a barcode image. Each of them relies on a unique way of encoding data characters.    

**One-dimensional (1D)**, or linear, barcodes represent data by varying the width and spacing of parallel lines. In general, a linear barcode is composed of a leading margin, start character, message characters, check character (if any), stop character, and a trailing margin. Based on this framework, all known symbologies define their own encoding principles. In 1D barcodes, bars represent the binary digits, 0 and 1, that may constitute various sequences to encode numbers and then get processed by a digital unit.  
  
**Two-dimensional (2D)** barcodes have been introduced to address the limitations of linear symbologies. 2D barcodes are more complex and can include not only text data but also other types of information: price, quantity, web address, etc. They can be composed of rectangles, dots, hexagons, or other geometric patterns called matrix codes. By storing data both horizontally and vertically to form a square or rectangle, significantly more information can be encoded. Accordingly, 2D barcodes encode much larger amounts of information compared with typical 1D symbologies. 2D symbologies benefit from high readability and can mitigate poor printing quality as they contain additional data so that even if one or more cells are damaged, the barcode is still readable.  
  
**Postal barcodes** correspond to a specific group of symbologies that are used exclusively by post services of different countries. Unlike 1D barcodes, postal ones are created by varying the height of bars to encode information. In this way, a postal barcode represents a series of long and short bars that may be used to encode ZIP and ZIP+4 codes, delivery addresses, etc. Then, postal services use automated barcode scanning equipment to process and sort mail based on barcodes. 
  
### **Key Barcode Properties**
In substance, barcode symbologies are similar to file formats, as they define the following key barcode properties:
- [**Data encoding format**](#dataencoding). Different barcode types are capable of encoding sets of characters with different limitations: only numerical digits, only alphabet and special characters, entire encodings, etc. 
- [**Data density**](#datadensity). Each symbology has a specified capacity of how much information can be encoded in a barcode. Accordingly, barcodes may have high or low data density. 
- [**Shape**](#shape). Barcode shapes can be rectangular, square, or adjusted to elongated spaces.
- [**Recognition precision**](#precision). Some 1D barcode types do not include checksum and corresponding controls, and thus it is impossible to verify whether all data contained in a barcode have been recognized and decrypted correctly. Such barcodes have low recognition precision. In contrast, 2D barcodes not only allow recovering partially corrupted data but also have high recognition precision because they provide mechanisms to guarantee that all barcode data have been read properly. 
  
### **Supported Symbologies**
All symbologies supported in ***Aspose.BarCode for .NET*** are outlined below.
  
<table> 
<tr> <th></th><th></th> 
<th><p align="center"><b>Supported Symbologies</b></p></th> 
</tr> 
<tr> <th rowspan="2">1D</th> 
<th>Numerical Only</th> 
<td>Code 11, Code 32, Codabar, Databar Omnidirectional, Databar Stacked Omnidirectional, Databar Limited, Databar Truncated, Databar Stacked, EAN 13, EAN 14, EAN 8,
IATA 2-of-5, Italian Post 25, Interleaved 2-of-5, ISBN ISMN, ISSN, ITF 6, ITF 14, Matrix 2-of-5, MSI, OPC, PatchCode, Pharmacode, PZN, SSCC 14, SSCC 18, 
Standard 2-of-5, EAN 5, EAN 2, UPC-A, UPC-E, UpcaGs1DatabarCoupon
</td> 
</tr> 
<tr> <th>Alpha-Numeric</th> 
<td>Code 128, Code 39, Code 93, Code 16K, CodablockF, Databar Expanded, Databar Expanded Stacked, GS1 CodablockF, GS1 Code 128, VIN</td> 
 </tr> 
<tr> <th colspan ="2" >2D</th> 
<td>QR Code, Micro QR Code, PDF417, Compact PDF417, Macro PDF417, Micro PDF417, Aztec, DataMatrix, DotCode, GS1 Data Matrix, GS1 QR, MaxiCode</td> 
 </tr> 
 <tr> <th colspan ="2">Postal</th> 
<td>Australia Post, AustralianPostParcel, Deutsche Post Identcode, Deutsche Post Leticode, Planet, Postnet, RM4SCC, SingaporePost, SwissPostParcel, USPS OneCode</td> 
 </tr> 
</tr> 
</table>
  

## **Setting Barcode Symbology in Aspose.BarCode**
***Aspose.BarCode for .NET*** supports nearly all widely used barcode symbologies. In general, to generate a barcode image, it is necessary to create an instance of class [*BarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) with two main parameters to be initialized: data contents to be encoded in the [*CodeText*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/properties/codetext) property and the barcode type in the [*BarcodeType*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/properties/barcodetype) property. The [*BarcodeType*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/properties/barcodetype) property is used to define the symbology of generated barcodes. Developers can assign any symbology to the [*BarcodeType*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/properties/barcodetype) property out of the list of predefined barcode types supported by class [*BarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator). However, not all barcode symbologies enable barcode generation with barcode text in a required format due to the limitations of a barcode type itself.  
  
Below, two barcode types, *Code 39* and *QR Code*, are considered as examples to demonstrate how to generate barcodes in ***Aspose.BarCode for .NET***. 
  
**Code 39**    
*Code 39* is a barcode symbology with variable length. Its specification is limited to 43 characters, including uppercase letters (A-Z), numerical digits, and some special characters (-, ., $, /, +, %, and space). Each character is decoded by nine elements: five bars and four spaces. This symbology has low data density and does not allow ensuring recognition accuracy as it does not require setting an obligatory checksum by default. 

<p align="center"><image src="code39extended.png"></p>
  
The code snippet provided below illustrates how to generate a barcode using the *Code 39* symbology.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code39Extended, "$&This Code#*");
gen.Save($"{path}Code39Extended.png", BarCodeImageFormat.Png);
{{< /highlight >}}  
  
**QR Code**  
*QR Code* is a 2D symbology that is used to encode long strings of alphanumeric data, typically text or URL. A *QR Code* label is composed of an array of black and white squares that can be recognized by smartphones and other readers. The *QR Code* symbology provides high data encoding density. Moreover, it supports the **Reed-Solomon** error correction that allows not only to restore corrupted data but also to ensure correct information decoding.  

<p align="center"><image src="qrcode.png"></p>
  
The code sample below can be used to generate a *QR Code* barcode.  

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Aspose常に先を行く");
gen.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.ECIEncoding;
gen.Parameters.Barcode.QR.QrECIEncoding = ECIEncodings.UTF8;
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}QrCode.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

## **Data Encoding Formats**
<a name="dataencoding"></a>

Different symbologies have different underlying data encoding approaches and capabilities. Accordingly, barcode label size and the amount of data to be encoded are predefined for each symbology. Some barcode types allow encoding only digits or a limited set of characters and digits, while others can accept any byte sequence without limitations.  
Further in the article, several barcode types (*EAN 13*, *Code 11*, *GS1 Code 128*, and *PDF417*)) with different data densities are presented as examples.   

**EAN 13**  
*EAN 13* barcodes can encode only numerical digits. Specifically, the *EAN 13* data encoding format requires encoding precisely 12 digits with the 13th one used as a control sum calculated according to the specified algorithm. 
  
<p align="center"><image src="ean13.png"></p>

The following code snippet explains how to generate *EAN13* barcodes.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN13, "1234567890128");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Save($"{path}Ean13.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
**Code 11**  
The *Code 11* symbology allows encoding a string of any length (theoretically, unlimited), including numerical digits and the dash sign (-).
  
<p align="center"><image src="code11.png"></p>
  
The following code sample demonstrates how to create a *Code 11* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code11, "1234-5678");
gen.Save($"{path}Code11.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
**GS1 Code 128**  
*GS1 Code 128* can encode any of ASCII alphanumeric characters similarly to the basic *Code 128* symbology. However, in *GS1 Code 128*, the data encoding format is defined strictly according to the GS1 standards.  
  
<p align="center"><image src="gs1code128.png"></p>
  
The code example provided below can be used to generate a *GS1 Code128* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.GS1Code128, "(02)04006664241007(37)1");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Save($"{path}GS1Code128.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
**PDF417**  
The *PDF417* barcode is a 2D high-density symbology that is capable of encoding any sequence of bytes, including text, numbers, files, and actual data bytes. It supports the Reed-Solomon error correction and thus provides high recognition accuracy.
  
<p align="center"><image src="pdf417.png"></p>
  
The following code snippet illustrates how to generate a *PDF417* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Save($"{path}Pdf417.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
## **Data Density**
<a name="datadensity"></a>
Data density is one of the most important properties of barcode symbologies. It defines how much information can be encoded in a single barcode. It is low for 1D barcodes and considerably high for 2D matrix barcode types. The difference in data density for 2D and 1D symbologies can exceed 10 times.
The barcode types discussed below, *Code93* and *Data Matrix*, are provided as examples of symbologies with different data densities.  

**Code 93**  
*Code 93* is a more secure and compact version of the *Code 39* symbology that can encode both alphabet characters and numerical digits. *Code 93* has quite low data density; therefore, with respect to other symbologies, it requires generating larger barcodes to encode the same amounts of information.  
  
<p align="center"><image src="code93extended.png"></p>
  
The following code sample shows how to generate a *Code93* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code93Extended, "$&This Code#*");
gen.Save($"{path}Code93Extended.png", BarCodeImageFormat.Png);
{{< /highlight >}}

**DataMatrix**  
*DataMatrix* is a 2D code that allows encoding large amounts of data in a compact space. A single *DataMatrix* can contain up to 2,335 alphanumeric or 3,116 numerical characters. This is 10 times greater than the standard data density of 1D barcodes.
  
<p align="center"><image src="datamatrix.png"></p>

The code example below can be used to create a *DataMatrix* barcode.  

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}DataMatrix.png", BarCodeImageFormat.Png);
{{< /highlight >}}

## **Barcode Shapes**
<a name="shape"></a>
In general, the surfaces to place printed barcodes can have various shapes. At the same time, barcodes can be of rectangular or square forms only. Accordingly, if there is a large space to put a rectangular barcode, the generation of a square-shaped barcode is unacceptable from the viewpoint of space usage.  
Further, two barcode types, *MicroQR* and *Compact PDF417*, are considered as examples of symbologies with different barcode shapes. 

**MicroQR Code**  
The *MicroQR Code* symbology provides large data density; however, it has a square shape and thus needs square space to be placed. A major feature of *MicroQR* is that it has only one position detection pattern instead of three ones for regular *QR Code* and requires a more compact placement area.
  
<p align="center"><image src="microqr.png"></p>
  
The following code snippet illustrates how to generate a *MicroQR* code.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Åspóse.Barcóde©");
gen.Parameters.Barcode.QR.QrEncodeType = QREncodeType.ForceMicroQR;
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}MicroQR.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
**Compact PDF417**    
*Compact PDF417* can be used when space limitations are the main concern and symbol damage is unlikely. It has less data density compared with other 2D barcodes; however, owing to its property to have a length 64 times larger than height, it is more suitable for narrow rectangular areas with size limitations.
  
<p align="center"><image src="compactpdf417.png"></p>
  
The code sample below can be used to create a *Compact PDF417* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
//Compact version of Pdf417
gen.Parameters.Barcode.Pdf417.Pdf417Truncate = true;
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Save($"{path}CompactPdf417.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

## **Barcode Recognition Precision**
<a name="precision"></a>
In some cases, the data fetched after barcode recognition may be incorrect. Generally, 1D barcodes do not include a checksum or contain only simple controls; accordingly, this may result in reading erroneous data from barcodes. In turn, the majority of 2D barcodes rely on the Reed-Solomon error correction, which allows ensuring correct barcode recognition and partially recovering the data from damaged barcodes.  
The symbologies outlined below, *Interleaved 2 of 5* and *Aztec*, are considered as examples of barcode types with different recognition accuracy.
  
**Interleaved 2-of-5**  
The *Interleaved 2-of-5* symbology can encode sequences of digits of any length as long as such a sequence contains an even number of digits. By default, it does not require setting a checksum and thus can be read with errors.
  
<p align="center"><image src="interleaved2of5.png"></p>
  
The following code example describes how to generate *Interleaved 2 of 5* barcodes.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Interleaved2of5, "1234567890");
gen.Save($"{path}Interleaved2of5.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
**Aztec**  
*Aztec* is a highly efficient 2D symbology that uses square modules with a unique finder pattern in the middle of a barcode, which allows barcode scanners to identify cell locations required for barcode reading. This barcode type not only enables encoding any sequence of bytes but also ensures correct data recognition.
  
<p align="center"><image src="aztecfull.png"></p>
  
The code snippet given below shows how to generate an *Aztec* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Aztec, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}AztecFull.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
## **Postal Symbologies** 
Postal symbologies correspond to the specific industrial barcode types that are used only for the needs of postal services. They have much lower data density compared with 2D barcodes and are capable of encoding limited sets of characters, mainly, only numerical ones. Unlike traditional barcodes, postal symbologies usually vary the height of bars to encode information. At present, postal services tend to replace specified postal symbologies with widely used 2D barcodes. However, this transition process cannot be completed immediately; therefore, ***Aspose.Barcode for .NET*** supports the most widely used postal symbologies in addition to 1D and 2D ones.

**Postnet**  
The *Postnet* symbology allows encoding only digits corresponding to ZIP or ZIP+4 codes in half- and full-height bars; its parameters are similar to those of 1D barcodes. In this barcode type, each digit is encoded by a set of five bars, two of which are of full height.
Two symbologies considered below, *Postnet* and *RM4SCC* are provided as examples of postal barcodes supported in ***Aspose.Barcode for .NET***. 
<p align="center"><image src="postnet.png"></p>
  
The following code example illustrates how to generate a *Postnet* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Postnet, "1159628792");
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}Postnet.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

**RM4SCC**  
*RM4SCC* is capable of encoding only digits and English alphabet capital characters. Its parameters are similar to those of 1D barcodes. In this barcode type, each character corresponds to four bars so that two of them are extended upwards and the other two - downwards. The combination of such bars with variable height provides combinations to encode 36 possible characters: 10 numerical and 26 alphabetical ones.
  
<p align="center"><image src="rm4scc.png"></p>

The code snippet given below shows how to generate a *Postnet* barcode.
   
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.RM4SCC, "N101HU9Z");
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}RM4SCC.png", BarCodeImageFormat.Png);
{{< /highlight >}} 


