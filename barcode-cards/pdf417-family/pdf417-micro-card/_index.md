---
title: Micro PDF417
description: "Description of Micro PDF417 specifics"
key words: "PDF417 barcode, pdf 417 barcodes, micro pdf417 symbology, Create pdf417 barcodes, Read micro pdf417 barcode, what is micro pdf417, pdf 417 barcodes, generate micro pdf417, matrix barcodes, 2D symbology, micro pdf417 specification, pdf417 generator, pdf417 reader, recognize micro pdf 417, scan micro pdf417"
type: docs
weight: 30
url: /info-cards/micro-pdf417/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/pdf417) and [Generate](https://products.aspose.app/barcode/generate/pdf417) PDF417 barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
Micro PDF417 is a two-dimensional variable-length stacked symbology that has been developed to encode a moderate amount of data in a very compact space in cases when minimizing the barcode label size is the main concern. It is based on the PDF417 specification and adopts its main features. 

Micro PDF417 is similar to PDF417 in terms of its encoding modes, error correction mechanism, and supported encoding sets. Micro PDF417 does not inherit the configuration of PDF417 with 17-module patterns and row indicators. Instead, it uses a unique set of address patterns with the size of 10 modules. This design has been introduced to decrease the barcode width and facilitate linear scanning for narrow barcodes (row heights twice wider than the [X-dimension](/barcode/info-cards/x-dimension/)). Unlike PDF417, Micro PDF417 labels can be generated only following pre-defined configurations with fixed numbers of rows, columns, and error correction codewords, up to a maximum of four data columns composed of 44 rows. This symbology is suitable for applications that require improved space usage efficiency but can be satisfied with a capacity lower than that of Basic PDF417. Micro PDF can be used to create composite barcodes together with GS1 [DataBar](/barcode/info-cards/databar-family) barcodes.

Micro PDF417 is defined in standard ISO/IEC 24728.

<p align="center"><img src="micropdf417code.png" alt="Micro PDF417 Barcode></p>

{{% alert color="primary" %}}You can find the detailed description of classes and properties that are used in ***Aspose.BarCode for .NET*** for PDF417 generation and recognition:
- [**PDF417 in Aspose.BarCode for .NET**](/barcode/net/pdf417-and-macropdf417-barcode/)

{{% /alert %}} 

## **Features**
  
### **Encoding Character Set**
This symbology supports encoding all 256 ASCII characters and 8-bit binary data.  
Micro PDF417 applies various data compaction schemes to increase encoding efficiency. The following modes are supported to map the input message and codeword sequences:
- Text compaction mode
- Byte compaction mode
- Numeric compaction mode

### **Structure**
Each Micro PDF417 barcode label may comprise between 4 and 44 rows and from 1 to 4 columns. Only certain configurations including fixed numbers of rows and columns are supported. Each codeword gets encoded in a set of 4 bars and 4 spaces composed of 17 rectangular modules in a single row. Row height can be adjusted. It is possible to store Macro 05 and Macro 06 symbols in Micro PDF417 barcodes to denote industry-specific prefixes and suffixes in a single symbol to decrease the overall number of symbols. Unlike Basic PDF417, Micro PDF417 does not contain start and stop characters.
  
|Number of columns|Allowed Number of Rows|
|---|---|
|1|11, 14, 17, 20, 24, 28|
|2|8, 11, 14, 17, 20, 23, 26|
|3|6, 8, 10, 12, 15, 20, 26, 32, 38, 44|
|4|4, 6, 8, 10, 12, 15, 20, 26, 32, 38, 44|
  
The structure includes the following elements per row:
- Starting quiet zone
- Left-row address pattern
- Input message codewords and central-row patterns according to the selected configuration:
    - One-column configuration: one codeword
    - Two-column configuration: two codewords
    - Three-column configuration: one codeword, the central-row address pattern, two codewords
    - Four-column configuration: two codewords, the central-row address pattern, two codewords
- Right-row address pattern
- Ending quiet zone

### **Size Dimensions**
Dimensions vary on the size of the input message to be encoded. The height of Micro PDF417 barcodes can range from 4 to 44 rows, and the row height can vary from 1X to 10X, where X is the current value of the [X-dimension](/barcode/info-cards/x-dimension/) parameter. The overall width of a barcode can be from 40X to 101X. Quiet zones of 1X (at minimum) are needed on four sides.

### **Encoding Capacity and Data Density**
Micro PDF417 is capable of encoding at most 150 bytes of data or 266 alphanumeric characters or 366 numerical digits in configurations including up to 4 columns and 44 rows.

### **Error Correction**
Micro PDF417 uses the Reed-Solomon algorithm for error correction. The number of error correction codewords is strictly fixed for each configuration.

## **Advantages and Weaknesses**
This barcode type is used to create composite codes combined with the GS1 DataBar barcodes. Owing to its ability to encode large input messages taking very compact space, Micro PDF417 is often used in food industry business tasks in which the placement space limitation needs to be addressed and barcodes must be scanned in a quick and easy way by hand-scanners to track important information about goods.

## **Aspose Code Samples for Micro PDF417 Generation and Recognition**
### **Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//generate Micro PDF417 Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MicroPdf417, "Aspose"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Save($"{path}MicroPDF417.png", BarCodeImageFormat.Png);
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

### **Recognition Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//recognize Micro PDF417 Barcode
using (BarCodeReader read = new BarCodeReader($"{path}MicroPDF417.png", DecodeType.MicroPdf417))
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
