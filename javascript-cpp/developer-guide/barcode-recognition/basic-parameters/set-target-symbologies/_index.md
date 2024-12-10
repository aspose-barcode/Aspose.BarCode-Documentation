---
title: Set Target Barcode Types for Recognition
linktitle: Set Target Barcode Types
type: docs
feedback: BARCODECOM
description: "This Article Describes How to Set Target Barcode Types for Recognition"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcode JavaScript"
weight: 20
url: /javascript-cpp/set-target-barcode-types/
---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
**Aspose.BarCode for JavaScript via C++** supports over 60 barcode types for recognition. To reduce recognition time and avoid processing outdated barcodes still used in some legacy industrial systems, it is recommended to specify the target barcode symbologies for recognition. If the exact symbologies in a source image are unknown, the default setting *DecodeType.AllSupportedTypes* can be used for the [*DecodeType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/decodetype) property. This will check the source image for all supported barcode types, though it may increase the recognition time.

## **List of Barcode Types in DecodeType**
Target barcode symbologies can be defined as a list and provided to the [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) constructor or the [*SetBarCodeReadType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition.barcodereader/setbarcodereadtype/methods/1) method.

The following code snippet shows how to set target symbologies (*Code 39*, *Code 128*, and *RM4SCC*) using [*DecodeType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/decodetype).

  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
var reader = new BarCodeInstance.BarCodeReader(`${path}multiple_codes.png`);
reader.SetBarCodeReadType("Code39Extended", "Code128,RM4SCC");
console.log("ReadDecodeTypeList:");
var barcodes = reader.ReadBarCodes();
for (var i = 0; i < barcodes.length; i++) {
    const result = barcodes[i];
    console.log(`${result.CodeType}: ${result.CodeText}`);
}

reader.delete();

```


## **Predefined Sets of Types**
Class [*DecodeTypes*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/decodetype) contains various predefined sets of symbologies for recognition, including the following ones:
-	*AllSupportedTypes* - all supported barcode types
-	*Types1D* - all supported 1D symbologies
-	*Types2D* - all supported 2D symbologies
-	*PostalTypes* - all supported postal symbologies that are mainly used by postal services
-	*MostCommonTypes* - a set of most widely used barcode standards defined according to the Aspose recommendations

 The required symbology set can be defined in the [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) constructor or the [*SetBarCodeReadType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition.barcodereader/setbarcodereadtype/methods/1) method.
  
The following code snippet illustrates how to specify target barcode types using the predefined set called *Types2D*.
  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "Types2D");
console.log("ReadTypes2D:");
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    var result = reader.FoundBarCodes(i);
    console.log(`CodeType: ${result.CodeType}`);
    console.log(`CodeText: ${result.CodeText}`);
}
reader.delete();

```

