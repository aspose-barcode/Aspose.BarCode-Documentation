---
title: Aztec Rune Code
description: ""
key words: ""
type: docs
weight: 20
url: /barcode/aztec-rune-card/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/aztec) and [Generate](https://products.aspose.app/barcode/generate/aztec) Aztec barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view the results online.{{% /alert %}}

## **Overview**
Aztec Runes are a series of small but distinct machine-readable marks designed to be graphically compatible with Aztec Code. They are in fact just the Core Symbol of a compact Aztec Code symbol with a numerically distinct Mode Message which in this case conveys 8 bits of actual data. Thus they comprise 256 11x11 module square marks which are conveniently found and read by an Aztec Code reader. It consists of the core symbol of the compact version of Aztec Code together with a numerically distinct data message that conveys 8 bits of data. Aztec Rune contains 256 11 x 11 module square marks that can be scanned by any Aztec Code reader. Printing white on black is an option.

Aztec Rune is defined in Annex A of standard ISO/IEC 24778 Information technology.

<p align="center"><img src="aztecrune.png"></p>

## **Features**
  
### Encoding Character Set
Aztec Rune allows encoding only numerical digits from 0 to 255.

### **Structure**
Each Aztec Rune consists of a bulls-eye finder pattern, orientation patterns, and a Reed-Solomon encoded data message. The finder and orientation patterns in an Aztec Rune are exactly as defined for compact Aztec Code symbols. Because Aztec Runes are read from the inside out, no quiet zone is required.

<details>  
<summary>Read more</summary>

Finder pattern: A square bull's-eye structure in the center that consists of four alternating black and white square rings that are one module wide and a center square that is one module wide and high. (This square is black unless the white-on-black option is being used).

Orientation patterns: The layer outside the outermost ring of the finder pattern is a one-module-wide layer that contains chevron-shaped orientation patterns in each corner. These patterns consist of three one-module squares. The first pattern, at the upper left corner, consists of three black modules. The second pattern, at the upper right, is one white module followed by two black modules. The third, at the lower right, is one black module followed by two white modules. The fourth, at the lower left, is three white modules.

Data message: The remainder of the barcode consists of one data layer that contains data and Reed-Solomon check characters. This layer is read in a clockwise direction. The character encodation method is the same as for the compact version of Aztec Code.
  
</details>

### **Size Dimentions**
Aztec Rune barcodes correspond to small machine-readable marks with the maximal size of 11 x 11 modules. It consists only of the core symbol of Compact Aztec Code. 

### **Encoding Capacity and Data Density**
Aztec Rune can encode up to 3 numerical digits or 1 byte.

### **Error Correction**
See article [Aztec Barcode Family](/aztec-cards/) for information about the error correction mechanism.  

## **Advantanges and Weaknesses**
Aztec Rune allows creating very small matrix barcodes that still provide damage resistance and data recovery owing to error correction. It is intended for specific applications in which input data can be limited to 3 digits.

## **Aspose Samples for Aztec Rune Generation and Recognition**
### **Aztec Rune Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//GENERATE
{{< highlight csharp>}}
//generate Aztec Rune Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Aztec, "123"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    //set symbol mode Rune
    gen.Parameters.Barcode.Aztec.AztecSymbolMode = AztecSymbolMode.Rune;
    gen.Save($"{path}AztecRune.png", BarCodeImageFormat.Png);
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

### **Aztec Rune Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//RECOGNIZE
{{< highlight csharp>}}
//recognize Aztec Rune Barcode
using (BarCodeReader read = new BarCodeReader($"{path}AztecRune.png", DecodeType.Aztec))
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
