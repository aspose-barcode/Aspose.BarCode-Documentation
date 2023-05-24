---
title: QrParameters
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 310
url: /python-net/api-reference/aspose.barcode.generation/qrparameters/
---

## QrParameters class

QR parameters.

The QrParameters type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|qr_eci_encoding|Extended Channel Interpretation Identifiers. It is used to tell the barcode reader details<br/>            about the used references for encoding the data in the symbol.<br/>            Current implementation consists all well known charset encodings.|
|qr_encode_mode|QR symbology type of BarCode's encoding mode.<br/>            Default value: QREncodeMode.Auto.|
|qr_encode_type|QR / MicroQR selector mode. Select ForceQR for standard QR symbols, Auto for MicroQR.|
|qr_error_level|Level of Reed-Solomon error correction for QR barcode.<br/>             From low to high: LevelL, LevelM, LevelQ, LevelH. see QRErrorLevel.|
|qr_version|Version of QR Code.<br/>            From Version1 to Version40 for QR code and from M1 to M4 for MicroQr.<br/>            Default value is QRVersion.Auto.|
|aspect_ratio|Height/Width ratio of 2D BarCode module.|
|code_text_encoding|Gets or sets the encoding of codetext.<br/>            Default value: UTF-8|
|structured_append|QR structured append parameters.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

