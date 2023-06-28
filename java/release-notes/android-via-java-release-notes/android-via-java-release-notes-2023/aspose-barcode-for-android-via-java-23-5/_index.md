---
title: Aspose.BarCode for Android via Java 23.5
type: docs
weight: 960
url: /java/aspose-barcode-for-android-via-java-23-5/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Android via Java 23.5](https://downloads.aspose.com/barcode/androidjava/new-releases/aspose.barcode-for-android-via-java-23.5/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-38578|Add support of codeset selection for Code128 encoder|Enhancement|
|BARCODENET-38574|Render one whitespace symbol to SVG windows bug|Bug|

## Public API changes and backwards compatibility

com.aspose.barcode.generation.Code128EncodeMode enum was added to select allowed code128 codesets.
Method getCode128():Code128Parameters was added to com.aspose.barcode.generation.BarcodeParameters
Method Code128EncodeMode getCode128EncodeMode() was added to com.aspose.barcode.generation.Code128Parameters
Method setCode128EncodeMode(Code128EncodeMode) was added to com.aspose.barcode.generation.Code128Parameters

```java
//Generate code 128 with ISO 15417 encoding
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ABCD1234567890");
generator.getParameters().getBarcode().getCode128().setCode128EncodeMode(Code128EncodeMode.AUTO);
generator.save(filePath, BarCodeImageFormat.PNG);

//Generate code 128 only with Codeset A encoding
 BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ABCD1234567890");
 generator.getParameters().getBarcode().getCode128().setCode128EncodeMode(Code128EncodeMode.CODE_A);
 generator.save(filePath, BarCodeImageFormat.PNG);
```