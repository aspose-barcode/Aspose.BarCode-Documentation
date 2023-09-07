---
title: Read Barcode Metadata
type: docs
description: "This article describes how to read barcode parameters and encoded metadata"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode C#"
weight: 30
url: /net/read-barcode-metadata/
---

## **Read Macro PDF417 and Macro PDF417 Metadata**

Metadata from *PDF417* barcodes can be obtained using methods of class [*Pdf417ExtendedParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/Pdf417ExtendedParameters) that are listed below.
  
|PDF417 Metadata Method|Description|
|---|---|
|*getPdf417MacroFileID*|Gets the unique identifier of a barcode series or a PDF417 file|
|*getPdf417MacroSegmentID*|Gets the current identifier of a segment|
|*getPdf417MacroSegmentsCount*|Returns the number of barcodes in a series|
|*getPdf417MacroFileName*|Returns the name of a file|
|*getPdf417MacroChecksum*|Gets the checksum value computed using CCITT-16 polynomial|
|*getPdf417MacroFileSize*|Returs the total size of bytes in a series|
|*getPdf417MacroTimeStamp*|Returns the time spent to generate/send the file|
|*getPdf417MacroAddressee*|Gets the address of the file sender|
|*getPdf417MacroSender*|Returns the name of the file sender|
  
<!--The following code sample explains how to obtain metadata from a *PDF417* barcode.  
 
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
{{< /highlight >}}-->
  
<p align="center"><img src="extpdf417meta.png"></p>  

## **Read Metadata from QR Codes with Structured Append**
To fetch metadata from *QR Code* barcodes with structured append, ***Aspose.BarCode for Java*** provides a special class called [*QRExtendedParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/QRExtendedParameters). Methods of this class enable reading the information from structured append that is used to combine several *QR Code* barcode into one. This data can be obtained using the following methods:

- *getQRStructuredAppendModeBarCodeIndex* - returns the sequence number of the current barcode (starting from 0)
- *getQRStructuredAppendModeBarCodesQuantity* - returns the number of barcodes in a composite *QR Code* barcode taht can take values from 2 to 16
- *getQRStructuredAppendModeParityData* - returns the checksum identifier byte that is usually computed as *XOR* of all bytes in which UTF16BE characters are encoded in two bytes  
  
<!--The code sample below shows how to fetch metadata from a sample *QR Code* barcode with structured append.
   
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
{{< /highlight >}}-->

<p align="center"><img src="extqrmeta.png"></p>
  
## **Read Metadata from DataBar Barcodes with 2D Components**
Metadata from *DataBar* barcodes with 2D components can be obtained using class called [*DataBarExtendedParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/DataBarExtendedParameters) that provides a special method called *is2DCompositeComponent*. This methods allows enabling or disabling a 2D component in *DataBar* barcodes.  
  
<!--The following code snippet shows how to fetch metadata from a sample *DataBar* barcode with a 2D component.
  
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
{{< /highlight >}}-->

<p align="center"><img src="extdatabarmeta.png"></p>

## **Read Metadata from 1D Barcodes**
Some 1D barcode types, i.e. *EAN 13*, allow separating barcode input information itself from the checksum value. To do this, class [*OneDExtendedParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/OneDExtendedParameters) provides the *getValue* method that allows getting 1D barcode text and the *getCheckSum* method that returns the result of checksum computation.
  
<!--The following code snippet explains how to get the barcode text of a EAN 13 barcode and its checksum value.
 
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.EAN_13, "1234567890128");
 generator.save("c:\\test.png");
 BarCodeReader reader = new BarCodeReader("c:\\test.png", DecodeType.EAN_13);
 for(BarCodeResult result : reader.readBarCodes())
 {
    System.out.println("BarCode Type: " + result.getCodeTypeName());
    System.out.println("BarCode CodeText: " + result.getCodeText());
    System.out.println("BarCode Value: " + result.getExtended().getOneD().getValue());
    System.out.println("BarCode Checksum: " + result.getExtended().getOneD().getCheckSum());
}-->
 
<p align="center"><img src="ean13.png"></p>
  
## **Get Raw Data from Code 128 Barcodes**
Input data stored in *Code 128* barcodes can be encoded in three ways: A, B, or C. Class [*Code128ExtendedParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/Code128ExtendedParameters) provides a special method called *getCode128DataPortions* that returns decoded parts of barcode input information and the encoding mode.

<!--The following code sample shows how to fetch *Code 128* raw data.

 BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Code128, "12345");
 generator.save("c:\\test.png");
 BarCodeReader reader = new BarCodeReader("c:\\test.png", DecodeType.CODE_128);
 for(BarCodeResult result : reader.readBarCodes())
 {
    System.out.println("BarCode Type: " + result.getCodeTypeName());
    System.out.println("BarCode CodeText: " + result.getCodeText());
    System.out.println("Code128 Data Portions: " + result.getExtended().getCode128());
 }-->

<p align="center"><img src="code128.png"></p>
