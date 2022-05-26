---
title: Aztec Family
description: 
key words:
type: docs
weight: 40
url: /aztec-cards/
---

{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/aztec) and [Generate](https://products.aspose.app/barcode/generate/aztec) Aztec barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view the results online.{{% /alert %}}

## Overview
Aztec is a highly efficient two-dimensional (2D) symbology that encodes information using square modules with a unique finder pattern in the center of the barcode label.Such finder patterns facilitate identifying cell locations while scanning and decoding Aztec barcodes. Aztec Code has been introduced to provide higher accuracy than other 2D symbologies. 

The Aztec symbology includes three barcode types:

- [Full-Range Aztec](/barcode/net/aztec-full-range-card/) - encodes up to 1,914 bytes or 3,832 numerical (3,067 alphanumeric) digits
- [Compact Aztec](/barcode/net/aztec-compact-card/) - can encode up to 53 byte or 110 numerical (89 alphanumeric) digits
- [Aztec Rune](/barcode/net/aztec-rune-card/) - encodes values from 0 to 255 and is intended to mark objects in Augmented Reality applications
  
In this article, the Full-Range Aztec type is discussed. 

<p align="center"><img src="aztecstructure.png"></p>

## Features
  
### Encoding Character Set
  
<details>  
<summary>Read more</summary>
The source sequence of data characters is translated into a sequence of message codewords in a two-step process. First the data characters in succession are converted to equivalent binary values, using intermediary shift and latch values as needed, producing a long binary stream of input data. Second this string is laid into a sequence of B-bit codewords using an exclusionary rule that avoids any occurrence of a codeword with all 0’s or with all 1’s.   
</details>

### Barcode Structure

<p align="center"><img src=".png"></p>

*Image source: Aztec Barcode Symbology Specification*

<details>  
<summary>Read more</summary>
  
</details>

### Size Dimentions
Full-Range Aztec Code barcodes up to 32 layers with the maximal size of 151x151 modules. Size restrictions: The smallest is 15 x 15 modules, and the largest is 151 x 151 modules. Aztec allows generating barcodes of the smallest possible size. For example, an Aztec label would be approximately 30 times smaller than a Code 39 barcode encoding the same information. A quiet zone is not required with Aztec barcodes because the unique finder pattern is in the center of the symbol. However, some barcode imagers may have difficulty decoding unless a 1-module quiet zone is present, which should be the same color as the background.

### Encoding Capacity and Data Density
Full-range Aztec barcodes can encode up to 1,914 bytes or 3,832 numerical (3,067 alphanumeric) digits.


### Error Correction
The Aztec symbology relies on Reed-Solomon error correction. The error correction level can be specified as a value from 5 to 95. Including more error correction data results in generating a larger symbol that however is more resistable to damages. It is not recommended to apply error correction levels over 23 in cases when large portions of data need to be encoded as this may exceed the symbol capacity. When its is known that Aztec barcodes will be utilized in the environment where the probability of barcode damaging is low, the error correction level may be set from 5 to 10 thus generating smaller barcode labels.

## Advantanges and Weaknesses
Aztec barcodes are suitable when sending barcoded documents via fax because the barcode can withstand many poor resolution and scanning issues.

## **Aspose Samples for Full-Range Aztec Generation and Recognition**
### **Aztec Full-Range Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

Insert Code

{{< /tab >}}

{{< tab tabNum="2" >}}

Insert Code

{{< /tab >}}

{{< tab tabNum="3" >}}

Insert Code

{{< /tab >}}

{{< /tabs >}}

### **Aztec Full-Range Recognition Code Samples**

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
<summary>Code Sample for Aztec Barcode Generation</summary>

{{< highlight csharp>}}
//generate Aztec Full Range Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Aztec, "Åspóse.Barcóde©"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    //set symbol mode FullRange
    gen.Parameters.Barcode.Aztec.AztecSymbolMode = AztecSymbolMode.FullRange;
    //set error correction capacity to 10% (can be from 5% to 95%)
    gen.Parameters.Barcode.Aztec.AztecErrorLevel = 10;
    gen.Save($"{path}AztecFullRange.png", BarCodeImageFormat.Png);
}
{{< /highlight >}}


</details>
  
<details>  
<summary>Code Sample for Aztec Barcode Recognition</summary>


{{< highlight csharp>}}
//recognize Aztec Full Range Barcode
using (BarCodeReader read = new BarCodeReader($"{path}AztecFullRange.png", DecodeType.Aztec))
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
{{< /highlight >}}

</details>  
  
### Aspose.BarCode for Java

<details>  
<summary>Code Sample for Aztec Barcode Generation</summary>
</details>
  
<details>  
<summary>Code Sample for Aztec Barcode Recognition</summary>
</details>  

### Aspose.BarCode for C++

<details>  
<summary>Code Sample for Aztec Barcode Generation</summary>
</details>
  
<details>  
<summary>Code Sample for Aztec Barcode Recognition</summary>
</details>  
