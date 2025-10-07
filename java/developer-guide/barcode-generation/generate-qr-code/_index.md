---
title: Generate QR Code
type: docs
weight: 20
url: /java/developer-guide/barcode-generation/generate-qr-code
---

# Generate QR Code

## Overview

QR Code (Quick Response Code) is one of the most popular 2D barcodes used for encoding text, URLs, contact information, and other data. This guide shows how to quickly generate a QR code using Aspose.BarCode for Java.

## Basic QR Code Generation

Here's the simplest way to generate a QR code:

```java
public void basicQRGeneration() throws IOException
{
    // Create barcode generator instance
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "Hello World");
    
    // Save barcode image
    generator.save("qrcode.png");
}
```

## Key Parameters

### Setting QR Code Size

You can control the size of QR code by setting the X-dimension (module width) and image resolution:

```java
public void defineQRCodeSize() throws IOException
{
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "Set QR size");
    
    // Set barcode dimensions in pixels
    generator.getParameters().getBarcode().getXDimension().setPixels(4);
    
    // Set image resolution
    generator.getParameters().setResolution(300);
    
    generator.save("qrcode_sized.png");
}
```

### Error Correction Level

QR codes support different error correction levels that allow the barcode to be read even if it's partially damaged:

```java
public void defineErrorCorrectionLevel() throws IOException
{
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "Data with error correction");
    
    // Set error correction level
    // Options: LEVEL_L (7%), LEVEL_M (15%), LEVEL_Q (25%), LEVEL_H (30%)
    generator.getParameters().getBarcode().getQR().setQrErrorLevel(QRErrorLevel.LEVEL_H);
    
    generator.save("qrcode_error_correction.png");
}
```

#### Error Correction Levels Explained

- **Level L**: ~7% of codewords can be restored
- **Level M**: ~15% of codewords can be restored (default)
- **Level Q**: ~25% of codewords can be restored
- **Level H**: ~30% of codewords can be restored

#### When to Use Each Level

**LEVEL_L (7% recovery)** - Lowest error correction:
- Clean, controlled environments
- Digital displays only (no printing)
- Large QR codes with minimal damage risk
- Maximum data capacity needed
- ✅ **Advantage**: Smallest QR code size for given data
- ⚠️ **Risk**: Low damage tolerance

**LEVEL_M (15% recovery)** - Medium error correction (Default):
- General purpose applications
- Indoor printing on quality materials
- Standard business cards, documents
- Balanced approach between size and reliability
- ✅ **Advantage**: Good balance of size and durability
- 📌 **Recommended**: Most common use case

**LEVEL_Q (25% recovery)** - High error correction:
- Industrial environments with some wear expected
- Outdoor use with moderate exposure
- Product packaging that may get scratched
- Smaller QR codes that are easier to damage
- ✅ **Advantage**: Good damage tolerance
- ⚠️ **Trade-off**: Larger code size

**LEVEL_H (30% recovery)** - Highest error correction:
- Harsh environments (construction sites, factories)
- Outdoor use with weather exposure
- Surfaces that will experience significant wear
- Marketing materials where partial coverage is intentional
- Production marking on rough surfaces
- Very small QR codes where each module matters
- ✅ **Advantage**: Maximum reliability, can be read even with 30% damage
- ⚠️ **Trade-off**: Largest code size, visually denser

### Encoding Mode

#### Understanding QREncodeMode vs ECIEncodings

Before diving into encoding examples, it's important to understand the difference between these two parameters:

**QREncodeMode** - HOW to encode the data:
- Defines the **encoding method/algorithm** used to pack data into the QR code
- Think of it as choosing "how to package the shipment"
- Examples: `AUTO`, `BINARY`, `ECI`, `EXTENDED`

**ECIEncodings** - WHICH character encoding to use:
- Defines the **character encoding standard** (like UTF-8, Windows-1251, Shift_JIS)
- Think of it as choosing "which language to write the address in"
- Only relevant when using `QREncodeMode.ECI`

**How They Work Together:**

```java
// Step 1: Choose the METHOD (how to encode)
generator.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.ECI);

// Step 2: Choose the CHARACTER ENCODING (which encoding to use)
generator.getParameters().getBarcode().getQR().setQrECIEncoding(ECIEncodings.UTF8);
```

#### Encoding Examples

**For Simple Data (Latin characters, numbers):**

