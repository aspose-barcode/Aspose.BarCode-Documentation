---
title: Basic Recognition Setup
description: "A minimal and stable baseline for barcode recognition with BarCodeReader."
type: docs
weight: 20
url: /java/developer-guide/barcode-recognition/basic-recognition-setup
---

# Basic Recognition Setup

This page shows a clean baseline setup for barcode recognition.
Start with this configuration, then adjust symbology, ROI, and quality settings only when you need to.

## Minimal example

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
