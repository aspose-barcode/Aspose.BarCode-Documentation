---
title: BarcodeSettings
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 80
url: /python-net/api-reference/aspose.barcode.barcoderecognition/barcodesettings/
---

## BarcodeSettings class

The main BarCode decoding parameters. Contains parameters which make influence on recognized data.

The BarcodeSettings type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|checksum_validation|Enable checksum validation during recognition for 1D and Postal barcodes.<br/>        Default is treated as Yes for symbologies which must contain checksum, as No where checksum only possible.<br/>        Checksum never used: Codabar, PatchCode, Pharmacode, DataLogic2of5<br/>        Checksum is possible: Code39 Standard/Extended, Standard2of5, Interleaved2of5, ItalianPost25, Matrix2of5, MSI, ItalianPost25, DeutschePostIdentcode, DeutschePostLeitcode, VIN<br/>        Checksum always used: Rest symbologies|
|strip_fnc|Strip FNC1, FNC2, FNC3 characters from codetext. Default value is false.|
|detect_encoding|The flag which force engine to detect codetext encoding for Unicode codesets. Default value is true.|
|australia_post|Gets AustraliaPost decoding parameters|

### See Also

* namespace [aspose.barcode.barcoderecognition](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

