---
title: Working with Symbologies
type: docs
weight: 20
url: /net/working-with-symbologies/
---

## Overview
A barcode is a machine-readable code composed of parallel lines and spaces of different width grouped together in some visual pattern to encode data and placed on a scannable surface. 
Barcodes have been introduced as machine-readable tags to enable fast automatical fetching from graphic data. Usually, a barcode may correspond to approximately 25 characters for 1D types and 2,000 for 2D ones. The more characters are inputted to encode, the bigger is the generated barcode.  
  
**Barcodes vs RFID**  
Barcode scanning involves using a beam of light to “read” the black and white lines of a barcode. The scanner includes a sensor that creates a signal from the reflected light, and a decoder then translates the signal into text and sends it to a computer or database. Barcode scanners require line of sight and must “see” each barcode one at a time in order to capture the data.  
RFID stands for radio-frequency identification, which uses radio waves to transmit information from RFID tags to an RFID reader. A tag contains a sensor attached to an antenna that enables the transmission of data to the reader. Each sensor typically contains unique identifiers, and a reader can simultaneously scan more than 100 tags and does not require line of sight visibility. This makes it easy to automate certain processes that would otherwise require extra time and resources, and be subject to human error. While barcode scanners require a line of sight to scan each code individually, RFID scanners can read multiple codes at once. RFID systems are much more efficient for scanning a large number of items but can be more expensive and require more setup than barcodes. On the other hand, barcode systems can sometimes be more accurate but are less durable and secure than RFID.

**Barcode Usage**  
Barcode usage: retail, industry, healthcare, pharmacy, post and delivery, documentation management, and many others. Some of the ways businesses use barcodes include:
- Inventory tracking. A basic inventory tracking system consists of software and a barcode scanner or mobile computer. Inventory items (like products you sell, supplies, or raw materials) will all have barcode labels, so when you remove an item from stock, you just scan the barcode to reduce the available count in your inventory tracking software, instead of having to type in a SKU.
- Asset tracking. Any business, no matter how large or small, has IT assets and fixed assets. Barcoded asset tags are attached to each individual asset, and can be scanned to check items in or out in your asset tracking software. It’s a great way to improve accountability and makes audits much easier.
- Billing and invoice management. Add a barcode that represents the customer number or the individual invoice number so when it’s returned with payment, you can easily locate the customer account or invoice number. This will prevent problems like applying payments to the incorrect customer account or invoice.
- Organizing admission desks. Movie theatres, event venues, travel tickets, etc have tickets with barcodes and they use scanners to verify the ticket and admission process. Using this in the events gives easy access to the database captured and track the revenue. At times, this also reduces the ticket printing costs for event organizing committees. Instead of printing the show tickets, they use the barcode at the venue. Today, online travel ticket bookings and boarding passes have barcodes that can be scanned easily.
- Storing business and personal data. QR codes are widely used to store information about organizations or persons.  

**Barcode Advantages**  
The main advantage of barcode systems is that they allow users to process detailed information at the moment the barcode is scanned, rather than simply storing information for later processing.
Barcode systems can be used to track products, prices, and stock levels for centralized management in a computer software system allowing for incredible increases in productivity and efficiency. 
Barcodes were developed to improve the speed of sales transactions, but there are other potential benefits to businesses, including: 

- Better accuracy - Relying on a barcode to process data is far more accurate than relying on manually-entered data, which is prone to errors.
- Data is immediately available - Because of the processing speed, information about inventory levels or sales is available in real time.
- Reduced training requirements - Thanks to the simplicity of the barcode scanner, employees need little in the way of training in how to use it. Additionally, thanks to barcodes, there is much less for employees to have to learn and retain.
- Improved inventory control - Being able to scan and track inventory yields a much more accurate count, as well as a better calculation of inventory turn. Companies can hold less inventory when they know how soon they will need it.
- Low cost implementation - Generating barcodes is quick and easy, as is installing a barcode system. Potential savings can be realized almost immediately.

## Definition of Symbology
Barcode symbology defines the way of encoding information into the barcode image. Each barcode symbology relies on a unique way of encoding data characters. One-dimensional (1D), or linear, barcodes represent data by varying the width and spacing of parallel lines. Later, two-dimensional (2D) barcodes have been introduced. 2D barcodes are more complex and can include not only text data but also other types of information: price, quantity, web address, or image. They can be composed of rectangles, dots, hexagons and other geometric patterns called matrix codes that can encode much larger amounts of information than a typical 1D barcode. In general, a linear barcode is composed of a leading margin, start character, message characters, check character (if any), stop character, and a trailing margin. Based on this framework, all known symbologies constitute their own encoding principles. In 1D barcodes, the bars represent the binary digits 0 and 1 that may constute various sequences to encode numbers from 0 to 9 and then be processed by a digital unit. The presence or absence of a bar of a particular width in a specific position in a sequence is read by the computer as 1 or 0.  
  
