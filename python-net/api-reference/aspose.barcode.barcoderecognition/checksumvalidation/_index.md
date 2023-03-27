---
title: ChecksumValidation
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 250
url: /python-net/api-reference/aspose.barcode.barcoderecognition/checksumvalidation/
---

## ChecksumValidation enumeration

Enable checksum validation during recognition for 1D and Postal barcodes.<br/>        Default is treated as Yes for symbologies which must contain checksum, as No where checksum only possible.<br/>        Checksum never used: Codabar, PatchCode, Pharmacode, DataLogic2of5<br/>        Checksum is possible: Code39 Standard/Extended, Standard2of5, Interleaved2of5, ItalianPost25, Matrix2of5, MSI, ItalianPost25, DeutschePostIdentcode, DeutschePostLeitcode, VIN<br/>        Checksum always used: Rest symbologies

## Members
| Member name | Description |
| :- | :- |
|DEFAULT|If checksum is required by the specification - it will be validated.|
|ON|Always validate checksum if possible.|
|OFF|Do not validate checksum.|

### See Also

* namespace [aspose.barcode.barcoderecognition](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

