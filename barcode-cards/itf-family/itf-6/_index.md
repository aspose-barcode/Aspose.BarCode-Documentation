---
title: ITF 6
description: " "
keywords: "ITF6, itf 6, itf6 barcode type, Create ITF 6 barcode, Read itf, what is itf6, itf6 barcodes, generate itf 6, linear barcodes, 1D barcode, linear barcode type, itf 6 extended, itf 6 specification"
type: docs
weight: 110
url: /info-cards/itf-6/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/itf) and [Generate](https://products.aspose.app/barcode/generate/itf) ITF barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
 

<p align="center"><img alt="ITF 6 Barcode" src=" .png"></p>

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

## **How to Generate and Read ITF 6 Barcodes**
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
