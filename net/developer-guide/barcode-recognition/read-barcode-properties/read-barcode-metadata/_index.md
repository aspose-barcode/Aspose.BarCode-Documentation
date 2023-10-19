---
title: Read Barcode Metadata
type: docs
description: "This article describes how to read barcode parameters and encoded metadata"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode C#"
weight: 30
feedback: BARCODECOM
url: /net/read-barcode-metadata/
---
  

## **Read Metadata from PDF417 and Macro PDF417 Barcodes**

To read metadata from *PDF417* barcodes, ***Aspose.BarCode for .NET*** provides a group of properties called [*Pdf417ExtendedParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/pdf417extendedparameters) that includes various fields as listed in the table below.
  
|PDF417 Metadata Field|Description|
|---|---|
|[*Pdf417MacroFileID*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/pdf417parameters/properties/pdf417macrofileid)|Unique identifier of a barcode series or PDF417 file|
|[*Pdf417MacroSegmentID*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/pdf417parameters/properties/pdf417macrosegmentid)|Current segment identifier|
|[*Pdf417MacroSegmentsCount*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/pdf417parameters/properties/pdf417macrosegmentscount)|Number of barcodes in a series|
|[*Pdf417MacroFileName*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/pdf417parameters/properties/pdf417macrofilename)|Name of a file|
|[*Pdf417MacroChecksum*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/pdf417parameters/properties/pdf417macrochecksum)|Checksum of a file that is calculated using CCITT-16 polynomial|
|[*Pdf417MacroFileSize*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/pdf417parameters/properties/pdf417macrofilesize)|Total size of bytes in a series|
|[*Pdf417MacroTimeStamp*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/pdf417parameters/properties/pdf417macrotimestamp)|Time of creating/sending the file|
|[*Pdf417MacroAddressee*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/pdf417parameters/properties/pdf417macroaddressee)|Address of the file sender|
|[*Pdf417MacroSender*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/pdf417parameters/properties/pdf417macrosender)|Name of the file sender|
  
The following code snippet shows how to get metadata from a sample *PDF417* barcode provided below.  
 
{{< highlight csharp>}}
//generate Macro PDF417 with metadata
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MacroPdf417, "Åspóse.Barcóde©"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Parameters.Barcode.Pdf417.Columns = 5;
    gen.Parameters.Barcode.Pdf417.Pdf417MacroFileID = 12345678;
    gen.Parameters.Barcode.Pdf417.Pdf417MacroSegmentID = 12;
    gen.Parameters.Barcode.Pdf417.Pdf417MacroSegmentsCount = 20;
    gen.Parameters.Barcode.Pdf417.Pdf417MacroFileName = "file01";
    //checksumm must be calculated in CCITT-16 / CRC-16-CCITT encoding
    //https://en.wikipedia.org/wiki/Cyclic_redundancy_check#Polynomial_representations_of_cyclic_redundancy_checks
    //for the example we use random number
    gen.Parameters.Barcode.Pdf417.Pdf417MacroChecksum = 1234;
    gen.Parameters.Barcode.Pdf417.Pdf417MacroFileSize = 400000;
    gen.Parameters.Barcode.Pdf417.Pdf417MacroTimeStamp = new DateTime(2019, 11, 1);
    gen.Parameters.Barcode.Pdf417.Pdf417MacroAddressee = "street";
    gen.Parameters.Barcode.Pdf417.Pdf417MacroSender = "aspose";
    gen.Save($"{path}ExtPDF417Meta.png", BarCodeImageFormat.Png);
}

//attempt to recognize PDF417 metadata
Console.WriteLine("ReadExtPDF417Meta:");
using (BarCodeReader read = new BarCodeReader($"{path}ExtPDF417Meta.png", DecodeType.MacroPdf417))
{
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine($"Pdf417MacroFileID:{result.Extended.Pdf417.MacroPdf417FileID}");
        Console.WriteLine($"Pdf417MacroSegmentID:{result.Extended.Pdf417.MacroPdf417SegmentID.ToString()}");
        Console.WriteLine($"Pdf417MacroSegmentsCount:{result.Extended.Pdf417.MacroPdf417SegmentsCount.ToString()}");
        Console.WriteLine($"Pdf417MacroFileName:{result.Extended.Pdf417.MacroPdf417FileName}");
        Console.WriteLine($"Pdf417MacroChecksum:{result.Extended.Pdf417.MacroPdf417Checksum.ToString()}");
        Console.WriteLine($"Pdf417MacroFileSize:{result.Extended.Pdf417.MacroPdf417FileSize.ToString()}");
        Console.WriteLine($"Pdf417MacroTimeStamp:{result.Extended.Pdf417.MacroPdf417TimeStamp.ToString()}");
        Console.WriteLine($"Pdf417MacroAddressee:{result.Extended.Pdf417.MacroPdf417Addressee}");
        Console.WriteLine($"Pdf417MacroSender:{result.Extended.Pdf417.MacroPdf417Sender}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="extpdf417meta.png"></p>  

## **Read Metadata from QR Code with Structured Append**
To read metadata from *QR Code* barcodes, it is necessary to use a group of properties called [*QrExtendedParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qrextendedparameters). These properties enable reading the information about *QR Code* barcodes with structured append that allows combining several *QR Code* labels into one. This information includes the following fields:

- [*QRStructuredAppendModeBarCodeIndex*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qrextendedparameters/properties/qrstructuredappendmodebarcodeindex) - the sequence number of the current barcode (starting from 0)
- [*QRStructuredAppendModeBarCodesQuantity*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qrextendedparameters/properties/qrstructuredappendmodebarcodesquantity) - the number of barcodes in a composite *QR Code* image (can take values from 2 to 16)
- [*QRStructuredAppendModeParityData*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qrextendedparameters/properties/qrstructuredappendmodeparitydata) - a byte that serves as a checksum identifier. In the general case, it is calculated as *XOR* of all bytes in which UTF16BE symbols are encoded using two bytes  
  
The code snippet given below explains how to get metadata for a sample *QR Code* image with structured append.
   
{{< highlight csharp>}}
//generate QR with metadata
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Åspóse.Barcóde©"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.QR.StructuredAppend.TotalCount = 3;
    gen.Parameters.Barcode.QR.StructuredAppend.SequenceIndicator = 1;
    gen.Parameters.Barcode.QR.StructuredAppend.ParityByte = 123;
    gen.Save($"{path}ExtQRMeta.png", BarCodeImageFormat.Png);
}

//attempt to recognize QR metadata
Console.WriteLine("ReadExtQRMeta:");
using (BarCodeReader read = new BarCodeReader($"{path}ExtQRMeta.png", DecodeType.QR))
{
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine($"BarCodesQuantity:{result.Extended.QR.QRStructuredAppendModeBarCodesQuantity}");
        Console.WriteLine($"BarCodeIndex:{result.Extended.QR.QRStructuredAppendModeBarCodeIndex}");
        Console.WriteLine($"ParityData:{result.Extended.QR.QRStructuredAppendModeParityData}");
    }
}
{{< /highlight >}}

