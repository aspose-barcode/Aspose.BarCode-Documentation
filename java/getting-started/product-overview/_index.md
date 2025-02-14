---
title: Product Overview
type: docs
weight: 10
feedback: BARCODECOM
url: /java/product-overview/
---

***Aspose.BarCode for Java*** is a robust and reliable barcode generation and recognition component written in Java that
allows developers to quickly and easily add barcode generation and recognition functionality to Java applications. It
provides a group of classes to work with barcodes on the backend, as well as GUI-based controls.
_**Aspose.BarCode for Java**_ offers a versatile and powerful solution for managing barcodes. One key advantage is the
ability to adjust barcode recognition engine variables, allowing you to balance reading quality and speed. One of its
standout features is the ability to configure barcode recognition engine variables, allowing you to strike the perfect
balance between reading quality and speed. This flexibility even enables the recognition of severely corrupted barcodes,
ensuring reliability in challenging scenarios. The library also provides extensive customisation options for barcode
appearance and parameters. You can adjust settings such as background colour, bar colour, rotation angle, X-dimension,
image quality, resolution, captions, size, and more, tailoring the output to fit your specific requirements.
***Aspose.BarCode for Java*** enables compatibility with most of the existing barcode standards and specifications. It
not only enables barcode generation but also provides an extensive framework to control the key aspects of barcode
processing.

## **Product Description**

***Aspose.BarCode for Java*** is a powerful and versatile library designed to streamline barcode processing tasks
in Java applications. Implemented with managed code, it offers seamless functionality for generating and recognizing
a wide variety of barcode types, both linear and matrix, at any angle—quickly and effortlessly.

This library is fully compatible with most existing barcode specifications and standards, supporting over 80
symbologies.

The detailed listing of all available barcode types is provided
in <a href="/barcode/java/barcode-types/" target="_blank">Supported Barcode Types</a>.

***Aspose.BarCode for Java*** has many characteristics that make it a flexible and easy-to-use tool.
It is a fully functional library that provides both generation and reading functionality.
Generated barcodes can be saved in five high-quality raster image formats and two vector ones.
The other advantage is that the library facilitates decoding even low-quality or damaged barcode images.
Therefore, it enables high recognition efficiency for most supported symbology types.

Developers can download fully featured demos and working examples written in Java to better understand our product.
Developers can download the fully functional **Aspose.BarCode for Java** library and working examples
to test the full version and better understand our product.   
Developers can download the fully functional **Aspose.BarCode for Java** library and working examples to test the full
version and better understand our product.   
The library is available for direct
download <a href="https://releases.aspose.com/barcode/java/" target="_blank">here</a> and can also be included via Maven
from <a href="https://releases.aspose.com/java/repo/com/aspose/aspose-barcode/" target="_blank">this repository</a>.

## **Main Features**

***Aspose.BarCode for Java*** offers a wide range of features to meet various business needs. One of its key
capabilities is the customization of barcode appearance-related properties, including barcode size, element colors,
rotation angle, image quality, X-dimension, resolution, text captions, and more.
The library offers excellent capabilities for barcode recognition and image processing.

The most important features are the following:

- **Barcode generation and recognition** for 80+ barcode types
- **Reading barcodes** at any angle and from images of various quality levels
- **Customizing barcode appearance**, including size, height, resolution, colors, rotation angle, text labels, captions,
  X-dimension, wide-to-narrow ratio, and more
- **Optimizing recognition engine settings** to balance accuracy and speed
- **Selecting a specific scanning region** for targeted barcode detection
- **Generating barcodes with special modes**, such as ECI, error correction, and embedded metadata
- **Rotating images** at any angle
- **Saving and loading barcodes** from files or data streams
- **Encoding and decoding non-English characters** in 2D barcode formats

## **Platform and Java Compatibility**

Aspose.BarCode for Java is compatible with any operating system that supports Java JDK/JRE. 
It requires Java SE 1.8 or later and works with various JDK distributions, including:

- **Oracle JDK**
- **BellSoft Liberica JDK**
- **Amazon Corretto**
- **OpenJDK**
- **and others**

## **Licensing**

License is required to get access to the advanced functionality of ***Aspose.BarCode for Java***.  
The evaluation mode of ***Aspose.BarCode for Java*** allows generating barcode images without restrictions. However, a
watermark will be displayed on the resulting barcode image (words “Aspose”). The unlicensed version can be used to read
barcodes of all supported types. Please note that only *Code 39* can be decoded without limitations; as a result of
reading barcodes corresponding to other types, 30% of decoded text will be masked with " * ". All other actions with
barcodes using ***Aspose.BarCode for Java*** need setting a license. After purchasing a license, you will get access to
the whole functionality of the library and the ability to perform barcode generation and reading without limitations and
watermark placement.

More information about how to buy and set the license is provided
in <a href="/barcode/java/licensing/" target="_blank"><strong>Licensing</strong></a>.  
If you want to evaluate the full functionality of ***Aspose.BarCode for Java***, you can obtain a temporary license that
is valid for 30 days.  
Please refer to <a href="https://purchase.aspose.com/temporary-license" target="_blank">How to get a Temporary
License</a> for details.

## **Library Contents**

