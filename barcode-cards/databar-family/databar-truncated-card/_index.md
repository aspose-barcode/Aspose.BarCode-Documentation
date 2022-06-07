---
title: DataBar Truncated / Stacked
type: docs
description: "Information about DataBar Truncated Barcode Type and Its Stacked Version"
key words: "DataBar, data bar barcode, databar symbology, Create databar barcodes, databar stacked, Read databar codes, what is databar, databar stacked barcodes, generate databar barcode, matrix barcodes, 2D symbology, 2D barcodes, databar specification, gs1, gs1 barcodes, gs1 databar, databar generator, databar reader, recognise data bar codes, scan databar barcode, databar family"
weight: 20
url: /info-cards/databar-truncated/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/databar) and [Generate](https://products.aspose.app/barcode/generate/databar) DataBar barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
**DataBar Truncated** is a GS1 DataBar specification that allows producing [DataBar Omnidirectional](/barcode/info-cards/databar-omnidirectional) barcodes decreased in height to 13 modules. It supports encoding Global Coupon Number (GCN) and selected Global Trade Item Number (GTIN) formats: GTIN-8, GTIN-12, GTIN-13, and GTIN-14.  
  
**DataBar Stacked** is a GS1 DataBar symbology that uses DataBar Omnidirectional barcodes reduced in height and divided into two rows with a separator pattern between them. It has a specification similar to [DataBar Stacked Omnidirectional](/barcode/info-cards/databar-omnidirectional) with the difference that the overall height is reduced from 33 to 13 modules. 
  
|Examples|DataBar Truncated|DataBar Stacked|
| :-: | :-: | :-: | 
| |<img src="databartruncated.png">|<img src="databarstacked.png">|
  
## **Features**
  
### **Encoding Character Set**
These barcode types can be used to encode numerical digits (0-9).

### **Structure**
**DataBar Truncated**  
  
Barcodes are composed of the following elements:
- Left guard pattern (narrow space, narrow bar)
- Left pair of data characters with a finder pattern in between including a check digit
- Right pair of data characters with a finder pattern in between including a check digit
- Right guard pattern (narrow space, narrow bar)

The first digit is used as a flag to denote whether this barcode will be processed as a part of a composite barcode, and the remaining 13 digits constitute data characters. Barcode contents are grouped in four segments that are placed between two finder patterns. The composition of bars and spaces is the same as in [DataBar Omnidirectional](/barcode/info-cards/databar-omnidirectional/) barcodes.
  
**DataBar Stacked**  
  
The barcode structure comprises the following elements:
- Top row composed of the left half of a DataBar Omnidirectional barcode (left guard pattern, first symbol character, finder pattern, second symbol character) followed by a guard pattern of a one-module bar and a one-module space
- Separator pattern
- Bottom row that includes a guard pattern followed by the right half of the code (fourth symbol character, finder pattern, third symbol character, right guard pattern)

The overall configuration is the same as in the stacked version of [DataBar Omnidirectional](/barcode/info-cards/databar-omnidirectional/) barcodes.  
Quiet zones are not necessary.

### **Size Dimensions**
DataBar Truncated barcodes contain 46 bars and spaces with 96 modules in total. In DataBar Stacked, to ensure that the overall height is limited to 13 modules, the top row has the height of five modules, and the height of the bottom row is 7 modules. The height of the separator pattern equals one module.

### **Encoding Capacity and Data Density**
DataBar Truncated and DataBar Stacked allow encoding 14-digit numerical data streams.

### **Checksum Controls**
These symbologies include check digits in the finder patterns that are based on the modulo 79 (mod 79) algorithm.

## **Advantages and Weaknesses**
These DataBar specifications benefit from generating small and high-density barcode labels. Owing to their compact size, such barcodes are widely used in healthcare applications. Due to the specifics of their configuration, DataBar Truncated and DataBar Stacked cannot be scanned omnidirectionally. Thus, they are not intended for use in retail point-of-sale.

## **Aspose Samples for DataBar Truncated and Stacked Barcodes**
### **DataBar Truncated Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

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
