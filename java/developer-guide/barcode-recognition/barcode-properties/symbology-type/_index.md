---
title: Symbology Type
description: "How to read the detected symbology type from BarCodeResult and use it in your logic."
type: docs
weight: 20
url: /java/developer-guide/barcode-recognition/barcode-properties/symbology-type
---

# Symbology Type

Each `BarCodeResult` tells you which symbology was detected.
This is useful when you allow multiple types and need to route results by type.

## Read the detected type

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

BarCodeReader reader = new BarCodeReader("mixed_barcodes.png", DecodeType.ALL_SUPPORTED_TYPES);

for (BarCodeResult result : reader.readBarCodes()) {
    DecodeType type = result.getCodeType();
    String typeName = result.getCodeTypeName();

    System.out.println("Type enum: " + type);
    System.out.println("Type name: " + typeName);
}
```

## Use type filtering to reduce false positives

If your system accepts only a few types, restrict recognition.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;

BarCodeReader reader = new BarCodeReader(
        "barcode.png",
        DecodeType.CODE_128,
        DecodeType.QR,
        DecodeType.DATA_MATRIX
);
```
