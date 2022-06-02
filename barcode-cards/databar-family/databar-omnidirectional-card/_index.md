---
title: DataBar Omnidirectional / Stacked Omnidirectional
type: docs
description: ""
key words: ""
weight: 20
url: /databar-omnidirectional-card/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/databar) and [Generate](https://products.aspose.app/barcode/generate/databar) DataBar barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view the results online.{{% /alert %}}

## **Overview**
**DataBar Omnidirectional** supports the encodation of the Global Coupon Number (GCN) and the following Global Trade Item Numbers (GTINs): GTIN-8, GTIN-12, GTIN-13, and GTIN-14. If the GCN or GTIN has fewer than 14 characters, leading zeros are appended to the left of the data so that a total of 14 characters is encoded.

The GS1 **DataBar Stacked Omnidirectional** symbol encodes a 14-digit numeric data stream. It supports the encodation of the Global Coupon Number (GCN) and the following Global Trade Item Numbers (GTINs): GTIN-8, GTIN-12, GTIN-13, and GTIN-14. If the GCN or GTIN has fewer than 14 characters, leading zeros are appended to the left of the data so that a total of 14 characters is encoded.

  
|Examples|DataBar Omnidirectional|DataBar Omnidirectional Stacked|
| :-: | :-: | :-: | 
| |<img src="databaromnidirectional.png">|<img src="databaromnidirectionalstacked.png">|
  
## **Features**
  
### **Encoding Character Set**
These barcode types allow encoding all numerical digits (0-9).  

### **Structure**
**DataBar Omnidirectional**  
  
Barcodes are composed of the following elements:
- Left guard pattern (narrow space, narrow bar)
- Left pair of symbol characters with a finder pattern between that contains a check digit
- Right pair of symbol characters with a finder pattern between that contains a check digit
- Right guard pattern (narrow space, narrow bar)
- The first digit is a flag that indicates whether the barcode is part of a composite barcode, and the 13 digits that follow comprise the data characters. 
 
The data itself is split into four groups called "symbol characters," which are interspersed between the two finder patterns. The left and right symbol characters are always read beginning with the character to the outside of the finder pattern. Therefore, the sequence in which symbol characters are read is: first, second, fourth, third.
The elements within each character are always read toward the finder pattern, so the second and third characters are read from right to left. The outside characters (first and third) are 16 modules wide with four bars and four spaces. The inside characters (second and fourth) are 15 modules wide with four bars and four spaces. The finder patterns are each 15 modules wide. The first finder pattern has three spaces and two bars, and the second has two spaces and three bars. A quiet zone is not required.
    
**DataBar Stacked Omnidirectional**  
  
The symbol comprises the following elements:
- Top row, which consists of the left half of the GS1 DataBar Omnidirectional code (left guard pattern, first symbol character, finder pattern, second symbol character) followed by a guard pattern of a one-module bar and a one-module space
- Separator pattern
- Bottom row, which consists of a guard pattern (one-module bar and one-module space) followed by the right half of the code (fourth symbol character, finder pattern, third symbol character, right guard pattern)

A quiet zone is not required.  

### **Size Dimentions**
Each DataBar Omnidirectional symbol contains 46 bars and spaces in a total of 96 modules.  
  
To make the DataBar Stacked Omnidirectional barcodes omnidirectionally readable, the height of each row must be at least 33 modules, and the height of the separator pattern must be at least three modules.

### **Encoding Capacity and Data Density**
These barcode types can be used to encode 14-digit numerical data stream.


### **Checksum Controls**
These symbologies require including check digits in the finder patterns that use the modulo 79 algorithm.

## **Advantanges and Weaknesses**
DataBar Omnidirectional and DataBar Omnidirectional Stacked have been introduced for use in retail point-of-sale operational tasks. Such barcodes can be scanned omnidirectionally. 

## **Aspose Samples for DataBar Omnidirectional and Omnidirectional Stacked Barcodes**
### **DataBar Omnidirectional Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//generate DataBar OmniDirectional Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarOmniDirectional, "(01)12345678901231"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Save($"{path}DataBarOmniDirectional.png", BarCodeImageFormat.Png);
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

### **DataBar Omnidirectional Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//recognize DataBar OmniDirectional Barcode
using (BarCodeReader read = new BarCodeReader($"{path}DataBarOmniDirectional.png", DecodeType.DatabarOmniDirectional, DecodeType.DatabarStackedOmniDirectional))
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

### **DataBar Omnidirectional Stacked Generation Code Samples**

{{< tabs tabTotal="3" tabID="3" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//generate DataBar OmniDirectional Stacked Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarStackedOmniDirectional, "(01)12345678901231"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Save($"{path}DataBarOmniDirectionalStacked.png", BarCodeImageFormat.Png);
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

### **DataBar Omnidirectional Stacked Recognition Code Samples**

{{< tabs tabTotal="3" tabID="4" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//recognize DataBar OmniDirectional Stacked Barcode
using (BarCodeReader read = new BarCodeReader($"{path}DataBarOmniDirectionalStacked.png", DecodeType.DatabarOmniDirectional, DecodeType.DatabarStackedOmniDirectional))
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

