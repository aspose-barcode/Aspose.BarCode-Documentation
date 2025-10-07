---
title: Generate QR Code
description: Learn how to generate QR codes using Aspose.BarCode for Java with examples of error correction levels, encoding modes, and common use cases.
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
    generator.save(folder + "qrcode.png");
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

    generator.save(folder + "qrcode_sized.png");
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

    generator.save(folder + "qrcode_error_correction.png");
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

    generator.save(folder + "qrcode_auto.png");
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

    generator.save(folder + "qrcode_utf8.png");
}
```

**For Binary Data:**

```java
public void binaryEncodingMode() throws IOException
{
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "BinaryData");

    // BINARY mode for raw binary data
    generator.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.BINARY);

    generator.save(folder + "qrcode_binary.png");
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
        generator.save(folder + "qrcode_complete.png");

        System.out.println("QR Code generated successfully!");

    } catch (Exception e) {
        e.printStackTrace();
    }
}
```

## Micro QR Code

### What is Micro QR Code?

Micro QR Code is a compact version of standard QR Code, designed for applications where space is limited but data requirements are minimal.

### QR Code vs Micro QR Code

#### Visual Differences

**Standard QR Code:**
- 3 position detection patterns (large squares in corners)
- Minimum size: 21×21 modules
- Maximum size: 177×177 modules

**Micro QR Code:**
- **Only 1 position detection pattern** (top-left corner)
- Minimum size: 11×11 modules
- Maximum size: 17×17 modules

#### Data Capacity

**Standard QR Code:**
- Numeric: up to **7,089 digits**
- Alphanumeric: up to **4,296 characters**
- Binary: up to **2,953 bytes**

**Micro QR Code:**
- Numeric: up to **35 digits**
- Alphanumeric: up to **21 characters**
- Binary: up to **15 bytes**

#### Versions

**Standard QR Code:**
- Versions 1-40 (size increases by 4 modules per version)

**Micro QR Code:**
- Versions M1, M2, M3, M4 (limited sizes)

#### Error Correction Support

**Standard QR Code:**
- All levels supported: L, M, Q, H

**Micro QR Code:**
- M1: Error detection only (no correction)
- M2: L, M levels
- M3: L, M levels
- M4: L, M, Q levels

#### When to Use Each Type

**Use Standard QR Code when:**
- ✅ Encoding large amounts of data (URLs, vCard, long text)
- ✅ Need for high error correction (Level H)
- ✅ Maximum scanner compatibility required
- ✅ Standard use cases (marketing, payments, etc.)

**Use Micro QR Code when:**
- ✅ Very limited data (serial numbers, short IDs)
- ✅ Space is extremely constrained (small components, microchips)
- ✅ Industrial marking of tiny parts
- ✅ Data is less than 20 characters
- ⚠️ Note: Not all scanners support Micro QR

**Simple Rule**: If data is less than 20 characters AND space is limited → use Micro QR. For all other cases → use standard QR Code.

### Generating Micro QR Code

```java
public void generateMicroQR() throws IOException
{
    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.MICRO_QR, "12345");
    
    // Micro QR specific settings
    generator.getParameters().getBarcode().getXDimension().setPixels(4);
    
    generator.save(folder + "micro_qr.png");
}
```

### Comparison Example

```java
public void compareQRandMicroQR() throws IOException
{
    // Standard QR - for URL or longer data
    BarcodeGenerator standardQR = new BarcodeGenerator(
        EncodeTypes.QR,
        "https://example.com/product/12345"
    );
    standardQR.save(folder + "standard_qr.png");
    
    // Micro QR - for short ID or serial number
    BarcodeGenerator microQR = new BarcodeGenerator(
        EncodeTypes.MICRO_QR,
        "ID-12345"
    );
    microQR.save(folder + "micro_qr.png");
}
```

## Common Use Cases

QR codes are widely used because they can be scanned quickly with smartphones and can encode various types of data. Here are some practical examples:

### URL Encoding

QR codes are commonly used to share website links, allowing users to visit a webpage by simply scanning the code.

```java
public void encodeURL() throws IOException
{
    BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "https://docs.aspose.com/"
    );
    generator.save(folder + "url_qrcode.png");
}
```

### Contact Information (vCard)

QR codes can store complete contact information in vCard format, making it easy to add contacts to a phone's address book.

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
    
    // Use ECI mode for proper UTF-8 encoding if contact contains international characters
    generator.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.ECI);
    generator.getParameters().getBarcode().getQR().setQrECIEncoding(ECIEncodings.UTF8);

    generator.save(folder + "vcard_qrcode.png");
}
```

### WiFi Configuration

WiFi QR codes allow users to connect to a wireless network by scanning the code, without manually entering the password.

```java
public void encodeWiFi() throws IOException
{
    // Format: WIFI:T:<encryption>;S:<network name>;P:<password>;;
    String wifi = "WIFI:T:WPA;S:MyNetwork;P:MyPassword;;";

    BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, wifi);
    generator.save(folder + "wifi_qrcode.png");
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

- <a href="/barcode/java/developer-guide/barcode-generation/customize-appearance/" target="_blank">Customizing Barcode Appearance</a>
- <a href="/barcode/java/developer-guide/2d-barcodes-overview/" target="_blank">2D Barcode Types</a>
- <a href="/barcode/java/developer-guide/barcode-recognition/basic-barcode-recognition/" target="_blank">Barcode Recognition</a>
