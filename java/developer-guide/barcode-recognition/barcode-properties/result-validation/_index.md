---
title: "Result Validation (Checksum Validation, Confidence, Quality Scores)"
description: "How to validate results using checksum behavior, confidence score, and strict vs relaxed recognition settings."
type: docs
weight: 50
url: /java/developer-guide/barcode-recognition/barcode-properties/result-validation
---

# Result Validation (Checksum Validation, Confidence, Quality Scores)

In production systems you usually need to decide whether a recognized barcode is trustworthy.
Typical signals are checksum validity (when available), recognition confidence, and your own business rules.

## Use strict mode by default

Strict mode means you do not allow potentially incorrect barcodes.

By default (`AllowIncorrectBarcodes` is `false`), the library **internally validates the checksum** if the symbology supports it (e.g. EAN-13, Code 128). If the checksum is invalid, the barcode is considered incorrectly read and is **not returned**.

> Note: The `getCheckSum()` method available in metadata is for reading the value (e.g. for logging). You do not need to manually calculate and verify it if you rely on the default strict behavior.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

BarCodeReader barCodeReader = new BarCodeReader("rv_ean13_valid.png", DecodeType.EAN_13);
// Default is false: invalid checksums are discarded automatically
barCodeReader.getQualitySettings().setAllowIncorrectBarcodes(false);

BarCodeResult[] results = barCodeReader.readBarCodes();
```

## Compare strict vs relaxed mode on damaged input

If you set `AllowIncorrectBarcodes(true)`, the engine may return results with invalid checksums or partial reads. Use this only if you need to recover data from damaged labels and perform your own validation.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

String imagePath = "rv_code39_damaged.png";

BarCodeReader strictReader = new BarCodeReader(imagePath, DecodeType.CODE_39);
strictReader.getQualitySettings().setAllowIncorrectBarcodes(false);
int strictCount = strictReader.readBarCodes().length;

BarCodeReader relaxedReader = new BarCodeReader(imagePath, DecodeType.CODE_39);
relaxedReader.getQualitySettings().setAllowIncorrectBarcodes(true);
BarCodeResult[] relaxedResults = relaxedReader.readBarCodes();

System.out.println("Strict count:  " + strictCount);
System.out.println("Relaxed count: " + relaxedResults.length);

if (relaxedResults.length > 0) {
    System.out.println("Text: " + relaxedResults[0].getCodeText());
    System.out.println("Confidence: " + relaxedResults[0].getConfidence());
}
```

## Fine-tune validation with ChecksumValidation enum

For more control, especially with symbologies where checksums are optional (like Code 39 or Code 11), use `ChecksumValidation`.

- `ChecksumValidation.DEFAULT`:
  - For types with **mandatory** checksum (e.g. EAN-13): Validates checksum.
  - For types with **optional** checksum (e.g. Code 39): Does **not** validate checksum.
- `ChecksumValidation.ON`: Forces checksum validation for all types.
- `ChecksumValidation.OFF`: Disables checksum validation.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.ChecksumValidation;

String imagePath = "code39_with_checksum.png";
BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.CODE_39_EXTENDED);

// Force checksum validation for Code 39 (normally optional)
reader.getBarcodeSettings().setChecksumValidation(ChecksumValidation.ON);

reader.readBarCodes();
```

## Use confidence as a filter

The confidence score indicates how sure the engine is about the result.
The value ranges from **0 to 100**, where 100 is the highest confidence.

Low confidence often indicates a partial match or significant noise.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

BarCodeReader reader = new BarCodeReader("barcode.png", DecodeType.ALL_SUPPORTED_TYPES);

for (BarCodeResult result : reader.readBarCodes()) {
    // Filter out weak matches
    if (result.getConfidence() >= 80) {
        System.out.println("Accepted: " + result.getCodeTypeName() + " -> " + result.getCodeText());
    } else {
        System.out.println("Rejected (low confidence): " + result.getCodeText());
    }
}
```
