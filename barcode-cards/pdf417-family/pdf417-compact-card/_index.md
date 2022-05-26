---
title: Compact PDF417 Symbology
description: 
key words:
type: docs
weight: 60
url: /compact-pdf417-card/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/pdf417) and [Generate](https://products.aspose.app/barcode/generate/pdf417) PDF417 barcode online. You can test the quality of ***Aspose.BarCode*** functionality and view the results online.{{% /alert %}}

The PDF417 (Portable Data File 417) group of standards uncludes 2D high-density stacked barcodes developed to store large amounts of information in compact-sized barcodes. The main peculiaruty of the PDF417 standards is the possibility of laser scanning in printed documents with high quality. PDF symbologies enable encoding both textual information and streams of bytes. The detailed PDF417 specification can be found in the [ISO/IEC 15438](https://www.iso.org/standard/43816.html) document.

## Overview
PDF417 (Portable Data File 417) is a group of 2D variable-length stacked symbologies that are similar to matrix barcodes in terms of various parameters used in a variety of applications, such as transport, identification cards, and inventory management. Compact PDF417 is used when space considerations are a main concern and symbol damage is improbable. Unlike other PDF417 types that support laser scanning for high-quality documents, Compact PDF417 requires photo scanning.

Compact PDF417, or Compact Portable Data File 417, has the same features as PDF417 standard. However, Compact PDF417 may be used where space considerations are a primary concern and symbol damage is unlikely. In an environment where label damage is unlikely (e.g. an office), the right row indicators, that PDF417 Symbols feature, may be omitted and the stop pattern may be reduced to one module width bar. This procedure reduces the non-data overhead from 4 codewords per row to 2 codewords per row, with some trade-off in decode performance and robustness, or the ability to withstand noise, damage, degradation, dust etc. This overhead reduction version is called Compact PDF417, which is fully decoder compatible with standard PDF417. 

<p align="center"><img src="compactpdf417.png"></p>

## Features
  
### Encoding Character Set
PDF417 standards enable encoding both byte streams and Unicode symbols. 
Of the 929 available code words, 900 are used for data, and 29 for special functions, such as shifting between major modes. 

  
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

### Barcode Structure
PDF417 barcodes may include from 3 to 90 rows, each of which is like a small linear bar code. All rows are the same width; each row has the same number of codewords. The codewords are represented by patterns of dark (bar) and light (space) regions. Each of these patterns contains four bars and four spaces (where the 4 in the name comes from). The total width is 17 times the width of the narrowest allowed vertical bar (the X dimension); this is where the 17 in the name comes from. Each pattern starts with a bar and ends with a space. The row height must be at least 3 times the minimum width: Y ≥ 3 X.
Truncated PDF417 contains only two row start columns. 

<details>  
<summary>Read more</summary>

Each row in a PDF417 barcode has:
- Starting quiet zone. This is a mandated minimum amount of white space before the bar code begins
- Start pattern which identifies the format as PDF417
- Left-side codeword containing information about the row (such as the row number and error correction level)
- 1–30 data codewords: Codewords are a group of bars and spaces representing one or more numbers, letters, or other symbols
- Right-side codeword with more information about the row
- Stop pattern
- Closing quiet zone.

<p align="center"><img src="pdf417-structure.png"></p>

</details>

### Size Dimentions
A truncated PDF417 symbol uses less area than the normal PDF417 barcode. By selecting this option, the right hand side of the symbol is removed or truncated. This option should be used primarily in a clean environment, since it is more susceptible to damage.
<details>  
<summary>Read more</summary>
  

  
</details>

### Encoding Capacity and Data Density
The basic PDF417 standard can encode up to 1,108 bytes or 1,850 alphanumeric (2,710 numerical) symbols in up to 30 columns and 90 rows while Micro PDF417 is capable of encoding at most 150 bytes of data or 266 alphanumeric (366 numerical) characters in up to 4 columns and 44 rows.

PDF417 uses a base 929 encoding. Each codeword represents a number from 0 to 928.

<details>  
<summary>Read more</summary>
</details>

### Error Correction
PDF417 barcodes include additional information for data recovery through Reed-Solomon error correction. When the PDF417 symbol is created, from 2 to 512 error detection and correction codewords are added. PDF417 uses Reed–Solomon error correction. When the symbol is scanned, the maximum number of corrections that can be made is equal to the number of codewords added, but the standard recommends that two codewords be held back to ensure reliability of the corrected information.

<details>  
<summary>Read more</summary>
 

  
</details>

## Advantanges and Weaknesses
<details>  
<summary>Read more</summary>

</details>

## Aspose Samples for Compact PDF417 Generation and Recognition
### **Compact PDF417 Generation Code Samples**

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

### **Compact PDF417 Recognition Code Samples**

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
<summary>Code Sample for Compact PDF417 Barcode Generation</summary>

//GENERATE
{{< highlight csharp>}}
//generate Compact PDF417 Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    //set Pdf417 truncated or Compact Pdf417
    gen.Parameters.Barcode.Pdf417.Pdf417Truncate = true;
    //set 3 columns
    gen.Parameters.Barcode.Pdf417.Columns = 3;
    //set error level 2
    gen.Parameters.Barcode.Pdf417.Pdf417ErrorLevel = Pdf417ErrorLevel.Level2;
    gen.Save($"{path}CompactPDF417.png", BarCodeImageFormat.Png);
}
{{< /highlight >}}

</details>
  
<details>  
<summary>Code Sample for Compact PDF417 Barcode Recognition</summary>

//RECOGNIZE
{{< highlight csharp>}}
//recognize Compact PDF417 Barcode
using (BarCodeReader read = new BarCodeReader($"{path}CompactPDF417.png", DecodeType.Pdf417, DecodeType.CompactPdf417, DecodeType.MacroPdf417))
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
{{< /highlight >}}

</details>  
  
### Aspose.BarCode for Java

<details>  
<summary>Code Sample for Compact PDF417 Barcode Generation</summary>
</details>
  
<details>  
<summary>Code Sample for Compact PDF417 Barcode Recognition</summary>
</details>  

### Aspose.BarCode for C++

<details>  
<summary>Code Sample for Compact PDF417 Barcode Generation</summary>
</details>
  
<details>  
<summary>Code Sample for Compact PDF417 Barcode Recognition</summary>
</details>  
