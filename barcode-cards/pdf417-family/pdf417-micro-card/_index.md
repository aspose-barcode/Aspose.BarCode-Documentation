---
title: Micro PDF417 Symbology
description: 
key words:
type: docs
weight: 50
url: /micro-pdf417-card/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/pdf417) and [Generate](https://products.aspose.app/barcode/generate/pdf417) PDF417 barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view the results online.{{% /alert %}}

The PDF417 (Portable Data File 417) barcode family includes 2D stacked barcode types providing high data density along with relatively small size. PDF417 barcodes printed on high-quality documents can be read through laser scanning. PDF417 symbologies allow encoding both streams of bytes and Unicode characters. The PDF417 specification is provided in the [ISO/IEC 15438](https://www.iso.org/standard/43816.html) document.

## Overview
Micro PDF417 is a two-dimensional, variable-length stacked symbology that is designed to encode a moderate amount of data in a very small space. It is based on PDF417 and shares several of its features. MicroP DF417 is defined in ISO/IEC 24728 Information technology - Automatic identification and data capture techniques - MicroPDF417 bar code symbology specification.
MicroPDF417 is two-dimensional (2D), multi-row symbology, derived from PDF417 that encodes up to 150 bytes. All of our MicroPDF417 products were created from ISO/IEC 24728. Micro-PDF417 is designed for applications requiring improved area efficiency, and is used for Composite Codes in GS1 DataBar.

<p align="center"><img src=".png"></p>

## Features
  
### Encoding Character Set

<details>  
<summary>Read more</summary>
 
</details>

### Barcode Structure
Each MicroPDF417 symbol contains between 4 and 44 rows and from one to four columns. Only certain combinations of rows and columns are allowed (see below). Each codeword consists of four bars and four spaces made up of 17 rectangular modules in one row. Row height is variable and adjustable. For a list of the available codewords, see the ISO/IEC 24728 standard.

You can include Macro 05 and Macro 06 characters in a MicroPDF417 barcode to abbreviate an industry-specific prefix and suffix into one character to reduce the number of characters that you need to encode data.

The MicroPDF417 symbol is comprised of a couple of components:

Start Pattern
Data Codewords - The codewords between the start and stop patterns, where the actual data is encoded.
Stop Pattern

<details>  
<summary>Read more</summary>

The symbol comprises the following elements per row:
- Leading quiet zone
- Left row address pattern
- Data codewords and center row patterns as follows, depending on the version:
- One-column version: One codeword
- Two-column version: Two codewords
- Three-column version: One codeword, a center row address pattern, two codewords
- Four-column version: Two codewords, a center row address pattern, two codewords
- Right row address pattern
- Stop bar
- Trailing quiet zone

|Number of columns|Allowed Number of Rows|
|---|---|
|1|11, 14, 17, 20, 24, 28|
|2|8, 11, 14, 17, 20, 23, 26|
|3|6, 8, 10, 12, 15, 20, 26, 32, 38, 44|
|4|4, 6, 8, 10, 12, 15, 20, 26, 32, 38, 44|

</details>

### Size Dimentions
MicroPDF417 symbol dimensions depend on the amount of data that is entered. The height of any MicroPDF417 symbol can range from 4 to 44 rows, and the row height can range from 1X to 10X, where "X" is the current X dimension. The width of a symbol can range from 40X to 101X. A minimum quiet zone of 1X is required on all sides.
<details>  
<summary>Read more</summary>
 
</details>

### Encoding Capacity and Data Density
The basic PDF417 standard can encode up to 1,108 bytes or 1,850 alphanumeric (2,710 numerical) symbols in up to 30 columns and 90 rows while Micro PDF417 is capable of encoding at most 150 bytes of data or 266 alphanumeric (366 numerical) characters in up to 4 columns and 44 rows.

<details>  
<summary>Read more</summary>

</details>

### Error Correction
MicroPDF417 uses the Reed-Solomon algorithm for error correction. The number of error correction codewords is fixed for each symbol version.
<details>  
<summary>Read more</summary>
  
</details>

## Advantanges and Weaknesses


## **Aspose Code Samples for Micro PDF417 Generation and Recognition**
### **Micro PDF417 Generation Code Samples**

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

### **Micro PDF417 Recognition Samples**

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
<summary>Code Sample for Micro PDF417 Barcode Generation</summary>

//GENERATE
{{< highlight csharp>}}
//generate Micro PDF417 Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MicroPdf417, "Aspose"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Save($"{path}MicroPDF417.png", BarCodeImageFormat.Png);
}
{{< /highlight >}}

</details>
  
<details>  
<summary>Code Sample for Micro PDF417 Barcode Recognition</summary>

//RECOGNIZE
{{< highlight csharp>}}
//recognize Micro PDF417 Barcode
using (BarCodeReader read = new BarCodeReader($"{path}MicroPDF417.png", DecodeType.MicroPdf417))
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
{{< /highlight >}}

</details>  
  
### Aspose.BarCode for Java

<details>  
<summary>Code Sample for Micro PDF417 Barcode Generation</summary>
</details>
  
<details>  
<summary>Code Sample for Micro PDF417 Barcode Recognition</summary>
</details>  

### Aspose.BarCode for C++

<details>  
<summary>Code Sample for Micro PDF417 Barcode Generation</summary>
</details>
  
<details>  
<summary>Code Sample for Micro PDF417 Barcode Recognition</summary>
</details>  
