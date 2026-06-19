---
title: "Generate QR Codes"
description: "Learn how to generate QR Codes and Micro QR Codes in Aspose.BarCode for Java, configure error correction, module size, UTF-8 ECI encoding, colors, URLs, vCards, and Wi-Fi data."
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/generate-qr-code/
---

# Generate QR Codes

QR Code is a two-dimensional symbology suitable for URLs, identifiers, contact information, Wi-Fi configuration, and multilingual text. Aspose.BarCode for Java supports standard QR Code and Micro QR Code generation, error correction levels, ECI encoding, module sizing, and visual customization.

The complete source code for the examples in this article is available on GitHub:

[View GenerateQRCode.java](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/GenerateQRCode.java)

You can also browse all barcode generation examples in the [Generation examples directory](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation).

## Generate a basic QR Code

Create a `BarcodeGenerator` with `EncodeTypes.QR`, provide the code text, and save the image.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "https://www.aspose.com"
);

generator.save("qrcode.png", BarCodeImageFormat.PNG);
```

## Configure error correction

QR Codes support several error correction levels. Higher levels allow more damaged modules to be restored but increase the symbol size for the same data.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "Data with error correction"
);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setQrErrorLevel(QRErrorLevel.LEVEL_H);

generator.save("qrcode_error_correction.png", BarCodeImageFormat.PNG);
```

Available levels are:

- `LEVEL_L` — approximately 7% recovery;
- `LEVEL_M` — approximately 15% recovery;
- `LEVEL_Q` — approximately 25% recovery;
- `LEVEL_H` — approximately 30% recovery.

Choose a higher level when the symbol may be scratched, obscured, or printed under difficult conditions.

## Set QR Code module size

For QR Codes, X-Dimension defines the module size.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "Set QR size"
);

generator.getParameters().getBarcode().getXDimension().setPixels(4);
generator.getParameters().setResolution(300);

generator.save("qrcode_sized.png", BarCodeImageFormat.PNG);
```

Increasing X-Dimension enlarges each module and therefore the complete QR Code image.

## Encode Unicode text with ECI

Use ECI mode and UTF-8 when the code text contains characters outside the default encoding.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "データ"
);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setQrEncodeMode(QREncodeMode.ECI);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setQrECIEncoding(ECIEncodings.UTF8);

generator.save("qrcode_utf8.png", BarCodeImageFormat.PNG);
```

The reader application must support the selected ECI encoding to reconstruct the original text correctly.

## Configure a complete QR Code

The following example combines module size, resolution, error correction, UTF-8 ECI encoding, and colors.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "https://www.aspose.com"
);

generator.getParameters().getBarcode().getXDimension().setPixels(4);
generator.getParameters().setResolution(300);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setQrErrorLevel(QRErrorLevel.LEVEL_M);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setQrEncodeMode(QREncodeMode.ECI);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setQrECIEncoding(ECIEncodings.UTF8);

generator.getParameters().setBackColor(java.awt.Color.WHITE);
generator.getParameters().getBarcode().setBarColor(java.awt.Color.BLACK);

generator.save("qrcode_complete.png", BarCodeImageFormat.PNG);
```

High contrast between the modules and background is recommended for reliable recognition.

## Generate a Micro QR Code

Micro QR Code is a compact QR variant intended for shorter data.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.MICRO_QR,
        "MicroQR1234567"
);

generator.getParameters().getBarcode().getXDimension().setPixels(4);
generator.save("micro_qr.png", BarCodeImageFormat.PNG);
```

Use standard QR Code for larger payloads and broad compatibility. Use Micro QR when the data is short and the available area is limited.

## Encode a URL

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "https://docs.aspose.com/"
);

generator.save("url_qrcode.png", BarCodeImageFormat.PNG);
```

The encoded data is plain text. The scanning application determines whether to open it as a URL.

## Compare standard QR and Micro QR

```java
BarcodeGenerator standardQrGenerator = new BarcodeGenerator(
        EncodeTypes.QR,
        "https://example.com/product/12345"
);
standardQrGenerator.save("standard_qr.png", BarCodeImageFormat.PNG);

BarcodeGenerator microQrGenerator = new BarcodeGenerator(
        EncodeTypes.MICRO_QR,
        "ID-12345"
);
microQrGenerator.save("micro_qr.png", BarCodeImageFormat.PNG);
```

The two variants differ in capacity, symbol structure, and supported configurations.

## Encode a vCard

A QR Code can contain a text representation of a vCard.

```java
String vcard = "BEGIN:VCARD\n"
        + "VERSION:3.0\n"
        + "FN:John Doe\n"
        + "TEL:+1-555-1234\n"
        + "EMAIL:john@example.com\n"
        + "END:VCARD";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        vcard
);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setQrEncodeMode(QREncodeMode.ECI);

generator.getParameters()
        .getBarcode()
        .getQR()
        .setQrECIEncoding(ECIEncodings.UTF8);

generator.save("vcard_qrcode.png", BarCodeImageFormat.PNG);
```

The contact application on the scanning device interprets the vCard structure.

## Encode Wi-Fi configuration

Wi-Fi configuration is encoded as a formatted text string.

```java
String wifi = "WIFI:T:WPA;S:MyNetwork;P:MyPassword;;";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        wifi
);

generator.save("wifi_qrcode.png", BarCodeImageFormat.PNG);
```

Keep in mind that the Wi-Fi password is stored directly in the QR Code payload.

## Recommendations

- Use a high-contrast color combination.
- Keep sufficient blank space around the QR Code.
- Select error correction according to expected damage and available symbol area.
- Use UTF-8 ECI for multilingual text when interoperability requires explicit encoding.
- Use Micro QR only when its smaller capacity is sufficient.
- Test URLs, vCards, and Wi-Fi strings with the target scanning applications.
