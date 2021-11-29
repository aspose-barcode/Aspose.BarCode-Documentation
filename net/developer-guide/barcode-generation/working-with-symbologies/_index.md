---
title: Working with Symbologies
type: docs
weight: 10
url: /net/working-with-symbologies/
---
This article introduces general information about barcode symbologies and describes key barcode properties along with sample barcode labels and code snippets to generate barcodes of different types. 

## Overview
A barcode is a graphical code composed of parallel lines and spaces of different widths combined together in a visual pattern to encode data. After being generated and printed out, barcodes get placed on scannable surfaces. Barcodes have been introduced as machine-readable tags to enable fast automatical information fetching from graphic data. Usually, a barcode may correspond to approximately 25 characters for 1D types or 2,000 for 2D ones. The more characters are inputted to encode, the larger is the generated barcode.
  
### Barcodes vs RFID
To read barcodes, a light beam is used to identify black and white lines in a barcode label. Barcode scanners rely on sensors that emit such signals and decoders that interpret signals into text. Barcode scanners require the line-of-sight visibility and need to observe one barcode at a time to read the data.  
Radio-frequency identification (RFID) may be considered as an alternative to barcode systems. This technology implies using radio waves to transmit the data captured from RFID tags to RFID readers for interpretation. Such a tag uses a sensor fixed on an antenna to enable data transmission to a reader. Sensors usually have unique ID so that one reader can scan multiple tags simultaneously without requesting the line-of-sight visibility.  
Summing up, RFID is more efficient when there is a need to scan a large number of items at once, but such systems are more expensive and require more sophisticated setup compared with barcode ones. Moreover, RFID has physical limitations in terms of use, such as, for example, working with metals or liquids. In turn, barcode systems are deemed more accurate than RFID. Even though they do not allow scanning multiple items at once, the use of barcodes ensures better accuracy and reliability as they capture only required items precisely.

### Barcode Usage
Barcodes have multiple applications in various spheres, such as retail, industry, healthcare, pharmacy, post and delivery, documentation management, and many others. Some examples of using barcode systems in business are mentioned below:
- *Inventory tracking*. A simple inventory tracking system includes software and barcode scanners or mobile computers. Each inventory item must have a unique barcode label so that all operations with this item can be tracked by scanning its barcode.
- *Asset tracking*. Any business posesses various assets. Barcode asset tags can be assigned to each asset and then scanned to manage items using asset tracking software. It allows improving accountability and facilitating audit processes.
- *Billing and invoice management*. A barcode can be associated with a customer number or an individual invoice number so that the corresponding customer account or invoice number can be easily identified.
- *Managing admission desks*. Cinema tickets, event passes, travel itineraries, and other similar documents may have unique barcodes to get verified, in this way, facilitating and speeding up an admission process. Such technology also allows reducing printing costs.
- *Storing business and personal data*. Nowadays, barcodes and specifically, QR codes, are widely used to store information about organizations or persons that can be read simply by a smartphone.  

## Symbology Definition
Barcode symbology defines the way of encoding information into the barcode image. Each barcode symbology relies on a unique way of encoding data characters. One-dimensional (1D), or linear, barcodes represent data by varying the width and spacing of parallel lines.  In general, a linear barcode is composed of a leading margin, start character, message characters, check character (if any), stop character, and a trailing margin. Based on this framework, all known symbologies constitute their own encoding principles. In 1D barcodes, the bars represent the binary digits 0 and 1 that may constute various sequences to encode numbers from 0 to 9 and then be processed by a digital unit. The presence or absence of a bar of a particular width in a specific position in a sequence is read by the computer as 1 or 0.  
Later, two-dimensional (2D) barcodes have been introduced.
  
2D barcodes are more complex and can include not only text data but also other types of information: price, quantity, web address, or image. They can be composed of rectangles, dots, hexagons and other geometric patterns called matrix codes that can encode much larger amounts of data than a typical 1D barcode. By storing data both horizontally and vertically to form a square or rectangle, significantly more information can be encoded than is possible with a 1D barcode. The 2D symbology is known for high readability and resistance to poor printing; they contain redundant data so even if one or more cells are damaged, the code is still readable.  
The other specific group of symbologies refers to postal barcodes that are used exclusively by post services of different countries. Unlike 1D barcodes, postal ones are created varying the height of bars to encode information. In this way, a postal barcode represents a series of long and short bars that may be used to encode ZIP codes, ZIP+4 codes, delivery addresses, etc. Postal services use automated barcode scanning equipment to process and sort mail by according to barcodes. 
  
