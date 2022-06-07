---
title: DataBar Limited
type: docs
description: "Information about DataBar Limited Barcode Type"
key words: "DataBar, data bar barcode, databar symbology, Create databar barcodes, databar stacked, Read databar codes, what is databar, databar stacked barcodes, generate databar barcode, matrix barcodes, 2D symbology, 2D barcodes, databar specification, gs1, gs1 barcodes, gs1 databar, databar generator, databar reader, recognise data bar codes, scan databar barcode, databar family"
weight: 40
url: /info-cards/databar-limited/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/databar) and [Generate](https://products.aspose.app/barcode/generate/databar) DataBar barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results online.{{% /alert %}}

## **Overview**
DataBar Limited is a fixed-length barcode type that supports encoding selected Global Trade Item Numbers (GTINs) that start with 0 or 1. It is intended for use in applications where space limitations are crucial and omnidirectional scanning is not needed. 

<p align="center"><img src="databarlimited.png"></p>

## **Features**
  
### **Encoding Character Set**
This symbology allows encoding all numerical digits (0-9). 

### **Barcode Structure**
The structure includes the following elements:
- Left guard pattern (narrow space, narrow bar)
- Left data character
- Check digit
- Right data character
- Right guard pattern (narrow space, narrow bar, wide space)

The first digit serves as a flag to specify whether this barcode will be utilized as a part of a composite barcode. The remaining 13 digits are used as data characters. The height of a barcode should be at least 10 modules. Data characters have a width of 26 modules including 7 bars and 7 spaces with a check character of 18 modules in between that also comprises 7 bars and 7 spaces. Quiet zones are not required.  

### **Size Dimensions**
DataBar Limited barcodes consist of 46 bars and spaces including 74 modules in total.

### **Encoding Capacity and Data Density**
This symbology allows encoding 14-digit numerical data streams.

### **Checksum Controls**
DataBar Limited barcodes include a check digit calculated using the modulo 89 algorithm.

## **Advantages and Weaknesses**
This DataBar specification is not intended for retail point-of-sale scanning. Its main advantage is high compactness, which can be useful in applications with strict placement space limitations.

## **Aspose Samples for DataBar Limited Barcodes**

### **Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//generate DataBar Limited Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarLimited, "(01)12345678901231"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Save($"{path}DataBarLimited.png", BarCodeImageFormat.Png);
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
//recognize DataBar Limited Barcode
using (BarCodeReader read = new BarCodeReader($"{path}DataBarLimited.png", DecodeType.DatabarLimited))
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
