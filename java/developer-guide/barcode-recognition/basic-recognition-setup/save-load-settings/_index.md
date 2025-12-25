---
title: "Saving & Loading Settings (XML)"
description: "How to save and load BarCodeReader configuration using XML for reuse or debugging."
type: docs
weight: 40
url: /java/developer-guide/barcode-recognition/basic-recognition-setup/save-load-settings
---

# Saving & Loading Settings (XML)

You can save the entire configuration of a `BarCodeReader` to an XML file or stream.
This is useful for:
- Sharing identical settings across different services.
- Debugging (saving the state of a reader that failed).
- Persisting configuration between application restarts.

> **Note:** The XML state includes recognition parameters (like `DecodeType`, `QualitySettings`, `ChecksumValidation`), but **not** the input image itself. You must provide the image again after loading.

## Export settings to XML

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;

BarCodeReader reader = new BarCodeReader();
reader.setBarCodeReadType(DecodeType.PDF_417, DecodeType.QR);
reader.getBarcodeSettings().setStripFNC(true);

// Save configuration to file
reader.exportToXml("reader_settings.xml");
```

## Import settings from XML

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;

// Load configuration from file
BarCodeReader reader = BarCodeReader.importFromXml("reader_settings.xml");

// The image is not part of the XML, so you must set it manually
reader.setBarCodeImage("source_image.png");

// Read using the loaded settings
BarCodeResult[] results = reader.readBarCodes();

for (BarCodeResult result : results) {
    System.out.println(result.getCodeTypeName() + ": " + result.getCodeText());
}
```
