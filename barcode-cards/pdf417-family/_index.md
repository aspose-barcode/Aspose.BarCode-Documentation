---
title: PDF417 Family
description: ""
key words: ""
type: docs
weight: 30
url: /barcode/pdf417-cards/
---

{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/pdf417) and [Generate](https://products.aspose.app/barcode/generate/pdf417) PDF417 barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

PDF417 (Portable Data File 417) is a family of 2D stacked barcode types introduced to store large amounts of data in relatively small barcodes. Here, "417" denotes the approach used to encode a single digit: 4 bars and 4 spaces constituting a 17-module pattern. This symbology can be used to encode both streams of bytes and Unicode symbols. PDF417 enables the extended format of metadata that allows splitting one portion of data into several labels and then include them in a printed document to re-assemble later. PDF417 supports laser scanning for high-quality documentation. The PDF417 specification is summarized in the [ISO/IEC 15438](https://www.iso.org/standard/43816.html) document.

## **Overview**
Basic PDF417 is a high-density variable-length barcode type supporting error correction. It allows encoding textual data, numerical digits, files, and streams of bytes. PDF417 suggests stacking many linear rows together thus increasing the amount of information that can be encoded compared to linear symbologies. PDF417 barcodes can be read by linear scanners, raster laser scanners, or special imaging devices. The shape of PDF417 barcode labels is rectangular. The size of a symbol can be customized according to specific business needs. It is important to maintain appropriate printing accuracy and suitable printer resolution to create high-quality barcode images. 
  
<p align="center"><img src="pdf417basic.png"></p>

{{% alert color="primary" %}}You can find the detailed description of classes and properties that are used in ***Aspose.BarCode for .NET*** for PDF417 generation and recognition:
- [**PDF417 in Aspose.BarCode for .NET**](/barcode/net/pdf417-and-macropdf417-barcode/)

{{% /alert %}} 

## **Features**
### **Encoding Character Set**
The PDF417 specification uses the base 929 encoding in which each codeword represents a number from 0 to 928. Among 929 available codewords, 900 are intended to encode input data, and 29 correspond to special functions, such as shifting between major modes. PDF417 enables encoding both byte streams and Unicode symbols. It can be used to encode all 256 ASCII characters and 8-bit binary data.  
PDF417 applies data compaction schemes to improve encoding efficiency. The following modes are provided to establish interrelations between input data and codeword sequences. It is possible to switch between different modes within one PDF417 barcode:
- Text Compaction mode: encoding all printable ASCII characters and selected special characters
- Byte Compaction mode: encoding all 256 possible 8-bit byte values including all ASCII characters with values from 0 to 127
- Numeric Compaction mode: efficient encoding of numerical digits

<details>  
<summary>Read more</summary>

The three major modes encode different types of data in different ways, and can be mixed as necessary within a single bar code:

- Byte: each group of 5 code words represents 6 bytes. (Because 9005 > 2566.) Additional bytes are encoded one per code word.
- Numeric: n digits are encoded in ⌊n/3⌋+1 code words, up to a maximum of 44 digits in 15 code words.
- Text: Each code word represents two base-30 digits, which are used by a system of four submodes to represent the printable ASCII characters (plus CR, LF and HT):
- Uppercase: A–Z, SP, Change to lowercase, Change to mixed, Interpret next digit as punctuation
- Lowercase: a–z, SP, Interpret next digit as uppercase, Change to mixed, Interpret next digit as punctuation
- Mixed: 0–9, &, CR, HT, comma, :, #, -, period, $, /, +, %, *, =, ^, Change to punctuation, SP, Change to lowercase, Change to uppercase, Interpret next digit as punctuation
- Punctuation:  ;, <, >, @, [, \, ], _, `, ~, !, CR, HT, comma, :, LF, -, period, $, /, ", |, *, (, ), ?, {, }, ', Change to uppercase

</details>

### **Structure**
The layout of PDF417 barcodes includes rows and columns. PDF417 encodes information in codewords that are stacked in columns to compose machine-readable patterns. A PDF417 printed label includes several linear rows of stacked codewords. PDF417 barcodes may include from 3 to 90 rows, each of which is like a small linear barcode. All rows have the same width; each row contains the same number of codewords. Codewords are denoted as patterns of dark (bar) and light (space) regions. Each of these patterns contains four bars and four spaces. The total width is 17 times the width of the narrowest allowed vertical bar (the X dimension). Each pattern starts with a bar and ends with a space. The row height must be at least 3 times the minimum width: Y ≥ 3 X.

<p align="center"><img src="pdf417structureorig.png"></p>

<details>  
<summary>Read more</summary>
 
Each character consists of 17 modules arranged into four bars and four spaces. The entire set of characters is divided into three mutually exclusive codeword sets (clusters). Each cluster encodes 929 supported character values (codewords) with distinct bar-space patterns so that one cluster can be clearly distinguished from another.  
  
Each row in a PDF417 barcode includes:
- Starting quiet zone
- Start pattern that determines the PDF417 format
- Left-row codeword that encodes information about the row (its number and the error correction level)
- Data codewords (from 1 to 30) that store input data
- Right-row codeword that encodes additional information about the row
- Stop pattern
- Closing quiet zone
  
</details>

### **Size Dimentions**
The size of a PDF417 barcode depends on the amount of information to be encoded. The height of any PDF417 symbol can range from 3 to 90 rows, and the row height can range from 1X to 10X, where "X" is the current X dimension. The width of a symbol can range from 90X to 583X. A minimum quiet zone of 2X is required on all sides.
In practice, a PDF417 symbol takes about four times the placement space of a DataMatrix or a QR Code. 

As the number of rows can change, and rows themselves are variable in length (the number of character "columns"), the height/width proportion (aspect ratio) of PDF417 barcodes may vary to comply with spatial printing limitations. However, the number of characters in all rows must be equal. 

<details>  
<summary>Read more</summary>

The X dimension is the width of the narrowest bar in a printed codeword. The Y dimension is the height of each row. The X dimension must be constant within a single PDF417 barcode. PDF417 labels are usually printed out with the aspect ratio that may range from 1:2 to 1:5, with 1:3 being the most widely used. Significant space can be saved as a result of decreasing the aspect ratio; however, some scanners do not support reading barcodes with aspect ratios of less than 1:3. 
  
</details>

### **Encoding Capacity and Data Density**
The basic PDF417 standard can encode up to 1,108 bytes or 1,850 alphanumeric (2,710 numerical) symbols in up to 30 columns and 90 rows.  
Due to internal data compression algorithms, the exact data capacity depends on the structure of information to be encoded. It is recommended to limit the amount of data in each symbol to 800 characters or less, using 20 columns or less. 

<details>  
<summary>Read more</summary>

The amount of data that can be encoded will vary depending upon the type of data, the compaction type, the error correction level chosen and the limitation of the scanner being used. For example, in the text compaction mode, the amount of compaction varies due to mode switching between different types of characters, such as between numbers, upper case, lower case and punctuation. In addition, many PDF417 scanners cannot accurately read more than 850 characters, and some scanners are limited to only 300 characters.  

</details>

### **Error Correction**
PDF417 uses the Reed-Solomon algorithm, which enables the code to be read even if up to 50% of it is damaged. Such barcodes include additional information for data recovery through Reed-Solomon error correction. When the PDF417 symbol is created, from 2 to 512 error detection and correction codewords are added. When the symbol is scanned, the maximum number of corrections that can be made is equal to the number of codewords added, but the standard recommends that two codewords be held back to ensure reliability of the corrected information. The error correction level is adjustable by the user between level 0 (just error detection) and level 8 (maximum error correction). Recommended error correction levels are between level 2 and 5, but the optimal value depends on amount of data, printing quality of the PDF417 symbol and decoding capabilities.

<details>  
<summary>Read more</summary>

Error correction identifies two types of errors: 1) rejection errors (so-called erasures) and 2) substitution errors (so-called errors). An erasure is a missing, unscanned, or unreadable character where the position of a character is known but not its value. An error is an incorrectly decoded or mislocated symbol character where both the position and value of a character is unknown.  
  
</details>

## **Advantages and Weaknesses**
PDF417 allows encoding large amounts of text and information securely and efficiently. PDF417 barcodes can be read from left to right in a linear order by simple linear scanners. PDF417 provides a means for low-cost data transmission in a wide variety of applications. In addition to typical features of 2D symbology, PDF417 provides the following benefits:
- Linking. PDF417 barcodes can be linked to other PDF labels and then scanned in a sequence increasing the amount of information to be stored
- User-specified dimensions. Users can determine the required the narrowest vertical bar heigh (X-dimension) the highest row width (Y dimension)
- Public domain format. This specification can be implemented without any license
  
PDF417 has many applications, such as: government-issued identification cards (such as driver licenses), airline boarding passes, postage stamps, package labels, and many others. 

## **Aspose Samples for Basic PDF417 Generation and Recognition**
### **Basic PDF417 Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//GENERATE
{{< highlight csharp>}}
//generate PDF417 Basic Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    //set 3 columns
    gen.Parameters.Barcode.Pdf417.Columns = 3;
    //set error level 2
    gen.Parameters.Barcode.Pdf417.Pdf417ErrorLevel = Pdf417ErrorLevel.Level2;
    gen.Save($"{path}PDF417Basic.png", BarCodeImageFormat.Png);
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

### **Basic PDF417 Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//RECOGNIZE
{{< highlight csharp>}}
//recognize PDF417 Basic Barcode
using (BarCodeReader read = new BarCodeReader($"{path}PDF417Basic.png", DecodeType.Pdf417, DecodeType.CompactPdf417, DecodeType.MacroPdf417))
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
