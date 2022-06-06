---
title: DataBar Truncated / Stacked
type: docs
description: ""
key words: ""
weight: 10
url: /databar-truncated-card/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/databar) and [Generate](https://products.aspose.app/barcode/generate/databar) DataBar barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
- **GS1 DataBar Truncated** is a GS1 DataBar Omnidirectional symbol that is reduced in height to as low as 13 modules. It supports the encodation of the Global Coupon Number (GCN) and the following Global Trade Item Numbers (GTINs): GTIN-8, GTIN-12, GTIN-13, and GTIN-14. If the GCN or GTIN has fewer than 14 characters, leading zeros are appended to the left of the data so that a total of 14 characters is encoded.

- **GS1 DataBar Stacked** is a GS1 DataBar Omnidirectional symbol that is reduced in height and split into two rows with a separator pattern between them. It is identical to GS1 DataBar Stacked Omnidirectional except that the total height is reduced to as low as 13 modules. 

GS1 DataBar Stacked encodes a 14-digit numeric data stream. It supports the encodation of the Global Coupon Number (GCN) and the following Global Trade Item Numbers (GTINs): GTIN-8, GTIN-12, GTIN-13, and GTIN-14. If the GCN or GTIN has fewer than 14 characters, leading zeros are appended to the left of the data so that a total of 14 characters is encoded. 

Due to the compact size, these barcode types are mainly used in the health care industry.


|Examples|DataBar Truncated|DataBar Stacked|
| :-: | :-: | :-: | 
| |<img src="databartruncated.png">|<img src="databarstacked.png">|

## **Features**
  
### **Encoding Character Set**
These barcode types can be used to encode numerical digits (0-9).

### **Structure**
**DataBar Truncated**  
  
The symbol comprises the following elements:
- Left guard pattern (narrow space, narrow bar)
- Left pair of symbol characters with a finder pattern between that contains a check digit
- Right pair of symbol characters with a finder pattern between that contains a check digit
- Right guard pattern (narrow space, narrow bar)

The first digit is a flag that indicates whether the barcode is part of a composite barcode, and the 13 digits that follow comprise the data characters. The data itself is split into four groups called "symbol characters," which are interspersed between the two finder patterns. The left and right symbol characters are always read beginning with the character to the outside of the finder pattern. Therefore, the sequence in which symbol characters are read is: first, second, fourth, third.
The elements within each character are always read toward the finder pattern, so the second and third characters are read from right to left.

The outside characters (first and third) are 16 modules wide with four bars and four spaces. The inside characters (second and fourth) are 15 modules wide with four bars and four spaces. The finder patterns are each 15 modules wide. The first finder pattern has three spaces and two bars, and the second has two spaces and three bars.

**DataBar Stacked**  
  
The symbol comprises the following elements:
-Top row, which consists of the left half of the GS1 DataBar Omnidirectional code (left guard pattern, first symbol character, finder pattern, second symbol character) followed by a guard pattern of a one-module bar and a one-module space
- Separator pattern
- Bottom row, which consists of a guard pattern (one-module bar and one-module space) followed by the right half of the code (fourth symbol character, finder pattern, third symbol character, right guard pattern)

### **Size Dimentions**
Each DataBar Truncated barcode contains 46 bars and spaces in a total of 96 modules.  
  
In DataBar Stacked, to limit the total barcode height to 13 modules, the top row is always five modules high, and the bottom row is always seven modules high. The separator pattern is at least one module high. A quiet zone is not required.

### **Encoding Capacity and Data Density**
DataBar Truncated and DataBar Stacked allow encoding 14-digit numerical data streams.

### **Checsum Controls**
These symbologies include check digits in the finder patterns that use the modulo 79 (mod 79) algorithm for error correction.


## **Advantanges and Weaknesses**
These DataBar subtypes benefit from producing compact and high-density barcode labels. However, due to specifics of their configurations, DataBar Truncated and DataBar Stacked cannot be read omnidirectionally. They are not intended for retail point-of-sale scanning.


## **Aspose Samples for DataBar Truncated and Stacked Barcodes**
### **DataBar Truncated Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//GENERATE
{{< highlight csharp>}}
//generate DataBar Truncated Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarTruncated, "(01)12345678901231"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    //minimum of 13X high
    gen.Parameters.Barcode.BarHeight.Pixels = 26;
    gen.Save($"{path}DataBarTruncated.png", BarCodeImageFormat.Png);
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

### **DataBar Truncated Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//recognize DataBar Truncated Barcode
using (BarCodeReader read = new BarCodeReader($"{path}DataBarTruncated.png", DecodeType.DatabarTruncated, DecodeType.DatabarStacked))
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

### **DataBar Stacked Generation Code Samples**

{{< tabs tabTotal="3" tabID="3" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//GENERATE
{{< highlight csharp>}}
//generate DataBar Stacked Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarStacked, "(01)12345678901231"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Save($"{path}DataBarStacked.png", BarCodeImageFormat.Png);
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

### **DataBar Stacked Recognition Code Samples**

{{< tabs tabTotal="3" tabID="4" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//RECOGNIZE
{{< highlight csharp>}}
//recognize DataBar Stacked Barcode
using (BarCodeReader read = new BarCodeReader($"{path}DataBarStacked.png", DecodeType.DatabarTruncated, DecodeType.DatabarStacked))
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
