---
title: Aspose.BarCode for .NET 23.4 Release Notes
date: "2023-04-18"
author: "Konstantin Alkhimov"
type: docs
weight: 10
url: /net/aspose-barcode-for-net-23-4-release-notes/
description: A summary of recent changes, enhancements and bug fixes in Aspose.BarCode for .NET 23.4.0 (April 2023) release.
keywords:
- 2023
- April
- new
- release
- changelog
- Code 128
- ISO 15417
---

{{% alert color="primary" %}} 

This article contains release notes information for [**Aspose.BarCode for .NET 23.4 (April 2023)**](https://downloads.aspose.com/barcode/net/new-releases/aspose.barcode-for-.net-23.4/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-38578|Add support of codeset selection for Code128 encoder|Enhancement|
|BARCODENET-38574|Render one whitespace symbol to SVG windows bug|Bug|

## Public API changes and backwards compatibility

Code128EncodeMode enum was added to select allowed code128 codesets.
Code128 parameters were added to BarcodeGenerator.Parameters.Barcode
Code128 parameters were added to WinForms, WPF and Reporting Services components.
Code128EncodeMode was added to Code128 parameters.

```cs
//Generate code 128 with ISO 15417 encoding
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Code128, "ABCD1234567890");
generator.Parameters.Barcode.Code128.Code128EncodeMode = Code128EncodeMode.Auto;
generator.Save(@"d:\save\rec\code128Auto.png", BarCodeImageFormat.Png);

//Generate code 128 only with Codeset A encoding
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Code128, "ABCD1234567890");
generator.Parameters.Barcode.Code128.Code128EncodeMode = Code128EncodeMode.CodeA;
generator.Save(@"d:\save\rec\code128CodeA.png", BarCodeImageFormat.Png);
```
