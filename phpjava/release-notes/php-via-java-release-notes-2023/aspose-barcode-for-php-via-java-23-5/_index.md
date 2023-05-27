---
title: Aspose.BarCode for PHP via Java 23.5
type: docs
weight: 9600
url: /phpjava/aspose-barcode-for-php-via-java-23-5/
aliases:
- /java/aspose-barcode-for-php-via-java-23-5/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for PHP via Java 23.5](https://downloads.aspose.com/barcode/php/new-releases/aspose.barcode-for-php-via-java-23.5/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-38578|Add support of codeset selection for Code128 encoder|Enhancement|
|BARCODENET-38574|Render one whitespace symbol to SVG windows bug|Bug|

## Public API changes and backwards compatibility

Generation->Code128EncodeMode class was added to select allowed code128 codesets.
Function getCode128():Code128Parameters was added to Generation->BarcodeParameters
Function Code128EncodeMode getCode128EncodeMode():int was added to Generation->Code128Parameters
Function setCode128EncodeMode(int) was added to Generation->Code128Parameters

```php
//Generate code 128 with ISO 15417 encoding
$generator = new BarcodeGenerator(EncodeTypes::Code128, "ABCD1234567890");
$generator->Parameters->Barcode->Code128->setCode128EncodeMode(Code128EncodeMode::AUTO);
$generator->Save(filePath, BarCodeImageFormat::Png);

//Generate code 128 only with Codeset A encoding
$generator = new BarcodeGenerator(EncodeTypes::Code128, "ABCD1234567890");
$generator->Parameters->Barcode->Code128->setCode128EncodeMode(Code128EncodeMode::CODE_A);
$generator->Save(filePath, BarCodeImageFormat::Png);
```