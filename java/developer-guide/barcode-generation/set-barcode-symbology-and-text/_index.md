---
title: Set Barcode Symbology and Text
type: docs
weight: 20
url: /java/developer-guide/barcode-generation2/set-barcode-symbology-and-text/
---

# Set Barcode Symbology and Text

## Overview

In Aspose.BarCode for Java, a generated barcode is defined by two inputs:

- The barcode symbology (for example, Code 128, QR, or GS1-128).
- The code text (the value to encode).

The main entry point for generation is the `BarcodeGenerator` class.

## Basic setup

Import the generation package:

```java
import com.aspose.barcode.generation.*;
```

## Create a BarcodeGenerator

Create a generator by passing `EncodeTypes` and the code text:

```java
import com.aspose.barcode.generation.*;

public class BasicGeneration {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ABC-12345");
        generator.save("code128.png", BarCodeImageFormat.PNG);
    }
}
```

## Choose a symbology (EncodeTypes)

`EncodeTypes` selects the encoding rules and barcode geometry. You must choose a symbology that matches your data requirements and target scanners.

The following example creates a QR code:

```java
import com.aspose.barcode.generation.*;

public class QrGeneration {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "https://example.com");

        gen.getParameters().getBarcode().getXDimension().setMillimeters(0.5f);
        gen.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.AUTO);
        gen.getParameters().getBarcode().getQR().setQrErrorLevel(QRErrorLevel.LEVEL_M);

        gen.save("qrcode.png", BarCodeImageFormat.PNG);
    }
}
```

## QR-specific parameters

This section lists common QR parameters. Configure them through `generator.getParameters().getBarcode().getQR()`.

### Error correction level

QR codes support different error correction levels. Higher levels increase damage tolerance but also increase symbol density.

| Level | Recovery Capacity | Best For | Trade-off |
|-------|-------------------|----------|-----------|
| **Level L** | ~7% | Clean environments, digital displays | Smallest size, lowest reliability |
| **Level M** | ~15% (Default) | Standard printing, labels | Balanced size and reliability |
| **Level Q** | ~25% | Industrial environments, outdoor use | Larger size, good damage tolerance |
| **Level H** | ~30% | Harsh environments, construction | Largest size, maximum reliability |

```java
import com.aspose.barcode.generation.*;

public class QrErrorCorrectionExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Data with error correction");

        // Set to highest level for maximum reliability
        gen.getParameters().getBarcode().getQR().setQrErrorLevel(QRErrorLevel.LEVEL_H);
        gen.save("qr_level_h.png", BarCodeImageFormat.PNG);
    }
}
```

### Encoding mode

`QREncodeMode` controls how data is encoded in the symbol. When you use `QREncodeMode.ECI`, you can also set `QrECIEncoding`.

```java
import com.aspose.barcode.generation.*;

public class QrEciEncodingExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "データ");

        gen.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.ECI);
        gen.getParameters().getBarcode().getQR().setQrECIEncoding(ECIEncodings.UTF8);

        gen.save("qr_eci_utf8.png", BarCodeImageFormat.PNG);
    }
}
```

## Micro QR Code

Micro QR Code is a compact version of standard QR Code, designed for applications where space is limited and data is short (up to 35 numeric digits or 21 alphanumeric characters).

### Comparison: QR vs Micro QR

| Feature | Standard QR Code | Micro QR Code |
|---------|------------------|---------------|
| **Position Patterns** | 3 (large squares in corners) | 1 (top-left corner only) |
| **Min Size** | 21×21 modules | 11×11 modules |
| **Capacity** | High (up to ~7000 digits) | Very Low (up to 35 digits) |
| **Use Case** | URLs, Payments, Data | Circuit boards, tiny serials |

### Generating Micro QR

```java
import com.aspose.barcode.generation.*;

public class MicroQrExample {
    public static void main(String[] args) throws Exception {
        // Use EncodeTypes.MICRO_QR
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.MICRO_QR, "12345");

        // Micro QR has versions M1-M4, handled automatically
        gen.getParameters().getBarcode().getXDimension().setPixels(4);
        
        gen.save("micro_qr.png", BarCodeImageFormat.PNG);
    }
}
```

## Common QR Code Recipes

Here are ready-to-use examples for common QR code applications.

### 1. WiFi Configuration

Allows scanning to connect to a WiFi network.

```java
// Format: WIFI:T:<encryption>;S:<network name>;P:<password>;;
String wifi = "WIFI:T:WPA;S:MyNetwork;P:MyPassword;;";

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, wifi);
gen.save("wifi_qr.png", BarCodeImageFormat.PNG);
```

### 2. vCard (Contact Information)

Encodes contact details for adding to a phone's address book.

```java
String vcard = "BEGIN:VCARD\n" +
               "VERSION:3.0\n" +
               "FN:John Doe\n" +
               "TEL:+1-555-1234\n" +
               "EMAIL:john@example.com\n" +
               "END:VCARD";

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, vcard);
gen.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.ECI);
gen.getParameters().getBarcode().getQR().setQrECIEncoding(ECIEncodings.UTF8);
gen.save("vcard_qr.png", BarCodeImageFormat.PNG);
```

