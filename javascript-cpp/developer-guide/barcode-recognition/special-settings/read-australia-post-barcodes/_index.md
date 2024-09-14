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
*Australia Post* is a 4-state postal symbology used in the Australian Post. In this barcode standard, input messages include specific 2-digit format control code (FCC) fields and 8-digit sorting code (SC) fields. FCC fields are used to indicate one of three available barcode types with different fixed lengths: 37, 52, or 67 bars. Depending on FCC, barcodes may contain a customer information (CI) field that identifies one of the encoding types that support numerical or alphanumeric symbols. Customer information can occupy 16 bars in 52-length barcodes or 31 bars in 67-length ones. The Australia Post standard contains a checksum and information used for Reed-Solomon data recovery.  
*See more details about this symbology [here](/barcode/javascript-cpp/postal-barcodes/#australia-post-symbology)*.  
  
Due to the possibility to add customer information in barcode input data, barcode recognition for *Australia Post* barcodes has some specifics. In ***Aspose.BarCode for JavaScript via C++***, developers can use class [*AustraliaPostSettings*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings) to customize recognition parameters for this barcode standard according to particular requirements. Further, the main properties of class [*AustraliaPostSettings*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings) are explained in detail.

## **Decode Customer Information in Standard Formats**
The *Australia Post* symbology allows encoding additional customer information in three different formats; automatic recognition of the format used for encoding is not possible. In ***Aspose.BarCode for JavaScript via C++***, the required decoding format can be set in the [*CustomerInformationInterpretingType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings/properties/customerinformationinterpretingtype) field that can take the following values as explained in the table below.
  
|Australia Post Encoding Table|Supported Symbols|
|---|---|
|CTable|Numerical digits, English letters, space symbol, and #|
|NTable|Numerical digits|
|Other|0, 1, 2, and 3 that correspond to H, A, D, and T states, respectively|
  
**CTable**  
  
The following code snippet explains how to set the decoding format using the *CTable* option for the barcode image shown below. 
  
{{< highlight csharp>}}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.AustraliaPost, "6201234567ASPOSE"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.BarHeight.Pixels = 50;
    gen.Parameters.Barcode.AustralianPost.AustralianPostEncodingTable = CustomerInformationInterpretingType.CTable;
    gen.Save($"{path}AustraliaPostCTable.png", BarCodeImageFormat.Png);
}

//read barcode image
Console.WriteLine("ReadAustraliaPostCTable:");
using (BarCodeReader read = new BarCodeReader($"{path}AustraliaPostCTable.png", DecodeType.AustraliaPost))
{
    read.BarcodeSettings.AustraliaPost.CustomerInformationInterpretingType = CustomerInformationInterpretingType.CTable;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="australiapostctable.png"></p>

**NTable**  
  
The following code sample shows how to apply the decoding format with the *NTable* option while reading the barcode image provided below. 
  
{{< highlight csharp>}}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.AustraliaPost, "620123456701234"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.BarHeight.Pixels = 50;
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
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="australiapostntable.png"></p>

**Other**  
  
The following code snippet demonstrates how to set the *Other* decoding format for the barcode image given below. 
  
{{< highlight csharp>}}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.AustraliaPost, "6201234567321032103210"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.BarHeight.Pixels = 50;
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
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="australiapostother.png"></p>

## **Remove Filling Patterns**
The *Australia Post* standard imposes using fixed size for each subtype. When barcode decoding is performed in the *CTable* format, the data filling empty space in the input message is decoded as symbol “z”. To avoid such a result, it is necessary to set the [*IgnoreEndingFillingPatternsForCTable*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings/properties/ignoreendingfillingpatternsforctable) property to *True*.  
  
The following code sample illustrates how to eliminate filling patters while using the *CTable* decoding mode for the barcode image demonstrated below. 

{{< highlight csharp>}}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.AustraliaPost, "6201234567END"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.BarHeight.Pixels = 50;
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
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
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
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="australiapostctableignoreending.png"></p>

## **Decode Customer Information in Custom Format**
***Aspose.BarCode for JavaScript via C++*** allows developers to decode customer information in their own format. For this purpose, the library provides a special interface called [*CustomerInformationDecoder*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings/properties/customerinformationdecoder). In such a way, decoding of barcode data is performed using this interface; the properties [*CustomerInformationInterpretingType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings/properties/customerinformationinterpretingtype
) and [*IgnoreEndingFillingPatternsForCTable*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/australiapostsettings/properties/ignoreendingfillingpatternsforctable) are ignored.  
  
The following code snippet explains how to decode customer information inputted in the *NTable* format while reading the sample *Australia Post* barcode shown below. 

{{< highlight csharp>}}
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
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.BarHeight.Pixels = 50;
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
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="australiapostcustomerinformationdecoder.png"></p>
