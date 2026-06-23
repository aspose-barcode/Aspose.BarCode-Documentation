---
title: "Set Barcode Checksum"
description: "Enable optional checksums and understand symbologies with mandatory check digits."
type: docs
weight: 40
url: /java/developer-guide/barcode-generation/set-barcode-checksum/
---

# Set Barcode Checksum

Checksums help detect data errors. Their behavior depends on the selected symbology.

## Enable an optional checksum

Some symbologies allow a checksum to be enabled or disabled.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.INTERLEAVED_2_OF_5,
        "123456"
);

generator.getParameters().getBarcode()
        .setChecksumEnabled(EnableChecksum.YES);
```

The reader can be configured to validate the checksum through `ChecksumValidation.ON`, `OFF`, or `DEFAULT`.

For Interleaved 2 of 5, enabling the checksum may append a Mod10 digit and may also cause a leading zero to be added so the encoded digit count remains valid for the symbology.

## Mandatory check digits

EAN, UPC, Code 128, Code 93, GS1-128, and several logistics symbologies require a check digit or checksum as part of their specification. For example, EAN-13 consists of 12 data digits plus one check digit.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.EAN_13,
        "590123412345"
);
```

The generated and decoded value is `5901234123457`.

See the <a href="https://docs.aspose.com/barcode/info-cards/ean-13/" target="_blank">EAN-13 standard overview</a>, <a href="https://docs.aspose.com/barcode/info-cards/code-128/" target="_blank">Code 128 standard overview</a>, and <a href="https://docs.aspose.com/barcode/info-cards/code-39/" target="_blank">Code 39 standard overview</a>.

Do not assume that `EnableChecksum.NO` can disable a checksum required by the barcode standard. Mandatory-checksum symbologies may reject such a configuration.

## Complete example


<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/checksum/EnforcedChecksumExamples.java" target="_blank">View EnforcedChecksumExamples.java</a>

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/checksum/OptionalChecksumExamples.java" target="_blank">View OptionalChecksumExamples.java</a>

You can also browse the <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation" target="_blank">Generation examples directory</a>.