---
title: DataBar Expanded / Expanded Stacked
type: docs
description: "Information about DataBar Expanded Barcode Type and Its Stacked Version"
key words: "DataBar, data bar barcode, databar symbology, Create databar barcodes, databar stacked, Read databar codes, what is databar, databar stacked barcodes, generate databar barcode, matrix barcodes, 2D symbology, 2D barcodes, databar specification, gs1, gs1 barcodes, gs1 databar, databar generator, databar reader, recognise data bar codes, scan databar barcode, databar family"
weight: 30
url: /info-cards/databar-expanded/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/databar) and [Generate](https://products.aspose.app/barcode/generate/databar) DataBar barcodes online. You can check ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
**DataBar Expanded** is intended for use in applications that require storing supplementary information. Besides Global Trade Item Numbers (GTINs) or Global Coupon Numbers (GCNs), DataBar Expanded can encode additional application identifiers and information (attributes), e.g. expiration date, product weight, lot number, etc. This barcode type supports the Serial Shipping Container Code (SSCC)-18 structure that uses "00" as an application identifier.  
  
**DataBar Expanded Stacked** is a specification based on DataBar Expanded that allows generating barcodes divided into many rows with a separator pattern between them.
    
|Examples|DataBar Expanded|DataBar Expanded Stacked|
| :-: | :-: | :-: | 
| |<img src="databarexpanded.png" heigh="75%" width="75%" alt="DataBar Expanded Barcode">|<img src="databarexpandedstacked.png" heigh="75%" width="75%" alt="DataBar Expanded Stacked Barcode">|
  
## **Features**
  
### **Encoding Character Set**
These barcode types can encode the following character sets: 
- All numeric digits (0-9)
- All uppercase and lowercase letters (A-Z and a-z)
- Special function symbol (FNC1)
- Special symbols: !, ", %, &, ', opening and closing parenthesis, *, +, ,, -, ., /, :, ;, (<), (=), (>), (?), (_), and space.

### **Barcode Structure**
**DataBar Expanded**  
  
Barcodes consist of the following elements:
- Left guard pattern (narrow space, narrow bar)
- Check digit
- 1 to 11 triplet sequences composed of a finder pattern and two data characters (if the number of characters is odd, the last triplet sequence is reduced to two elements)
- Right guard pattern (narrow bar, narrow space)

The first digit is used as a flag to indicate whether this barcode will be a part of a composite barcode. The input message is divided into groups that comprise two data characters (17 modules each) and one finder pattern. Finder patterns have a width of 15 modules wide and include five bars and spaces in total.
  
**DataBar Expanded Stacked**  
  
The structure includes the following elements:

- Top row composed of the left guard pattern (narrow space, narrow bar), a check digit, an even number of data characters (with a finder pattern between each pair), and the right guard pattern (narrow bar, narrow space)
- Separator pattern
- Auxiliary rows and separator patterns
- Bottom row comprising the left guard pattern, at least two data characters with finder patterns, and the right guard pattern

Quiet zones are not needed.

### **Size Dimensions**
DataBar Expanded is a variable-length barcode type that allows varying the width of a barcode from 53 to 543 modules.  
  
DataBar Expanded Stacked barcodes can include from 2 to 11 rows. The height of each row is 34 modules, and the height of the separator pattern equals 3 modules. This configuration enables omnidirectional readability for such barcodes.

### **Encoding Capacity and Data Density**
These symbologies allow encoding at most 74 numerical digits or 41 alphanumeric characters.

### **Checksum Controls**
Barcodes include check digits computed based on the modulo 211 algorithm.

## **Advantages and Weaknesses**
DataBar Expanded and DataBar Expanded Stacked have been developed for use in retail point-of-sale applications. Such barcodes can be read omnidirectionally. Unlike other DataBar symbologies that can use only selected GTIN formats, Expanded DataBar specifications are compatible with any of them. The enhanced capacity results in creating larger barcodes thus being inferior in terms of compactness compared with DataBar Omnidirectional.

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
