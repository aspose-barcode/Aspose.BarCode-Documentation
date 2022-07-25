---
title: EAN-5
description: " "
keywords: "EAN, EAN5, EAN barcodes, ean-5, ean 5 barcode type, Create ean 5 barcode, Read ean 5, what is ean5, ean 5 barcodes, generate ean 5, linear barcodes, 1D barcode, linear barcode type, ean5 specification"
type: docs
weight: 50
url: /info-cards/ean-5/
---

## **Overview**

EAN-5 and EAN 2 add-ons are only used in addition to EAN-13, EAN-8, and UPC. The EAN 5 and EAN 2 add-ons cannot be read by a scanner if they are used without these codes. 

<p align="center"><img alt="EAN-5 Barcode" src=" .png"></p>

{{% alert color="primary" %}}You can find additional information of classes and properties that are used in ***Aspose.BarCode*** for linear barcode generation and recognition:
- [**EAN-2 and EAN-5 as Supplement**](/barcode/net/ean2-and-ean5-as-supplement/)

{{% /alert %}} 

## **Usage Scenarios**
The EAN 5 add-on is often used for the price of books together with the ISBN code. 
  
## **Characteristics**
### **Encoding Character Set**
 
### **Barcode Structure**
The structure of the barcode is based on the value of the two digit to be encoded. The two digits treated as a single two-digit number is reduced modulo 4 and used to find the parity pattern to be used. The parity pattern repeats every 4 values.

### **Size Dimensions**

### **Encoding Capacity and Data Density**

### **Checksum Controls**
No check symbol is included in such add-on barcodes.

## **Advantages and Limitations**

## **How to Generate and Read EAN-5 Barcodes**
### **Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

```csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN13, "1234567890128");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.Barcode.Supplement.SupplementSpace.Pixels = 20;

//add the EAN-5 supplement barcode
gen.Parameters.Barcode.Supplement.SupplementData = "12345";
gen.Save($"{path}SupplementEAN5.png", BarCodeImageFormat.Png);

``` 

{{< /tab >}}

{{< tab tabNum="2" >}}


{{< /tab >}}

{{< tab tabNum="3" >}}


{{< /tab >}}

{{< /tabs >}}

### **Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}


{{< /tab >}}

{{< tab tabNum="2" >}}


{{< /tab >}}

{{< tab tabNum="3" >}}


{{< /tab >}}

{{< /tabs >}}