```java
public void autoEncodingMode() throws IOException
{
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "Simple123");
    
    // AUTO mode automatically selects optimal encoding
    generator.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.AUTO);
    
    generator.save("qrcode_auto.png");
}
```

**For Unicode Text (Cyrillic, Chinese, Japanese, etc.):**

```java
public void defineEncodingMode() throws IOException
{
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "データ");
    
    // Use ECI mode for explicit character encoding
    generator.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.ECI);
    generator.getParameters().getBarcode().getQR().setQrECIEncoding(ECIEncodings.UTF8);
    
    generator.save("qrcode_utf8.png");
}
```

**For Binary Data:**

```java
public void binaryEncodingMode() throws IOException
{
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "BinaryData");
    
    // BINARY mode for raw binary data
    generator.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.BINARY);
    
    generator.save("qrcode_binary.png");
}
```

#### Available Encoding Modes

- `AUTO` - Automatically selects the best encoding method (recommended for most cases)
- `BINARY` - Binary data encoding (for raw bytes)
- `ECI` - Extended Channel Interpretation (use with ECIEncodings for specific character sets)
- `EXTENDED` - Extended mode supporting FNC1 and Multi-ECI (advanced use cases)

## Complete Example

```java
public void completeExample() throws IOException
{
    try {
        // Initialize barcode generator
        BarcodeGenerator generator = new BarcodeGenerator(
            EncodeTypes.QR,
            "https://www.aspose.com"
        );
        
        // Configure appearance
        generator.getParameters().getBarcode().getXDimension().setPixels(4);
        generator.getParameters().setResolution(300);
        
        // Configure QR-specific settings
        generator.getParameters().getBarcode().getQR()
            .setQrErrorLevel(QRErrorLevel.LEVEL_M);
        generator.getParameters().getBarcode().getQR()
            .setQrEncodeMode(QREncodeMode.ECI);
        generator.getParameters().getBarcode().getQR()
            .setQrECIEncoding(ECIEncodings.UTF8);
        
        // Set colors
        generator.getParameters().setBackColor(java.awt.Color.WHITE);
        generator.getParameters().getBarcode().setBarColor(java.awt.Color.BLACK);
        
        // Save to file
        generator.save("qrcode_complete.png");
        
        System.out.println("QR Code generated successfully!");
        
    } catch (Exception e) {
        e.printStackTrace();
    }
}
```

## Micro QR Code

For smaller data amounts, you can use Micro QR Code which is a more compact version:

```java
public void generateMicroQR() throws IOException
{
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.MICRO_QR, "12345");
    
    // Micro QR specific settings
    generator.getParameters().getBarcode().getXDimension().setPixels(4);
    
    generator.save("micro_qr.png");
}
```

## Common Use Cases

### URL Encoding

```java
public void encodeURL() throws IOException
{
    BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR, 
        "https://www.example.com/product/12345"
    );
    generator.save("url_qrcode.png");
}
```

### Contact Information (vCard)

```java
public void encodeVCard() throws IOException
{
    String vcard = "BEGIN:VCARD\n" +
                   "VERSION:3.0\n" +
                   "FN:John Doe\n" +
                   "TEL:+1-555-1234\n" +
                   "EMAIL:john@example.com\n" +
                   "END:VCARD";
    
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, vcard);
    
    // Use ECI mode for proper UTF-8 encoding
    generator.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.ECI);
    generator.getParameters().getBarcode().getQR().setQrECIEncoding(ECIEncodings.UTF8);
    
    generator.save("vcard_qrcode.png");
}
```

### WiFi Configuration

```java
public void encodeWiFi() throws IOException
{
    String wifi = "WIFI:T:WPA;S:MyNetwork;P:MyPassword;;";
    
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, wifi);
    generator.save("wifi_qrcode.png");
}
```

## Best Practices

1. **Choose appropriate error correction level**: Higher levels increase reliability but make the QR code larger
2. **Use ECI mode with UTF8 encoding** for international characters
3. **Set adequate resolution** (at least 300 DPI) for printing
4. **Keep data concise** - smaller data creates simpler, more scannable codes
5. **Test scanning** on multiple devices before production use
6. **Use AUTO mode** for general purposes - it automatically optimizes encoding

## Next Steps

- Learn about [Customizing Barcode Appearance](../customize-appearance)
- Explore [2D Barcode Types](../../2d-barcodes-overview)
- Read about [Barcode Recognition](../../barcode-recognition/basic-barcode-recognition)
