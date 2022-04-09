---
title: Decoding Barcode Properties and Metadata
type: docs
description: "This article describes how to read barcode parameters and encoded metadata"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcodes in Java"
weight: 40
url: /java/read-barcode-properties/
---

{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can test the quality of ***Aspose.BarCode*** recognition functionality and view the results online.{{% /alert %}}
  
## **Overview**
As a result of barcode reading, ***Aspose.BarCode for Java*** allows not only decoding the main data stored in a barcode, but also getting information about its technical parameters, such as type, placement region, orientation angle, and metadata. The library saves this information in a specific object type called [*BarCodeResult*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult) so that each instance of this class corresponds to one processed barcode. Further in this article, it is explained how to get the required information about barcode properties using the functionality of ***Aspose.BarCode for Java***. 

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Getting Barcode Type and Encoded Data**
To get the data encoded in a barcode and identify its type, class [*BarCodeResult*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult) provides the two most important methods, *getCodeText* and *getCodeType*, respectively. The *getCodeTypeName* method allows getting the text name of a barcode symbology.
  
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
  
## **Reading Barcode Data as Byte Stream**
In cases when it is necessary to get the data encoded in a barcode in the form of a byte stream, it can be read using a specific method of class [*BarCodeResult*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult) that is called *getCodeBytes*.  
  
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

## **Decoding Barcode Text in Unicode**
In cases when the barcode data is encoded using a particular Unicode encoding, it can be read by calling the *getCodeText* method passing the required encoding: getCodeText(java.nio.charset.Charset encoding).  
  
The following code snippet shows how to get the data encoded in UTF8 as a result of reading a sample *DataMatrix* barcode given below.
   
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
   
## **Recognition Quality Check**
In many cases, it is necessary to estimate whether the barcode has been recognized accurately. In ***Aspose.BarCode for Java***, this can be done using two specific methods of class [*BarCodeResult*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult): *getConfidence* and *getReadingQuality*.  
As a result of barcode reading, the *getConfidence* method returns a value from the [*BarCodeConfidence*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeConfidence) enum that corresponds to the recognition confidence level. Possible values of the [*BarCodeConfidence*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeConfidence) enumeration (*None*, *Moderate*, and *Strong*) are explained in the table below. The *getReadingQuality*]() parameter returns the estimate of recognition quality according to the identified confidence level: 0 for *None*; from 1 to 99; 100 for *Strong*.
  
|Confidence Level|Reading Quality Value|Description|
|---|---|---|
|None|0|If the confidence level returns *None*, it usually means that the source barcode is incorrect and its input data has been decoded with errors. However, it is still possible to get its type and place orientation in the source image, as well as partially decode inputted data|
|Moderate|80|Is returned for 1D and postal barcodes with weak or missing checksum settings. In this case, it is required to analyze the result of the *getReadingQuality* method; however, even in the case of high values (close to 80), the absolute correctness of barcode recognition is not guaranteed|
|Strong|100|Is returned for all 2D barcode types with Reed-Solomon error correction in case the quality setting has not been set to *getQualitySettings().setAllowIncorrectBarcodes(true)*. When this confidence level is returned, it means that barcode text has been decoded correctly, and the recognition process has been completed successfully|
  
The following code snippet explains how to get the recognition quality estimate for a sample barcode image.
  
{{< highlight csharp>}}
//recognize image
Console.WriteLine("ReadExtQuality:");
using (BarCodeReader read = new BarCodeReader($"{path}qr_code128.png", DecodeType.QR, DecodeType.Code128))
{
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine($"Confidence:{result.Confidence.ToString()}");
        Console.WriteLine($"ReadingQuality:{result.ReadingQuality.ToString()}");
    }
}
{{< /highlight >}}
  
## **Getting Barcode Placement Region and Orientation Angle**
In some cases, developers may need to get information about the placement region of a source barcode and its orientation angle. To enable such a possibility, ***Aspose.BarCode for Java*** provides a class called [*BarCodeRegionParameters*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeRegionParameters) that stores the following information:
-	Quadrangle – a quadrangle object that bounds a barcode
-	Rectangle - a rectangle object that bounds a barcode
-	Points – an array of points constituting a barcode
-	Angle – an orientation angle in degrees
  
The following code sample illustrates how to get the information about barcode placement region and orientation angle for the example barcode image provided below.

