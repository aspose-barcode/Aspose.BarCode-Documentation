---
title: "Special Parameters (StripFNC, AustraliaPost, DetectEncoding, AllowIncorrectBarcodes)"
description: "Less common recognition settings that change how code text is decoded and validated."
type: docs
weight: 30
url: /java/developer-guide/barcode-recognition/basic-recognition-setup/special-parameters
---

# Special Parameters (StripFNC, AustraliaPost, DetectEncoding, AllowIncorrectBarcodes)

This page lists recognition settings that you normally touch only when you have a specific requirement.
Each setting changes either output text interpretation or result validation behavior.

## StripFNC

Use `StripFNC` to control whether FNC control characters are removed from `getCodeText()`.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;

BarCodeReader reader = new BarCodeReader("path", DecodeType.CODE_128);

// Remove FNC control characters from the decoded text (default)
reader.getBarcodeSettings().setStripFNC(true);

// Or preserve FNC control characters
reader.getBarcodeSettings().setStripFNC(false);
```

## Australia Post settings

Australia Post barcodes have a customer information field that must be interpreted using the right table.
Use `CustomerInformationInterpretingType` to define how this field is decoded.

| Interpreting type | Enum value | Payload characteristics |
|---|---|---|
| **C Table** | `C_TABLE` | Alphanumeric (A-Z, a-z, 0-9, space, #). |
| **N Table** | `N_TABLE` | Numeric digits only. |
| **Other** | `OTHER` | Raw data (0-3 symbolic characters). |

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;
import com.aspose.barcode.barcoderecognition.CustomerInformationInterpretingType;

String imagePath = "aus_post.png";
BarCodeReader barCodeReader =
        new BarCodeReader(imagePath, DecodeType.AUSTRALIA_POST);

// Interpret customer information as C table (alphanumeric)
barCodeReader.getBarcodeSettings()
        .getAustraliaPost()
        .setCustomerInformationInterpretingType(CustomerInformationInterpretingType.C_TABLE);
```

## DetectEncoding

Enable encoding detection when payloads can contain non-ASCII text.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.DecodeType;

BarCodeReader reader =
        new BarCodeReader("qr_utf8_detectencoding_enabled.png", DecodeType.QR);
reader.getBarcodeSettings().setDetectEncoding(true);
```

## AllowIncorrectBarcodes

When enabled, the engine can return results that would normally be filtered out as invalid or inconsistent.
Treat such results as untrusted until you validate them in your application.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

String imagePath = "code39_damaged_allowed.png";
BarCodeReader barCodeReader = new BarCodeReader(imagePath, DecodeType.CODE_39);

// Relax validation: allow potentially incorrect barcodes
barCodeReader.getQualitySettings().setAllowIncorrectBarcodes(true);

BarCodeResult[] barCodeResults = barCodeReader.readBarCodes();
for (BarCodeResult barCodeResult : barCodeResults) {
    System.out.println("Code text (possibly invalid): " + barCodeResult.getCodeText());
}
```
