---
title: Basic Barcode Recognition Parameters
linktitle: Basic Reading Parameters
type: docs
description: "This Article Describes How Basic Recognition Parameters"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcode JavaScript"
feedback: BARCODECOM
weight: 10
---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can test the quality of ***Aspose.BarCode*** recognition functionality and view the results online.{{% /alert %}}

## **Overview**
***Aspose.BarCode for JavaScript via C++*** provides the [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) class for recognizing barcodes in images, supporting over 60 symbologies. To perform barcode recognition:

1. Specify the source image containing the barcodes. The source can be a file or base64 bitmap string.
2. Define the target symbologies using the [*DecodeType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/decodetype) property. If not specified, the default *AllSupportedTypes* setting is used, which increases recognition time as all supported symbologies are checked.

{{% alert color="primary" %}}
For additional support, visit [Aspose Technical Support](/barcode/javascript-cpp/technical-support/), ask questions in the [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13), or contact the [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).
{{% /alert %}}

## **Basic Recognition Parameters**
To read barcodes from an image using ***Aspose.BarCode for JavaScript via C++***, follow these steps:

- Specify the image source (e.g., file path or base64 bitmap string).
- Set the target symbologies for recognition. By default, [*DecodeType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/decodetype) is set to *AllSupportedTypes*, which increases recognition time due to checking all supported barcode types.

 In ***Aspose.BarCode for JavaScript via C++***, barcode recognition is executed using the [*ReadBarCodes*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/readbarcodes) method. The recognition results, represented as [*BarCodeResult*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderesult) objects, can be accessed via the [*FoundCount*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/foundcount) property and [*FoundBarCodes*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/foundbarcodes) method.

The following code demonstrates how to specify multiple target barcode types for recognition in a single image. In this example, only *PDF417*, *QR Code*, *Code 39*, and *Code 128* barcodes will be recognized, while other types, such as *DataMatrix* and *RM4SCC*, will be ignored.

[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Read multiple barcodes from an image with specified decode types
var reader = new BarCodeInstance.BarCodeReader(
    `${path}multiple_codes.png`, "Pdf417,DataMatrix,QR,Code39Extended,Code128,RM4SCC"
);

console.log("ReadSimpleExample:");
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}

reader.delete();

```
  
<p align="center"><img src="multiple_codes.png" hight="50%" width="50%"></p>  


## **Get Recognition Results**

To retrieve barcode recognition results, use the [*ReadBarCodes*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/readbarcodes) method. Access the recognition output through the [*FoundBarCodes*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/properties/foundbarcodes) method, which returns results of type [*BarCodeResult*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderesult). To get the count of processed barcodes, use the [*FoundCount*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/properties/foundcount) property.

Below is a code sample demonstrating how to load recognition results for the image mentioned above.

  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Read multiple barcodes from an image and print the results with the count
var reader = new BarCodeInstance.BarCodeReader(
    `${path}multiple_codes.png`,
    "Pdf417,DataMatrix,QR,Code39Extended,Code128,RM4SCC"
);

// Read barcodes
reader.ReadBarCodes();
console.log("ReadFoundBarCodes:");
console.log(`BarCodes count: ${reader.FoundCount}`);

// Iterate through found barcodes
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}

reader.delete();

```

## Manual and Timeout Methods for Recognition Abortion

The [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) class provides options for aborting the recognition process when it is no longer feasible. This can be done in two ways:

### 1. Using the [*TimeOut*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/properties/timeout) Property
Set the [*TimeOut*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/properties/timeout) property to automatically interrupt the recognition process if the specified timeout value is exceeded. By default, the [*TimeOut*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/properties/timeout) property is set to 0.

### 2. Using the [*Abort*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/abort) Method
Call the [*Abort*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/abort) method to stop the recognition process if it was started in a separate thread. This method returns control immediately without blocking the process.

### Exception Handling
Both methods of abortion result in a [*RecognitionAbortedException*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/recognitionabortedexception) being thrown if the recognition process is not completed.

### Example
The following code snippet demonstrates how to abort the recognition process and handle the exception.

  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Read multiple barcodes from an image with a timeout and handle exceptions
var reader = new BarCodeInstance.BarCodeReader(
    `${path}multiple_codes.png`,
    "Pdf417,DataMatrix,QR,Code39Extended,Code128,RM4SCC"
);

console.log("ReadWithTimeout:");
reader.Timeout = 1000;

try {
    reader.ReadBarCodes();
    console.log(`BarCodes count: ${reader.FoundCount}`);
} catch (e) {
    console.log(e.message);    
}

reader.delete();

```
