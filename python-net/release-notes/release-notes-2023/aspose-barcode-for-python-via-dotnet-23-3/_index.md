---
title: Aspose.BarCode for Python via .NET 23.3
type: docs
weight: 10
url: /python-net/aspose-barcode-for-python-via-dotnet-23-3/
---

{{% alert color="primary" %}} 

This article contains release notes information for [**Aspose.BarCode for Python via .NET 23.3**](https://releases.aspose.com/barcode/python-net/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37948|Investigate replacement of Reed-Solomon library|Enhancement|
|BARCODENET-38360|Add AntiAlias to barcode properties|Enhancement|
|BARCODENET-38322|Remove obsolete properties and warnings|Enhancement|
|BARCODENET-36917|Investigate multithreading addition to the Datamatrix region detection algorithms|Enhancement|

## Public API changes and backwards compatibility
The following API was added:
- aspose.barcode.generation.BaseGenerationParameters.use_anti_alias

The following obsolete API was removed:
- aspose.barcode.generation.BarcodeParameters.auto_size_mode
- aspose.barcode.generation.BarcodeParameters.bar_code_height
- aspose.barcode.generation.BarcodeParameters.bar_code_width
- aspose.barcode.generation.BarcodeParameters.fore_color
- aspose.barcode.barcoderecognition.BarCodeReader.strip_fnc
- aspose.barcode.barcoderecognition.BarCodeReader.customer_information_interpreting_type
- aspose.barcode.barcoderecognition.BarCodeReader.checksum_validation
- aspose.barcode.barcoderecognition.BarCodeReader.detect_encoding