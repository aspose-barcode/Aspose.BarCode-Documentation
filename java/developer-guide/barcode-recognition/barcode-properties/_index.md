---
title: Reading Barcode Properties
description: "How to read code text, symbology, coordinates, metadata, and validation signals from BarCodeResult."
type: docs
weight: 40
url: /java/developer-guide/barcode-recognition/barcode-properties
---

# Reading Barcode Properties

After recognition, each detected barcode is returned as a `BarCodeResult`.
This object contains decoded text, the detected type, geometry information, and extended metadata.

## Topics in this section

Use these pages to read specific result fields:

- [Reading code text](reading-codetext) shows how to access decoded data and related output.
- [Symbology type](symbology-type) shows how to read the detected barcode type and type names.
- [Barcode coordinates and angle](barcode-coordinates-and-angle) shows how to read position and orientation.
- [Barcode metadata](barcode-metadata) shows how to access extended information when it is available.
- [Result validation](result-validation) describes validation signals and how to filter unreliable results.

## Minimal example

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.ALL_SUPPORTED_TYPES);

for (BarCodeResult result : reader.readBarCodes()) {
    System.out.println("Type: " + result.getCodeTypeName());
    System.out.println("Text: " + result.getCodeText());
    System.out.println("Confidence: " + result.getConfidence());
}
```
