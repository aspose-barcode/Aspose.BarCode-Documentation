---
title: Code 39
description: ""
key words: ""
type: docs
weight: 100
url: /barcode/code39-card/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/code39) and [Generate](https://products.aspose.app/barcode/generate/code39) Aztec barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**

Code 39 (also known as Code 3 of 9, Alpha39 or Barcode39) is a technical standard developed by Intermec Corporation in 1974 and used to encode information in the form of a barcode. Code 39 is a barcode symbology with variable length. Its specification is limited to 43 characters, including uppercase letters (A-Z), numerical digits, and some special characters. Each character is decoded by nine elements: five bars and four spaces. The Code 39 barcode is the easiest of the alpha-numeric barcodes to use and is designed for character self-checking, thus eliminating the need for check character calculations. 
This barcode type has low data density and does not allow ensuring reading accuracy as it does not require setting an obligatory checksum by default.  It was the first barcode symbology to use alphabetic characters in addition to numeric digits. Variations of Code 39 have been used extensively in multiple industries, notably in the US military as a component of the Logistics Applications of Automated Marking and Reading Symbols (LOGMARS) system.

<p align="center"><img src="code39.png"></p>

## **Features**
  
### **Encoding Character Set**
Code 39 supports encoding the 43-character ASCII set, including uppercase English letters, numerical digits, and special characters (-, ., $, /, +, %, and space). A special symbol '*' is used for both start and stop characters.

### **Structure**
Each Code 39 data character is represented by nine elements: five bars and four spaces, three of which are wide and six narrow. 

The symbol comprises the following elements:

- Starting quiet zone
- Start character
- One or more pairs of symbol characters that represent data (including an optional check digit)
- Stop character
- Ending quiet zone
- Intercharacter spaces (one module wide) that separate characters within the symbol

### **Size Dimentions**
The recommended minimum symbol height for manual scanning is 5.0 mm or 15 percent of the symbol width (excluding quiet zones), whichever is greater. The quiet zones must be at least 10X wide, where "X" is the current X dimension<!-->Create 'What is x-dimension?' page and add link to it here<-->.  
Code 39 can be to produced in different proportions: 2:1 and 3:1. This is the proportion between the thin and the thick lines of the code. As higher the proportion, the wider is the printed barcode with same contents, but even better is readability.

### **Encoding Capacity and Data Density**
Code 39 barcodes are variable length and usually store from 20 to 23 alphanumerical symbols.  
Although Code 39 - Full ASCII has the advantage of representing all 128 ASCII characters, it does sacrifice barcode character density to do so. When you encode characters that are native to the 43-character Code 39 - Regular character set into Code 39 - Full ASCII, your barcodes do not undergo any degradation in character density. However, because Full ASCII characters are represented by a two-character combination, they take up more space. 

### **Chechsum Controls**
Code 39 does not provide high recognition precision as it does not require setting obligatory checksum controls. It allows adding an optional check digit that is based on the modulo 43 (mod 43) algorithm.

## **Advantanges and Limitations**
Because of the amount of characters it can encode, Code 39 can be used to encode most of the information required in industrial applications. Moreover, barcodes created with the code 39 standards can be read by most of the barcode readers in the market.
As a drawback, the more information is encoded using code 39, the longer the code becomes. As a result, barcodes created with code 39 are not suitable for small labels. Code 39 barcode can be easily damaged and distorted like any linear barcode. It is a width-encoding code 39 symbology which can be quickly become unreadable on a slight ink-spread during printing.

## **Aspose Samples for Code 39 Generation and Recognition**

### **Code 39 Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//GENERATE
{{< highlight csharp>}}
//generate Code39 Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code39Extended, "Aspose"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Save($"{path}Code39.png", BarCodeImageFormat.Png);
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

### **Code 39 Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//RECOGNIZE
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
