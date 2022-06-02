---
title: DataBar Expanded / Expanded Stacked
type: docs
description: ""
key words: ""
weight: 30
url: /databar-expanded-card/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/databar) and [Generate](https://products.aspose.app/barcode/generate/databar) DataBar barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
- **DataBar Expanded** is intended for applications that require supplementary data to be encoded. In addition to encoding the Global Trade Item Number (GTIN) or Global Coupon Number (GCN), GS1 DataBar Expanded can encode additional application identifiers and data (known as "attributes"), such as sell-by date, weight, lot number, or expiration date. This symbol also supports the Serial Shipping Container Code (SSCC)-18 numbering structure when the "00" application identifier is used. 

- **DataBar Expanded Stacked** is a GS1 DataBar Expanded barcode that is split into multiple rows with a separator pattern between them.
GS1 DataBar Expanded Stacked is intended for applications that require supplementary data to be encoded. In addition to encoding the Global Trade Item Number (GTIN) or Global Coupon Number (GCN), DataBar Expanded Stacked can encode additional application identifiers and data (known as "attributes"), such as sell-by date, weight, lot number, or expiration date. This symbol also supports the Serial Shipping Container Code (SSCC)-18 numbering structure when the "00" application identifier is used.
  
|Examples|DataBar Expanded|DataBar Expanded Stacked|
| :-: | :-: | :-: | 
| |<img src="databarexpanded.png" heigh="75%" width="75%">|<img src="databarexpandedstacked.png" heigh="75%" width="75%">|
  
## **Features**
  
### **Encoding Character Set**
These barcode types can encode the following characters: 
- All numeric digits (0-9)
- All uppercase and lowercase letters (A-Z and a-z)
- Special function character (FNC1)
- Special characters: !, ", %, &, ', opening and closing parenthesis, *, +, ,, -, ., /, :, ;, (<), (=), (>), (?), (_), space.

### **Barcode Structure**
**DataBar Expanded**  
  
The **DataBar Expanded** barcode comprises the following elements:
- Left guard pattern (narrow space, narrow bar)
- Check digit
- One to eleven triplet sequences that consist of a finder pattern followed by two symbol characters (unless there is an odd number of characters, in which case the last triplet sequence has two elements instead of three)
- Right guard pattern (narrow bar, narrow space)

The first digit is a flag that indicates whether the barcode is part of a composite barcode. The data itself is split into groups that contain two data characters and one finder pattern. Each data character is 17 modules wide, using four bars and four spaces. The finder patterns separating the groups are 15 modules wide, using five bars and spaces total.
  
**DataBar Expanded Stacked**  
  
The symbol comprises the following elements:

- Top row, which consists of the left guard pattern (narrow space, narrow bar), a check digit, an even number of symbol characters (with a finder pattern between each symbol character pair), and the right guard pattern (narrow bar, narrow space)
- Separator pattern
- Additional rows and separator patterns as needed
- Bottom row, which consists of the left guard pattern, at least two symbol characters with finder patterns, and the right guard pattern

A quiet zone is not required.

### **Size Dimentions**
- **DataBar Expanded** is a variable-length symbology, the width of a symbol can vary from 53 to 543 modules. 
   
- **DataBar Expanded Stacked** barcodes can contain from two to 11 rows. The height of each row must be 34 modules, and the height of the separator pattern must be three modules. These dimensions make the symbol omnidirectionally readable.

### **Encoding Capacity and Data Density**
Each **DataBar Expanded** barcode can encode at most 74 numeric or 41 alphanumeric characters.

### **Checksum Controls**
DataBar Expanded and DataBar Expanded Stacked include a check digit that is compupted based on the modulo 211 algorithm.

## **Advantanges and Weaknesses**
DataBar Expanded and DataBar Expanded Stacked have been developed to be used in retail point-of-sale applications. These barcodes can be read omnidirectionally. These DataBar subtypes can apply any of GTIN formats, not only GTIN 12, 13, and 14.

## **Aspose Samples for DataBar Expanded and Expanded Stacked Barcpdes**
### **DataBar Expanded Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//generate DataBar Expanded Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarExpanded, "(01)12345678901231(21)SERIAL1234"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Parameters.Barcode.DataBar.IsAllowOnlyGS1Encoding = true;
    gen.Save($"{path}DataBarExpanded.png", BarCodeImageFormat.Png);
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

### **DataBar Expanded Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//recognize DataBar Expanded Barcode
using (BarCodeReader read = new BarCodeReader($"{path}DataBarExpanded.png", DecodeType.DatabarExpanded, DecodeType.DatabarExpandedStacked))
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

### **DataBar Expanded Stacked Generation Code Samples**

{{< tabs tabTotal="3" tabID="3" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//generate DataBar Expanded Stacked Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarExpandedStacked, "(01)12345678901231(21)SERIAL1234"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Parameters.Barcode.DataBar.IsAllowOnlyGS1Encoding = true;
    //set 3 rows
    gen.Parameters.Barcode.DataBar.Rows = 3;
    gen.Save($"{path}DataBarExpandedStacked.png", BarCodeImageFormat.Png);
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

### **DataBar Expanded Stacked Recognition Code Samples**

{{< tabs tabTotal="3" tabID="4" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//recognize DataBar Expanded Stacked Barcode
using (BarCodeReader read = new BarCodeReader($"{path}DataBarExpandedStacked.png", DecodeType.DatabarExpanded, DecodeType.DatabarExpandedStacked))
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
