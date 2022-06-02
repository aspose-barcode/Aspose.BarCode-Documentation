---
title: Macro PDF417
description: ""
key words: ""
type: docs
weight: 10
url: /barcode/macro-pdf417-card/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/pdf417) and [Generate](https://products.aspose.app/barcode/generate/pdf417) PDF417 barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
Macro PDF417 is used to divide files that are too large to be encoded in a single symbol into smaller, encodable segments. Macro PDF417 is an implementation of PDF417 capable of encoding very large amounts of data into multiple PDF417 barcodes. These multiple barcodes are then scanned by a Macro PDF-compatible scanner, which reassembles them into one string of data. Each MacroPDF barcode segment shares a file ID with the other segments, which make up the entire barcode sequence. If the file ID is not the same, the scanner will assume that each of the segments belong to a different barcode sequence. To reassemble barcodes in the correct order, each segment of the barcode must have a unique segment index, starting at zero. This unique segment index allows the scanner to know how to reassemble the barcode segments, and allows reading symbols in non-sequential order. 

<p align="center"><img src="macropdf417permanent.png"></p>

## **Features**
  
### **Encoding Character Set**
See article [PDF417 Barcode Family](/barcode/pdf417-cards/) for information about characters supported for encoding in Macro PDF417 barcodes.  

### **Structure**
Macro PDF417 barcodes may contain from 1 to 30 columns with input data, 2 columns with auxiliary metainformation (such as row indicator, the number of rows and columns) and then, start and stop patterns. The number of rows can vary from 3 to 90. The main distinction between Macro PDF417 and Basic PDF417 is the possibility to encode additional metadata about barcode contents. This redundancy associated with auxiliary metadata allows reading such barcodes using laser scanners as well as reducing barcode image quality requirements.  
Macro PDF417 barcodes differ from Basic PDF417 as they contain additional control information used to support this distributed representation. This allows a decoder to make use of this information to correctly reconstruct and verify the file independently of the scanning order. 

### **Size Dimentions**
Macro PDF417 is applied to link together multiple basic PDF417 barcodes. See information about PDF417 sizing in article [PDF417 Barcode Family](/barcode/pdf417-cards/). 

### **Encoding Capacity and Data Density**
The capacity of Macro PDF417 is theoretically unlimited as it allows biding together up to 99,999 PDF417 labels. See more details about PDF417 capacity in article [PDF417 Barcode Family](/barcode/pdf417-cards/). 

### **Error Correction**
See article [PDF417 Barcode Family](/barcode/pdf417-cards/)

## **Advantanges and Weaknesses**
Macro PDF allows files of data to be represented logically and consecutively in a number of PDF417 symbols. Up to 99,999 PDF417 barcodes can be linked or concatenated and then scanned in any sequence to enable the original data file to be correctly reconstructed.

## **Aspose Samples for Macro PDF417 Generation and Recognition**
### **Macro PDF417 Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//GENERATE
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

### **Macro PDF417 Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

//RECOGNIZE
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