<p align="center"><img src="extqrmeta.png"></p>
  
## **Read Metadata from DataBar Barcodes with 2D Components**
To read metadata from *DataBar* barcodes with 2D components, the library provides a group of properties called [*DataBarExtendedParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/databarextendedparameters). This property group includes a special parameter called [*Is2DCompositeComponent*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/databarextendedparameters/properties/is2dcompositecomponent) that is used to enable or disable a 2D component in *DataBar* barcodes.  
  
The following code sample illustrates how to get metadata from a sample *DataBar* barcode with a 2D component (shown below).
  
{{< highlight csharp>}}
//generate Databar with metadata
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarExpandedStacked, "ASPOSE.BARCODE"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Parameters.Barcode.DataBar.Rows = 2;
    gen.Parameters.Barcode.DataBar.Is2DCompositeComponent = true;
    gen.Save($"{path}ExtDataBarMeta.png", BarCodeImageFormat.Png);
}

//attempt to recognize Databar metadata
Console.WriteLine("ReadExtDataBarMeta:");
using (BarCodeReader read = new BarCodeReader($"{path}ExtDataBarMeta.png", DecodeType.DatabarExpanded, DecodeType.DatabarExpandedStacked))
{
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine($"Is2DCompositeComponent:{result.Extended.DataBar.Is2DCompositeComponent}");
    }
}
{{< /highlight >}}

<p align="center"><img src="extdatabarmeta.png"></p>

## **Read Metadata from 1D Barcodes**
For some 1D symbologies, such as, for example, *EAN 13*, it is possible to separate the decoded barcode data into barcode information itself and the checksum value. This can be done using a group of properties called [*OneDExtendedParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/onedextendedparameters) that provides the following fields: [*Value*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/onedextendedparameters/properties/value) that stores the decoded 1D barcode text and [*CheckSum*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/onedextendedparameters/properties/checksum) that contains the result of checksum calculation.
  
{{< highlight csharp>}}
//generate EAN 13 with metadata
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN13, "1234567890128"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Save($"{path}EAN13.png", BarCodeImageFormat.Png);
}

//attempt to recognize EAN 13 with the value and checksum
Console.WriteLine("ReadExtOneD:");
using (BarCodeReader read = new BarCodeReader($"{path}EAN13.png", DecodeType.EAN13))
{
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine($"Value:{result.Extended.OneD.Value}");
        Console.WriteLine($"CheckSum:{result.Extended.OneD.CheckSum}");
    }
}
{{< /highlight >}}

<p align="center"><img src="ean13.png"></p>
  
## **Get Raw Data from Code 128 Barcodes**
The input data in *Code 128* barcodes can be encoded in three different modes: A, B, or C. The library provides a group of properties called [*Code128ExtendedParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/code128extendedparameters) with a special field called [*Code128DataPortions*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/code128extendedparameters/properties/code128dataportions
) that stores decoded parts of the input data together with information about their encoding mode.

{{< highlight csharp>}}
//generate Code 128 with metadata
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "Aspose1234"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Save($"{path}Code128.png", BarCodeImageFormat.Png);
}

//try to recognize Code 128 with data portions
Console.WriteLine("ReadExtCode128Meta:");
using (BarCodeReader read = new BarCodeReader($"{path}Code128.png", DecodeType.Code128))
{
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        string data = "";
        foreach (Code128DataPortion portion in result.Extended.Code128.Code128DataPortions)
            data += "Type{" + portion.Code128SubType.ToString() +"}, Data{" + portion.Data + "};";
        Console.WriteLine($"Code128DataPortions:{data}");
    }
}
{{< /highlight >}}

<p align="center"><img src="code128.png"></p>
