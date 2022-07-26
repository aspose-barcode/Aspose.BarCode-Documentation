---
title: UPC-E
description: "Overview on main parameters of UPC-E Barcode Type"
keywords: ""
type: docs
weight: 110
url: /info-cards/upc-e/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/code39) and [Generate](https://products.aspose.app/barcode/generate/code39) Code 39 barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
The UPC-E barcode is a Universal Product Code, the most widely used barcode in the United States. UPC-E is a variation of UPC-A, which allows for a more compact barcode by eliminating "extra" zeros. As the resulting UPC-E barcode is about half the size as an UPC-A barcode, UPC-E is generally used on products with very small packaging where a full UPC-A barcode could not fit.

<!--<p align="center"><img alt="UPC-E Barcode" src=".png"></p>-->

{{% alert color="primary" %}}You can find additional information of classes and properties that are used in ***Aspose.BarCode*** for linear barcode generation and recognition:
- [**Specific Parameters for 1D barcodes**](https://docs.aspose.com/barcode/net/managing-different-barcode-settings/)

{{% /alert %}} 

## **Usage Scenarios**
UPC-E is the condensed version of the standard sized UPC-A numeric barcode, used in grocery stores and other retail establishments across the country. The condensed version is used on smaller products whose packages don't have room to place the full sized UPC-A code.
  
## **Characteristics**
### **Encoding Character Set**
This type encodes numerical digits from 0 to 9 only.

### **Barcode Structure**
The symbol comprises the following elements:

- Leading quiet zone
- Guard pattern (start character)
- Six symbol characters
- Guard pattern (stop character)
- Trailing quiet zone

UPC-E encodes six digits of numeric message data together with a number system digit and a check digit, for a total of eight digits.

### **Size Dimensions**
With four available printing widths for the bars and spaces instead of just two, UPC-E takes about half the number of bars and spaces relative to Interleaved 2 of 5 to represent each character. However, the use of the wider bars and spaces nullifies this space savings. Interleaved 2 of 5 codes pack data more densely than UPC-E does.

### **Encoding Capacity and Data Density**
A UPC-E barcode is half the size of UPC-A, with 6 digits instead of 12. Other than that, the two codes are set up the same way, with a digit at the beginning to designate the type of product being scanned (regular product, coupon, weighted item, etc.) followed by a manufacturer's code, a product code, and, finally, a check digit to ensure accuracy.  
  
### **Checksum Controls**
UPC-A contains a check digit that is based on the modulo 10 (mod 10) algorithm.

## **Advantages and Limitations**
Its condensed size allows it to fit on smaller packages. It also has a check digit, to ensure accuracy when typing a code in by hand.
It is only a numeric code and cannot encode letters. Additionally, the fixed length limits the amount of information that can be encoded, making it fine for supermarkets, but inadequate for communicating more detailed information.

## **How to Generate and Read UPC-E Barcodes**
### **Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}


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
