---
title: Product Overview
type: docs
weight: 10
description: "Aspose.BarCode for .NET: Product Description, Main Features, and General Information"
keywords: "Generate Barcodes, Read Barcodes, How to Generate Barcodes in C# .NET, Use Advanced Settings to Style and Customize Barcodes, Aspose.BarCode, C#"
url: /net/product-overview/
---
The present article introduces ***Aspose.BarCode for .NET*** and its main concepts, as well as general technical details that are important to start working with the library. Here, you can find the description of its purpose, functionality, key features, input and output image formats, important classes, and supported platforms.

## **Product Description**

***Aspose.BarCode for .NET*** is a multifunctional component library implemented through Managed C# to address various barcode processing tasks. It allows deploying generation and recognition functionality for different barcode types (linear and matrix) at any angle in a fast and easy way. This library enables compatibility with most of the existing barcode specifications and standards, supporting over 70 symbologies (1D, 2D including QR codes, and postal ones). The detailed listing of all available barcode symbologies is provided in [Barcode Types and Image Formats](/barcode/net/barcode-types-and-image-formats/).  
  
***Aspose.BarCode for .NET*** can be used for development in different ways: through a console application, a web appication, .Net MAUI mobile application, Windows Forms, or Windows Presentation Foundation (WPF). For developers who want to create barcodes in the backend, the library provides the corresponding class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator). Alternatively, using GUI controls in ***Aspose.BarCode for .NET***, developers can drag and drop controls onto Windows Forms and set properties in the GUI-based mode. Finally, ***Aspose.BarCode for .NET*** supports the WPF framework to facilitate the development of WPF-based barcode applications.  
  
***Aspose.BarCode for .NET*** benefits from important characteristics that make it an efficient, flexible, and easy-to-use tool. First, it is a fully functional library that enables both generating and reading barcodes. Moreover, barcodes can be saved in various high-quality image formats including two vector ones. The other key advantage is that the library allows recognizing barcodes even of very low quality or being significantly distorted. Accordingly, the recognition precision is high for most of the available barcode types.

***Aspose.BarCode for .NET*** provides full-featured demos and code samples written in C# to give developers a better understanding of the library and its capabilities.

## **Main Features**

***Aspose.BarCode for .NET*** supports multiple features to address specific business needs. It is noteworthy that it enables a wide range of functionality for setting an efficient barcode processing system. One of the most important functions is the possibility to customize the appearance parameters of generated barcodes, such as background color, bar color, rotation angle, X-dimension, image quality, resolution, captions, size, and others. Moreover, this library provides rich barcode reading and imaging functionality.  
The main features include: 
- Barcode generation and recognition of 70+ symbologies (including QR codes)
- Reading 1D and 2D barcodes at any angle and from any image quality
- Wide range of options to manipulate barcode image appearance (size, resolution, height, background color, bar color, rotation angle, X-dimension, image quality, captions, wide-to-narrow-ratio, and others)
- Customizing recognition engine variables to reach the best trade-off between reading speed and quality
- Specifying image areas to scan barcodes
- Generating barcodes with specific parameters, such as error correction mode, ECI, or embedded metadata
- Image rotation at any angle 
- Label printing 
- Saving to or loading from stream or file 
- Encoding and decoding non-English characters in 2D types
- and many others.
  
The full list of features can be found in [Product Features](/barcode/net/product-features/).  

