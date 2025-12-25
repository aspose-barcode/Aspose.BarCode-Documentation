---
title: Basic Recognition Setup
description: "A minimal and stable baseline for barcode recognition with BarCodeReader."
type: docs
weight: 20
url: /java/developer-guide/barcode-recognition/basic-recognition-setup
---

# Basic Recognition Setup

This page shows a stable baseline for barcode recognition.
Use it when you need correct results with minimal configuration.

## What to configure first

In most projects, recognition quality is defined by three choices:

1. Input source and image quality.
2. Expected barcode types (symbologies).
3. The search area (ROI) when the barcode location is known.

If you need more control than the examples below, continue with these pages:

- [Choose recognition symbology](choose-recognition-symbology)
- [Use ROI](use-roi)
- [Save and load settings](save-load-settings)
- [Special parameters](special-parameters)

## Minimal example

This example reads a single expected symbology from a file.
If you do not know the symbology, use `DecodeType.ALL_SUPPORTED_TYPES`, but expect slower recognition.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.CODE_128);

for (BarCodeResult result : reader.readBarCodes()) {
    System.out.println("CodeType: " + result.getCodeTypeName());
    System.out.println("CodeText: " + result.getCodeText());
}
```

## Read multiple barcodes from one image

Pass several `DecodeType` values when you expect more than one barcode type in the same image.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

BarCodeReader reader = new BarCodeReader(
        "multiple_barcodes.png",
        DecodeType.CODE_128,
        DecodeType.QR,
        DecodeType.EAN_13
);

BarCodeResult[] results = reader.readBarCodes();
System.out.println("Found " + results.length + " barcodes:");

for (int i = 0; i < results.length; i++) {
    System.out.println("Barcode " + (i + 1) + ":");
    System.out.println("  Type: " + results[i].getCodeTypeName());
    System.out.println("  Text: " + results[i].getCodeText());
}
```

## Handle the “no results” case

`readBarCodes()` returns an empty array when nothing is recognized.
Always handle this case, especially when images come from external systems.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.ALL_SUPPORTED_TYPES);

BarCodeResult[] results = reader.readBarCodes();
if (results.length == 0) {
    System.out.println("No barcodes found in the image");
}
```

## Basic error handling

Reader creation and recognition may throw exceptions when the input is missing, corrupted, or not a valid image.
Handle exceptions at your application boundary and log enough context to troubleshoot.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

try {
    BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.CODE_128);
    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println(result.getCodeText());
    }
} catch (Exception ex) {
    System.err.println("Recognition error: " + ex.getMessage());
}
```

## Next steps

- If you need to control how images are loaded: see [Input Sources](../input-sources).
- If recognition is slow or unstable: see [Performance & Quality](../performance).
