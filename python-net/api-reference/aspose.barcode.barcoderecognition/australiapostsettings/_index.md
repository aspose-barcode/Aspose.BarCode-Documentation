---
title: AustraliaPostSettings
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 20
url: /python-net/api-reference/aspose.barcode.barcoderecognition/australiapostsettings/
---

## AustraliaPostSettings class

AustraliaPost decoding parameters. Contains parameters which make influence on recognized data of AustraliaPost symbology.

The AustraliaPostSettings type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|customer_information_interpreting_type|Gets or sets the Interpreting Type for the Customer Information of AustralianPost BarCode.Default is CustomerInformationInterpretingType.Other.|
|ignore_ending_filling_patterns_for_c_table|The flag which force AustraliaPost decoder to ignore last filling patterns in Customer Information Field during decoding as CTable method.<br/>            CTable encoding method does not have any gaps in encoding table and sequnce "333" of filling paterns is decoded as letter "z".|
|customer_information_decoder|Public interface for Customer Information Field decoding which is used in AustraliaPost symbology.|

### See Also

* namespace [aspose.barcode.barcoderecognition](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