### Key Barcode Properties 
In substance, barcode symbologies are similar to file formats, as they define the following key barcode properties:
- [Data encryption format](#dataencryption). Different barcode types are capable of encoding sets of characters with different limitations: only numerical digits, only alphabet and special characters, entire encodings, etc. 
- [Data density](#datadensity). Each symbology has a specified capacity of how much information can be encoded in a barcode. Accordingly, barcodes may have high or low data density. 
- [Shape](#shape). Barcode shape can be rectangular, square, or adjusted to elongated spaces.
- [Recognition precision](#precision). Some barcode types do not include checksum and corresponding controls, and thus, it is impossible to verify whether all data contained in a barcode have been recognized and decrypted correctly. Such barcodes have low recognition precision. In contrats, 2D barcodes not only allow recovering partially corrupted data, but also have high recognition precision because they provide mechanisms to guarantee that all barcode data have been read properly. 
  
### Supported Symbologies
All symbologies supported in ***Aspose.BarCode for .NET*** are outlined below.
<table> 
<tr> <th></th><th></th> 
<th><p align="center"><b>Supported Symbologies</b></p></th> 
</tr> 
<tr> <th rowspan="2">1D (Linear)</th> 
<th>Numeric Only</th> 
<td>Code 11, Code 32, Codabar, Databar OmniDirectional, Databar Stacked OmniDirectional, DatabarLimited, DatabarTruncated, Databar Stacked, EAN 13, EAN 14, EAN 8,
IATA 2 of 5, Italian Post 25, Interleaved 2 of 5, ISBN ISMN, ISSN, ITF6, ITF 14, Matrix 2 of 5, MSI, OPC, PatchCode, Pharmacode, PZN, SSCC 14, SSCC 18, 
Standard 2 of 5, EAN 5, EAN 2, UPC A, UPC E, UpcaGs1DatabarCoupon
</td> 
</tr> 
<tr> <th>Alpha-Numeric</th> 
<td>Code 128, Code 39, Code 93, Code 16K, CodablockF, Databar Expanded, Databar Expanded Stacked, GS1 CodablockF, GS1 Code 128, VIN</td> 
 </tr> 
<tr> <th colspan ="2" >2D</th> 
<td>QR, MicroQR, PDF 417, Compact PDF 17, Macro PDF 17, Micro PDF 17, Aztec, Data Matrix, DotCode, GS1 Data Matrix, GS1 QR, MaxiCode</td> 
 </tr> 
 <tr> <th colspan ="2">Postal</th> 
<td>Australia Post, AustralianPosteParcel, Deutsche Post Identcode, Deutsche Post Leticode, Planet, Postnet, RM4SCC, SingaporePost, SwissPostParcel, USPS OneCode</td> 
 </tr> 
</tr> 
</table>

## Setting Barcode Symbology in Aspose.BarCode
***Aspose.BarCode for .NET*** supports nearly all widely used barcode symbologies. In general, to generate a barcode image, it is necessary to create an instance of class *BarcodeGenerator* with two main parameters to be initialized: data contents to be encoded *CodeText* and barcode symbology *EncodeType*.
Barcode generating classes, such as *LinearBarCode* and *BarCodeGeneratorControl*, have a common property called *EncodeType* that is used to define the symbology of a barcode. Developers can assign any symbology to the *SymbologyType* property out of pre-defined barcode types supported by the *BarcodeGenerator* class. However, it must be noted that not all barcode symbologies enable generating barcodes with code text in a required format due to the limitations of a barcode type itself.  
Below, two barcode types, Code39 and QR, are considered as examples to demonstrate how to generate barcodes in ***Aspose.BarCode for .NET***. 
  
**Code39**    
*Code39* is a barcode symbology with variable length. Its specification is limited to 43 characters, including uppercase letters (A through Z), numeric digits (0 through 9) and a number of special characters (-, ., $, /, +, %, and space). An additional character (denoted ‘*’) is used for both start and stop delimiters. Each character is decoded by nine elements: five bars and four spaces. This symbology has low data density and does not allow ensuring recading accuracy as it does not require by default setting a checksum. 

<p align="center"><image src="Code39Extended.png"></p>
  
The code snippet provided below illustrates how to generate a barcode of the *Code39* symbology.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code39Extended, "$&This Code#*");
gen.Save($"{path}Code39Extended.png", BarCodeImageFormat.Png);
{{< /highlight >}}  
  
**QR Code**  
*QR Code* is a 2D symbology that is used to encode long strings of alphanumeric data, typically text or a URL. A QR code is composed of an array of black and white squares that can be read by smartphones and other readers. The data encoded in a QR-Code may include all Unicode alphabetic characters, text, numbers, double characters, and URLs. Moreover, *QR Code* provides high data encoding density. This symbology supports the **Reed-Solomon** correction that allows not only to restore corrupted data but also to ensure correct information recognition.  
<p align="center"><image src="QrCode.png"></p>
  
The code sample below can be used to generate a barcode of the *QR Code* symbology.  

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Aspose常に先を行く");
gen.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.ECIEncoding;
gen.Parameters.Barcode.QR.QrECIEncoding = ECIEncodings.UTF8;
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}QrCode.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

## Data Encryption Formats
<a name="dataencryption"></a>

Different barcode symbologies have different underlying data encryption approaches and capabilities. Some barcode specifications can be used to encode only numerical sequences so that barcode label size and the amount of data to be encoded are predefined for each symbology. Other barcodes imply encoding only digits or a limited set of characters and digits, while others can accept any byte sequence without limitations. 
Further, several barcode types(EAN13, Code11, GS1 Code128, and PDF17)) with different data density are presented as examples.   

**EAN13**  
*EAN13* barcodes can encode only numerci digits. Specifically, *EAN13* data encryption format requires encoding precisely 12 digits with the 13-th digits used as a control sum calculated according to the specified algorithm. 
  
<p align="center"><image src="Ean13.png"></p>

The following code snippet explains how to generate an *EAN13* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN13, "1234567890128");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Save($"{path}Ean13.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
**Code11**  
The *Code11* symbology can encode a string of any length (theoretically, unlimited) including numerical digits and the dash sign (-).
  
<p align="center"><image src="Code11.png"></p>
  
The following code sample demonstrates how to create a *Code11* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code11, "1234-5678");
gen.Save($"{path}Code11.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
**GS1 Code128**  
*GS1 Code128* can encode all ASCII alphanumeric characters similarly as the base *Code128* symbology. However, in *GS1 Code128*, data encryption format is defined strictly according to the GS1 standards.  
  
<p align="center"><image src="GS1Code128.png"></p>
  
The code example provided below can be used to generate a *GS1 Code128* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.GS1Code128, "(02)04006664241007(37)1");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Save($"{path}GS1Code128.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
**PDF17**  
The PDF417 barcode is a 2D high-density symbology that is capable of encoding any sequence of bytes, including text, numbers, files, and actual data bytes. It supports the Reed-Solomon error correction, and therefore, provides high recogniition precision.
  
<p align="center"><image src="Pdf417.png"></p>
  
The following code snippet illustrates how to generate a *PDF17* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Save($"{path}Pdf417.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
## Data Density
<a name="datadensity"></a>
Data density is one of the most important properties of barcode symbologies. It defines how much information can be encoded in a signle bacode. It is low for 1D barcodes and considerably high for 2D matrix barcode types. The difference in data density for 2D and 1D symbologies can exceed 10 times.
  
**Code93**  
*Code 93* is a more secure and compact version of the *Code39* symbology that can encode both alphabet characters and numerical digits. *Code93* has quite low data density; therefore, with respect to other symbologies, it requires generating a larger barcode to encode the same amount of information.  
  
<p align="center"><image src="Code93Extended.png"></p>
  
The following code sample shows how to generate a *Code93* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code93Extended, "$&This Code#*");
gen.Save($"{path}Code93Extended.png", BarCodeImageFormat.Png);
{{< /highlight >}}

**Data Matrix**  
*Data Matrix* is a 2D code that can encode large amounts of data in a compact space. A single *Data Matrix can contain up to 2,335 alphanumeric or 3,116 numerical characters that is 10 times more than for 1D barcodes.
  
<p align="center"><image src="DataMatrix.png"></p>

The code example below can be used to create a *Data Matrix* barcode.  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}DataMatrix.png", BarCodeImageFormat.Png);
{{< /highlight >}}

