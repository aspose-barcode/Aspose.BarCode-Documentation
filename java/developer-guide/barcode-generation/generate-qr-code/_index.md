---
title: "Generate QR Codes"
description: "Learn how to generate QR Codes and Micro QR Codes in Aspose.BarCode for Java, configure error correction, module size, UTF-8 ECI encoding, colors, URLs, vCards, and Wi-Fi data."
type: docs
weight: 40
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
String codeText = "https://www.aspose.com";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        codeText
);

generator.save("qrcode.png", BarCodeImageFormat.PNG);
```

The default generation parameters are sufficient for a basic QR Code.

## Configure error correction

QR Codes support several error correction levels. Higher levels allow more damaged modules to be restored but increase the symbol size for the same data.

```java
String codeText = "Data with error correction";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        codeText
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

The available error correction combinations depend on the selected QR variant and version. Micro QR supports fewer combinations than standard QR Code.

## Set QR Code module size

For QR Codes, X-Dimension defines the width and height of one module.

```java
String codeText = "Set QR size";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        codeText
);

generator.getParameters().getBarcode().getXDimension().setPixels(4);
generator.getParameters().setResolution(300.0f);

generator.save("qrcode_sized.png", BarCodeImageFormat.PNG);
```

Increasing X-Dimension enlarges each module and therefore the complete QR Code image.

In this example, X-Dimension is specified directly in pixels. The resolution value is mainly relevant when barcode dimensions are specified in physical units such as millimeters, inches, or points. Setting a higher resolution does not by itself increase an X-Dimension that is already defined in pixels.

## Encode Unicode text with ECI

Use ECI mode and UTF-8 when the code text contains characters outside the default encoding.

```java
String codeText = "データ";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        codeText
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

ECI encoding is supported for standard QR Code but is not supported for Micro QR Code.

## Configure a complete QR Code

The following example combines module size, error correction, UTF-8 ECI encoding, colors, and a four-module blank margin around the symbol.

```java
String codeText = "Aspose QR — データ";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        codeText
);

generator.getParameters().getBarcode().getXDimension().setPixels(4);
generator.getParameters().setResolution(300.0f);

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

// X-Dimension is 4 px, so 16 px reserves a four-module margin.
generator.getParameters().getBarcode().getPadding().getLeft().setPixels(16);
generator.getParameters().getBarcode().getPadding().getRight().setPixels(16);
generator.getParameters().getBarcode().getPadding().getTop().setPixels(16);
generator.getParameters().getBarcode().getPadding().getBottom().setPixels(16);

generator.save("qrcode_complete.png", BarCodeImageFormat.PNG);
```

High contrast between the modules and background is recommended for reliable recognition. The required blank margin should be calculated from the module size rather than treated as a universal pixel value.

## Generate a Micro QR Code

Micro QR Code is a compact QR variant intended for shorter data.

```java
String codeText = "MicroQR1234567";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.MICRO_QR,
        codeText
);

generator.getParameters().getBarcode().getXDimension().setPixels(4);
generator.save("micro_qr_basic.png", BarCodeImageFormat.PNG);
```

Use standard QR Code for larger payloads and broad compatibility. Use Micro QR when the data is short and the available area is limited.

Micro QR does not support all standard QR features and combinations. In particular, ECI mode is not supported.

## Encode a URL

```java
String codeText = "https://docs.aspose.com/";

BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        codeText
);

generator.save("url_qrcode.png", BarCodeImageFormat.PNG);
```

The encoded data is plain text. The scanning application determines whether to open it as a URL.

## Compare standard QR and Micro QR

```java
String standardQrText = "https://example.com/product/12345";
BarcodeGenerator standardQrGenerator = new BarcodeGenerator(
        EncodeTypes.QR,
        standardQrText
);
standardQrGenerator.save("standard_qr.png", BarCodeImageFormat.PNG);

String microQrText = "ID-12345";
BarcodeGenerator microQrGenerator = new BarcodeGenerator(
        EncodeTypes.MICRO_QR,
        microQrText
);
microQrGenerator.save("micro_qr_comparison.png", BarCodeImageFormat.PNG);
```

The two variants differ in capacity, symbol structure, and supported configurations.

## Encode a vCard

A QR Code can contain a text representation of a vCard. This example uses a Unicode contact name so that UTF-8 ECI configuration is meaningful.

```java
String vcard = "BEGIN:VCARD\n"
        + "VERSION:3.0\n"
        + "FN:山田 太郎\n"
        + "TEL:+81-3-1234-5678\n"
        + "EMAIL:taro@example.com\n"
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
- Reserve sufficient blank space around the QR Code based on the selected module size.
- Select error correction according to expected damage and available symbol area.
- Use UTF-8 ECI for multilingual text when interoperability requires explicit encoding.
- Do not use ECI mode with Micro QR.
- Use Micro QR only when its smaller capacity and supported feature set are sufficient.
- Test URLs, vCards, and Wi-Fi strings with the target scanning applications.
