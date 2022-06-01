---
title: Aztec Compact Code
description: ""
key words: ""
type: docs
weight: 30
url: /barcode/aztec-compact-card/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/aztec) and [Generate](https://products.aspose.app/barcode/generate/aztec) Aztec barcodes online. You can test the quality of ***Aspose.BarCode*** recognition functionality and view results.{{% /alert %}}

## **Overview**
Aztect Compact Code is a version of Aztec Code that allows creating smaller barcodes using a simplified pattern configuration. A compact Aztec Code label has 2 white and 2 black finder pattern rings in addition to the center square, from 1 to 4 data layers only, and no reference grid. This symbology may be useful in cases when space limitations are crucial and the amount of data to be encoded is small.

<p align="center"><img src="azteccompact.png"></p>

## **Features**
  
### **Encoding Character Set**
This symbology supports all 255 ASCII characters (digits 0-9, text, and binary data). 

### **Structure**
A compact Aztec Code symbol has two white and two black finder pattern rings (in addition to the center square), one to four data layers, and no reference grid. The core symbol, always square and at the exact center of an Aztec Code symbol, consists of a finder pattern, orientation patterns, and a mode message. This core covers an 11x11 module area in compact symbols. It is called the core symbol as it must be successfully detected and decoded before decoding can proceed into the surrounding data fields. Compact Aztec Code symbols, which are of limited size, have no reference grid structure. Because Aztec Runes are read from the inside out, no quiet zone is required.

<details>  
<summary>Read more</summary>
- The finder pattern in Aztec Code is a set of concentric square rings. Centered on a single dark module, there is a ring of light modules surrounded by a larger ring of dark modules, and so forth outward to a second 9x9 module dark ring in compact symbols
- Four 3-module chevron-shaped orientation patterns are located at the corners of the finder pattern. The upper lefthand pattern is all dark and the lower lefthand pattern is all light, while the upper righthand pattern has 2 modules dark and the lower right pattern has just 1 module dark
- Mode message. The single layer of bits adjoining the finder pattern, excluding the orientation patterns and in full-range symbols also excluding the center bit along each side (which is part of the reference grid), comprises an error-corrected Mode Message wrapped in a clockwise direction starting from the upper left corner. This message explicitly encodes both the number of data layers in the overall symbol (and thus its size) and the number of datawords in those layers, the rest being error correction checkwords for that message
- The data fields symmetrically surround the Core Symbol with one or more data layers
- The message data themselves plus their error correction words are laid into 2-module thick layers, spiralling clockwise from the upper left corner of the Core Symbol outward, and in full-range symbols necessarily skipping over module positions occupied by the reference grid. Compact Aztec Code symbols can have from one to four data layers, while full-range Aztec Code symbols can have from one up to 32 data layers

</details>

### **Size Dimentions**
In compact Aztec Code barcodes, the core may be surrounded by 1 to 4 layers thus the label size can vary from 15 × 15 to 27 × 27 modules.

### **Encoding Capacity and Data Density**
Compact Aztec can encode up to 53 byte or 110 numerical (89 alphanumeric) digits. One-layer Compact Aztec barcode composed of 15 x 15 modules (the smallest option) can encode at most 13 textual symbols or 12 numerical digits. The description of all available size combinations and corresponding data capacity values can be found in the ISO standard specification for Aztec Code. 

### **Error Correction**
See article [Aztec Barcode Family](/barcode/aztec-cards/)   

## **Advantanges and Weaknesses**
See article [Aztec Barcode Family](/barcode/aztec-cards/)

## **Aspose Samples for Aztec Compact Generation and Recognition**
### **Aztec Compact Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//GENERATE
{{< highlight csharp>}}
//generate Aztec Compact Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Aztec, "Åspóse.Barcóde©"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    //set symbol mode Compact
    gen.Parameters.Barcode.Aztec.AztecSymbolMode = AztecSymbolMode.Compact;
    //set error correction capacity to 10% (can be from 5% to 95%)
    gen.Parameters.Barcode.Aztec.AztecErrorLevel = 10;
    gen.Save($"{path}AztecCompact.png", BarCodeImageFormat.Png);
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

### **Aztec Compact Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//RECOGNIZE
{{< highlight csharp>}}
//recognize Aztec Compact Barcode
using (BarCodeReader read = new BarCodeReader($"{path}AztecCompact.png", DecodeType.Aztec))
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

