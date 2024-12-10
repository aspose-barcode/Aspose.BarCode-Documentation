---
title: Set Barcode Source
type: docs
description: "This Article Describes How to Set Barcode Source for Recognition"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcode JavaScript"
feedback: BARCODECOM
weight: 10
url: /javascript-cpp/set-barcode-source/

---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## Overview

In ***Aspose.BarCode for JavaScript via C++***, you can define the barcode recognition source in three ways: as an image file, a stream, or a bitmap. Supported image formats for barcode reading include BMP, PNG, JPEG, GIF, and TIFF. Implementation details for each mode are provided below.

## Read Barcodes from File

To set an image file as the source for barcode recognition, specify the full or relative path to the file in the [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) constructor, or use the [*SetBarCodeImage*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition.barcodereader/setbarcodeimage) method to pass the path to an existing [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) object.

### Example
The following code snippet demonstrates how to set an image file as the barcode reading source by specifying the path to the image.


[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Read multiple barcode types from an image file
var reader = new BarCodeInstance.BarCodeReader(`${path}multiple_codes.png`,
        "Pdf417,DataMatrix,QR,Code39Extended,Code128,RM4SCC");

console.log("ReadFromFile:");
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}

reader.delete();
```
  
The code sample below illustrates how to define the path to the already created recognition source object.
  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Read multiple barcode types from an image file using SetBarCodeImage
var reader = new BarCodeInstance.BarCodeReader();
reader.SetBarCodeImage(`${path}multiple_codes.png`);
reader.SetBarCodeReadType("Pdf417,DataMatrix,QR,Code39Extended,Code128,RM4SCC");

console.log("ReadSetBarCodeImageFromFile:");
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}

reader.delete();

```

## **Read Barcodes from Base64 image string**
In ***Aspose.BarCode for JavaScript via C++***, it is possible to read barcodes from base64 image string. To set the recognition source as base64 image string, it is necessary to pass the base64 image string to the [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) constructor or the [*SetBarCodeImage*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition.barcodereader/setbarcodeimage) method similarly to the case of using a raster image file.
  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Generate a QR barcode
var gen = new BarCodeInstance.BarcodeGenerator("QR", "ASPOSE.BARCODE");
const base64image = gen.GenerateBarCodeImage(); // Generate base64 barcode image

// Read multiple barcode types from a bitmap image
var reader = new BarCodeInstance.BarCodeReader(base64image, "Pdf417,DataMatrix,QR,Code39Extended,Code128,RM4SCC");

console.log("ReadFromBitmap:");
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}

gen.delete();
reader.delete();

```

