---
title: "Barcode Generation"
description: "Generate and configure barcodes with Aspose.BarCode for Java."
type: docs
weight: 1
url: /java/developer-guide/barcode-generation/
---

# Barcode Generation

Aspose.BarCode for Java provides a unified generation API for linear, postal, and two-dimensional barcode symbologies. A typical workflow consists of selecting an encode type, supplying the code text, configuring generation parameters, and saving the result.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "BARCODE-GENERATION"
);

generator.save("barcode.png", BarCodeImageFormat.PNG);
```

The generation API is organized around `BarcodeGenerator` and its parameter tree. Common parameters control image size, resolution, colors, borders, captions, human-readable text, padding, and rotation. Symbology-specific parameter objects expose options such as QR error correction, Data Matrix versions, ITF-14 bearer bars, or Australian Post short-bar height.

This section contains the following topics:

- Set Barcode Symbology and Text
- Visual Parameters & Layout
- Save Generated Barcodes
- Set Barcode Checksum
- Printing

## Complete example

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/overview/BarcodeGenerationOverview.java" target="_blank">View BarcodeGenerationOverview.java</a>

You can also browse the <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation" target="_blank">Generation examples directory</a>.
