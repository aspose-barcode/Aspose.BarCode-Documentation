---
title: Aztec Code Family
description: "General Overview on Aztec Code Barcode Type"
keywords: "Aztec Code, aztec barcode, aztec code full-range, full range aztec barcode, Create aztec barcodes, Read aztec codes, what is aztec code, aztec barcodes, generate aztec code, matrix barcodes, 2D symbology, 2D barcodes, aztec specification, aztec generator, aztec reader, recognise aztec codes, scan aztec barcode"
type: docs
weight: 40
url: /info-cards/aztec-full-range/
---

{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/aztec) and [Generate](https://products.aspose.app/barcode/generate/aztec) Aztec barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view results.{{% /alert %}}

Aztec Code is a family of two-dimensional (2D) barcode types that encode information in square modules with unique finder patterns in the center of barcode labels. Such finder patterns facilitate identifying cell locations while scanning and decoding Aztec barcodes. Aztec Code was introduced by Andrew Longacre and Robert Hussey at Welch Allyn, Inc in 1995 to provide higher reading accuracy than other 2D types. This type got his name based on the similarity of the central finder pattern to an Aztec pyramid viewed from above.
  
The Aztec Code barcode group includes three subtypes:

- [Full-Range Aztec Code](/barcode/info-cards/aztec-full-range/)
- [Aztec Rune](/barcode/info-cards/aztec-rune/)
- [Compact Aztec Code](/barcode/info-cards/aztec-compact/)
  
Further in this article, Full-Range Aztec Code is discussed. This information card outlines its key specifics, including the supported character set, barcode structure, size dimensions, data capacity, and error correction capability. Code samples for barcode generation and recognition through the ***Aspose.BarCode*** library are given [below](#asposesamples).

## **Overview**
Full-range Aztec Code is a 2D barcode type that allows encoding streams of bytes and alphanumeric symbols. Such barcodes are designed as square labels composed of black and white modules and several rings constituting a unique pattern in the center that improves scanning and decoding. This type supports the mechanism of Reed-Solomon error correction that allows ensuring data integrity and restoring barcode information in case of damage. Aztec Code benefits from increased density and reading precision. 

<p align="center"><img src="aztecfullrange.png" alt="Aztec Code Full-Range Barcode"></p>

{{% alert color="primary" %}}You can find the detailed description of classes and properties that are used in ***Aspose.BarCode for .NET*** for Aztec generation and recognition:
- [**Aztec Code in Aspose.BarCode for .NET**](/barcode/net/aztec-barcode/)

{{% /alert %}} 

## **Usage Scenarios**
Aztec Code is widely used to work with travel documents (e.g. airline tickets), car registration documentation, and healthcare applications. This barcode type is suitable for small item marking and tracking.

## **Characteristics**
### **Encoding Character Set**
This barcode type supports all 255 ASCII characters (digits 0-9, text, binary data), as well as FNC1 Flag 7 symbols.

### **Barcode Structure**
Full-range Aztec Code barcodes the core symbol is always square and is placed in the exact center of a barcode. It comprises a finder pattern, orientation patterns, and a mode message. The finder pattern has the central square, 3 black, and 3 white finder pattern rings. It is surrounded by several data layers (from 4 to 32) and a reference grid. In full-range Aztec barcodes, the core has a configuration composed of 15 x 15 modules. It is crucial to successfully detect and decode the core symbol before proceeding with decoding information fields. As Aztec Codes are read starting from the central symbol, no quiet zone is required.

<details>  
<summary>Read more</summary>

- Finder pattern: a square bull's-eye sign in the center that is composed of black and white square rings. The number of rings varies according to the size of a barcode.

- Orientation patterns: the first layer of modules surrounding the finder pattern that includes chevron-shaped orientation patterns in all corners. The first pattern placed at the upper left corner contains three black modules. The second one positioned upper-right is one white module followed by two black modules. The third one placed lower-right is one black module followed by two white modules. The fourth one placed lower-left includes three white modules.

- Mode message: determines the size of a barcode and the length of the input message.

- Reference grid: serves as an extension of the finder pattern to facilitate accurate mapping of the information field. It comprises one-module-wide rows and columns of black and white squares. One row and column go from the center of the finder pattern to label edges. Other rows and columns are placed at every 16th row and column counting from the finder pattern. Each of these rows and columns is embedded into the structure rather than surrounding the center as the data layers do.

- Data layers: the remaining elements of an Aztec Code label constitute one or more two-module-wide data layers that store input information and check digits. These layers are decoded in a clockwise direction. The first data layer is positioned near the first orientation pattern. Scanners can recognize data layers moving along a spiral.

</details>

### **Size Dimensions**
Full-Range Aztec barcodes include up to 32 data layers reaching the maximum size of 151 x 151 modules. In total, there are 33 various size configurations.  
The smallest possible number of modules is 15x15, and the largest possible configuration includes 151x151 modules. Aztec Code is one of the most compact barcode types. An Aztec label can be approximately 30 times smaller than a Code 39 barcode for the same input message. A quiet zone is not required as the unique finder pattern is placed in the center of barcodes.

### **Encoding Capacity and Data Density**
Aztec Code can encode both small and large input messages with customizable error correction settings. The barcode size gets adjusted automatically based on the amount of information to be encoded.  
  
Full-range Aztec can encode at most 3,832 numerical digits or 3,067 alphanumeric symbols or 1,914 bytes, which corresponds to the maximal Aztec Code configuration composed of 32 data layers and 151 x 151 modules. The smallest Aztec barcode can store up to 13 numeric or 12 alphabetic characters or 6 bytes. 

<details>  
<summary>Read more</summary>

Aztec Code capacity varies for different configurations depending on the preferred error correction level. One-layer full-range Aztec barcode with the size of 19 x 19 modules can encode at most 18 textual symbols or 15 numerical digits. The detailed table describing all supported configurations and their encoding capacities is provided in the ISO standard specification for Aztec Code. 

</details>

### **Error Correction**
This specification supports Reed-Solomon error correction. The required error correction level can be defined as a value from 5% to 95%. Error correction data cannot take less than three codewords. Setting a greater level of error correction leads to generating larger labels that are more resistant to distortions.  
  
Error correction levels over 23% are not recommended for use in cases when large input messages need to be encoded as this may lead to exceeding the barcode capacity. When barcodes are used in safe environments where the probability of damage is low, it is recommended to set the error correction level of 5%-10%. This will allow producing more compact barcode labels.

## **Advantages and Limitations**
This type has extremely high damage resistance capability. This barcode type uses the space more efficiently than other matrix types. The size can be also adjusted allowing for larger amounts of information to be stored. Such barcodes may be useful in the case of sending documentation via fax as they provide good readability even for low-resolution images.  
Compared with [QR Code](/barcode/info-cards/qr-code/), Aztec Code is more compact, does not require quiet zones and has better density. However, it does not support Kana or Kanji symbols.

## **How to Generate and Read Full-Range Aztec Barcodes**
<a name="asposesamples"></a>

### **Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}
//generate Aztec Full Range Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Aztec, "Åspóse.Barcóde©"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    //set symbol mode FullRange
    gen.Parameters.Barcode.Aztec.AztecSymbolMode = AztecSymbolMode.FullRange;
    //set error correction capacity to 10% (can be from 5% to 95%)
    gen.Parameters.Barcode.Aztec.AztecErrorLevel = 10;
    gen.Save($"{path}AztecFullRange.png", BarCodeImageFormat.Png);
}

{{< /highlight >}}


{{< /tab >}}

{{< tab tabNum="2" >}}
{{< highlight csharp>}}
public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "AztecFullRange.png";//"path/to/image.png";
        //generate
        BarcodeGenerator bg = new BarcodeGenerator(EncodeTypes.AZTEC, "Åspóse.Barcóde©");
        {
            bg.getParameters().getBarcode().getXDimension().setPixels(4);
            //set symbol mode FullRange
            bg.getParameters().getBarcode().getAztec().setAztecSymbolMode(AztecSymbolMode.FULL_RANGE);
            //set error correction capacity to 10% (can be from 5% to 95%)
            bg.getParameters().getBarcode().getAztec().setAztecErrorLevel(10);
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

{{< highlight cpp>}}

//generate Aztec Full Range Barcode

System::SharedPtr<BarcodeGenerator> gen = System::MakeObject<BarcodeGenerator>(EncodeTypes::Aztec, u"Åspóse.Barcóde©");
gen->get_Parameters()->get_Barcode()->get_XDimension()->set_Pixels(4.0f);
//set symbol mode FullRange
gen->get_Parameters()->get_Barcode()->get_Aztec()->set_AztecSymbolMode(Aspose::BarCode::Generation::AztecSymbolMode::FullRange);
//set error correction capacity to 10% (can be from 5% to 95%)
gen->get_Parameters()->get_Barcode()->get_Aztec()->set_AztecErrorLevel(10);
gen->Save(path + u"AztecFullRange.png", Aspose::BarCode::Generation::BarCodeImageFormat::Png);

{{< /highlight >}}

{{< /tab >}}

{{< /tabs >}}

### **Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

{{< highlight csharp>}}

//recognize Aztec Full Range Barcode
using (BarCodeReader read = new BarCodeReader($"{path}AztecFullRange.png", DecodeType.Aztec))
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
        String filePath = Global.getTestDataFolder("cards") + "AztecFullRange.png";//"path/to/image.png";
     
        //recognize
        BarCodeReader br = new BarCodeReader(filePath, DecodeType.AZTEC);
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

//recognize Aztec Full Range Barcode     
       
System::SharedPtr<BarCodeReader> read = System::MakeObject<BarCodeReader>(path + u"AztecFullRange.png", DecodeType::Aztec);
for (System::SharedPtr<BarCodeResult> result : read->ReadBarCodes())
    {
        System::Console::WriteLine(System::String(u"CodeType:") + result->get_CodeTypeName());
        System::Console::WriteLine(System::String(u"CodeText:") + result->get_CodeText());
    }

{{< /highlight >}}
 

{{< /tab >}}

{{< /tabs >}}