{{< highlight csharp>}}
//recognize image
Console.WriteLine("ReadExtRegion:");
using (BarCodeReader read = new BarCodeReader($"{path}qr_code128.png", DecodeType.QR, DecodeType.Code128))
{
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine($"Quadrangle:{result.Region.Quadrangle.ToString()}");
        Console.WriteLine($"Angle:{result.Region.Angle.ToString()}");
        Console.WriteLine($"Rectangle:{result.Region.Rectangle.ToString()}");
        string ptStr = "";
        foreach (Point pt in result.Region.Points)
            ptStr += pt.ToString() + "";
        Console.WriteLine($"Points:{ptStr}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="qr_code128.png" width="20%" height="20%"></p>

## **Getting Barcode Metadata**

### **Reading Metadata for Macro PDF417 and Macro PDF417 Standards**

To read metadata from *PDF417* barcodes, ***Aspose.BarCode for .NET*** provides a class called [*Pdf417ExtendedParameters*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/Pdf417ExtendedParameters) that provides various methods as listed in the table below.
  
|PDF417 Metadata Field|Description|
|---|---|
|*getPdf417MacroFileID*|Unique identifier of a barcode series or PDF417 file|
|*getPdf417MacroSegmentID*|Current segment identifier|
|*getPdf417MacroSegmentsCount*|Number of barcodes in a series|
|*getPdf417MacroFileName*|Name of a file|
|*getPdf417MacroChecksum*|Checksum of a file that is calculated using CCITT-16 polynomial|
|*getPdf417MacroFileSize*|Total size of bytes in a series|
|*getPdf417MacroTimeStamp*|Time of creating/sending the file|
|*getPdf417MacroAddressee*|Address of the file sender|
|*getPdf417MacroSender*|Name of the file sender|
  
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

### **Reading Metadata from QR Code with Structured Append**
To read metadata from *QR Code* barcodes, it is necessary to use a special class called [*QRExtendedParameters*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/QRExtendedParameters). These properties enable reading the information about *QR Code* barcodes with structured append that allows combining several *QR Code* labels into one. This information includes the following fields:

- *getQRStructuredAppendModeBarCodeIndex* - the sequence number of the current barcode (starting from 0)
- *getQRStructuredAppendModeBarCodesQuantity* - the number of barcodes in a composite *QR Code* image (can take values from 2 to 16)
- *getQRStructuredAppendModeParityData* - a byte that serves as a checksum identifier. In the general case, it is calculated as *XOR* of all bytes in which UTF16BE symbols are encoded using two bytes  
  
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
  
### **Reading Metadata from DataBar Barcodes with 2D Components**
To read metadata from *DataBar* barcodes with 2D components, the library provides a class called [*DataBarExtendedParameters*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/DataBarExtendedParameters). This property group includes a special method called *iss2DCompositeComponent* that is used to enable or disable a 2D component in *DataBar* barcodes.  
  
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

### **Reading Metadata for 1D Symbologies**
For some 1D symbologies, such as, for example, *EAN 13*, it is possible to separate the decoded barcode data into barcode information itself and the checksum value. This can be done using a special class called [*OneDExtendedParameters*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/OneDExtendedParameters) that provides the following method: *getValue* that stores the decoded 1D barcode text and *getCheckSum* that contains the result of checksum calculation.
  
This sample shows how to get 1D barcode value and checksum
 
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.EAN_13, "1234567890128");
 generator.save("c:\\test.png");
 BarCodeReader reader = new BarCodeReader("c:\\test.png", DecodeType.EAN_13);
 for(BarCodeResult result : reader.readBarCodes())
 {
    System.out.println("BarCode Type: " + result.getCodeTypeName());
    System.out.println("BarCode CodeText: " + result.getCodeText());
    System.out.println("BarCode Value: " + result.getExtended().getOneD().getValue());
    System.out.println("BarCode Checksum: " + result.getExtended().getOneD().getCheckSum());
}
 
<p align="center"><img src="ean13.png"></p>
  
### **Getting Raw Data from Code 128 Barcodes**
The input data in *Code 128* barcodes can be encoded in three different modes: A, B, or C. The library provides a class called [*Code128ExtendedParameters*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/Code128ExtendedParameters) with a special method called *getCode128DataPortions* that stores decoded parts of the input data together with information about their encoding mode.

This sample shows how to get code128 raw values
 
 BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Code128, "12345");
 generator.save("c:\\test.png");
 BarCodeReader reader = new BarCodeReader("c:\\test.png", DecodeType.CODE_128);
 for(BarCodeResult result : reader.readBarCodes())
 {
    System.out.println("BarCode Type: " + result.getCodeTypeName());
    System.out.println("BarCode CodeText: " + result.getCodeText());
    System.out.println("Code128 Data Portions: " + result.getExtended().getCode128());
 }

<p align="center"><img src="code128.png"></p>
