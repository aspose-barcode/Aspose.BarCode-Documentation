---
title: Generate QR Code
type: docs
weight: 20
url: /java/developer-guide/barcode-generation/Generate-QR-Code
---
# Generate QR Code - Quick Example

## Overview

QR Code (Quick Response Code) is one of the most popular 2D barcodes used for encoding text, URLs, contact information, and other data. This guide shows how to quickly generate a QR code using Aspose.BarCode for Java.

## Basic QR Code Generation

Here's the simplest way to generate a QR code:

```java
import com.aspose.barcode.generation.*;

public class QRCodeExample {
    public static void main(String[] args) {
        // Create barcode generator instance
        BarcodeGenerator generator = new BarcodeGenerator(
            EncodeTypes.QR, 
            "Hello World"
        );
        
        // Save barcode image
        generator.save("qrcode.png");
    }
}
```

## Key Parameters

### 1. Setting QR Code Size

```java
public void defineErrorCorrectionLevel() throws IOException
{
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "Data with error correction");
    // Set error correction level
    // Options: LEVEL_L (7%), LEVEL_M (15%), LEVEL_Q (25%), LEVEL_H (30%)
    generator.getParameters().getBarcode().getQR().setQrErrorLevel(QRErrorLevel.LEVEL_H);
    generator.save(folder + "qrcode_error_correction.png");
}
```

### 2. Error Correction Level

QR codes support different error correction levels that allow the barcode to be read even if it's partially damaged:

```java
public void defineQRCodeSize() throws IOException
{
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "Set QR size");
    // Set barcode dimensions in pixels
    generator.getParameters().getBarcode().getXDimension().setPixels(4);
    // Set image resolution
    generator.getParameters().setResolution(300);
    generator.save(folder + "qrcode_sized.png");
}
```

Error correction levels explained:
- **Level L**: ~7% of codewords can be restored
- **Level M**: ~15% of codewords can be restored (default)
- **Level Q**: ~25% of codewords can be restored
- **Level H**: ~30% of codewords can be restored

### 3. Encoding Mode

```java
public void defineEncodingMode() throws IOException
{
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "データ");
    generator.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.ECI);
    generator.getParameters().getBarcode().getQR().setQrECIEncoding(ECIEncodings.UTF8);
    generator.save(folder + "qrcode_utf8.png");
}
```

Available encoding modes:
- `AUTO` - automatically selects the best encoding
- `BYTES` - binary data encoding
- `UTF_8` - UTF-8 text encoding
- `UTF_16_BE` - UTF-16 Big Endian encoding

## Complete Example

```java
public void completeExample() throws IOException
{
    try {
        // Initialize barcode generator
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR,"https://www.aspose.com"
        );

        // Configure appearance
        generator.getParameters().getBarcode().getXDimension().setPixels(4);
        generator.getParameters().setResolution(300);

        // Configure QR-specific settings
        generator.getParameters().getBarcode().getQR()
                .setQrErrorLevel(QRErrorLevel.LEVEL_M);
        generator.getParameters().getBarcode().getQR()
                .setQrECIEncoding(ECIEncodings.UTF8);
        generator.getParameters().getBarcode().getQR()
                .setQrEncodeMode(QREncodeMode.ECI);

        // Set colors
        generator.getParameters().setBackColor(java.awt.Color.WHITE);
        generator.getParameters().getBarcode().setBarColor(java.awt.Color.BLACK);

        // Save to file
        generator.save(folder + "qrcode_complete.png");

        System.out.println("QR Code generated successfully!");

    } catch (Exception e) {
        e.printStackTrace();
    }
}
```

## Micro QR Code

For smaller data amounts, you can use Micro QR Code:

```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.MICRO_QR, "12345");

// Micro QR specific settings
generator.getParameters().getBarcode().getXDimension().setPixels(4);

generator.save("micro_qr.png");
```

## Common Use Cases

### URL Encoding
```java
BarcodeGenerator generator = new BarcodeGenerator(
    EncodeTypes.QR, 
    "https://www.example.com/product/12345"
);
generator.save("url_qrcode.png");
```

### Contact Information (vCard)
```java
String vcard = "BEGIN:VCARD\n" +
               "VERSION:3.0\n" +
               "FN:John Doe\n" +
               "TEL:+1-555-1234\n" +
               "EMAIL:john@example.com\n" +
               "END:VCARD";

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, vcard);
generator.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.UTF_8);
generator.save("vcard_qrcode.png");
```

### WiFi Configuration
```java
String wifi = "WIFI:T:WPA;S:MyNetwork;P:MyPassword;;";

BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, wifi);
generator.save("wifi_qrcode.png");
```

## Best Practices

1. **Choose appropriate error correction level**: Higher levels increase reliability but make the QR code larger
2. **Use UTF-8 encoding** for international characters
3. **Set adequate resolution** (at least 300 DPI) for printing
4. **Keep data concise** - smaller data creates simpler, more scannable codes
5. **Test scanning** on multiple devices before production use

## Next Steps

- Learn about [QR Code Advanced Settings](./qr-advanced-settings.md)
- Explore [2D Barcode Error Correction](./2d-error-correction.md)
- Read about [Barcode Recognition](./read-barcode-image.md)