## **System Compatibility**
***Aspose.BarCode for .NET*** supports any 32-bit or 64-bit operating system having installed: .NET framework 2.0 or later / .Net Core 2.1 or later with [Aspose.Drawing.Common](https://www.nuget.org/packages/Aspose.Drawing.Common/) (.Net 7 included) / any other .NET framework supporting the fist two ones. The library can be used in any .NET application, including WinForms, WPF, ASP.NET, Mono, .Net MAUI, and .NET Core. More technical details on this subject are provided in [System Requirements](/barcode/net/system-requirements/).

## **Licensing**
License is required to obtain access to the advanced functionality of ***Aspose.BarCode for .NET***. The evaluation mode allows generating barcodes without any restrictions; however, a watermark is placed on the resulting image. Moreover, barcode recognition is available without limitations only for Code39 barcodes; for all other symbologies, 30% of the resulting text will be masked. 
More information about how to buy and set the license is provided in [Licensing](/barcode/net/licensing/). If you want to try ***Aspose.BarCode for .NET***, you can request a temporary license for 30 days. Please refer to [How to get a Temporary License](https://purchase.aspose.com/temporary-license) for details.

## **Library Contents**
***Aspose.BarCode for .NET*** includes two main classes: [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) to perform barcode scanning and recognizing, [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) to provide barcode generation according to the desired format requirements. A namespace denoted as [*ComplexBarcode*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode) serves to work with specific barcodes, such as Swiss QR Code, MaxiCode, and HIBC LIC. 
  
### **Class BarCodeReader**
***Aspose.BarCode for .NET*** contains class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) that is aimed at handling barcode image recognition. [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) has the following basic settings. First, it is required to specify the symbology type in the constructor of class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) and call the [*BarCodeReader.ReadBarCodes()*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/readbarcodes) method to read barcodes from an image. Then, class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) applies machine vision algorithms to extract machine-readable tags from the captured image.  
In ***Aspose.BarCode for .NET***, image reading and identifying barcode regions can be performed for all recognized barcodes in an image. Before reading, barcodes have to be distinguished from other text lines/objects in the image by detecting their edges. To implement this, the [*BarCodeReader.ReadBarCodes()*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/readbarcodes) method is used. Then, the region of a barcode is identified using *BarCodeResult.Region* that returns the recognized region and the barcode angle.  
Class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) provides the following features to achieve the best possible trade-off between recognition speed and quality depending on specific requirements:
-	Multi-threading support. This feature involves additional processor cores to speed up algorithm calculations, where possible.
-	Barcode type selection. Specifying required barcode types instead of setting [*DecodeType.AllSupportedTypes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/decodetype/fields/allsupportedtypes) allows reducing recognition time.
-	Quality settings. This group of options allows customizing the barcode reading engine according to the type of image and possible distortions. Disabling some options allows increasing recognition speed while their activation improves recognition quality.
-	Region selection. It is possible to select target regions in which barcode images might be located so that the reading engine will read barcode data only from the selected regions.

### **Class BarcodeGenerator**
One of the key features of ***Aspose.BarCode for .NET*** is to perform barcode generation. To create a barcode label, it is necessary to specify symbologies, set code text (information to be encoded to a barcode image), customize appearance-related properties. Class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) supports various 1D and 2D barcode types (including QR codes). It encapsulates both types of barcodes into one unified interface. Developers can create an instance of this class, set properties as required, and then save the generated barcode image to any location according to the customized settings. In the general case, two main parameters need to be initialized: [*CodeText*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/properties/codetext) to define data contents to be encoded and [*EncodeTypes*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/encodetypes) to set the barcode symbology. Developers can assign any symbology to the [*EncodeTypes*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/encodetypes) property out of pre-defined barcode types supported by class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator).


### **ComplexBarcode**
Namespace [*ComplexBarcode*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode) allows generating barcode documents to work with complex barcodes. At present, it supports Swiss QR Code and Royal Mail 2D Mailmark symbologies. Swiss QR Code is used to manage QR bills in payments that replace previous payment slips. Swiss QR Code contains all necessary payment information required to initiate payments or to process a QR invoice. [*ComplexBarcode*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode) contains classes [*SwissQRBill*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/swissqrbill) and [*SwissQRCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/swissqrcodetext) that enable various functions to work with Swiss QR codes, such as getting or setting the account number of a creditor, alternative payments schemes, payment amount, currency, etc.

### **Examples**
Below you can see some code samples for simple operations, such as generating *Code 128* barcodes or recognizing a barcode from a file or stream.
  
#### Generate Barcodes using Code 128
{{< highlight csharp>}}
// instantiate object and set different barcode properties
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Code128, "1234567");
generator.Parameters.Barcode.XDimension.Millimeters = 1f;

// save the image to your system and set its image format to PNG
generator.Save(dir + "output.png", BarCodeImageFormat.PNG);
{{< /highlight >}} 

#### Read Barcodes from File
{{< highlight csharp>}}
// Read a barcode image file from directory using DecodeType.EAN13
using (BarCodeReader reader = new BarCodeReader(dataDir + "Scan.png", DecodeType.EAN13))
{
    foreach (BarCodeResult result in reader.ReadBarCodes())
    {
        // Read symbology type and code text
        Console.WriteLine("Symbology Type: " + result.CodeType);
        Console.WriteLine("CodeText: " + result.CodeText);
    }
}
{{< /highlight >}} 

#### Read Barcodes from Stream
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
