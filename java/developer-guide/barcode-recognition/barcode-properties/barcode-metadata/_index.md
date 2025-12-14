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

## Example: 1D checksum metadata

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
        System.out.println("OneD checksum = " + oneD.getCheckSum());
    }
}
```

## Example: QR metadata (error level, version)

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
    }
}
```
