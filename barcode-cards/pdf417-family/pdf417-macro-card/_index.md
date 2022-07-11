---
title: Macro PDF417
description: "Description of Macro PDF417 Specification"
keywords: "PDF417 barcode, pdf 417 barcodes, macro pdf417 type, Create pdf417 barcodes, Read macro pdf417 barcode, what is macro pdf417, pdf 417 barcodes, generate macro pdf417, matrix barcodes, 2D symbology, macro pdf417 specification, pdf417 generator, pdf417 reader, recognize macro pdf 417, scan pdf417, many pdf417 barcodes, multiple pdf417, how to put back together macro pdf417"
type: docs
weight: 10
url: /info-cards/macro-pdf417/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/pdf417) and [Generate](https://products.aspose.app/barcode/generate/pdf417) PDF417 barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

## **Overview**
Macro PDF417 is a special feature that serves to divide files that are too large to be encoded in a single barcode into smaller encodable segments. Macro PDF417 is an implementation of the PDF417 standard that is capable of encoding very large amounts of information into multiple PDF417 barcodes. These labels can be then scanned by a Macro PDF-compatible scanner to reassemble them into a single massive of data. Each Macro PDF segment has a common file ID with the other segments thus constituting a barcode sequence. If file IDs do not match, the scanner will interpret such segments as those corresponding to different barcode sequences. To reassemble segments in the correct order, each barcode label must have a unique segment index that allows the scanner to identify how to reassemble barcode segments in the correct order even after reading them in a non-sequential order. 

<p align="center"><img src="macropdf417permanent.png" alt="Macro PDF417 Barcode"></p>

{{% alert color="primary" %}}You can find the detailed description of classes and properties that are used in ***Aspose.BarCode*** for PDF417 generation and recognition:
- [**PDF417 in Aspose.BarCode for .NET**](/barcode/net/pdf417-and-macropdf417-barcode/)

{{% /alert %}} 

## **Usage Scenarios**
Macro PDF417 can be used to divide information from a large file into multiple blocks that get encoded in a sequence of PDF417 barcodes and then can be reassembled together in the correct order.

## **Characteristics**
### **Encoding Character Set**
See the article [PDF417 Barcode Family](/barcode/info-cards/pdf417-family/) for the information about character sets supported for encoding in PDF417 barcodes.  

### **Barcode Structure**
Available configurations may contain from 1 to 30 columns with input information, 2 columns with metainformation (i.e. row indicator, the number of rows and columns), and finally, start and stop patterns. The number of rows can range from 3 to 90. The main distinction between Macro PDF417 and Basic PDF417 is the capability to encode additional metadata about barcode contents. This redundancy corresponding to auxiliary metadata allows reading such barcodes with laser scanners, as well as reducing image quality requirements.  
Macro PDF417 barcodes contain additional control data used to facilitate this distributed representation. It allows decoders to correctly reassemble and validate encoded segments regardless of the scanning order. 

### **Size Dimensions**
Macro PDF417 serves to link multiple PDF417 barcodes. See the information about PDF417 sizing in the article [PDF417 Barcode Family](/barcode/info-cards/pdf417-family/). 

### **Encoding Capacity and Data Density**
The capacity of Macro PDF417 is theoretically unlimited as it allows binding together up to 99,999 PDF417 labels. See more details about Basic PDF417 capacity in the article [PDF417 Barcode Family](/barcode/pdf417-cards/). 

### **Error Correction**
The same error correction mechanism as in Basic PDF417 is applied. See more information in the article [PDF417 Barcode Family](/barcode/info-cards/pdf417-family/).

## **Advantages and Limitations**
Macro PDF allows representing multiple files in logical and consecutive sequences of PDF417 barcode segments. Up to 99,999 PDF417 barcodes can be linked or concatenated and then scanned in any sequence to enable the correct reconstruction of the original file.

## **How to Generate and Read Macro PDF417**
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

{{< highlight csharp>}}

public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "MacroPDF417.png";//"path/to/image.png";
        //generate
        BarcodeGenerator bg = new BarcodeGenerator(EncodeTypes.PDF_417, "Åspóse.Barcóde©");
        {
            bg.getParameters().getBarcode().getXDimension().setPixels(2);
            //set 3 columns
            bg.getParameters().getBarcode().getPdf417().setColumns(3);
            //set error level 2
            bg.getParameters().getBarcode().getPdf417().setPdf417ErrorLevel(Pdf417ErrorLevel.LEVEL_2);
            //set metadata
            bg.getParameters().getBarcode().getPdf417().setPdf417MacroFileID(12345678);
            bg.getParameters().getBarcode().getPdf417().setPdf417MacroSegmentID(12);
            bg.getParameters().getBarcode().getPdf417().setPdf417MacroSegmentsCount(20);
            bg.getParameters().getBarcode().getPdf417().setPdf417MacroFileName("file01");
            //checksumm must be calculated in CCITT-16 / CRC-16-CCITT encoding
            //https://en.wikipedia.org/wiki/Cyclic_redundancy_check#Polynomial_representations_of_cyclic_redundancy_checks
            //for the example we use random number
            bg.getParameters().getBarcode().getPdf417().setPdf417MacroChecksum(1234);
            bg.getParameters().getBarcode().getPdf417().setPdf417MacroFileSize(400000);
            bg.getParameters().getBarcode().getPdf417().setPdf417MacroTimeStamp(new GregorianCalendar(2019, Calendar.FEBRUARY, 11).getTime());
            bg.getParameters().getBarcode().getPdf417().setPdf417MacroAddressee("street");
            bg.getParameters().getBarcode().getPdf417().setPdf417MacroSender("aspose");
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
    //generate Macro PDF417 Barcode
    System::SharedPtr<BarcodeGenerator> gen = System::MakeObject<BarcodeGenerator>(EncodeTypes::Pdf417, u"Åspóse.Barcóde©");
    gen->get_Parameters()->get_Barcode()->get_XDimension()->set_Pixels(2.0f);
    //set 3 columns
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Columns(3);
    //set error level 2
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Pdf417ErrorLevel(Aspose::BarCode::Generation::Pdf417ErrorLevel::Level2);
    //set metadata
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Pdf417MacroFileID(12345678);
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Pdf417MacroSegmentID(12);
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Pdf417MacroSegmentsCount(20);
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Pdf417MacroFileName(u"file01");
    //checksumm must be calculated in CCITT-16 / CRC-16-CCITT encoding
    //https://en.wikipedia.org/wiki/Cyclic_redundancy_check#Polynomial_representations_of_cyclic_redundancy_checks
    //for the example we use random number
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Pdf417MacroChecksum(1234);
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Pdf417MacroFileSize(400000);
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Pdf417MacroTimeStamp(System::DateTime(2019, 11, 1));
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Pdf417MacroAddressee(u"street");
    gen->get_Parameters()->get_Barcode()->get_Pdf417()->set_Pdf417MacroSender(u"aspose");
    gen->Save(path + u"MacroPDF417.png", Aspose::BarCode::Generation::BarCodeImageFormat::Png);
    {{< /highlight >}}
    
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

{{< highlight csharp>}}

public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "MacroPDF417.png";//"path/to/image.png";
        
        //recognize
        BarCodeReader br = new BarCodeReader(filePath, DecodeType.PDF_417,DecodeType.COMPACT_PDF_417,DecodeType.MACRO_PDF_417);
        BarCodeResult[] barCodeResults = br.readBarCodes();
        for (BarCodeResult result : barCodeResults)
        {
            System.out.println("CodeType: " + result.getCodeTypeName());
            System.out.println("CodeText: " + result.getCodeText());
            System.out.println("Pdf417MacroFileID:" + result.getExtended().getPdf417().getMacroPdf417FileID());
            System.out.println("Pdf417MacroSegmentID:" + result.getExtended().getPdf417().getMacroPdf417SegmentID());
            System.out.println("Pdf417MacroSegmentsCount:" + result.getExtended().getPdf417().getMacroPdf417SegmentsCount());
            System.out.println("Pdf417MacroFileName:" + result.getExtended().getPdf417().getMacroPdf417FileName());
            System.out.println("Pdf417MacroChecksum:" + result.getExtended().getPdf417().getMacroPdf417Checksum());
            System.out.println("Pdf417MacroFileSize:" + result.getExtended().getPdf417().getMacroPdf417FileSize());
            System.out.println("Pdf417MacroTimeStamp:" + result.getExtended().getPdf417().getMacroPdf417TimeStamp().toString());
            System.out.println("Pdf417MacroAddressee:" + result.getExtended().getPdf417().getMacroPdf417Addressee());
            System.out.println("Pdf417MacroSender:" + result.getExtended().getPdf417().getMacroPdf417Sender());
           
        }
    }

{{< /highlight >}} 

{{< /tab >}}

{{< tab tabNum="3" >}}

    {{< highlight csharp>}}
    //recognize Macro PDF417 Barcode
    System::SharedPtr<BarCodeReader> read = System::MakeObject<BarCodeReader>(path + u"MacroPDF417.png", System::MakeArray<System::SharedPtr<BaseDecodeType>>({DecodeType::Pdf417, DecodeType::CompactPdf417, DecodeType::MacroPdf417}));
    for (System::SharedPtr<BarCodeResult> result : read->ReadBarCodes())
    {
        System::Console::WriteLine(System::String(u"CodeType:") + result->get_CodeTypeName());
        System::Console::WriteLine(System::String(u"CodeText:") + result->get_CodeText());
        System::Console::WriteLine(System::String(u"Pdf417MacroFileID:") + result->get_Extended()->get_Pdf417()->get_MacroPdf417FileID());
        System::Console::WriteLine(System::String(u"Pdf417MacroSegmentID:") + System::Convert::ToString(result->get_Extended()->get_Pdf417()->get_MacroPdf417SegmentID()));
        System::Console::WriteLine(System::String(u"Pdf417MacroSegmentsCount:") + System::Convert::ToString(result->get_Extended()->get_Pdf417()->get_MacroPdf417SegmentsCount()));
        System::Console::WriteLine(System::String(u"Pdf417MacroFileName:") + result->get_Extended()->get_Pdf417()->get_MacroPdf417FileName());
        System::Console::WriteLine(System::String(u"Pdf417MacroChecksum:") + System::Convert::ToString(result->get_Extended()->get_Pdf417()->get_MacroPdf417Checksum()));
        System::Console::WriteLine(System::String(u"Pdf417MacroFileSize:") + System::Convert::ToString(result->get_Extended()->get_Pdf417()->get_MacroPdf417FileSize()));
        System::Console::WriteLine(System::String(u"Pdf417MacroTimeStamp:") + System::ObjectExt::ToString(result->get_Extended()->get_Pdf417()->get_MacroPdf417TimeStamp()));
        System::Console::WriteLine(System::String(u"Pdf417MacroAddressee:") + result->get_Extended()->get_Pdf417()->get_MacroPdf417Addressee());
        System::Console::WriteLine(System::String(u"Pdf417MacroSender:") + result->get_Extended()->get_Pdf417()->get_MacroPdf417Sender());
    }
    {{< /highlight >}}

{{< /tab >}}

{{< /tabs >}}
