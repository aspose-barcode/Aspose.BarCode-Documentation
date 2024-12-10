---
title: Read Australia Post Barcodes
type: docs
description: "This article describes how to decode Australia Post barcodes in Aspose.BarCode for JavaScript via C++"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcode JavaScript"
weight: 30
feedback: BARCODECOM
url: /javascript-cpp/read-australia-post/
---

{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can test the quality of ***Aspose.BarCode*** recognition functionality and view the results online.{{% /alert %}}
## **Overview**
*Australia Post* is a 4-state postal symbology used in the Australian Post. Input messages in this barcode standard include specific 2-digit format control code (FCC) fields and 8-digit sorting code (SC) fields. FCC fields indicate one of three available barcode types with fixed lengths of 37, 52, or 67 bars. Depending on the FCC, barcodes may include a customer information (CI) field that identifies one of the encoding types supporting numerical or alphanumeric symbols. Customer information can occupy 16 bars in 52-length barcodes or 31 bars in 67-length ones. The Australia Post standard also includes a checksum and Reed-Solomon data recovery information.  
*Learn more about this symbology [here](/barcode/javascript-cpp/postal-barcodes/#australia-post-symbology)*.

Given the option to add customer information in barcode input data, barcode recognition for *Australia Post* barcodes has specific considerations. In ***Aspose.BarCode for JavaScript via C++***, the [*AustraliaPostSettings*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings) class can be used to customize recognition settings for this barcode standard based on requirements. The main properties of [*AustraliaPostSettings*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings) are detailed below.

## **Decode Customer Information in Standard Formats**
The *Australia Post* symbology supports encoding additional customer information in three formats, but automatic recognition of the format used is not possible. In ***Aspose.BarCode for JavaScript via C++***, the required decoding format can be set using the [*CustomerInformationInterpretingType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings/properties/customerinformationinterpretingtype) property, which accepts the following values:

|Australia Post Encoding Table|Supported Symbols|
|---|---|
|CTable|Numerical digits, English letters, space, and #|
|NTable|Numerical digits only|
|Other|0, 1, 2, and 3 corresponding to H, A, D, and T states|

**CTable**

The following code snippet demonstrates how to set the decoding format to *CTable* for the barcode image shown below.

  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Generate Australia Post barcode with C Table encoding
var gen = new BarCodeInstance.BarcodeGenerator("AustraliaPost", "6201234567ASPOSE");
gen.Parameters.Barcode.XDimension = "4px";
gen.Parameters.Barcode.BarHeight = "50px";
gen.Parameters.Barcode.AustralianPost.AustralianPostEncodingTable = BarCodeInstance.CustomerInformationInterpretingType.CTable;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display the barcode image

// Read barcode image
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "AustraliaPost");
reader.BarcodeSettings.AustraliaPost.CustomerInformationInterpretingType = BarCodeInstance.CustomerInformationInterpretingType.CTable;
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    var result = reader.FoundBarCodes(i);
    console.log(`CodeType: ${result.CodeType}`);
    console.log(`CodeText: ${result.CodeText}`);
}

gen.delete();
reader.delete();

```
  
<p align="center"><img src="australiapostctable.png"></p>

**NTable**  
  
The following code sample shows how to apply the decoding format with the *NTable* option while reading the barcode image provided below. 
  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.AustraliaPost, "620123456701234"))
{
    gen.Parameters.Barcode.XDimension = "4px";
    gen.Parameters.Barcode.BarHeight = "50px";
    gen.Parameters.Barcode.AustralianPost.AustralianPostEncodingTable = CustomerInformationInterpretingType.NTable;
    gen.Save($"{path}AustraliaPostNTable.png", BarCodeImageFormat.Png);
}

//read barcode image
Console.WriteLine("ReadAustraliaPostNTable:");
using (BarCodeReader read = new BarCodeReader($"{path}AustraliaPostNTable.png", DecodeType.AustraliaPost))
{
    read.BarcodeSettings.AustraliaPost.CustomerInformationInterpretingType = CustomerInformationInterpretingType.NTable;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeType}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
```
  
<p align="center"><img src="australiapostntable.png"></p>

**Other**  
  
The following code snippet demonstrates how to set the *Other* decoding format for the barcode image given below. 
  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.AustraliaPost, "6201234567321032103210"))
{
    gen.Parameters.Barcode.XDimension = "4px";
    gen.Parameters.Barcode.BarHeight = "50px";
    gen.Parameters.Barcode.AustralianPost.AustralianPostEncodingTable = CustomerInformationInterpretingType.Other;
    gen.Save($"{path}AustraliaPostOther.png", BarCodeImageFormat.Png);
}

