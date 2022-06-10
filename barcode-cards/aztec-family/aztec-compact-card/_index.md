---
title: Aztec Compact Code
description: "Overview on Aztec Compact Code Barcode Type"
keywords: "Aztec Code, aztec compact code, aztec compact barcode, aztec compact type, Create aztec compact barcodes, Read aztec codes, read aztec compact code, what is aztec compact barcode, aztec compact barcodes, generate aztec compact code, matrix barcodes, 2D symbology, 2D barcodes, aztec specification, aztec compact generator, aztec compact reader, recognise aztec codes, scan aztec barcode"
type: docs
weight: 30
url: /info-cards/aztec-compact/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/aztec) and [Generate](https://products.aspose.app/barcode/generate/aztec) Aztec barcodes online. You can test the quality of ***Aspose.BarCode*** recognition functionality and view results.{{% /alert %}}

## **Overview**
Aztec Compact Code is a version of Aztec Code that allows creating more compact barcodes using the simplified pattern configuration. Compact Aztec Code labels comprise 2 white and 2 black finder pattern rings in addition to the center square, from 1 to 4 data layers only, and no reference grid.

<p align="center"><img src="azteccompact.png"></p>

## **Usage Scenarios**
This barcode type may be useful in cases when space limitations are crucial and the size of the input message to be encoded is not large. It is widely implemented in various healthcare applications, e.g. patient identification, specimen tracking, and marking of medical items.

## **Characteristics**
### **Encoding Character Set**
All 255 ASCII characters (digits 0-9, text, and binary data) are supported for encoding. 

### **Barcode Structure**
Compact Aztec Code barcodes are composed of the central black square, two white, and two black finder pattern rings that constitute the core symbol. Then, it is surrounded by several data layers (from 1 to 4). No reference grid is included. The core symbol is placed at the center of a label and comprises a finder pattern, orientation patterns, and a mode message. In Compact Aztec barcodes, the core symbol has the size of 11x11 modules. No quiet zones are needed.

<details>  
<summary>Read more</summary>

- The finder pattern is a set of concentric square rings and a single dark module.
- Four three-module chevron-shaped orientation patterns are located at the corners of the finder pattern.
- Mode message is the single layer of bits attached to the finder pattern. It contains error correction codewords that are structured in a clockwise direction starting from the upper left corner.
- Data fields symmetrically surround the core symbol with one or more data layers (1-4).
- Input message together with error correction codewords is organized in 2-module thick layers that are placed along a spiral clockwise from the upper left corner of the core symbol. 

</details>

### **Size Dimensions**
In Compact Aztec Code, the core symbol may be surrounded by 1 to 4 layers thus the label size can vary from 15×15 to 27×27 modules.

### **Encoding Capacity and Data Density**
This type can encode up to 53 bytes or 110 numerical or 89 alphanumeric characters. The most compact configuration corresponds to a one-layer Compact Aztec barcode comprising 15x15 modules that can encode at most 13 textual symbols or 12 numerical digits. The description of all available size combinations and corresponding capacity values can be found in the ISO standard specification for Aztec Code. 

### **Error Correction**
See the article [Aztec Barcode Family](/barcode/info-cards/aztec-full-range/)   

## **Advantages and Limitations**
See the article [Aztec Barcode Family](/barcode/info-cards/aztec-full-range/)

## **How to Generate and Read Aztec Compact Barcodes**
### **Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

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

### **Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

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
