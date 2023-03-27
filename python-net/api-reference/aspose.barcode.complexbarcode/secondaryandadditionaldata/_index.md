---
title: SecondaryAndAdditionalData
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 230
url: /python-net/api-reference/aspose.barcode.complexbarcode/secondaryandadditionaldata/
---

## SecondaryAndAdditionalData class

Class for storing HIBC LIC secondary and additional data.

The SecondaryAndAdditionalData type exposes the following members:
## Constructors
| Name | Description |
| :- | :- |
|SecondaryAndAdditionalData()|Initializes a new instance of the SecondaryAndAdditionalData class|
## Properties
| Name | Description |
| :- | :- |
|expiry_date_format|Identifies expiry date format.|
|expiry_date|Identifies expiry date. Will be used if ExpiryDateFormat is not set to None.|
|lot_number|Identifies lot or batch number. Lot/batch number must be alphanumeric string with up to 18 sybmols length. .|
|serial_number|Identifies serial number. Serial number must be alphanumeric string up to 18 sybmols length.|
|date_of_manufacture|Identifies date of manufacture.<br/>            Date of manufacture can be set to DateTime.MinValue in order not to use this field.<br/>            Default value: DateTime.MinValue|
|quantity|Identifies quantity, must be integer value from 0 to 500. <br/>            Quantity can be set to -1 in order not to use this field.<br/>            Default value: -1|
## Methods
| Name | Description |
| :- | :- |
|parse_from_string(secondary_data_codetext)|Instantiates secondary and additional supplemental data from string format according HIBC LIC specification.|

### See Also

* namespace [aspose.barcode.complexbarcode](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

