---
title: Working with Symbologies
type: docs
weight: 10
url: /net/working-with-symbologies/
---
This articles introduced general information about barcode symbologies and describes key barcode properties illustrated by sample barcode labels and code snippets used to generated barcodes of different types. 

## Overview
A barcode is a graphical code composed of parallel lines and spaces of different widths combined together in a visual pattern to encode data. After being generated and printed out, barcodes get placed on scannable surfaces. Barcodes have been introduced as machine-readable tags to enable fast automatical information fetching from graphic data. Usually, a barcode may correspond to approximately 25 characters for 1D types or 2,000 for 2D ones. The more characters are inputted to encode, the bigger is the generated barcode.
  
### Barcodes vs RFID
To recognize barcodes, using a light beam is required to identify black and white lines in a barcode label. Scanners rely on sensors that emit signals, as well as decoders that interpret signals into text and then send decoded information to a database. Barcode scanners require the line-of-sight visibility and need to observe one barcode at a time to read the data.   
Radio-frequency identification (RFID) may be considered as an alternative to barcode systems. This technology implies using radio waves to transmit data captured from RFID tags to RFID readers for interpretation. Such a tag uses a sensor fixed on an antenna to enables data transmission to a reader. Sensors usually have unique ID so that one reader can scan multiple tags simultaneously without requesting the line-of-sight visibility.  
Summing up, RFID is more efficient when there is a need to scan a large number of items at once, but such systems are more expensive and require more sophisticated setup than barcode ones. Moreover, there are physical limitations to use RFID, such as, for example, working with metals or liquids. In turn, barcode systems are deemed more accurate than RFID. Even though they do not allow scanning multiple items at once, the use of barcodes ensures better accuracy and reliability owing to precise capturing only required items.

### Barcode Usage
Barcode usage: retail, industry, healthcare, pharmacy, post and delivery, documentation management, and many others. Businesses use barcodes in the following ways:
- *Inventory tracking*. A basic inventory tracking system consists of software and a barcode scanner or mobile computer. Inventory items (like products you sell, supplies, or raw materials) will all have barcode labels, so when you remove an item from stock, you just scan the barcode to reduce the available count in your inventory tracking software, instead of having to type in a SKU.
- *Asset tracking*. Any business, no matter how large or small, has IT assets and fixed assets. Barcoded asset tags are attached to each individual asset, and can be scanned to check items in or out in your asset tracking software. It is a great way to improve accountability and makes audits much easier.
- *Billing and invoice management*. Add a barcode that represents the customer number or the individual invoice number so when it’s returned with payment, you can easily locate the customer account or invoice number. This will prevent problems like applying payments to the incorrect customer account or invoice.
- *Organizing admission desks*. Movie theatres, event venues, travel tickets, etc have tickets with barcodes and they use scanners to verify the ticket and admission process. Using this in the events gives easy access to the database captured and track the revenue. At times, this also reduces the ticket printing costs for event organizing committees. Instead of printing the show tickets, they use the barcode at the venue. Today, online travel ticket bookings and boarding passes have barcodes that can be scanned easily.
- *Storing business and personal data*. QR codes are widely used to store information about organizations or persons.  

### Barcode Advantages 
The main advantage of barcode systems is that they allow users to process detailed information at the moment the barcode is scanned, rather than simply storing information for later processing.
Barcode systems can be used to track products, prices, and stock levels for centralized management in a computer software system allowing for incredible increases in productivity and efficiency. 
Barcodes were developed to improve the speed of sales transactions, but there are other potential benefits to businesses, including: 

- Better accuracy - Relying on a barcode to process data is far more accurate than relying on manually-entered data, which is prone to errors.
- Data is immediately available - Because of the processing speed, information about inventory levels or sales is available in real time.
- Reduced training requirements - Thanks to the simplicity of the barcode scanner, employees need little in the way of training in how to use it. Additionally, thanks to barcodes, there is much less for employees to have to learn and retain.
- Improved inventory control - Being able to scan and track inventory yields a much more accurate count, as well as a better calculation of inventory turn. Companies can hold less inventory when they know how soon they will need it.
- Low cost implementation - Generating barcodes is quick and easy, as is installing a barcode system. Potential savings can be realized almost immediately.

## Symbology Definition
Barcode symbology defines the way of encoding information into the barcode image. Each barcode symbology relies on a unique way of encoding data characters. One-dimensional (1D), or linear, barcodes represent data by varying the width and spacing of parallel lines.  In general, a linear barcode is composed of a leading margin, start character, message characters, check character (if any), stop character, and a trailing margin. Based on this framework, all known symbologies constitute their own encoding principles. In 1D barcodes, the bars represent the binary digits 0 and 1 that may constute various sequences to encode numbers from 0 to 9 and then be processed by a digital unit. The presence or absence of a bar of a particular width in a specific position in a sequence is read by the computer as 1 or 0.  
Later, two-dimensional (2D) barcodes have been introduced.
  
