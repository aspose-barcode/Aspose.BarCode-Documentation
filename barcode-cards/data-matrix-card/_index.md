---
title: DataMatrix Symbology
description: 
key words:
type: docs
weight: 70
url: /datamatrix-card/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/datamatrix) and [Generate](https://products.aspose.app/barcode/generate/datamatrix) DataMatrix barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view the results online.{{% /alert %}}

## Overview
DataMatrix is a highly efficient two-dimensional (2D) barcode symbology that encodes data in graphical symbols composed of square modules with a unique border pattern that facilitates detecting cell locations and further decoding. It is a widespread industrial barcode standard that enables encoding sets of characters and byte streams in square or rectangular barcodes. The normative standards for the DataMatrix symbology are described in the [ISO/IEC 16022:2000]() and [ISO/IEC 24720:2006]() specifications. This symbology supports two main groups of standards that are described further.


<p align="center"><img src="datamatrixcode.png"></p>

<details>  
<summary>Read more</summary>

|DataMatrix Standard|Description|
|---|---|
|ECC 000-140|Outdated standards that enable only square-shaped configuration, use obsolete encoding methods, and provide error correction based on convolutional codes. They are applied only to resolve industrial needs based on legacy specifications|
|ECC 200|Actual standard that allows generating both square and rectangular barcodes, relies on modern encoding methods, and supports Reed-Solomon error correction. It is recommended for use in modern applications|

</details>

## Features
  
### Encoding Character Set
DataMatrix barcodes can be used to encode alphabetical characters, numbers, and bytes of data, including Unicode characters and images. Specifically, this barcode type supports ASCII, ISO, and Extended Binary Coded Decimal Interchange Code (EBCDIC) characters.  
  
More specifically, the DataMatrix standard includes six encoding modes: ASCII, Text, C40, X12, EDIFACT, and Base 256. The ASCII encoding is the most often used one. The encoding and decoding processes are quite complex.
<details>  
<summary>Read more</summary>
There are multiple encoding modes used to store different kinds of information for Data Matrix ECC 200:

- ASCII: Double digit numerics, ASCII values 0 - 127, and Extended ASCII values 128 - 255
- C40: Upper-case alphanumeric, Lower case and special characters
- Text: Lower-case alphanumeric, Upper case and special characters
- X12: ANSI X12 EDI data set
- EDIFACT: ASCII values 32 - 94
- Base 256: All byte values 0 - 255

 
</details>

### Barcode Structure
A DataMatrix code is a 2D code that is made of black and white cells that are typically arranged in a square pattern (although rectangular patterns also exist). Each Data Matrix is comprised of quiet zone, a finder pattern and alignment patterns. And the dimensions of them are decided by X that indicates the horizontal and vertical width of a module. The finder pattern around the perimeter of the symbol consists of a solid line on the left and bottom edges and a pattern of alternating black and white modules along the right and top edges. The data area of DataMatrix codes is surrounded by an L-shaped frame called the alignment pattern and dotted lines called the clock pattern. Readers capture these patterns to determine the position of the code with image processing. Thus, DataMatrix codes can be read from any direction. 
Data Matrix requires a one-module-wide quiet zone on all sides.

<details>  
<summary>Read more</summary>
Data regions that contain square modules in an array
Quiet zone: Surrounds the symbol on all four sides and the minimum quiet zone is originally equal to X.
Finder pattern: Located between the data region and quiet zone. And its width should be the value of X.
Alignment pattern: In larger Data Matrix, this pattern will be presented, whose width should be equivalent to value of 2X.

</details>

### Size Dimentions
The most popular application for Data Matrix is marking small items, due to the code's ability to encode fifty characters in a symbol that is readable at 2 or 3 mm2.
The size of a Data Matrix symbol depends on the amount of data that is entered. If ECC 000-140 is used, the symbol size in modules can be from 9 x 9 to 49 x 49, with an odd number of rows and columns. If ECC 200 is used, the symbol size in modules can be anywhere from 10 x 10 to 144 x 144, with an even number of rows and columns. It is possible for an ECC 200 symbol to have more columns than rows and therefore have a rectangular shape. The Data Matrix Rectangular Extension (DMRE) provides additional rectangular formats like 8x48 or 8x64. 
DataMatrix barcodes can be divided into at most 16 parts if required. Thereafter, the input information still can be reconstructed accurately regardless of the order when those symbols are scanned.

<details>  
<summary>Read more</summary>

DataMatrix includes 24 square formats but only six rectangular formats with a data capacity in the lower range. Specifically small surfaces benefit from rectangular formats; thus resulting in a demand for rectangular versions with higher data volume.
Data Matrix ECC200 configurations can be divided into two categories:
- 24 square symbol configurations sizing from 10x10 to 144x144 (even values only and not including quiet zones);
- 6 rectangular symbol configurations sizing respectively 8x18, 8x32, 12x26, 12x36, 16x36, 16x48 (not including quiet zones).

The actual size of the DataMatrix code is determined by multiplying the symbol size by the printable size of the module.

When the size of the module is 0.25 mm,
- Symbol size: 10 x 10 modules = 2.5 x 2.5 mm
- Symbol size: 32 x 32 modules = 8.0 x 8.0 mm
- Symbol size: 8 x 18 modules = 2.0 x 4.5 mm

</details>

### Encoding Capacity and Data Density
In the maximal configuration, DataMatrix barcodes include 144 rows and columns and contain up to 1,555 bytes or 3,116 numerical (2,335 ASCII) symbols. Data Matrix symbols are printed in square or sometimes a rectangular pattern. Each dot of a Data Matrix symbol represents a bit. This is in contrast to linear bar-codes, where the information is encoded in the ratio of the bars or spaces to each other. Usually a black dot in a Data Matrix symbol is equivalent with the bit-value 1, but Data Matrix may also be printed white on black. Due to internal data compression algorithms the exact data capacity depends on the structure of the data to be encoded. The maximum Data Matrix capacity is also influenced by available printing space and the printer resolution.

<details>  
<summary>Read more</summary>
It is recommended to limit the amount of data encoded in each symbol to 800 characters or less if possible. Although the AIM Data Matrix specifications state, “up to 2335 alpha numeric characters can be encoded,” it has been determined that these numbers are not realistic. The amount of data that can be encoded will vary depending upon the type of data, the encoding mode and what the scanner can read. In most implementations, the amount of data that can be encoded is significantly decreased due to mode switching between different types of characters, such as between numbers, upper case, lower case and punctuation.
</details>

### Error Correction
DataMatrix barcodes include additional information that is used in error correction for data integrity check and data recovery. Owing to this, even severely distorted or damaged barcode labels can be decoded at least partially. The DataMatrix ECC 200 specification relies on the Reed-Solomon algorithm to perform error detection and correction, while ECC 000-140 standards use convolutional error correction. The majority of existing implementations comply with the ECC 200 error correction method endorsed by ANSI/AIM BC11 and the ISO/IEC 16022 specifications. ***Aspose.BarCode*** supports both these standards. 
<details>  
<summary>Read more</summary>
Reed-Solomon error correction allows correcting two types of incorrect codewords: improperly scanned or unreadable character or a incorrectly decoded symbol. 

</details>

## Advantages and Weaknesses
First of all, DataMatrix barcodes are capable of encoding large portions of data in a compact format. DataMatrix allows generating barcode labels that are approximately 30 times smaller than Code 39 ones representing the same amount of data. Moreover, DataMatrix is recommended for use for the purposes of sending barcodes over faxed documents as it allows mitigating various resolution and scanning issues.

<details>  
<summary>Read more</summary>

DataMatrix has been actively used in various spheres, such as defense, healthcare, business, finance, logistics management, and many others. Owing to the fact that the minimal achievable size of a DataMatrix label is the smallest among various barcode types, it is specifically suitable to mark small items. At present, it is also widely used to mark printed media, such as, for example, letters.  
  
In addition, it can be noted that in the special study conducted at The Center of Automatic Identification at Ohio University, it has been found that the statistical probability of DataMatrix barcode incorrect reading is 1 across 10.5 million scans. This is the reason to consider DataMatrix barcodes highly reliable compared with linear Code 39 barcodes that demonstrated the probability of incorrect recognition equal to 1 in 1.7 million cases.

</details>

## **Aspose Samples for DataMatrix Generation and Recognition**
### **DataMatrix Generation Code Samples**

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

### **DataMatrix Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

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

  
<details>  
<summary>Code Sample for DataMatrix Barcode Generation</summary>

{{< highlight csharp>}}
//generate DataMatrix Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "Åspóse.Barcóde©"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    //set DataMatrix Ecc to 200
    gen.Parameters.Barcode.DataMatrix.DataMatrixEcc = DataMatrixEccType.Ecc200;
    //set rows 22 columns 22
    gen.Parameters.Barcode.DataMatrix.Columns = 22;
    gen.Parameters.Barcode.DataMatrix.Rows = 22;
    gen.Save($"{path}DataMatrix.png", BarCodeImageFormat.Png);
}
{{< /highlight >}}

</details>
  
<details>  
<summary>Code Sample for DataMatrix Barcode Recognition</summary>

{{< highlight csharp>}}
//recognize DataMatrix Barcode
using (BarCodeReader read = new BarCodeReader($"{path}DataMatrix.png", DecodeType.DataMatrix))
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
{{< /highlight >}}

</details>  
  
### Aspose.BarCode for Java

<details>  
<summary>Code Sample for DataMatrix Barcode Generation</summary>
</details>
  
<details>  
<summary>Code Sample for DataMatrix Barcode Recognition</summary>
</details>  

### Aspose.BarCode for C++

<details>  
<summary>Code Sample for DataMatrix Barcode Generation</summary>
</details>
  
<details>  
<summary>Code Sample for DataMatrix Barcode Recognition</summary>
</details>  
