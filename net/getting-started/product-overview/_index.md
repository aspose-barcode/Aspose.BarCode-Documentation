---
title: Product Overview
type: docs
weight: 10
url: /net/product-overview/
---
The present article introduces ***Aspose.BarCode for .NET*** and its main concepts, as well as general technical details that are important to start working with the library. Here, you can find the description of its purpose, functionality, key features, requirements to input and output image formats, important classes, and supported platforms.

## **Product Description**

Aspose.BarCode for .NET is a multifunctional component library realised through Managed C# to address various barcode processing tasks. It allows deploying generation and recognition functionality for different barcode types (linear, matrix, and postal) at any angle in a fast and easy way. This library enables compatibility with most of existing barcode specifications and standards, supporting over 60 symbologies (1D, 2D including QR codes, and postal). The detailed listing of all available barcode symbologies is provided in [Barcode Types and Image Formats](/barcode/net/barcode-types-and-image-formats/).  
  
Aspose.BarCode for .NET can be utilized in three ways: through a console application, Windows Forms, or WPF. Using GUI controls in Aspose.BarCode for .NET, developers can drag and drop controls on Windows Forms and set properties in the GUI-mode. For developers who want to work with barcodes in the backend, the library provides the corresponding class ***BarcodeGenerator***. Finally, Aspose.BarCode for .NET enables a DLL for the Microsoft WPF framework to allow implementing WPF-based barcode applications.  
  
Aspose.BarCode for .NET benefits from important characteristics that make it an efficient, flexible, and easy to use tool. First, it is a fully functional library that enables both generating and recognizing barcodes. Moreover, barcodes can be generated in various high-quality image formats inlcuding two vector ones. The other key advantage is that Aspose.BarCode for .NET allows recognizing barcodes even of a very low quality or being significantly distorted. Therefore, the recognition quality is very High for most of available barcode types.
Aspose.BarCode for .NET provides full-featured demos and code samples prepared in C# to allow developers getting a better understanding of the library and its capabilities.

<!--Aspose.BarCode for .NET is implemented using Managed C#. 

It allows developers to quickly and easily add barcode generation and recognition functionality to their Microsoft .NET applications (WinForms, WPF, and ASP.NET). Aspose.BarCode provides fully featured demos and working examples written in C# for developers to have a better understanding of our product. Using these demos, developers can quickly learn about the features provided by Aspose.BarCode. Using GUI controls in Aspose.BarCode, developers can drag and drop the controls on Windows Forms and set their properties in GUI mode like other controls in the .NET Framework. For the developers who are only interested in the backend processing of barcodes, Aspose.BarCode also provides a simple barcode class to ease their jobs.Aspose.BarCode for .NET supports the most established barcode standards and barcode specifications. It can export to multiple image formats including BMP, GIF, JPEG, PNG, TIFF, EMF, and SVG. Developers can use any kind of printer to print barcodes but naturally, the quality of the printed barcode images will be affected by the printer's resolution. Aspose.BarCode also supports the WPF framework, so that you can generate and recognize barcodes in your WPF applications.-->

## **Main Features**

Aspose.BarCode for .NET supports multiple features to adress specific business needs. It is noteworthy that Aspose.BarCode for .NET enables wide functionality for setting and tailoring an efficient barcode processing system. One of the most important functions is the possiblity to customize the parameters of generated barcodes, such as background color, bar color, rotation angle, X-dimension, image quality, resolution, captions, size, and others. Moreover, this library supports various recognition and imaging features.  
The main features include: 
- Barcode generation and recognition of 60+ symbologies
- Reading 1D and 2D barcodes at any angle and from any image quality
- Generating barcodes with specific parameters, such as error correction mode, ECI, or embedded matadata
- Image rotation at any angle 
- Label printing 
- Saving to or loading from stream or file 
- Encoding and decoding non-English characters in 2D types
- Scanning from multi-page TIFF
- and many others.
  
The full list of features can be found in [Product Features](/barcode/net/product-features/).  

## **System Compatibility**
Aspose.BarCode for .NET supports any 32-bit or 64-bit operating system having installed .NET framework 2.0 or later / .Net Core 2.1 or later with System.Drawing.Common (.Net 5 inlcuded) / any other .NET framework supporting the fist two ones. Aspose.BarCode for .NET can be used in any .NET application, including WinForms, WPF, ASP.NET, Mono, Xamarin, UWP, and .NET core. More technical details on this subject are provided in [System Requirements](/barcode/net/system-requirements/).

