---
title: Compact PDF417
description: "Overview on Compact PDF417 Barcode Type"
keywords: "PDF417 barcode, pdf 417 barcodes, compact pdf417 type, Create pdf417 barcodes, Read compact pdf417 barcode, what is compact pdf417, pdf 417 barcodes, generate compact pdf417, matrix barcodes, 2D symbology, compact pdf417 specification, pdf417 generator, pdf417 reader, recognize compact pdf 417, scan compact pdf417"
type: docs
weight: 20
url: /info-cards/compact-pdf417/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/pdf417) and [Generate](https://products.aspose.app/barcode/generate/pdf417) PDF417 barcode online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
Compact PDF417 (also known as Truncated PDF417) inherits main features from the PDF417 standard. This barcode type can be useful in cases when space considerations are crucial and barcode image damage is unlikely. In safe environments (e.g. an office), it is possible to use PDF417 barcodes in which right row indicators are omitted and the stop pattern is reduced to a single one-module bar. This configuration allows descreasing the amount of supporting symbols from 4 codewords to 2 codewords per row, achieving a sort of a trade-off between reading performance and damage resistance.

<p align="center"><img src="compactpdf417.png" alt="Compact PDF417 Barcode"></p>

{{% alert color="primary" %}}You can find the detailed description of classes and properties that are used in ***Aspose.BarCode for .NET*** for PDF417 generation and recognition:
- [**PDF417 in Aspose.BarCode for .NET**](/barcode/net/pdf417-and-macropdf417-barcode/)

{{% /alert %}} 

## **Usage Scenarios**
This barcode type can be useful in applications with strict placement limitations and a low probability of barcode damage. 

## **Characteristics**
### **Encoding Character Set**
Compact PDF417 allows encoding both byte streams and Unicode characters. 

### **Barcode Structure**
Compact PDF417 has the structure similar to Basic PDF417 and includes the following elements:
- Starting quiet zone
- Start pattern that defines the PDF417 format
- Left-row codeword that encodes information about the row (its number and the error correction level)
- Input message codewords (from 1 to 30) that store input information
- Stop pattern
- Closing quiet zone
  
The main difference between Compact PDF417 and Basic PDF417 is that the former contains the stop character pattern that is reduced to a single narrow bar and does not commprise the right-row codeword. 

### **Size Dimensions**
Compact PDF417 barcodes require less area compared with Basic PDF417 as the right-hand elements are removed (or truncated). 

### **Encoding Capacity and Data Density**
This barcode type can encode at most 1,108 bytes or 1,850 alphanumeric characters or 2,710 numerical digits in the maximum configuration of 30 columns and 90 rows.

### **Error Correction**
Error correction capability of this type is reduced compared with Basic PDF417 due to specifics of its design.

## **Advantages and Limitations**
The main advantage of Compact PDF417 is its compact size. However, it should be utilized primarily in safe and clean environments, as it is more prone to damage.

## **How to Read and Generate Compact PDF417**
### **Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//generate Compact PDF417 Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    //set Pdf417 truncated or Compact Pdf417
    gen.Parameters.Barcode.Pdf417.Pdf417Truncate = true;
    //set 3 columns
    gen.Parameters.Barcode.Pdf417.Columns = 3;
    //set error level 2
    gen.Parameters.Barcode.Pdf417.Pdf417ErrorLevel = Pdf417ErrorLevel.Level2;
    gen.Save($"{path}CompactPDF417.png", BarCodeImageFormat.Png);
}
{{< /highlight >}}

{{< /tab >}}

{{< tab tabNum="2" >}}

{{< highlight csharp>}}

public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "CompactPDF417.png";//"path/to/image.png";
        //generate
        BarcodeGenerator bg = new BarcodeGenerator(EncodeTypes.PDF_417, "Aspose");
        {
            bg.getParameters().getBarcode().getXDimension().setPixels(2);
            //set Pdf417 truncated or Compact Pdf417
            bg.getParameters().getBarcode().getPdf417().setPdf417Truncate(true);
            //set 3 columns
            bg.getParameters().getBarcode().getPdf417().setColumns(3);
            //set error level 2
            bg.getParameters().getBarcode().getPdf417().setPdf417ErrorLevel(Pdf417ErrorLevel.LEVEL_2);
            try
            {
                bg.save(filePath, BarCodeImageFormat.PNG);
            }
            catch (IOException e)
            {
                e.printStackTrace();
            }
        }       
    }

{{< /highlight >}} 

{{< /tab >}}

{{< tab tabNum="3" >}}

    {{< highlight csharp>}}
    //generate Compact PDF417 Barcode
    System::SharedPtr<BarcodeGenerator> gen = System::MakeObject<BarcodeGenerator>(EncodeTypes::Pdf417, u"Åspóse.Barcóde©");
    gen->get_Parameters()->get_Barcode()->get_XDimension()->set_Pixels(2.0f);
    //set Pdf417 truncated or Compact Pdf417
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Pdf417Truncate(true);
    //set 3 columns
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Columns(3);
    //set error level 2
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Pdf417ErrorLevel(Aspose::BarCode::Generation::Pdf417ErrorLevel::Level2);
    gen->Save(path + u"CompactPDF417.png", Aspose::BarCode::Generation::BarCodeImageFormat::Png);
    {{< /highlight >}}

{{< /tab >}}

{{< /tabs >}}

### **Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//recognize Compact PDF417 Barcode
using (BarCodeReader read = new BarCodeReader($"{path}CompactPDF417.png", DecodeType.Pdf417, DecodeType.CompactPdf417, DecodeType.MacroPdf417))
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
{{< /highlight >}}

{{< /tab >}}

{{< tab tabNum="2" >}}

{{< highlight csharp>}}

public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "CompactPDF417.png";//"path/to/image.png";
     
        //recognize
        BarCodeReader br = new BarCodeReader(filePath, DecodeType.PDF_417,DecodeType.COMPACT_PDF_417,DecodeType.MACRO_PDF_417);
        BarCodeResult[] barCodeResults = br.readBarCodes();
        for (BarCodeResult result : barCodeResults)
        {
            System.out.println("CodeType: " + result.getCodeTypeName());
            System.out.println("CodeText: " + result.getCodeText());
        }
    }

{{< /highlight >}} 

{{< /tab >}}

{{< tab tabNum="3" >}}

    {{< highlight csharp>}}
    //recognize Compact PDF417 Barcode
    System::SharedPtr<BarCodeReader> read = System::MakeObject<BarCodeReader>(path + u"CompactPDF417.png", System::MakeArray<System::SharedPtr<BaseDecodeType>>({DecodeType::Pdf417, DecodeType::CompactPdf417, DecodeType::MacroPdf417}));
    for (System::SharedPtr<BarCodeResult> result : read->ReadBarCodes())
    {
        System::Console::WriteLine(System::String(u"CodeType:") + result->get_CodeTypeName());
        System::Console::WriteLine(System::String(u"CodeText:") + result->get_CodeText());
    }
    {{< /highlight >}}


{{< /tab >}}

{{< /tabs >}}