***Aspose.BarCode for Java*** includes three main classes:  
<a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader" target="_blank"><em>
BarCodeReader</em></a> for barcode recognition,  
<a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeGenerator" target="_blank"><em>
BarcodeGenerator</em></a> for barcode generation according to the required format,
<a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode" target="_blank"><em>  
ComplexBarcode</em></a>, which handles specific barcode types such as Swiss QR Code, MaxiCode, and HIBC LIC.

### **Class BarCodeReader**

***Aspose.BarCode for Java*** provides
the <a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader" target="_blank"><em>
BarCodeReader</em></a> class for barcode image recognition. To use it, first specify the symbology type in the constructor of <em>
BarCodeReader</em> and then call
the <a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader#readBarCodes--" target="_blank"><em>
readBarCodes()</em></a> method to read barcodes from an image. The <em>BarCodeReader</em> class utilizes computer vision algorithms to
extract machine-readable data from the provided image.

Image reading and barcode region identification can be performed for all detected barcodes in an image. 
Before recognition, barcodes must be distinguished from other text lines or objects by detecting their edges.
To achieve this, the <a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader#readBarCodes--" target="_blank"><em>
BarCodeReader.readBarCodes()</em></a> method is used. 
Then, the barcode region is determined
using <a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult#getRegion--" target="_blank"><em>
BarCodeResult.getRegion()</em></a>, which returns the detected barcode area along with its orientation angle.

The class provides features for optimizing the balance between recognition speed and accuracy:

- **Multi-threading support** – Utilizes multiple CPU cores to accelerate barcode recognition.
- **Barcode type selection** – Defining only the required barcode types instead of using  
  <a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/decodetype/#ALL-SUPPORTED-TYPES" target="_blank"><em>DecodeType.ALL_SUPPORTED_TYPES</em></a> 
  improves performance by reducing processing time.
- **Quality settings** – Provides adjustable recognition parameters to handle various image conditions and distortions.
- **Region selection** – Enables targeting specific areas in an image for optimized barcode detection.


### **Class BarcodeGenerator**

One of the key features of ***Aspose.BarCode for Java*** is barcode generation. 
To generate a barcode, developers need to specify the symbology, set the code text (data to be encoded), 
and configure appearance-related properties.

The <a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeGenerator" target="_blank"><em>
BarcodeGenerator</em></a> class supports various 1D and 2D barcode types, including QR codes, and provides a unified interface for
barcode creation. Developers can instantiate this class, configure the necessary properties, and save the generated barcode image
according to customized settings.

Two main parameters must be set:
- <a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeGenerator#setCodeText-java.lang.String-" target="_blank"><em>
  CodeText</em></a> – Specifies the data to be encoded.
- <a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/EncodeTypes" target="_blank"><em>
  EncodeTypes</em></a> – Defines the barcode symbology.

The <em>EncodeTypes</em> property allows developers to assign any barcode type from the predefined set of supported symbologies
available in the <em>BarcodeGenerator</em> class.

### **ComplexBarcode**
The <a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode" target="_blank"><em>ComplexBarcode</em></a> 
namespace enables the generation of barcodes that encode structured financial and postal data. 
Currently, it supports the Swiss QR Code and Royal Mail 2D Mailmark symbologies.

Swiss QR Code is used for managing QR bills in payment systems, replacing traditional payment slips. It contains all the necessary
payment details required to initiate transactions or process QR invoices.

The <em>ComplexBarcode</em> namespace includes the 
<a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/SwissQRBill" target="_blank"><em> 
SwissQRBill</em></a> and <a href="https://reference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/SwissQRCodetext" 
target="_blank"><em>SwissQRCodetext</em></a> classes, which provide various functionalities for working with Swiss QR Codes, such 
as retrieving or setting the creditor's account
number, defining alternative payment schemes, specifying the payment amount, currency, and more.

### **Examples**
{{< highlight java >}}
    public void generate_Barcodes_using_Code_128() throws IOException
    {
        String filePath = folderPath + "output.png";
        // Instantiate the BarcodeGenerator object and set barcode properties
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "1234567");
        generator.getParameters().getBarcode().getXDimension().setMillimeters(1f);
        // Save the barcode image to the specified directory in PNG format
        generator.save(filePath, BarCodeImageFormat.PNG);
    }

{{< /highlight >}}

{{< highlight java >}}
    public void read_Barcodes_from_File() throws IOException
    {
        String filePath = folderPath + "output.png";
        BarCodeReader reader = new BarCodeReader(filePath, DecodeType.ALL_SUPPORTED_TYPES);
        for (BarCodeResult result : reader.readBarCodes())
        {
            // Read symbology type and code text
            System.out.printf("Symbology Type: %s%n", result.getCodeType());
            System.out.printf("CodeText: %s%n", result.getCodeText());
        }
    } 
{{< /highlight >}}

{{< highlight java >}}
     public void Read_Barcodes_from_Stream1() throws IOException
     {
        String filePath = folderPath + "image.png";
        try (FileInputStream fileStream = new FileInputStream(filePath))
        {
            BarCodeReader reader = new BarCodeReader(fileStream);
            for (BarCodeResult result : reader.readBarCodes())
            {
              System.out.printf("Symbology Type: %s%n", result.getCodeType());
              System.out.printf("CodeText: %s%n", result.getCodeText());
            }
        }
        catch (IOException e)
        {
          e.printStackTrace();
        }
     }

{{< /highlight >}}

