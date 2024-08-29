---
title: QrParameters
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 370
url: /python-net/api-reference/aspose.barcode.generation/qrparameters/
---

## QrParameters class

QR parameters.

The QrParameters type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|qr_eci_encoding|Extended Channel Interpretation Identifiers. It is used to tell the barcode reader details<br/>            about the used references for encoding the data in the symbol.<br/>            Current implementation consists all well known charset encodings.<br/>            Not supported by MicroQR.|
|qr_encode_mode|QR symbology type of BarCode's encoding mode.<br/>            Default value: QREncodeMode.Auto.|
|qr_encode_type|QR / MicroQR selector mode. Select ForceQR for standard QR symbols, Auto for MicroQR.|
|qr_error_level|Level of Reed-Solomon error correction for QR, MicroQR and RectMicroQR barcode.<br/>             From low to high: LevelL, LevelM, LevelQ, LevelH. See QRErrorLevel.|
|qr_version|Version of QR Code.From Version1 to Version40.<br/>            Default value is QRVersion.Auto.|
|micro_qr_version|Version of MicroQR Code. From version M1 to version M4.<br/>            Default value is MicroQRVersion.Auto.|
|rect_micro_qr_version|Version of RectMicroQR Code. From version R7x59 to version R17x139.<br/>            Default value is RectMicroQRVersion.Auto.|
|aspect_ratio|Height/Width ratio of 2D BarCode module.|
|structured_append|QR structured append parameters.<br/>            Structured append mode is not suppported by MicroQR and RectMicroQR barcodes.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