## Barcode Shapes
<a name="shape"></a>
In general, the surfaces to place printed barcodes can have various shapes. At the same time, barcodes can be of rectangular or square forms only. Accordingly, if there is large space to put a rectangular barcode, the generation of a square-shaped barcode is inacceptable from the viewpoint of space usage.    
Как видно Micro QR обладает большой плотностью размещения данных, но при этом является квадратным баркодом, размещение которого требует большого квадратного пространства.


**MicroQR**  
The *MicroQR* symbology provides large data density; however, it has a square shape and accordingly, requires square space to be placed. A major feature of *MicroQR* Code is that it has only one position detection pattern instead of three ones for regular *QR Code* and thus requires a smaller placement area.
  
<p align="center"><image src="MicroQR.png"></p>
  
The following code snippet illustrates how to generate a *MicroQR* code.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Åspóse.Barcóde©");
gen.Parameters.Barcode.QR.QrEncodeType = QREncodeType.ForceMicroQR;
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}MicroQR.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
**Compact PDF417**    
*Compact PDF417* can be used when space limitations are the main concern and symbol damage is unlikely. It has lss data density compared with other 2D barcodes; however, owing to its property to have the length 64 times larger that height, it is more suitable for narrow rectangular areas with limited size.
  
<p align="center"><image src="CompactPdf417.png"></p>
  