## **Library Contents**
Aspose.BarCode for .NET includes three main clasess: BarcodeReader to realize barcode scanning and recognizing, BarcodeGenerator to implement barcode generation according to the desired format requirements, and ComplexBarcode to work with specific barcodes, such as SWISS QR and others. 
<!--For detailed instructions how to work with these classes and their methods, you can refer to [Developer Guide](/barcode/net/product-features/)-->
### **Class BarcodeReader**
Aspose.BarCode for .NET contains class BarCodeReader that is aimed at handling barcode image recognition. BarCodeReader has the following basic settings. First, it requires to specify the symbology type in the constructor of BarCodeReader class and call BarCodeReader.ReadBarCodes() method to recognize barcodes from an image. Then, BarCodeReader applies machine vision algorithms to extract machine-readable tags from the captured image.  
In Aspose.BarCode for .NET, image reading and identifying barcode regions can be performed for all recognized barcodes in an image. Before reading, barcodes have to be distinguished from other text lines/objects in the image by detecting their edges. To implement this, BarCodeReader.ReadBarCodes() method is used. Then, the region of a barcode is identified using BarCodeResult.Region that returns the recognized region and the barcode angle.  
Class BarCodeReader provides the following features to achieve the best possible balance depending on specific requirements:
-	Multi-threading support. This feature involves additional processor cores to speed up algorithm calculations, where possible.
-	Barcode type selection. Specifying required barcode types instead of using AllSupportedTypes allows reducing recognition time.
-	Quality settings. This set of options allows customizing the barcode reading engine according to a type of image and possible distortions. Disabling some options allows increasing recognition speed while enabling options increases recognition quality.
-	Region selection. It is possible to select target regions in which barcode images might be located so that the reading engine will read barcode data only from the selected regions. However, BarCodeReader uses its own algorithms for barcode area identification, and the incorrect use of this option may increase recognition time.

### **Class BarcodeGenerator**
One of the key features of Aspose.BarCode for .NET is barcode generation performed through specifying symbologies, setting code text (information to be encoded to a barcode image), and customizing appearance-related properties. Class BarCodeGenerator supports both 1D and 2D barcode types. It encapsulates both types of barcodes into one unified interface. 

### **Class ComplexBarcode**
Class ComplexBarcode allows implementing the generation of barcode documents to work with complex barcodes. At present, it supports processing only Swiss QR Code. The Swiss QR Code is used to manage QR bill in payments that replace previous payment slips. The Swiss QR Code contains all necessary payment information required to initiate payments or to process a QR invoice. Class ComplexBarcode contains SwissQRBill and SwissQRCodetext classes that enable various functions to work with Swiss QR Codes, such as getting or setting the account number of a creditor, alternative payments schemes, payment amount, currency, etc.

### **Examples**
Here, you can see some code samples for simple operations, such as generating a barcode using Code128 or recognizing a barcode from a stream.
#### **Generate a Barcode using Code128**
{{< highlight csharp>}}
// instantiate object and set different barcode properties
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Code128, "1234567");
generator.Parameters.Barcode.XDimension.Millimeters = 1f;

// save the image to your system and set its image format to Jpeg
generator.Save(dir + "output.png", BarCodeImageFormat.PNG);
{{< /highlight >}} 

#### **Recognize Barcodes from a File**
{{< highlight csharp>}}
// Read file from directory with DecodeType.EAN13
using (BarCodeReader reader = new BarCodeReader(dataDir + "Scan.зтп", DecodeType.EAN13))
{
    foreach (BarCodeResult result in reader.ReadBarCodes())
    {
        // Read symbology type and code text
        Console.WriteLine("Symbology Type: " + result.CodeType);
        Console.WriteLine("CodeText: " + result.CodeText);
    }
}
{{< /highlight >}} 

#### **Recognize a Barcode from a Stream**
{{< highlight csharp>}}
using (FileStream lStream = new FileStream(dataDir + "Scan.png", FileMode.Open, FileAccess.Read, FileShare.Read))
{
    using (BarCodeReader reader = new BarCodeReader(lStream))
    {
        //other way to set
        reader.SetBarCodeImage(lStream);
        foreach (BarCodeResult result in reader.ReadBarCodes())
            Console.WriteLine("BarCode CodeText: " + result.CodeText);
    }
}
{{< /highlight >}} 

