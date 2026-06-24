---
title: "Troubleshoot Complex Barcodes"
description: "Learn how to distinguish recognition failures, decoding failures, missing fields, and standard validation errors."
type: docs
weight: 100
url: /java/developer-guide/complex-barcode/troubleshooting/
---

# Troubleshoot Complex Barcodes

Complex barcode problems can occur at different stages: image recognition, standardized text decoding, required-field validation, or standard-specific range validation. Diagnosing the correct stage avoids misleading fixes.

The complete source code for this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/complex/troubleshooting/ComplexBarcodeTroubleshooting.java" target="_blank">View ComplexBarcodeTroubleshooting.java</a>

## Barcode image is not recognized

A blank or damaged image produces no results:

```java
BarCodeReader reader = new BarCodeReader(
        outputPath,
        DecodeType.ALL_SUPPORTED_TYPES
);

BarCodeResult[] results =
        reader.readBarCodes();

Assert.assertEquals(results.length, 0);
```

This is an image-recognition problem rather than a complex codetext problem. Check image quality, contrast, quiet zones, scaling, and the selected carrier type.

## Recognized text cannot be decoded

A carrier can be recognized while its text is invalid for the requested complex format:

```java
String invalidCodetext =
        "NOT-A-COMPLEX-BARCODE";

Assert.assertNull(
        ComplexCodetextReader.tryDecodeSwissQR(
                invalidCodetext
        )
);
```

The `tryDecode...` methods return `null` for unsupported data.

## Required fields are missing

Constructing codetext can raise `BarCodeException` when required data is absent:

```java
SwissQRCodetext incomplete =
        new SwissQRCodetext();

try {
    incomplete.getConstructedCodetext();
} catch (BarCodeException exception) {
    // Inspect the validation message.
}
```

For Swiss QR, a missing or invalid IBAN is one possible cause.

## Data violates a standard limit

The API validates standard-specific ranges before generation:

```java
MailmarkCodetext invalid =
        new MailmarkCodetext();

invalid.setItemID(100_000_000);
```

An out-of-range Mailmark item identifier causes `BarCodeException` during codetext construction.

## Use a staged diagnostic workflow

Check failures in this order:

1. verify that the image exists and is readable;
2. recognize the carrier barcode;
3. confirm the recognized `DecodeType`;
4. inspect the recognized text;
5. call the matching complex decoder;
6. validate required decoded fields.

## Recommendations

- Do not treat an empty recognition result as a decoding failure.
- Check for `null` from `tryDecode...` methods.
- Validate required fields before generation.
- Catch `BarCodeException` around codetext construction.
- Include standard-limit cases in automated tests.
- Log carrier type and recognized text when diagnosing failures.
