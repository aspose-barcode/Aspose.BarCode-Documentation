---
title: Aztec Code Rune
description: "Description of the Aztec Code Rune barcode type"
keywords: "Aztec Code, aztec rune code, aztec rune barcode, aztec rune type, Create aztec rune barcodes, Read aztec codes, read aztec rune code, what is aztec rune barcode, aztec rune barcodes, generate aztec rune code, matrix barcodes, 2D symbology, 2D barcodes, aztec specification, aztec rune generator, aztec rune reader, recognise aztec codes, scan aztec barcode"
type: docs
weight: 20
url: /info-cards/aztec-rune/
---
{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/aztec) and [Generate](https://products.aspose.app/barcode/generate/aztec) Aztec barcodes online. You can test the quality of ***Aspose.BarCode*** functionality and view the results online.{{% /alert %}}

## **Overview**
Aztec Rune corresponds to a small but distinct machine-readable mark designed on the basis of the Aztec Code specification. Such barcodes contain only the core symbol of a full-range Aztec Code label with an 8-bit mode message protected by error correction. This barcode type includes 256 tiny square marks having the size of 11x11 modules. Aztec Rune barcodes can be detected and decoded by Aztec Code scanners.  
Aztec Rune is defined in Annex A of standard ISO/IEC 24778.

<p align="center"><img src="aztecrune.png"></p>

## **Usage Scenarios**
It is intended for specific applications in which the input message can be limited to 3 digits, e.g. object tracking in Augmented Reality systems and marking of very small items.

## **Characteristics**
### Encoding Character Set
Aztec Rune allows encoding only numerical digits from 0 to 255.

### **Barcode Structure**
Each Aztec Rune includes a bulls-eye finder pattern, orientation patterns, and the input message with Reed-Solomon data. The finder and orientation patterns in an Aztec Rune are exactly as defined in the Aztec Code specification. As Aztec Runes are scanned from the center, no quiet zone is needed.

<details>  
<summary>Read more</summary>

- Finder pattern: a square bull's-eye symbol in the center that comprises 4 black and white square rings and the center black square.
- Orientation patterns: the layer surrounding the finder pattern that includes chevron-shaped orientation patterns in all corners composed of three one-module squares. 
- Data message: the rest of a barcode contains one data layer with the input message and Reed-Solomon data. This layer is scanned and decoded in a clockwise direction. 

</details>

### **Size Dimensions**
Aztec Rune barcodes have amaximum size of 11 x 11 modules and are very tiny. 

### **Encoding Capacity and Data Density**
Aztec Rune can encode up to 3 numerical digits or 1 byte.

### **Error Correction**
See the article [Aztec Barcode Family](/aztec-cards/) for information about the error correction mechanism.  

## **Advantages and Limitations**
Aztec Rune allows creating very compact matrix barcodes that still provide damage resistance and data recovery owing to the error correction mechanism.

## **How to Generate and Read Aztec Rune Barcodes**
### **Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

```csharp

//generate Aztec Rune Barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Aztec, "123"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    //set symbol mode Rune
    gen.Parameters.Barcode.Aztec.AztecSymbolMode = AztecSymbolMode.Rune;
    gen.Save($"{path}AztecRune.png", BarCodeImageFormat.Png);
}

```

{{< /tab >}}

{{< tab tabNum="2" >}}

```java

public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "AztecRune.png";//"path/to/image.png";
        //generate
        BarcodeGenerator bg = new BarcodeGenerator(EncodeTypes.CODE_39_EXTENDED, "Aspose");
        {
            bg.getParameters().getBarcode().getXDimension().setPixels(2);
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
 
```

{{< /tab >}}

{{< tab tabNum="3" >}}

```cpp

//generate Aztec Rune Barcode
    
System::SharedPtr<BarcodeGenerator> gen = System::MakeObject<BarcodeGenerator>(EncodeTypes::Aztec, u"123");
gen->get_Parameters()->get_Barcode()->get_XDimension()->set_Pixels(4.0f);
//set symbol mode Rune
gen->get_Parameters()->get_Barcode()->get_Aztec()->set_AztecSymbolMode(Aspose::BarCode::Generation::AztecSymbolMode::Rune);
gen->Save(path + u"AztecRune.png", Aspose::BarCode::Generation::BarCodeImageFormat::Png);

```

{{< /tab >}}

{{< /tabs >}}

### **Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

```csharp

//recognize Aztec Rune Barcode
using (BarCodeReader read = new BarCodeReader($"{path}AztecRune.png", DecodeType.Aztec))
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }

```

{{< /tab >}}

{{< tab tabNum="2" >}}

```java

public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "AztecRune.png";//"path/to/image.png";
        
        //recognize
        BarCodeReader br = new BarCodeReader(filePath, DecodeType.CODE_39_EXTENDED);
        BarCodeResult[] barCodeResults = br.readBarCodes();
        for (BarCodeResult result : barCodeResults)
        {
            System.out.println("CodeType: " + result.getCodeTypeName());
            System.out.println("CodeText: " + result.getCodeText());
        }
    }
 
```

{{< /tab >}}

{{< tab tabNum="3" >}}

```cpp

//recognize Aztec Rune Barcode
System::SharedPtr<BarCodeReader> read = System::MakeObject<BarCodeReader>(path + u"AztecRune.png", DecodeType::Aztec);
for (System::SharedPtr<BarCodeResult> result : read->ReadBarCodes())
    
    {
        System::Console::WriteLine(System::String(u"CodeType:") + result->get_CodeTypeName());
        System::Console::WriteLine(System::String(u"CodeText:") + result->get_CodeText());
    }

```

{{< /tab >}}

{{< /tabs >}}