**Key Barcode Properties**  
In substance, barcode symbologies are similar to file formats, as they define the following key barcode properties:
- [Data encryption format](#dataencryption)
- [Data density](#datadensity)
- [Shape](#shape)
- [Recognition precision](#precision)
  
**Supported Symbologies** 
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
***Aspose.BarCode for .NET*** supports nearly all widely used barcode symbologies. In general, to generate a barcode image, it is necessary to use the *BarcodeGenerator* class with two main parameters to be initialized: data contents to be encoded *CodeText* and barcode symbology *EncodeType*.
Barcode generating classes, such as *LinearBarCode* and *BarCodeGeneratorControl*, have a common property called *EncodeType* that is used to define the symbology of a barcode. Developers can assign any symbology to the *SymbologyType* property out of pre-defined barcode types supported by the *BarcodeGenerator* class. However, it must be noted that not all barcode symbologies enable generating barcodes with code text in a required format due to the limitations of a barcode type itself.  

**Code39**  
*Code39* is a barcode symbology with variable length. Its specification is limited to 43 characters, including uppercase letters (A through Z), numeric digits (0 through 9) and a number of special characters (-, ., $, /, +, %, and space). An additional character (denoted ‘*’) is used for both start and stop delimiters. Each character is composed of nine elements: five bars and four spaces. This symbology has low data density and does not allow ensuring recading accuracy as it does not have a checksum required by default. 
The code snippet provided below illustrates how to generate a barcode in Code39. 
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code39Extended, "$&This Code#*");
gen.Save($"{path}Code39Extended.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="Code39Extended.png"></p>

QR Code
QR Code is a 2D symbology that is used to encode long strings of alphanumeric data, typically text or a URL. A QR code is composed of an array of black and white squares that can be read by smartphones and other readers.  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Aspose常に先を行く");
gen.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.ECIEncoding;
gen.Parameters.Barcode.QR.QrECIEncoding = ECIEncodings.UTF8;
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}QrCode.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="QrCode.png"></p>

## Data Encryption Formats
<a name="dataencryption"></a>

Different barcode symbologies have different underlying data encryption approaches and capabilities. Some barcode specifications can be used to encode only numerical sequences so that barcode label size and the amount of data to be encoded are predefined for each symbology. Other barcodes imply encoding only digits or a limited set of characters and digits, while others can accept any byte sequence without limitations. 

**EAN+13**
EAN-13 is the most commonly recognized barcode in Europe, used in supermarkets and other retail establishments for basic product identification. As their name implies, EAN-13 barcodes store a total of 13 digits, as opposed to UPC-A codes, which store 12. The first two digits are the GS1 Prefix, which identify the product's country of origin. Then is a five digit company number, to identify the brand, followed by a five digit item number, to identify the product itself. After that, there is a check number, to ensure the code's accuracy. Finally, there is a > symbol, indicating a "quiet zone," which signifies the end of the barcode.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN13, "1234567890128");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Save($"{path}Ean13.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="Ean13.png.png"></p>

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code11, "1234-5678");
gen.Save($"{path}Code11.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="Code11.png"></p>

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.GS1Code128, "(02)04006664241007(37)1");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Save($"{path}GS1Code128.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="GS1Code128.png"></p>

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Save($"{path}Pdf417.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="Pdf417.png"></p>

## Data Density
<a name="datadensity"></a>

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code93Extended, "$&This Code#*");
gen.Save($"{path}Code93Extended.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="Code93Extended.png"></p>

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}DataMatrix.png", BarCodeImageFormat.Png);
{{< /highlight >}}

<p align="center"><image src="DataMatrix.png"></p>


## Barcode Shapes
<a name="shape"></a>

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Åspóse.Barcóde©");
gen.Parameters.Barcode.QR.QrEncodeType = QREncodeType.ForceMicroQR;
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}MicroQR.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="MicroQR.png"></p>

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
//Compact version of Pdf417
gen.Parameters.Barcode.Pdf417.Pdf417Truncate = true;
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Save($"{path}CompactPdf417.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="CompactPdf17.png"></p>

## Barcode Recognition Precision
<a name="precision"></a>

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Interleaved2of5, "1234567890");
gen.Save($"{path}Interleaved2of5.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="Interleaved2of5.png"></p>

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Aztec, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}AztecFull.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="AztecFull.png"></p>

## Postal Symbologies 