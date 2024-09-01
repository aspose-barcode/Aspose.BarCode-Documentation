---
title: Product Overview
type: docs
weight: 10
feedback: BARCODECOM
description: "Aspose.BarCode for JavaScript via C++: Product Description, Main Features, and General Information"
keywords: "Generate Barcodes, Read Barcodes, How to Generate Barcodes in JavaScript, Use Advanced Settings to Style and Customize Barcodes, Aspose.BarCode"
url: /javascript-cpp/product-overview/
---

The present article provides an overview of ***Aspose.BarCode for JavaScript via C++***, detailing its core concepts and technical specifics essential for getting started with the library. This includes a description of its purpose, features, supported image formats, key classes, and compatible platforms.

## **Product Description**
***Aspose.BarCode for JavaScript via C++*** is a versatile WebAssembly-based library designed for barcode generation and recognition. It offers an efficient solution for adding barcode functionality to applications, handling various barcode types (both linear and matrix) at any orientation. The library supports more than 80 symbologies, including 1D, 2D (like QR codes), and postal barcodes. For a comprehensive list of supported barcode types, see [Supported Barcode Types](/barcode/javascript-cpp/barcode-types/).

This library is designed for efficiency and ease of use, providing robust barcode generation and recognition capabilities. It supports saving barcodes in various high-quality image formats, including vector formats, and offers high accuracy in recognizing even poorly scanned or distorted barcodes. Full-featured demos and code samples are available to help developers understand and leverage the library's capabilities.

## **Main Features**

***Aspose.BarCode for JavaScript via C++*** includes a range of features to meet diverse business needs. Key functionalities include:

- Generation and recognition of over 80 symbologies, including QR codes
- Barcode reading from images at any angle and quality
- Extensive options for customizing barcode appearance, including size, resolution, colors, rotation, and captions
- Fine-tuning recognition engine parameters for optimal performance
- Customizable barcode settings such as error correction mode, ECI, and embedded metadata
- Image rotation and label printing capabilities
- Support for saving and loading barcodes from streams or files
- Encoding and decoding non-English characters in 2D barcodes
- And more

A full list of features is available in [Product Features](/barcode/javascript-cpp/product-features/).

## **System Compatibility**
***Aspose.BarCode for JavaScript via C++*** is compatible with any modern browser and operates across all major operating systems. For detailed technical requirements, see [System Requirements](/barcode/javascript-cpp/system-requirements/).

## **Licensing**
To access the advanced features of ***Aspose.BarCode for JavaScript via C++***, a license is required. The evaluation version allows unrestricted barcode generation but includes a watermark on images and limited barcode recognition (30% masking for all but Code39 barcodes). For licensing details and to request a temporary 30-day license, see [Licensing](/barcode/javascript-cpp/licensing/) and [How to get a Temporary License](https://purchase.aspose.com/temporary-license).

## **Library Contents**
The library includes two primary classes: [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) for scanning and recognizing barcodes, and [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) for generating barcodes. Additionally, the [*ComplexBarcode*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode) namespace supports complex barcode formats such as Swiss QR Code and Royal Mail 2D Mailmark.

### **Class BarCodeReader**
The [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) class is designed for recognizing barcodes within images. After initializing this class with the desired symbology type, use the [*ReadBarCodes()*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/readbarcodes) method to detect barcodes. The class applies computer vision algorithms to extract barcode data from the image. Key features include:

- Selecting specific barcode types to reduce recognition time
- Adjusting quality settings to balance speed and accuracy

### **Class BarcodeGenerator**
The [*BarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator) class facilitates barcode creation. To generate a barcode, specify the symbology, code text, and appearance properties. This class supports various 1D and 2D barcodes and provides a unified interface for barcode generation. Essential properties include [*CodeText*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/properties/codetext) and [*EncodeTypes*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/encodetypes), allowing you to set the desired barcode symbology.

### **ComplexBarcode**
The [*ComplexBarcode*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode) namespace manages complex barcodes such as Swiss QR Code and Royal Mail 2D Mailmark. The [*SwissQRBill*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/swissqrbill) and [*SwissQRCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/swissqrcodetext) classes offer functionalities for Swiss QR codes, including managing account numbers, payment amounts, and currency.

### **Examples**
Below are code samples for generating a *Code 128* barcode and reading a barcode from a file.

```html
<script type="text/javascript" src="Aspose.BarCode.JS.Cpp.js" async onload="initializeModule()"></script>
<script>
// Global BarCode module instance
var BarCodeInstance;

// Async function for module initialization
async function initializeModule() {
    try {
        BarCodeInstance = await BarCode();
        console.log('BarCode module has loaded');
        // Enable barcode-related controls here
    } catch (error) {
        console.error("BarCode module initialization error:", error);
    }
}
</script>

<img id="generatedImage"/>
```
#### Generate Barcodes using Code 128
```
// instantiate object and set different barcode properties
var generator = new BarCodeInstance.BarcodeGenerator("Code128", "1234567");

// Generate image    
const img = generator.GenerateBarCodeImage();

// Display image
document.getElementById("generatedImage").src = img;

// Save image
generator.Save("generated.png");

// Cleanup resources
generator.delete()
```

#### Read Barcodes from File
```js
// Read a barcode image file from directory using Code128 decode type
var reader = new BarCodeInstance.BarCodeReader("generated.png", "Code128");
reader.ReadBarCodes();

//Display found barcodes count
const count = reader.FoundCount;
console.log('Barcodes found: ' + count);

// Ensure there are barcodes found
if (count > 0) {
    // Iterate through each found barcode
    for (let i = 0; i < count; i++) {
        // Retrieve the barcode at the current index
        const res = reader.FoundBarCodes(i);
        
        // Print the code text of the barcode
        console.log(`Barcode ${i + 1}: ${res.CodeText}`);
    }
} else {
    console.log('No barcodes found.');
}

// Cleanup resources
reader.delete()
```
