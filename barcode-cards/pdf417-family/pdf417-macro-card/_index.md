---
title: Macro PDF417
description: "Description of Macro PDF417 Specification"
key words: "PDF417 barcode, pdf 417 barcodes, macro pdf417 symbology, Create pdf417 barcodes, Read macro pdf417 barcode, what is macro pdf417, pdf 417 barcodes, generate macro pdf417, matrix barcodes, 2D symbology, macro pdf417 specification, pdf417 generator, pdf417 reader, recognize macro pdf 417, scan pdf417, many pdf417 barcodes, multiple pdf417, how to put back together macro pdf417"
type: docs
weight: 10
url: /info-cards/macro-pdf417/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/pdf417) and [Generate](https://products.aspose.app/barcode/generate/pdf417) PDF417 barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
Macro PDF417 is a special feature that serves to divide files that are too large to be encoded in a single barcode into smaller encodable segments. Macro PDF417 is an implementation of the PDF417 standard that is capable of encoding very large amounts of information into multiple PDF417 barcodes. These labels can be then scanned by a Macro PDF-compatible scanner to reassemble them into a single massive of data. Each Macro PDF segment has a common file ID with the other segments thus constituting a barcode sequence. If file IDs do not match, the scanner will interpret such segments as those corresponding to different barcode sequences. To reassemble segments in the correct order, each barcode label must have a unique segment index that allows the scanner to identify how to reassemble barcode segments in the correct order even after reading them in a non-sequential order. 

<p align="center"><img src="macropdf417permanent.png" alt="Macro PDF417 Barcode"></p>

{{% alert color="primary" %}}You can find the detailed description of classes and properties that are used in ***Aspose.BarCode for .NET*** for PDF417 generation and recognition:
- [**PDF417 in Aspose.BarCode for .NET**](/barcode/net/pdf417-and-macropdf417-barcode/)

{{% /alert %}} 

## **Features**
  
### **Encoding Character Set**
See the article [PDF417 Barcode Family](/barcode/info-cards/pdf417-family/) for the information about character sets supported for encoding in PDF417 barcodes.  

### **Structure**
Available configurations may contain from 1 to 30 columns with input information, 2 columns with metainformation (i.e. row indicator, the number of rows and columns), and finally, start and stop patterns. The number of rows can range from 3 to 90. The main distinction between Macro PDF417 and Basic PDF417 is the capability to encode additional metadata about barcode contents. This redundancy corresponding to auxiliary metadata allows reading such barcodes with laser scanners, as well as reducing image quality requirements.  
Macro PDF417 barcodes contain additional control data used to facilitate this distributed representation. It allows decoders to correctly reassemble and validate encoded segments regardless of the scanning order. 

### **Size Dimensions**
Macro PDF417 serves to link multiple PDF417 barcodes. See the information about PDF417 sizing in the article [PDF417 Barcode Family](/barcode/info-cards/pdf417-family/). 

### **Encoding Capacity and Data Density**
The capacity of Macro PDF417 is theoretically unlimited as it allows binding together up to 99,999 PDF417 labels. See more details about Basic PDF417 capacity in the article [PDF417 Barcode Family](/barcode/pdf417-cards/). 

### **Error Correction**
The same error correction mechanism as in Basic PDF417 is applied. See more information in the article [PDF417 Barcode Family](/barcode/info-cards/pdf417-family/).

## **Advantages and Weaknesses**
Macro PDF allows representing multiple files in logical and consecutive sequences of PDF417 barcode segments. Up to 99,999 PDF417 barcodes can be linked or concatenated and then scanned in any sequence to enable the correct reconstruction of the original file.

## **Aspose Samples for Macro PDF417 Generation and Recognition**
### **Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//generate Macro PDF417 Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    //set 3 columns
    gen.Parameters.Barcode.Pdf417.Columns = 3;
    //set error level 2
    gen.Parameters.Barcode.Pdf417.Pdf417ErrorLevel = Pdf417ErrorLevel.Level2;
    //set metadata
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
    gen.Save($"{path}MacroPDF417.png", BarCodeImageFormat.Png);
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

### **Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//read Macro PDF417 Barcode
using (BarCodeReader read = new BarCodeReader($"{path}MacroPDF417.png", DecodeType.Pdf417, DecodeType.CompactPdf417, DecodeType.MacroPdf417))
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine("Pdf417MacroFileID:" + result.Extended.Pdf417.MacroPdf417FileID);
        Console.WriteLine("Pdf417MacroSegmentID:" + result.Extended.Pdf417.MacroPdf417SegmentID.ToString());
        Console.WriteLine("Pdf417MacroSegmentsCount:" + result.Extended.Pdf417.MacroPdf417SegmentsCount.ToString());
        Console.WriteLine("Pdf417MacroFileName:" + result.Extended.Pdf417.MacroPdf417FileName);
        Console.WriteLine("Pdf417MacroChecksum:" + result.Extended.Pdf417.MacroPdf417Checksum.ToString());
        Console.WriteLine("Pdf417MacroFileSize:" + result.Extended.Pdf417.MacroPdf417FileSize.ToString());
        Console.WriteLine("Pdf417MacroTimeStamp:" + result.Extended.Pdf417.MacroPdf417TimeStamp.ToString());
        Console.WriteLine("Pdf417MacroAddressee:" + result.Extended.Pdf417.MacroPdf417Addressee);
        Console.WriteLine("Pdf417MacroSender:" + result.Extended.Pdf417.MacroPdf417Sender);
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