## **Licencing**
License is required to obtain the acces to some advance properties of Aspose.BarCode for .NET. The evaliuation mode allows generating barcodes without any restrictions; however, a watermark is placed on the resulting image. The evaluation version of Aspose.BarCode only supports recognising of Code39 barcodes. To test how recognition works, a full-featured demo is available for all supported barcode symbologies. 
More detailed information about why and how to apply for a license and how to sei it is provided in [Licensing](/barcode/net/licensing/). If you want to try Aspose.BarCode for .NET, you can request a temporary license for 30 days. Please refer to [How to get a Temporary License?](https://purchase.aspose.com/temporary-license) for more information.

<!--## **Supported Barcode Symbologies**
### **Numeric Only Symbologies**
- EAN13
- EAN8
- UPCA
- UPCE
- ISBN
- ISMN
- ISSN
- Interleaved2of5
- Standard2of5
- MSI
- Code11
- Codabar
- Postnet
- Planet
- EAN14(SCC14)
- SSCC18
- ITF14
- IATA 2 of 5
- DatabarOmniDirectional
- DatabarStackedOmniDirectional
- DatabarExpandedStacked
- DatabarStacked
- DatabarLimited
- DatabarTruncated
### **Alpha-Numeric Symbologies**
- GS1Code128
- Code128
- Code39 Extended
- Code39 Standard
- Code93 Extended
- Code93 Standard
- Australia Post
- Italian Post 25
- Matrix 2 of 5
- DatabarExpanded
- PatchCode
### **2D Symbologies**
- PDF417
- DataMatrix
- Aztec
- QR
- MicroQR
- GS1DataMatrix
- Code16K
- CompactPDF417
- Swiss QR (QR Bill)

Aspose.BarCode supports both encoding and decoding (generation and recognition) for all the listed symbologies.-->

<!--## **Edition Types**
Aspose.BarCode offers only one edition type: Enterprise. The features of Enterprise Edition are summarized in the following table.

|**Features**|**Aspose.BarCode for .NET**|
| :- | :- |
|**General**| |
|Written completely in C#, works with .NET Framework 1.1 and 2.0|X|
|Supports Windows applications|X|
|Supports WPF framework|X|
|Programmers Guide and API Reference in HTML format|X|
|API Reference in Microsoft Help format|X|
|Fully featured demos|X|
|**Barcode Generation Symbologies**| |
|Code128|X|
|Code39 Standard|X|
|Code39 Extended|X|
|Code93 Standard|X|
|Code93 Extended|X|
|Code11|X|
|Codabar|X|
|ISSN|X|
|ISBN|X|
|ISMN|X|
|GS1DataMatrix|X|
|EAN13|X|
|EAN8|X|
|GS1Code128|X|
|Interleaved2of5|X|
|Standard2of5|X|
|MSI|X|
|Postnet|X|
|Planet|X|
|UPCA|X|
|UPCE|X|
|EAN14(SCC14)|X|
|SSCC18|X|
|ITF14|X|
|BarCode supplement|X|
|PDF417|X|
|QR|X|
|Aztec|X|
|Datamatrix|X|
|Australia Post|X|
|Matrix 2 of 5|X|
|Italian Post 25|X|
|IATA 2 of 5|X|
|Code16K|X|
|Swiss QR|X|
|**Barcode Recognition Symbologies**| |
|Code128|X|
|Code39 Standard|X|
|Code39 Extended|X|
|Code93 Standard|X|
|Code93 Extended|X|
|Code11|X|
|Codabar|X|
|ISSN|X|
|ISBN|X|
|ISMN|X|
|GS1DataMatrix|X|
|EAN13|X|
|EAN8|X|
|GS1Code128|X|
|Interleaved2of5|X|
|Standard2of5|X|
|Postnet|X|
|Planet|X|
|UPCA|X|
|UPCE|X|
|EAN14(SCC14)|X|
|SSCC18|X|
|ITF14|X|
|BarCode supplement|X|
|PDF417|X|
|QR|X|
|MSI|X|
|Aztec|X|
|Datamatrix|X|
|Matrix 2 of 5|X|
|Australia Post|X|
|Italian Post 25|X|
|IATA 2 of 5|X|
|Code16K|X|
|Swiss QR|X|
|**Image Formats**| |
|Bitmap|X|
|Jpeg|X|
|Gif|X|
|png|X|
|Tiff|X|
|EMF|X|
|SVG|X|
|**Barcode Features**| |
|Font Handling|X|
|X-Dimension|X|
|Y-Dimension|X|
|Bar Height Customization|X|
|Bar size Customization|X|
|Encoding and decoding of Non-English Characters|X|
|Checksum|X|
|Supplement Data|X|
|Wide narrow ratio|X|
|Background Color|X|
|ForeColor|X|
|Barcode Alignment & Location|X|
|WYSIWYG Editing|X|
|**Image Formatting Features**| |
|Background Color|X|
|Fore Color|X|
|Border Style|X|
|Image Margin|X|
|The rotation at any angle|X|
|Customized Resolution|X|
|Caption Above|X|
|Caption Below|X|
|Auto Sizing|X|
|High Image Quality|X|
|Image Scaling|X|
|**Other Features**| |
|Enumerate local available printers and resolutions|X|
|Http Handler Support|X|
|Median smoothing image processing for recognition|X|
|HLS image processing for recognition|X|
|Grayscale image processing for recognition|X|
|ISO/IEC 8859-1 encoding with FNC4 character to Code128 encoder|X|
|ISO/IEC 8859-1 decoding with FNC4 character to Code128 decoder|X|-->
