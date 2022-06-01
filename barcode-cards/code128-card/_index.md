---
title: Code 128
type: docs
description: ""
key words: ""
weight: 120
url: /barcode/code128-card/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/code128) and [Generate](https://products.aspose.app/barcode/generate/code128) Code 128 barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
Code 128 is an efficient, high-density linear (1D) barcode type that allows encoding alphanumeric information. It includes verification protection both via a checksum digit and byte parity checking. Code 128 was invented in 1981 by Ted Williams of Laserlight Corporation to solve the problem of representing both alphabetic and numeric characters without sacrificing barcode density. This symbology has been widely implemented in many applications where a relatively large amount of data must be encoded in a relatively small amount of space. Its specific structure also allows numeric data to be encoded at, effectively, double-density. Today, Code 128 is one of the most widely used barcode types, for example for warehouse management, in the transport industry (e.g. by UPS or DHL) and in retail and non-retail environments, such as library books, membership cards, small items, etc.  
  
The specification for Code 128 is available in standard ISO/IEC 15417:2007.


<p align="center"><img src="code128.png"></p>

## **Features**
  
### **Encoding Character Set**
Code 128 supports encoding symbols from the full ASCII 128 character set.
Three different code sets or sub types are defined for Code 128 (namely Code 128 A, Code 128 B, and Code 128 C) that determine how the code is interpreted by the barcode scanner. The code sets differ in compactness and encodable character set.

<details> 
<summary>Read more</summary>

Code 128 A: all numeric values (0-9), uppercase alphabetic characters (A-Z), punctuation marks, seven special characters, and "control" characters (ASCII values 00 through 95)
Code 128 B: all numeric values (0-9), uppercase and lowercase alphabetic characters (A-Z, a-z), punctuation marks, and seven special characters (ASCII values 32 through 127)
Code 128 C: all numeric digit pairs from 00 through 99 and three special characters. This code set is numeric-only, but any one character actually represents two digits

The code set to use is indicated to the scanner by the start symbol or start character. Also available are various mode switching or shift characters to switch from one set to another within a barcode symbol. Usually the sub type selection and switching within a symbol is handled by the barcode software that creates the code.
  
</details>

### **Structure**
A Code 128 barcode has seven sections:

- Quiet zone
- Start symbol
- Encoded data
- Check symbol (mandatory)
- Stop symbol
- Final bar (often considered part of the stop symbol)
- Quiet zone

Each symbol in the barcode is composed of three bars and three spaces. Each bar or space is 1, 2, 3 or 4 units wide, the sum of the widths of bars must be even (4, 6 or 8 units), the sum of the widths of the spaces must be odd (3, 5 or 7 units), and total 11 units per symbol.

<details>  
<summary>Read more</summary>

For instance, encoding the ASCII character "0" can be viewed as 10011101100, where 1 corresponds to a bar and 0 to a space. A single 1 would be the thinnest line in the bar code. Three 1's in sequence (111) indicates a bar three times as thick as a single 1 bar.

There are 108 possible 11-unit wide symbols, and the code uses all possible symbols. Two of the symbols are used for stop (end-of-barcode) indication, stop and reverse stop. The two stop symbols are special because they are always followed by a 2-unit bar, forming a 13-unit long stop pattern. Reading the stop pattern left to right is the stop symbol (followed by a 2-unit bar), and reading the stop pattern right to left is the reverse stop symbol (followed by a 2-unit bar).
  
</details>

### **Size Dimentions**
The recommended minimum symbol height for manual scanning is 5.0 mm or 15 percent of the symbol width (excluding quiet zones), whichever is greater. The quiet zones must be at least 10X wide, where "X" is the current X dimension. The most basic unit of measure within a barcode is the x-dimension and is equivalent to the width of the most narrow bar or space within the barcode.  Each character is 11 x-dimensions wide (except for the STOP character which is 13 wide).  The minimum size of the x-dimension is 0.0075 inches.  The overall length of a barcode varies because the number of DATA characters may vary.

### **Encoding Capacity and Data Density**
Code 128 is a variable length code, which in principle can encode an arbitrary length of data. The practical content limit for Code 128 is at 30 characters (large cap and small cap letters) or a maximum of 60 digits (purely numeric code). Code-128 can be very compact due to the "double-density compression" of data, when two numbers are written into one barcode modulus, which makes encoding long strings of digits much more efficient.

### **Checksum Controls**
Code 128 requires adding a mandatory check digit to detect errors. Chechsum calculation is based on the modulo 103 algorithm. It is calculated by summing the start code 'value' to the products of each symbol's 'value' multiplied by its position in the barcode string. The start symbol and first encoded symbol are in position 1. The sum of the products is then reduced modulo 103. The remainder is then converted back to one of the 103 non-delimiter symbols (following the instructions given below) and appended to the barcode, immediately before the stop symbol.


## **Advantanges and Limitations**
For 1D barcodes, Code 128 is generally the most compact (able to encode the most data in the smallest physical space).  The amount of data is variable allowing the user to encode as much or as little data as is needed.  And finally, it maintains a high level of data integrity with parity bits to verify each character and a check character to verify the data package as a whole.

As CODE 128 uses 4 types of bar size, printers with high print quality are required. CODE 128 is not suitable for printing with dot matrix printers and FA ink-jet printers and for flexographic printing on corrugated cardboards. 

## **Aspose Samples for Code 128 Generation and Recognition**
### **Code 128 Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//GENERATE
{{< highlight csharp>}}
//generate Code128 Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "Aspose"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Save($"{path}Code128.png", BarCodeImageFormat.Png);
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

### **Code 128 Limited Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//RECOGNIZE
{{< highlight csharp>}}
//recognize Code128 Barcode
using (BarCodeReader read = new BarCodeReader($"{path}Code128.png", DecodeType.Code128))
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
