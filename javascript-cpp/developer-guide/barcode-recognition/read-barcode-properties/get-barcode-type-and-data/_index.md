---
title: Get Barcode Type and Encoded Data
type: docs
description: "This article describes how to read barcode parameters"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode JavaScript"
weight: 10
feedback: BARCODECOM
url: /javascript-cpp/get-barcode-type-and-data/
---
  
## **Decode Barcode Type and Data**

To retrieve the data encoded in a barcode and determine its type, the class [*BarCodeResult*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderesult) provides the key fields:

- **[*CodeText*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderesult/properties/codetext)** – the decoded data from the barcode.
- **[*CodeType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderesult/properties/codetype)** – the type of barcode.


The following code sample shows how to extract the data and barcode type from a sample barcode image (in this case, a *QR Code*).

 
```javascript
// Create a QR barcode
var gen = new BarCodeInstance.BarcodeGenerator("QR", "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 4;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display QR code image

// Recognize the QR barcode from the image
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "QR");
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`CodeText: ${result.CodeText}`);
    console.log(`CodeType: ${result.CodeType}`);
}

gen.delete();
reader.delete();

```

<p align="center"><img src="qrcodetext.png"></p> 
   
  
