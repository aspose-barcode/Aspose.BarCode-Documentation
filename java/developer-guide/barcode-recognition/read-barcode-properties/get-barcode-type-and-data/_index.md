---
title: Get Barcode Type and Encoded Data
type: docs
description: "This article describes how to read barcode parameters"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode C#"
weight: 10
url: /net/get-barcode-type-and-data/
---
  
## **Get Barcode Type and Encoded Data**
To obtain input barcode data and its symbology, *getCodeText* and *getCodeType* methods of class [*BarCodeResult*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult) can be used. The other method called *getCodeTypeName* returns the text name of the barcode type.
  
<!--The following code snippet shows how to use these methods.
 
{{< highlight csharp>}}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Åspóse.Barcóde©"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Save($"{path}QRCodetext.png", BarCodeImageFormat.Png);
}

//recognize image
Console.WriteLine("ReadExtCodetext:");
using (BarCodeReader read = new BarCodeReader($"{path}QRCodetext.png", DecodeType.QR))
{
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine($"CodeType:{result.CodeType.ToString()}");
        Console.WriteLine($"CodeTypeName:{result.CodeTypeName}");
    }
}
{{< /highlight >}}-->

<p align="center"><img src="qrcodetext.png"></p> 
  
## **Get Barcode Data as Byte Stream**
It is possible to load barcode data as a byte stream using a special method of class [*BarCodeResult*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult) that is called *getCodeBytes*. 

<!--The following code sample explains how to fetch barcode data as a byte stream.  
   
{{< highlight csharp>}}
byte[] encodedArr = { 0xFF, 0xFE, 0xFD, 0xFC, 0xFB, 0xFA, 0xF9 };

//encode array to string
StringBuilder strBld = new StringBuilder(encodedArr.Length);
foreach (byte bval in encodedArr)
    strBld.Append((char)bval);

//encode array of bytes
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, strBld.ToString()))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Parameters.Barcode.Pdf417.Pdf417CompactionMode = Pdf417CompactionMode.Binary;
    gen.Parameters.Barcode.Pdf417.Columns = 2;
    gen.Parameters.Barcode.CodeTextParameters.TwoDDisplayText = "Bytes mode";
    gen.Save($"{path}ExtCodeBytes.png", BarCodeImageFormat.Png);
}

//attempt to recognize array of bytes
Console.WriteLine("ReadExtCodeBytes:");
using (BarCodeReader read = new BarCodeReader($"{path}ExtCodeBytes.png", DecodeType.Pdf417))
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeTypeName:{result.CodeTypeName}");
        Console.WriteLine($"CodeBytes:{BitConverter.ToString(result.CodeBytes)}");
    }
{{< /highlight >}}-->

<p align="center"><img src="extcodebytes.png"></p>

## **Decode Barcode Text in Unicode**
For barcodes in which the barcode data is encoded in a Unicode encoding, the library provides the *getCodeText* method that can be used to enable the required encoding in the following format: getCodeText(java.nio.charset.Charset encoding).  
  
<!--The following code snippet shows how to get barcode data encoded using the UTF8 encoding.
   
{{< highlight csharp>}}
//create encoded Unicode codetext
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "Aspose常に先を行く"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.DataMatrix.CodeTextEncoding = Encoding.UTF8;
    gen.Save($"{path}ExtUnicodeCodeText.png", BarCodeImageFormat.Png);
}

//try to recognize Unicode codetext
Console.WriteLine("ReadExtUnicodeCodeText:");
using (BarCodeReader read = new BarCodeReader($"{path}ExtUnicodeCodeText.png", DecodeType.DataMatrix))
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeTypeName:{result.CodeTypeName}");
        Console.WriteLine($"GetCodeText:{result.GetCodeText(Encoding.UTF8)}");
    }
{{< /highlight >}}-->

<p align="center"><img src="extunicodecodetext.png"></p>
