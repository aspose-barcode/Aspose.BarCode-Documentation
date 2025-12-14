---
title: Reading color-inverted barcodes
description: "How to recognize white-on-black barcodes using InverseImageMode."
type: docs
weight: 60
url: /java/developer-guide/barcode-recognition/performance/reading-color-inverted
---

# Reading color-inverted barcodes

Some images contain barcodes with inverted colors, for example white bars on a black background.
By default, the engine focuses on normal (non-inverted) barcodes.

To support inverted barcodes, enable inverse image processing in the quality settings.

## Enable Inverse Image Mode

Using `InverseImageMode.ENABLED` tells the reader to perform additional recognition passes for inverted images. This allows it to recognize both normal and inverted barcodes, though it may increase total processing time.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.InverseImageMode;

String imagePath = "Code128Invert.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_128);

// Enable additional search for inverted barcodes
barCodeReader.getQualitySettings().setInverseImage(InverseImageMode.ENABLED);

BarCodeResult[] results = barCodeReader.readBarCodes();
```