2D barcodes are more complex and can include not only text data but also other types of information: price, quantity, web address, or image. They can be composed of rectangles, dots, hexagons and other geometric patterns called matrix codes that can encode much larger amounts of information than a typical 1D barcode. By storing data both horizontally and vertically to form a square or rectangle, significantly more information can be encoded than is possible with a 1-D barcode. The 2-D symbology is known for high readability and resistance to poor printing; they contain redundant data so even if one or more cells are damaged, the code is still readable. 
  
### Key Barcode Properties 
In substance, barcode symbologies are similar to file formats, as they define the following key barcode properties:
- [Data encryption format](#dataencryption). Some barcode types are capable of encoding only numbers, only main characters with specific symbols, or entire encodings.
- [Data density](#datadensity)
- [Shape](#shape). It can be rectangular, square, or suitable for long linear spaces.
- [Recognition precision](#precision). Some barcode types do not include checksum and its controls, and accordingly, it is impossible to verify whether all data contained in a barcode have been recognized and decrypted correctly. Such barcodes have low recognition precision. In contrats, 2D barcodes not only allow recovering partially corrupted data, but also have high recognition precision because they provide mechanisms to guarantee that all barcode data have been read properly. 
  
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
***Aspose.BarCode for .NET*** supports nearly all widely used barcode symbologies. In general, to generate a barcode image, it is necessary to use the *BarcodeGenerator* class with two main parameters to be initialized: data contents to be encoded *CodeText* and barcode symbology *EncodeType*.
Barcode generating classes, such as *LinearBarCode* and *BarCodeGeneratorControl*, have a common property called *EncodeType* that is used to define the symbology of a barcode. Developers can assign any symbology to the *SymbologyType* property out of pre-defined barcode types supported by the *BarcodeGenerator* class. However, it must be noted that not all barcode symbologies enable generating barcodes with code text in a required format due to the limitations of a barcode type itself.  
  
**Code39**    
*Code39* is a barcode symbology with variable length. Its specification is limited to 43 characters, including uppercase letters (A through Z), numeric digits (0 through 9) and a number of special characters (-, ., $, /, +, %, and space). An additional character (denoted ‘*’) is used for both start and stop delimiters. Each character is composed of nine elements: five bars and four spaces. This symbology has low data density and does not allow ensuring recading accuracy as it does not have a checksum required by default. 

<p align="center"><image src="Code39Extended.png"></p>
  
The code snippet provided below illustrates how to generate a barcode in Code39.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code39Extended, "$&This Code#*");
gen.Save($"{path}Code39Extended.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
  
**QR Code**  
QR Code is a 2D symbology that is used to encode long strings of alphanumeric data, typically text or a URL. A QR code is composed of an array of black and white squares that can be read by smartphones and other readers. QR-Code is a two-dimensional (2D) barcode type similar to Data Matrix or Aztec, which is capable of encoding large amounts of data. QR means Quick Response, as the inventor intended the symbol to be quickly decoded. The data encoded in a QR-Code may include alphabetic characters, text, numbers, double characters and URLs. The symbology uses a small area of square modules with a unique perimeter pattern, which helps the barcode scanner determine cell locations to decode the symbol. 

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
   
**EAN 13**  
EAN-13 is the most commonly recognized barcode in Europe, used in supermarkets and other retail establishments for basic product identification. As their name implies, EAN-13 barcodes store a total of 13 digits, as opposed to UPC-A codes, which store 12. The first two digits are the GS1 Prefix, which identify the product's country of origin. Then is a five digit company number, to identify the brand, followed by a five digit item number, to identify the product itself. After that, there is a check number, to ensure the code's accuracy. Finally, there is a > symbol, indicating a "quiet zone," which signifies the end of the barcode.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN13, "1234567890128");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Save($"{path}Ean13.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="Ean13.png"></p>

**Code 11**  
Code-11 is a barcode symbology developed by Intermec in 1977 and used mainly in telecommunications. The symbol can encode a string of any length (though Labeljoy limits it to 255 characters), consisting of the digits 0-9 and the dash sign (-). One or two check digit(s) can be included.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code11, "1234-5678");
gen.Save($"{path}Code11.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="Code11.png"></p>

**GS1 Code128**  
GS1-128 (formerly UCC/EAN-128) is a variant of Code 128, which can encode all ASCII alphanumeric characters in barcode format. GS1-128 defines both data types and formats that are used for exchange and logistics between entities. Companies use this barcoding format to share company, product, and shipping information. 
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.GS1Code128, "(02)04006664241007(37)1");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Save($"{path}GS1Code128.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="GS1Code128.png"></p>

**PDF17**  
The PDF417 barcode is a two-dimensional (2D), high-density symbology capable of encoding text, numbers, files and actual data bytes. This FAQ provides information and answers to commonly asked questions. Large amounts of text and data can be stored securely and inexpensively when using the PDF417 barcode symbology. The printed symbol consists of several linear rows of stacked codewords. Each codeword represents 1 of 929 possible values from one of three different clusters. A different cluster is chosen for each row, repeating after every three rows. Because the codewords in each cluster are unique, the scanner is able to determine what line each cluster is from. PDF417 uses Reed Solomon error correction instead of check digits. This error correction allows the symbol to endure some damage without causing loss of data. AIM standards recommend a minimum error correction level of 2. The error correction level depends on the amount of data that needs to be encoded, the size and the amount of symbol damage that could occur. 
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Save($"{path}Pdf417.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="Pdf417.png"></p>

## Data Density
<a name="datadensity"></a>

**Code93**  
The Code 93 barcode is an updated, more secure and compact version of the Code 39 barcode, which is able to read both letters and numbers. It is used in the military and automotive fields, as well as by Canada Post to encode special delivery information. The Code 93 barcode is an updated, more secure and compact version of the Code 39 barcode, which is able to read both letters and numbers. It is used in the military and automotive fields, as well as by Canada Post to encode special delivery information. Unlike Code 39, Code 93 is not self-checking and, as such, requires a check digit.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code93Extended, "$&This Code#*");
gen.Save($"{path}Code93Extended.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="Code93Extended.png"></p>

**Data Matrix**  
A Data Matrix is a 2D matrix code, capable of encoding very large amounts of data in a compact space. Data Matrix codes are made up of small black and white squares that form a big square or rectangle. They're used in a variety of industries, including aerospace, component labeling, food and beverage, pharmaceutical, defense, mail, and printed media because those organizations often run complicated operations where tracking and traceability is critical. A Data Matrix is capable of encoding up to 2,335 alphanumeric characters, or up to 3,116 numerical characters. It is composed of several blocks of black and white cells, that form a square or rectangular pattern. Each Data Matrix has a perimeter finder and a timing pattern. It can also encode symbols of various sizes, both large and small. Along the edges of each data matrix code is a quiet zone. A Data Matrix barcode is designed to be read even when it's up to 30% damaged, due to a built in error correction system. It's also capable of encoding either letters, numerical data, or other ASCII characters. Data Matrix codes can be read with image-based barcode readers or mobile devices; a lower resolution is acceptable for scan readability in any position.

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}DataMatrix.png", BarCodeImageFormat.Png);
{{< /highlight >}}

<p align="center"><image src="DataMatrix.png"></p>


## Barcode Shapes
<a name="shape"></a>

**MicroQR**  
A major feature of Micro QR Code is it has only one position detection pattern, compared with regular QR Code that require a certain amount of area because position detection patterns are located at the three corners of a symbol. Furthermore, QR Code requires at least a four-module wide margin around a symbol, whereas a two-module wide margin is enough for Micro QR Code. This configuration of Micro QR Code allows printing in areas even smaller than QR Code. There are four different versions (sizes) of Micro QR codes: the smallest is 11×11 modules; the largest can hold 35 numeric characters.

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Åspóse.Barcóde©");
gen.Parameters.Barcode.QR.QrEncodeType = QREncodeType.ForceMicroQR;
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}MicroQR.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="MicroQR.png"></p>

**Compact PDF417**    
Compact PDF417 is used when space considerations are a main concern and symbol damage is unlikely.
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
//Compact version of Pdf417
gen.Parameters.Barcode.Pdf417.Pdf417Truncate = true;
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Save($"{path}CompactPdf417.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

<p align="center"><image src="CompactPdf417.png"></p>

## Barcode Recognition Precision
<a name="precision"></a>

**Interleaved 2 of 5**
Interleaved 2 of 5 (ITF) barcodes are two-width numeric codes that can encode information of any length, as long as there is an even number of digits in the code. Information is encoded based on the width of the bars and spaces, and exactly 2 out of every 5 bars are wide. Their predecessor, the Standard or Industrial 2 of 5 barcode, could encode information only in the width of the bars, but not the spaces. ITF barcodes are generally used for distribution and warehouse identification purposes. They are often used to identify cartons or crates which themselves contain items with their own UPC barcodes. Additionally, they are often used to label 135 film. The Interleaved 2 of 5 barcode begins with a start character, to indicate the beginning of the code. Then comes the encoded data, followed by an optional check digit, and the stop character. The ITF barcode can only encode an even number of digits, since each character is made up of two interleaving digits. If a code has an odd number of digits, a zero is added to the front of the barcode. Additionally, it is self-checking and does not require a check digit, though one can be added.

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