//read barcode image
Console.WriteLine("ReadAustraliaPostOther:");
using (BarCodeReader read = new BarCodeReader($"{path}AustraliaPostOther.png", DecodeType.AustraliaPost))
{
    read.BarcodeSettings.AustraliaPost.CustomerInformationInterpretingType = CustomerInformationInterpretingType.Other;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeType}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
```
  
<p align="center"><img src="australiapostother.png"></p>

## **Remove Filling Patterns**
The *Australia Post* standard imposes using fixed size for each subtype. When barcode decoding is performed in the *CTable* format, the data filling empty space in the input message is decoded as symbol “z”. To avoid such a result, it is necessary to set the [*IgnoreEndingFillingPatternsForCTable*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings/properties/ignoreendingfillingpatternsforctable) property to *True*.  
  
The following code sample illustrates how to eliminate filling patters while using the *CTable* decoding mode for the barcode image demonstrated below. 

[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.AustraliaPost, "6201234567END"))
{
    gen.Parameters.Barcode.XDimension = "4px";
    gen.Parameters.Barcode.BarHeight = "50px";
    gen.Parameters.Barcode.AustralianPost.AustralianPostEncodingTable = CustomerInformationInterpretingType.CTable;
    gen.Save($"{path}AustraliaPostCTableIgnoreEnding.png", BarCodeImageFormat.Png);
}

Console.WriteLine("ReadAustraliaPostCTableIgnoreEnding:");
//read barcode image with IgnoreEndingFillingPatternsForCTable set to true
Console.WriteLine("IgnoreEndingFillingPatternsForCTable: true");
using (BarCodeReader read = new BarCodeReader($"{path}AustraliaPostCTableIgnoreEnding.png", DecodeType.AustraliaPost))
{
    read.BarcodeSettings.AustraliaPost.CustomerInformationInterpretingType = CustomerInformationInterpretingType.CTable;
    read.BarcodeSettings.AustraliaPost.IgnoreEndingFillingPatternsForCTable = true;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeType}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}

//read barcode image with IgnoreEndingFillingPatternsForCTable set to false
Console.WriteLine("IgnoreEndingFillingPatternsForCTable: false");
using (BarCodeReader read = new BarCodeReader($"{path}AustraliaPostCTableIgnoreEnding.png", DecodeType.AustraliaPost))
{
    read.BarcodeSettings.AustraliaPost.CustomerInformationInterpretingType = CustomerInformationInterpretingType.CTable;
    read.BarcodeSettings.AustraliaPost.IgnoreEndingFillingPatternsForCTable = false;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeType}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
```
  
<p align="center"><img src="australiapostctableignoreending.png"></p>

## **Decode Customer Information in Custom Format**
***Aspose.BarCode for JavaScript via C++*** allows developers to decode customer information in their own format. For this purpose, the library provides a special interface called [*CustomerInformationDecoder*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings/properties/customerinformationdecoder). In such a way, decoding of barcode data is performed using this interface; the properties [*CustomerInformationInterpretingType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings/properties/customerinformationinterpretingtype
) and [*IgnoreEndingFillingPatternsForCTable*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings/properties/ignoreendingfillingpatternsforctable) are ignored.  
  
The following code snippet explains how to decode customer information inputted in the *NTable* format while reading the sample *Australia Post* barcode shown below. 

[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
class NTableDecoder : AustraliaPostCustomerInformationDecoder
{
    string[] N_Table = { "00", "01", "02", "10", "11", "12", "20", "21", "22", "30" };
    public string Decode(string customerInformationField)
    {
        StringBuilder bd = new StringBuilder();
        for (int i = 0; i < customerInformationField.Length; i += 2)
        {
            if (i + 2 <= customerInformationField.Length)
            {
                string tmp = customerInformationField.Substring(i, 2);
                for (int j = 0; j < N_Table.Length; j++)
                {
                    if (N_Table[j].Equals(tmp))
                    {
                        bd.Append(j);
                        break;
                    }
                }
            }
        }
        return bd.ToString();
    }
}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.AustraliaPost, "620123456701234"))
{
    gen.Parameters.Barcode.XDimension = "4px";
    gen.Parameters.Barcode.BarHeight = "50px";
    gen.Parameters.Barcode.AustralianPost.AustralianPostEncodingTable = CustomerInformationInterpretingType.NTable;
    gen.Save($"{path}AustraliaPostCustomerInformationDecoder.png", BarCodeImageFormat.Png);
}

//read barcode image
Console.WriteLine("ReadAustraliaPostCustomerInformationDecoder:");
using (BarCodeReader read = new BarCodeReader($"{path}AustraliaPostCustomerInformationDecoder.png", DecodeType.AustraliaPost))
{
    read.BarcodeSettings.AustraliaPost.CustomerInformationDecoder = new NTableDecoder();
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeType}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
```
  
<p align="center"><img src="australiapostcustomerinformationdecoder.png"></p>
