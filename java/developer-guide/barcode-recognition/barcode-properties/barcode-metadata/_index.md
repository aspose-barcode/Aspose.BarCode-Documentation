---
title: Read Barcode Metadata
description: "How to use BarCodeExtendedParameters to access symbology-specific metadata."
type: docs
weight: 40
url: /java/developer-guide/barcode-recognition/barcode-properties/barcode-metadata
---

# Read Barcode Metadata

Some symbologies provide extra metadata beyond text and type.
Aspose.BarCode exposes this via `BarCodeResult.getExtended()`.

## How extended metadata is organized

Extended metadata is split into symbology-specific groups.
Each group has its own class with properties related to that symbology.

`BarCodeResult.getExtended()` returns a `BarCodeExtendedParameters` instance.
For a given result, only the relevant group is usually populated. The other groups may be `null`.

The main groups are:

- `OneDExtendedParameters` via `getOneD()`
- `QRExtendedParameters` via `getQR()`
- `Pdf417ExtendedParameters` via `getPdf417()`
- `DataMatrixExtendedParameters` via `getDataMatrix()`
- `AztecExtendedParameters` via `getAztec()`

## Common pattern for reading metadata

This pattern keeps your code safe when a group is missing:

```java
BarCodeExtendedParameters ext = result.getExtended();
if (ext != null && ext.getQR() != null) {
    QRExtendedParameters qr = ext.getQR();
    // Read QR metadata from qr
}
```

## Example: 1D checksum metadata

For many 1D symbologies, you can read the checksum and the value without checksum.
This is useful for logging and diagnostics.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.BarCodeExtendedParameters;
import com.aspose.barcode.barcoderecognition.OneDExtendedParameters;

String imagePath = "rv_ean13_valid.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.EAN_13);
BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();

if (barCodeResults.length > 0) {
    BarCodeExtendedParameters ext = barCodeResults[0].getExtended();
    if (ext != null && ext.getOneD() != null) {
        OneDExtendedParameters oneD = ext.getOneD();
        System.out.println("OneD value (no checksum) = " + oneD.getValue());
        System.out.println("OneD checksum = " + oneD.getCheckSum());
    }
}
```

## Example: QR metadata (error level, version)

For QR, you can read the error correction level and the version.
If the QR uses Structured Append, you can also read sequence information.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.QualitySettings;
import com.aspose.barcode.barcoderecognition.BarCodeExtendedParameters;
import com.aspose.barcode.barcoderecognition.QRExtendedParameters;

String imagePath = "qr_high_ec.png";

BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.QR);
barCodeReader.setQualitySettings(QualitySettings.getHighQuality());

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
if (barCodeResults.length > 0) {
    BarCodeExtendedParameters ext = barCodeResults[0].getExtended();
    if (ext != null && ext.getQR() != null) {
        QRExtendedParameters qr = ext.getQR();
        System.out.println("QR error level = " + qr.getQRErrorLevel());
        System.out.println("QR version     = " + qr.getQRVersion());
        System.out.println("QR SA quantity = " + qr.getQRStructuredAppendModeBarCodesQuantity());
        System.out.println("QR SA index    = " + qr.getQRStructuredAppendModeBarCodeIndex());
        System.out.println("QR SA parity   = " + qr.getQRStructuredAppendModeParityData());
    }
}
```

## PDF417 metadata (Macro PDF417)

Macro PDF417 can contain file and segment information.
This metadata is present only when the input uses the Macro PDF417 format.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.BarCodeExtendedParameters;
import com.aspose.barcode.barcoderecognition.Pdf417ExtendedParameters;

String imagePath = "macro_pdf417.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.PDF_417);
BarCodeResult[] results = reader.readBarCodes();

if (results.length > 0) {
    BarCodeExtendedParameters ext = results[0].getExtended();
    if (ext != null && ext.getPdf417() != null) {
        Pdf417ExtendedParameters pdf = ext.getPdf417();
        System.out.println("Macro file ID     = " + pdf.getMacroPdf417FileID());
        System.out.println("Macro segment ID  = " + pdf.getMacroPdf417SegmentID());
        System.out.println("Macro file name   = " + pdf.getMacroPdf417FileName());
        System.out.println("Macro file size   = " + pdf.getMacroPdf417FileSize());
    }
}
```

## DataMatrix metadata (Structured Append, reader programming)

DataMatrix Structured Append provides sequence information across multiple symbols.
DataMatrix can also carry commands for reader programming in some workflows.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.BarCodeExtendedParameters;
import com.aspose.barcode.barcoderecognition.DataMatrixExtendedParameters;

String imagePath = "dm_structured_append.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.DATA_MATRIX);
for (BarCodeResult result : reader.readBarCodes()) {
    BarCodeExtendedParameters ext = result.getExtended();
    if (ext != null && ext.getDataMatrix() != null) {
        DataMatrixExtendedParameters dm = ext.getDataMatrix();
        System.out.println("DM SA barcode ID  = " + dm.getStructuredAppendBarcodeId());
        System.out.println("DM SA count       = " + dm.getStructuredAppendBarcodesCount());
        System.out.println("DM SA file ID     = " + dm.getStructuredAppendFileId());
        System.out.println("DM reader program = " + dm.isReaderProgramming());
    }
}
```

## Aztec metadata (Structured Append, reader initialization)

Aztec Structured Append provides sequence information across multiple symbols.
Aztec can also include initialization instructions for some reader workflows.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.BarCodeExtendedParameters;
import com.aspose.barcode.barcoderecognition.AztecExtendedParameters;

String imagePath = "aztec_structured_append.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.AZTEC);
for (BarCodeResult result : reader.readBarCodes()) {
    BarCodeExtendedParameters ext = result.getExtended();
    if (ext != null && ext.getAztec() != null) {
        AztecExtendedParameters az = ext.getAztec();
        System.out.println("Aztec SA barcode ID  = " + az.getStructuredAppendBarcodeId());
        System.out.println("Aztec SA count       = " + az.getStructuredAppendBarcodesCount());
        System.out.println("Aztec SA file ID     = " + az.getStructuredAppendFileId());
        System.out.println("Aztec reader init    = " + az.isReaderInitialization());
    }
}
```
