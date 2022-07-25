---
title: EAN-2
description: " "
keywords: "EAN, EAN2, EAN barcodes, ean-2, ean 2 barcode type, Create ean 2 barcode, Read ean 2, what is ean2, ean 2 barcodes, generate ean 2, linear barcodes, 1D barcode, linear barcode type, ean2 specification"
type: docs
weight: 40
url: /info-cards/ean-2/
---

## **Overview**

EAN-2 add-on barcodes are only used in addition to EAN 13, EAN 8 and UPC. The EAN 5 and EAN 2 add-ons cannot be read by a scanner if they are used without these codes. 

<p align="center"><img alt="EAN-2 Barcode" src=" .png"></p>

{{% alert color="primary" %}}You can find additional information of classes and properties that are used in ***Aspose.BarCode*** for linear barcode generation and recognition:
- [**EAN-2 and EAN-5 as Supplement**](/barcode/net/ean2-and-ean5-as-supplement/)

{{% /alert %}} 

## **Usage Scenarios**
The EAN 2 add-on is often used on newspapers, periodicals, and magazines to indicate an issue number. 
  
## **Characteristics**
### **Encoding Character Set**
 
### **Barcode Structure**

### **Size Dimensions**

### **Encoding Capacity and Data Density**

### **Checksum Controls**
No check digit is added for this type.

## **Advantages and Limitations**

## **How to Generate and Read EAN-2 Barcodes**
### **Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

```csharp

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN13, "1234567890128");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Parameters.Barcode.Supplement.SupplementSpace.Pixels = 20;
//add the EAN-2 supplement barcode
gen.Parameters.Barcode.Supplement.SupplementData = "12";
gen.Save($"{path}SupplementEAN2.png", BarCodeImageFormat.Png);

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