### 3. Website URL

```java
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "https://www.aspose.com");
gen.save("url_qr.png", BarCodeImageFormat.PNG);
```

## Set or update the code text

You can reuse a `BarcodeGenerator` instance and only update the code text. This is useful for batch generation.

```java
import com.aspose.barcode.generation.*;

public class BatchGeneration {
    public static void main(String[] args) throws Exception {
        String[] codes = {"PROD001", "PROD002", "PROD003"};

        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, codes[0]);

        gen.getParameters().getBarcode().getXDimension().setMillimeters(0.3f);
        gen.getParameters().getBarcode().getBarHeight().setMillimeters(10.0f);
        gen.getParameters().setResolution(300.0f);

        for (String code : codes) {
            gen.setCodeText(code);
            gen.save("batch_" + code + ".png", BarCodeImageFormat.PNG);
        }
    }
}
```

## Code 128 notes: subsets

Code 128 uses three subsets (A, B, C). The library automatically switches between subsets to reduce barcode length.

| Subset | Character set | Best for | Encoding |
|--------|---------------|----------|----------|
| **A** | Uppercase + control | Control codes and uppercase | 1 char per symbol |
| **B** | Printable ASCII | Mixed-case text | 1 char per symbol |
| **C** | Numeric pairs (00–99) | Pure numeric data | 2 digits per symbol |

### Optimization Tips
- **Use numeric data** when possible: Subset C is twice as dense as A or B.
- **Group data types**: Keep numbers together and letters together to minimize subset switching overhead.
- **Let the library handle it**: Aspose.BarCode automatically optimizes the subset switching for you.

## Example: GS1-128 (Application Identifiers)

GS1-128 is a variant of Code 128 that uses Application Identifiers (AIs) for structured data.

```java
import com.aspose.barcode.generation.*;

public class GS1Code128Example {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(
            EncodeTypes.GS_1_CODE_128,
            "(01)09501101530008(17)251231(10)BATCH-42"
        );

        gen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
        gen.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);
        gen.getParameters().setResolution(300.0f);

        gen.save("gs1_128.png", BarCodeImageFormat.PNG);
    }
}
```

### Common GS1 Application Identifiers

| AI | Description | Format | Example |
|----|-------------|--------|---------|
| `(01)` | GTIN (Global Trade Item Number) | 14 digits | `(01)09501101530008` |
| `(10)` | Batch/Lot Number | Variable | `(10)BATCH-2025` |
| `(17)` | Expiration Date | YYMMDD | `(17)251231` |
| `(21)` | Serial Number | Variable | `(21)SN12345678` |
| `(30)` | Quantity | Variable | `(30)100` |
| `(310n)` | Net Weight (kg) | Variable | `(3103)001234` |
| `(400)` | Customer Purchase Order | Variable | `(400)PO123456` |

### Advanced GS1-128 Example

This example demonstrates how to encode a complex label with multiple application identifiers (GTIN, Expiration, Batch, Serial).

```java
import com.aspose.barcode.generation.*;

public class GS1CompleteExample {
    public static void main(String[] args) throws Exception {
        // Complex GS1 data string with multiple AIs
        String gs1Data = "(01)09512345678900" +  // GTIN
                         "(17)260630" +           // Expiration: June 30, 2026
                         "(10)LOT2025A" +         // Batch number
                         "(21)SERIAL123456";      // Serial number

        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.GS_1_CODE_128, gs1Data);

        // Professional label settings
        gen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
        gen.getParameters().getBarcode().getBarHeight().setMillimeters(16.0f);
        gen.getParameters().setResolution(300.0f);

        // Add quiet zones
        gen.getParameters().getBarcode().getPadding().getLeft().setMillimeters(3.0f);
        gen.getParameters().getBarcode().getPadding().getRight().setMillimeters(3.0f);

        // Show human-readable text below
        gen.getParameters().getBarcode().getCodeTextParameters().setLocation(CodeLocation.BELOW);
        
        gen.save("gs1_128_complete.png", BarCodeImageFormat.PNG);
    }
}
```

## Error handling

If input data does not match the symbology rules, generation can fail. The following example shows basic error handling.

For example, EAN-13 requires 13 digits with a valid checksum digit.

```java
import com.aspose.barcode.generation.*;

public class ErrorHandlingExample {
    public static void main(String[] args) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN_13, "invalid");
            gen.save("test.png", BarCodeImageFormat.PNG);

        } catch (BarCodeException ex) {
            System.err.println("Barcode Error: " + ex.getMessage());
            System.err.println("Check data format and EncodeTypes compatibility");

        } catch (Exception ex) {
            System.err.println("General Error: " + ex.getMessage());
            ex.printStackTrace();
        }
    }
}
```
