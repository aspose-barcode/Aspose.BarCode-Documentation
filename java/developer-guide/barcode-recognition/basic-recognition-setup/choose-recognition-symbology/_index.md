---
title: Choose Recognition Symbology
description: "How to use DecodeType to control recognition speed and reduce false positives."
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/basic-recognition-setup/choose-recognition-symbology
---

# Choose Recognition Symbology

`DecodeType` defines which symbologies the reader will try to detect.
Limiting the set usually improves performance and reduces false positives.

## Recognize one exact type

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;

String imagePath = "code128.png";

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.CODE_128);
```

## Recognize several specific types

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

BarCodeReader reader = new BarCodeReader(
        "mixed_barcodes.png",
        DecodeType.CODE_128,
        DecodeType.QR
);

for (BarCodeResult result : reader.readBarCodes()) {
    System.out.println("Found: " + result.getCodeTypeName());
    System.out.println("Text: " + result.getCodeText());
}
```

## Use type groups

If you only know the category, use grouped decode types:

- `DecodeType.TYPES_1D` for linear symbologies.
- `DecodeType.TYPES_2D` for 2D symbologies.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;

String imagePath = "ean13.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.TYPES_1D);
barCodeReader.setQualitySettings(QualitySettings.getNormalQuality());
```

## Use all supported types for discovery

This is the broadest search. Use it for diagnostics and unknown inputs.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.ALL_SUPPORTED_TYPES);

for (BarCodeResult result : reader.readBarCodes()) {
    System.out.println("Type: " + result.getCodeTypeName());
    System.out.println("Data: " + result.getCodeText());
    System.out.println("Confidence: " + result.getConfidence());
}
```

## Define a custom subset at runtime

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;

String imagePath = "dm.png";

BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.ALL_SUPPORTED_TYPES);

barCodeReader.setBarCodeReadType(
        DecodeType.CODE_128,
        DecodeType.QR,
        DecodeType.DATA_MATRIX
);
```
