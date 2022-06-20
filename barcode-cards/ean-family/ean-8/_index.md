---
title: EAN-8
description: " "
keywords: "EAN, EAN8, EAN barcodes, ean-8, ean 8 barcode type, Create ean 8 barcode, Read ean 8, what is ean-8, ean 8 barcodes, generate ean-8, linear barcodes, 1D barcode, linear barcode type, ean88 specification"
type: docs
weight: 30
url: /info-cards/ean-8/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/code39) and [Generate](https://products.aspose.app/barcode/generate/code39) EAN barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
An EAN-8 is a barcode derived from the longer European Article Number (EAN-13) code. EAN-8 barcodes may be used to encode GTIN-8s which are another set of product identifiers from the GS1 System. It begins with a 2- or 3-digit GS1 prefix (which is assigned to each national GS1 authority) 5- or 4-digit item reference element depending on the length of the GS1 prefix, and a checksum digit.

<p align="center"><img alt="EAN-8 Barcode" src=" .png"></p>

{{% alert color="primary" %}}You can find additional information of classes and properties that are used in ***Aspose.BarCode*** for linear barcode generation and recognition:
- [**Specific Parameters for 1D barcodes**](https://docs.aspose.com/barcode/net/managing-different-barcode-settings/)

{{% /alert %}} 

## **Usage Scenarios**
It was introduced for use on small packages where an EAN-13 barcode would be too large; for example on cigarettes, pencils, and chewing gum packets.
  
## **Characteristics**
### **Encoding Character Set**
 
### **Barcode Structure**

### **Size Dimensions**

### **Encoding Capacity and Data Density**

### **Checksum Controls**

## **Advantages and Limitations**

## **How to Generate and Read EAN-8 Barcodes**
### **Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

Code

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
//recognize Code39 Barcode
using (BarCodeReader read = new BarCodeReader($"{path}Code39.png", DecodeType.Code39Standard, DecodeType.Code39Extended))
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