The code sample below can be used to create a *Compact PDF417* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
//Compact version of Pdf417
gen.Parameters.Barcode.Pdf417.Pdf417Truncate = true;
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Save($"{path}CompactPdf417.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

## Barcode Recognition Precision
<a name="precision"></a>

**Interleaved 2 of 5**
Interleaved 2 of 5 barcodes are two-width numeric codes that can encode sequences of digits of any length, as long as there is an even number of digits in the code. By default, it does not require setting a checksum and therefore, can be read with errors.

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Interleaved2of5, "1234567890");
gen.Save($"{path}Interleaved2of5.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="Interleaved2of5.png"></p>

**Aztec**  
Aztec barcodes are very efficient two-dimensional (2D) symbologies that use square modules with a unique finder pattern in the middle of the symbol, which helps the barcode scanner to determine cell locations to decode the symbol. Characters, numbers, text and bytes of data may be encoded in an Aztec barcode. Unlike most other 2D matrix codes, an Aztec code does not require a quiet zone around the edge. Therefore, it is potentially able to store more data in a smaller space. The finder pattern is in the very center of the Aztec code, with the other data encoded around it in concentric square rings. Aztec barcodes are some of the smallest and most dependable symbologies in use today. Compared to other types, Aztec barcodes are approximately 30 times smaller than a Code 39 barcode representing the same data. Aztec barcodes are also good to use when sending barcoded documents via fax because the barcode can withstand many poor resolution and scanning issues. A quiet zone is not required with Aztec barcodes because the unique finder pattern is in the center of the symbol. However, some barcode imagers may have difficulty decoding unless a 1-module quiet zone is present, which should be the same color as the background.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Aztec, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}AztecFull.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="AztecFull.png"></p>

## Postal Symbologies 
The postal code symbology lies somewhere in between a 2-D and 1-D linear barcode. Instead of encoding the data in the black bar and white space widths, postal codes primarily use the height of the bars. The majority of postal codes only use numbers, but some are now starting to include letters as well.

**Postnet**
The *Postnet* symbologies allows encoding only digits. Concerning its parameters, it similar to 1D barcodes.
  
<p align="center"><image src="Postnet.png"></p>
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Postnet, "1159628792");
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}Postnet.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

**RM4SCC**
RM4SCC is capable of encoding only digits and English alphabet capital letters. Its parameters are similar to those of 1D barcodes.
  
<p align="center"><image src="RM4SCC.png"></p>
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.RM4SCC, "N101HU9Z");
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}RM4SCC.png", BarCodeImageFormat.Png);
{{< /highlight >}} 


