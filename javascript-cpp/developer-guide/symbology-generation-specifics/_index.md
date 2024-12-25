---
title: Barcode Generation Specifics in JavaScript
linktitle: Barcode Generation Specifics
type: docs
description: "Description of Various Barcode Types Supported in Aspose.BarCode for JavaScript via C++"
keywords: "Generate Barcodes, Barcode Types, Barcode Symbology, How to Generate Barcodes in JavaScript .NET, Barcode types in Aspose.BarCode for JavaScript via C++, 2D Barcodes, Linear Barcodes, 1D Barcode, Postal Barcodes, Generate QR, QR Code, Generate Code 39, Generate PDF 417, Generate Micro QR Code, Generate Data Matrix"
weight: 20
feedback: BARCODECOM
url: /javascript-cpp/generate-barcode-types/
---
## Introduction
This section provides an overview of barcode symbologies, their key properties, and examples of barcode labels and code snippets for generating various barcode types.

## Overview
A barcode is a visual code made up of parallel lines, spaces of varying widths, or other shapes arranged in a pattern to represent data. Once generated and printed, barcode labels are placed on surfaces for scanning. Barcodes are machine-readable tags designed for quick data retrieval from visual patterns. A single barcode can encode about 25 characters for 1D types or up to 2,000 characters for 2D types. The more characters a barcode holds, the larger its size.

