---
title: "MaxiCode Barcodes"
description: "Learn how to generate and read structured MaxiCode mode 2 and mode 3 barcodes."
type: docs
weight: 80
url: /java/developer-guide/complex-barcode/supported_types/maxicode/
---

# MaxiCode Barcodes

Aspose.BarCode for Java provides typed models for MaxiCode mode 2 and mode 3. The modes differ mainly in the postal-code format and both support structured second messages.

The complete source code for this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/complex/supported_types/maxicode/MaxiCodeBarcodes.java" target="_blank">View MaxiCodeBarcodes.java</a>

## Create MaxiCode mode 2

Mode 2 uses a numeric postal code:

```java
MaxiCodeCodetextMode2 codetext =
        new MaxiCodeCodetextMode2();

codetext.setPostalCode("524032140");
codetext.setCountryCode(56);
codetext.setServiceCategory(999);
```

## Add a structured second message

```java
MaxiCodeStructuredSecondMessage message =
        new MaxiCodeStructuredSecondMessage();

message.add("MODE 2 MESSAGE");
message.add("WAREHOUSE 12");
message.setYear(26);

codetext.setSecondMessage(message);
```

## Create MaxiCode mode 3

Mode 3 supports an alphanumeric postal code:

```java
MaxiCodeCodetextMode3 codetext =
        new MaxiCodeCodetextMode3();

codetext.setPostalCode("B1050");
codetext.setCountryCode(56);
codetext.setServiceCategory(999);
```

## Read the recognized mode

The recognized MaxiCode mode is available through extended parameters:

```java
int mode = results[0]
        .getExtended()
        .getMaxiCode()
        .getMode();
```

Pass the mode and recognized text to the decoder:

```java
MaxiCodeCodetext decoded =
        ComplexCodetextReader.tryDecodeMaxiCode(
                mode,
                results[0].getCodeText()
        );
```

## Validate the decoded subtype

Check whether the result is `MaxiCodeCodetextMode2` or `MaxiCodeCodetextMode3` before casting. Then validate postal code, country code, service category, year, and second-message identifiers.

## Recommendations

- Use mode 2 for numeric postal codes.
- Use mode 3 for alphanumeric postal codes.
- Read the recognized mode from extended parameters.
- Pass the mode to `tryDecodeMaxiCode`.
- Validate the decoded subtype before casting.
