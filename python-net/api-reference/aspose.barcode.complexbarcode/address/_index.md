---
title: Address
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 10
url: /python-net/api-reference/aspose.barcode.complexbarcode/address/
---

## Address class

Address of creditor or debtor.<br/>            <br/>            You can either set street, house number, postal code and town (type

The Address type exposes the following members:
## Constructors
| Name | Description |
| :- | :- |
|Address()|Creates instance of Address|
## Properties
| Name | Description |
| :- | :- |
|type|Gets the address type.<br/>            <br/>            The address type is automatically set by either setting street / house number<br/>            or address line 1 and 2. Before setting the fields, the address type is|
|name|Gets or sets the name, either the first and last name of a natural person or the<br/>            company name of a legal person.|
|address_line1|Gets or sets the address line 1.<br/>            <br/>            Address line 1 contains street name, house number or P.O. box.<br/>            <br/>            Setting this field sets the address type to [COMBINED_ELEMENTS](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/) unless it's already<br/>            [STRUCTURED](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/), in which case it becomes [CONFLICTING](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/).<br/>            <br/>            This field is only used for combined elements addresses and is optional.|
|address_line2|Gets or sets the address line 2.<br/>            <br/>            Address line 2 contains postal code and town.<br/>            <br/>            Setting this field sets the address type to [COMBINED_ELEMENTS](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/) unless it's already<br/>            [STRUCTURED](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/), in which case it becomes [CONFLICTING](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/).<br/>            <br/>            This field is only used for combined elements addresses. For this type, it's mandatory.|
|street|Gets or sets the street.<br/>            <br/>            The street must be speicfied without house number.<br/>            <br/>            Setting this field sets the address type to [STRUCTURED](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/) unless it's already<br/>            [COMBINED_ELEMENTS](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/), in which case it becomes [CONFLICTING](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/).<br/>            <br/>            This field is only used for structured addresses and is optional.|
|house_no|Gets or sets the house number.<br/>            <br/>            Setting this field sets the address type to [STRUCTURED](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/) unless it's already<br/>            [COMBINED_ELEMENTS](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/), in which case it becomes [CONFLICTING](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/).<br/>            <br/>            This field is only used for structured addresses and is optional.|
|postal_code|Gets or sets the postal code.<br/>            <br/>            Setting this field sets the address type to [STRUCTURED](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/) unless it's already<br/>            [COMBINED_ELEMENTS](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/), in which case it becomes [CONFLICTING](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/).<br/>            <br/>            This field is only used for structured addresses. For this type, it's mandatory.|
|town|Gets or sets the town or city.<br/>            <br/>            Setting this field sets the address type to [STRUCTURED](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/) unless it's already<br/>            [COMBINED_ELEMENTS](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/), in which case it becomes [CONFLICTING](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/).<br/>            <br/>            This field is only used for structured addresses. For this type, it's mandatory.|
|country_code|Gets or sets the two-letter ISO country code.<br/>             <br/>            The country code is mandatory unless the entire address contains|
## Methods
| Name | Description |
| :- | :- |
|clear()|Clears all fields and sets the type to [UNDETERMINED](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/addresstype/).|
|equals(other)|Determines whether the specified object is equal to the current object.|

### See Also

* namespace [aspose.barcode.complexbarcode](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

