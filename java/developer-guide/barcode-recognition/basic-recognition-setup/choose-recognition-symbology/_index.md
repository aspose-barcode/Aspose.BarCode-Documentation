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

## Why it matters

Recognition is not a simple lookup. The reader tries multiple detection strategies and decoders.
If you allow many symbologies, the reader has more work to do and has more chances to interpret noise as a valid barcode.

In practice, choosing the right `DecodeType` set helps you:

- reduce latency for large images and batch processing
- reduce false positives when images contain patterns, text, or graphics
- make results easier to validate because the expected type is known

## Practical selection rules

Use these rules as a default:

1. If you know the exact symbology, pass one `DecodeType` to the reader.
2. If you know a small set of possible symbologies, pass only that set.
3. If you only know the category, start with `DecodeType.TYPES_1D` or `DecodeType.TYPES_2D`.
4. Use `DecodeType.ALL_SUPPORTED_TYPES` only for unknown inputs and diagnostics.

If results are still unstable, restrict the search area using ROI. See [Use ROI](../use-roi).

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

## Next steps

- If you want a stable baseline and common patterns: see [Basic Recognition Setup](../..).
- If you need to speed up recognition or tune robustness: see [Performance & Quality](../../performance).
