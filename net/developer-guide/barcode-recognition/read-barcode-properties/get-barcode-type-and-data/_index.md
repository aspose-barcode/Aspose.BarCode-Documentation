---
title: Get Barcode Type and Encoded Data
type: docs
description: "This article describes how to read barcode parameters"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode C#"
ai_search_scope: "barcode_dotnet_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 10
feedback: BARCODECOM
url: /net/get-barcode-type-and-data/
---
  
## **Decode Barcode Type and Data**
To get the data encoded in a barcode and identify its type, class [*BarCodeResult*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult) provides the two most important fields, [*CodeText*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/codetext) and [*CodeType*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/codetype), respectively. The other parameter [*CodeTypeName*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/codetypename) represents the text name of a barcode symbology.
  
The following code sample explains how to get the data encoded in a barcode and its type for the sample barcode image provided below (in this case, a *QR Code* label).
 
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
{{< /highlight >}}

<p align="center"><img src="qrcodetext.png"></p> 
  
## **Read Barcode Data as Byte Stream**
In cases when it is necessary to get the data encoded in a barcode in the form of a byte stream, it can be read from the specific field of class [*BarCodeResult*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult) that is called [*CodeBytes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/codebytes).  
  
The following code snippet illustrates how to obtain barcode data as a stream of bytes for the sample *PDF417* barcode image provided below.  
   
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
{{< /highlight >}}

<p align="center"><img src="extcodebytes.png"></p>

## **Decode Barcode Data in Unicode Format**
In cases when the barcode data is encoded using a particular Unicode encoding, it can be read by calling the [*GetCodeText*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/methods/getcodetext) method and specifying the required encoding.  
  
The following code snippet shows how to get the data encoded in UTF8 as a result of reading a sample *Data Matrix* barcode given below.
   
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
{{< /highlight >}}

<p align="center"><img src="extunicodecodetext.png"></p>
   
  