{{% alert color="primary" %}}*For any questions or clarifications, please contact [Aspose Technical Support](/barcode/javascript-cpp/technical-support/). Join discussions at the [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or reach out to [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

### Barcodes vs RFID
Barcodes are read by sensors in scanners that emit light beams to detect the black and white lines in the barcode label. These scanners require a line-of-sight to scan one barcode at a time and convert the light signals into readable text.

RFID (Radio-Frequency Identification) is an alternative technology that uses radio waves to transfer data from RFID tags to readers. RFID tags have sensors with unique IDs, allowing a reader to scan multiple tags simultaneously without line-of-sight.

RFID systems are more suitable for scanning large quantities of items but come with higher costs and more complex setups. They also have limitations when used with metals or liquids. Barcodes, on the other hand, provide higher accuracy and reliability, as they ensure precise data reading, even if they cannot scan multiple items at once.

### Barcode Usage
Barcodes are used in a variety of industries, including retail, healthcare, logistics, pharmacy, documentation management, and more. Below are examples of common business applications for barcodes:

- **Inventory tracking**: This involves using barcode scanners or mobile devices paired with specialized software. Each item is tagged with a unique barcode, allowing for easy tracking of all operations related to that item.
- **Asset tracking**: Businesses often need to manage assets efficiently. Placing barcode tags on assets and scanning them helps track and manage these items, improving accountability and simplifying audits.
- **Billing and invoice management**: Barcodes can be linked to customer numbers or invoice identifiers, making it easy to access and process customer or invoice data.
- **Admission management**: Tickets for events, travel itineraries, and similar documents can have barcodes for quick verification, speeding up admission processes and reducing printing costs.
- **Data storage**: Barcodes, especially QR codes, are commonly used to store business and personal information. Smartphones can easily read these barcodes, providing fast and straightforward access to data.

## Barcode Type Definition
Barcode types determine how data is encoded within the barcode image. Each type uses a unique method for encoding characters.

**One-dimensional (1D)** barcodes, or linear barcodes, encode data by varying the width and spacing of parallel lines.

**Two-dimensional (2D)** barcodes were developed to overcome the limitations of 1D barcodes. They use patterns such as rectangles, dots, hexagons, or other geometric shapes called matrix codes.

**Postal barcodes** refer to specific symbologies used by postal services across different countries. Unlike 1D barcodes, postal barcodes encode data by adjusting the height of bars. This allows them to encode information like ZIP and ZIP+4 codes and delivery addresses, which postal services process using automated scanning equipment.
### Key Barcode Properties
Barcode symbologies share similarities with file formats, as they define essential barcode properties:

- [**Data encoding format**](#dataencoding): Different barcode types have varying capabilities for encoding characters. Some can only encode numerical digits, others can handle alphabetic and special characters, while others support full encoding sets.
- [**Data density**](#datadensity): Each symbology has a defined capacity for encoding information, resulting in barcodes with either high or low data density.
- [**Shape**](#shape): Barcodes can come in different shapes, such as rectangular, square, or elongated.
- [**Recognition precision**](#precision): Certain 1D barcodes lack checksums and controls, making it difficult to verify that all data has been correctly read and decrypted. This results in lower recognition precision. Conversely, 2D barcodes offer higher recognition precision, as they include mechanisms to recover partially corrupted data and ensure accurate reading.

### Supported Barcode Types
The following are the barcode types supported by ***Aspose.BarCode for JavaScript via C++***.
| **Supported Symbologies** | |
|----------------------------|-----------------------------|
| **1D**                     |                             |
| **Numerical Only**         | Code 11, Code 32, Codabar, Databar Omnidirectional, Databar Stacked Omnidirectional, Databar Limited, Databar Truncated, Databar Stacked, EAN 13, EAN 14, EAN 8, IATA 2-of-5, Italian Post 25, Interleaved 2-of-5, ISBN ISMN, ISSN, ITF 6, ITF 14, Matrix 2-of-5, MSI, OPC, PatchCode, Pharmacode, PZN, SSCC 14, SSCC 18, Standard 2-of-5, EAN 5, EAN 2, UPC-A, UPC-E, UpcaGs1DatabarCoupon |
| **Alpha-Numeric**          | Code 128, Code 39, Code 93, Code 16K, CodablockF, Databar Expanded, Databar Expanded Stacked, GS1 CodablockF, GS1 Code 128, VIN |
| **2D**                     | QR Code, Micro QR Code, PDF417, Compact PDF417, Macro PDF417, Micro PDF417, Aztec, DataMatrix, DotCode, GS1 Data Matrix, GS1 QR Code, MaxiCode, DotCode, Han Xin Code |
| **Postal**                 | Australia Post, Australian Post Parcel, Deutsche Post Identcode, Deutsche Post Leticode, Planet, Postnet, RM4SCC, Singapore Post, Swiss Post Parcel, USPS OneCode |
## **Set Barcode Type in Aspose.BarCode**
***Aspose.BarCode for JavaScript via C++*** supports most widely used barcode symbologies. To generate a barcode image, create an instance of the [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) class and set two main parameters: the data to be encoded in the [*CodeText*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/properties/codetext) property and the barcode type in the [*BarcodeType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/properties/barcodetype) property. The [*BarcodeType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/properties/barcodetype) property specifies the symbology used for generating barcodes. Developers can select any supported symbology from the predefined list in the [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) class. However, not all symbologies support all text formats due to inherent limitations.

### **Code 39**
*Code 39* is a variable-length barcode symbology limited to 43 characters, including uppercase letters (A-Z), numerical digits, and some special characters (-, ., $, /, +, %, and space). Each character is represented by nine elements: five bars and four spaces. This symbology has low data density and does not include a mandatory checksum, which can affect recognition accuracy.

<p align="center"><image src="code39extended.png"></p>

Below is a code snippet to generate a barcode using the *Code 39* symbology.

  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Generate a Code39Extended barcode
var gen = new BarCodeInstance.BarcodeGenerator("Code39FullASCII", "$&This Code#*");
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

gen.delete();

```  
  
## **Data Encoding Formats**
<a name="dataencoding"></a>

Barcode symbologies use different data encoding techniques and have varied capabilities. The barcode label size and the data amount to be encoded are defined for each symbology. Some barcode types can only encode numerical digits or limited character sets, while others can encode any byte sequence without restrictions.

Below, we present examples of different barcode types, such as *EAN 13*, *Code 11*, *GS1 Code 128*, and *PDF417*, which showcase various data densities.

### **EAN 13**
*EAN 13* barcodes are designed to encode only numerical digits. Specifically, the data encoding format for *EAN 13* requires encoding exactly 12 digits, with the 13th digit serving as a control sum calculated based on a specific algorithm.

<p align="center"><image src="ean13.png"></p>

Here's an example code snippet to generate *EAN 13* barcodes.

  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Generate an EAN13 barcode
var gen = new BarCodeInstance.BarcodeGenerator("EAN13", "1234567890128");
gen.Parameters.Barcode.XDimension = "2px";
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

gen.delete();

``` 
  
## Code 11
The *Code 11* symbology supports encoding a string of any length (theoretically unlimited), including numeric digits and the dash (-) character.

<p align="center"><image src="code11.png"></p>

The following code sample shows how to generate a *Code 11* barcode.

  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Generate a Code11 barcode
var gen = new BarCodeInstance.BarcodeGenerator("Code11", "1234-5678");
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

gen.delete();

```
  
## GS1 Code 128
*GS1 Code 128* can encode any ASCII alphanumeric characters, similar to the standard *Code 128* symbology. However, the data encoding format in *GS1 Code 128* follows strict GS1 standards.

<p align="center"><image src="gs1code128.png"></p>

The code example below demonstrates how to create a *GS1 Code 128* barcode.

  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Generate a GS1 Code128 barcode
var gen = new BarCodeInstance.BarcodeGenerator("GS1Code128", "(02)04006664241007(37)1");
gen.Parameters.Barcode.XDimension = "2px";
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

gen.delete();

```
  
  
## Data Density
Data density is a key property of barcode symbologies, indicating how much information can be stored in a single barcode. It is typically low for 1D barcodes and significantly higher for 2D matrix barcodes, with 2D barcodes offering over 10 times more data capacity than 1D symbologies.

## Barcode Shapes
Barcodes can be printed on various surfaces and have different shapes. However, barcodes themselves are typically limited to rectangular or square forms. Using a square barcode in an area meant for a large, rectangular space is not efficient in terms of space usage.

## Barcode Recognition Precision
Sometimes, data read from barcodes can be incorrect. 1D barcodes often do not include a checksum or only have basic error checks, making them more susceptible to errors. In contrast, most 2D barcodes use Reed-Solomon error correction, which helps ensure accurate reading and can recover data from partially damaged barcodes.

### Interleaved 2-of-5
*Interleaved 2-of-5* can encode digit sequences of any length, provided the sequence has an even number of digits. By default, it does not include a checksum, making it possible to read erroneous data.

<p align="center"><image src="interleaved2of5.png"></p>

The code example below shows how to generate an *Interleaved 2-of-5* barcode.

  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Generate an Interleaved 2 of 5 barcode
var gen = new BarCodeInstance.BarcodeGenerator("Interleaved2of5", "1234567890");
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

gen.delete();

```
  
  
## Postal Types
Postal symbologies are specialized barcode types designed exclusively for postal services. They typically have lower data density than 2D barcodes and can encode only numerical characters. Unlike traditional barcodes, postal symbologies often encode information by varying the height of bars. While many postal services are transitioning to widely used 2D barcodes, this change is gradual. ***Aspose.BarCode for JavaScript via C++*** supports key postal symbologies along with 1D and 2D barcodes.

### Postnet
The *Postnet* symbology encodes only digits corresponding to ZIP or ZIP+4 codes using half- and full-height bars, similar to 1D barcodes. Each digit is represented by five bars, two of which are full height.

<p align="center"><image src="postnet.png"></p>

The code example below shows how to generate a *Postnet* barcode.

[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Generate a Postnet barcode
var gen = new BarCodeInstance.BarcodeGenerator("Postnet", "1159628792");
gen.Parameters.Barcode.XDimension = "3px";
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

gen.delete();

``` 

### RM4SCC
*RM4SCC* can encode only digits and uppercase English alphabet characters. It follows 1D barcode parameters, with each character represented by four bars: two extending upward and two downward. This bar arrangement creates 36 possible combinations, representing 10 digits and 26 letters.

<p align="center"><image src="rm4scc.png"></p>

The following code snippet demonstrates how to generate an *RM4SCC* barcode.

   
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Generate an RM4SCC barcode
var gen = new BarCodeInstance.BarcodeGenerator("RM4SCC", "123ABC");
gen.Parameters.Barcode.XDimension = "3px";
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

gen.delete();

``` 


