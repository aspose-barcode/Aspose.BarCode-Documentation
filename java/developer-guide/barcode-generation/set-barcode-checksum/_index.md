---
title: Set Barcode Checksum
type: docs
weight: 50
url: /java/developer-guide/barcode-generation2/set-barcode-checksum/
---

# Set Barcode Checksum

## Overview

A checksum (check digit) is an error detection mechanism used in many 1D barcode standards. A checksum is usually the last symbol in the barcode sequence. Barcode scanners calculate the checksum from the preceding data and compare it with the checksum value.

Some 1D symbologies have an optional checksum. Other symbologies have an obligatory checksum that is part of the standard.

## Barcode checksum settings

Aspose.BarCode for Java provides checksum control through barcode parameters. For 1D barcodes, you can enable or disable checksum generation depending on the symbology rules.

The following table lists symbologies with optional and obligatory checksum requirements.

|Checksum requirements|1D symbologies|
|---|---|
|**Optional**|Codabar, Code39, Italian Post 25, Interleaved 2 of 5, Matrix 2 of 5, MSI, Pharmacode, PatchCode, PZN, Standard 2 of 5|
|**Obligatory**|CodablockF, Code11, Code128, Code16K, Code32, Code93, Databar Expanded Stacked, Databar Expanded, Databar OmniDirectional, Databar Stacked OmniDirectional, Databar Stacked, DatabarLimited, DatabarTruncated, EAN13, EAN14, EAN2, EAN5, EAN8, GS1 CodablockF, GS1 Code128, IATA 2 of 5, ISBN, ISMN, ISSN, ITF14, ITF6, OPC, SSCC14, SSCC18, UPCA, UPCE, UpcaGs1DatabarCoupon, VIN|

## Optional checksum controls

For symbologies with an optional checksum, you can enable or disable checksum generation.

The following example shows how to control checksum generation for Code 39.

```java
import com.aspose.barcode.generation.*;

public class Code39ChecksumExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_39, "CODE");

        gen.getParameters().getBarcode().setChecksumEnabled(EnableChecksum.NO);
        gen.save("code39_without_checksum.png", BarCodeImageFormat.PNG);

        gen.getParameters().getBarcode().setChecksumEnabled(EnableChecksum.YES);
        gen.save("code39_with_checksum.png", BarCodeImageFormat.PNG);
    }
}
```

## Obligatory checksum controls

For symbologies with an obligatory checksum, the library computes the checksum according to the standard.

If you try to disable the checksum for a symbology where it is required, the setting may be ignored or may cause an exception, depending on the symbology.

## Display checksum for Code 128

For Code 128 and GS1 Code 128, the library provides `setChecksumAlwaysShow`. When enabled, the checksum digit is included in the human-readable text.

```java
import com.aspose.barcode.generation.*;

public class Code128ChecksumDisplayExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "CODE");

        gen.getParameters().getBarcode().setChecksumAlwaysShow(false);
        gen.save("code128_checksum_hidden.png", BarCodeImageFormat.PNG);

        gen.getParameters().getBarcode().setChecksumAlwaysShow(true);
        gen.save("code128_checksum_shown.png", BarCodeImageFormat.PNG);
    }
}
```
