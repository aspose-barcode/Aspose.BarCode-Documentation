---
title: ITF 14
description: " "
keywords: "ITF14, itf 14, itf14 barcode type, Create ITF 14 barcode, Read itf, what is itf14, itf14 barcodes, generate itf 14, linear barcodes, 1D barcode, linear barcode type, itf 14 extended, itf 14 specification"
type: docs
weight: 10
url: /info-cards/itf-39/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/code39) and [Generate](https://products.aspose.app/barcode/generate/code39) Code 39 barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
 

<p align="center"><img alt="ITF 14 Barcode" src=" .png"></p>

{{% alert color="primary" %}}You can find additional information of classes and properties that are used in ***Aspose.BarCode*** for ITF barcode generation and recognition:
- [**ITF Barcodes**](https://docs.aspose.com/barcode/net/itf-barcodes/)

{{% /alert %}} 

## **Usage Scenarios**

## **Characteristics**
### **Encoding Character Set**

### **Barcode Structure**

### **Size Dimensions**

### **Encoding Capacity and Data Density**

### **Checksum Controls**

## **Advantages and Limitations**

## **How to Generate and Read ITF 14 Barcodes**
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
