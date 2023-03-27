---
title: SwissQRBill
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 240
url: /python-net/api-reference/aspose.barcode.complexbarcode/swissqrbill/
---

## SwissQRBill class

SwissQR bill data

The SwissQRBill type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|version|Gets or sets the version of the SwissQR bill standard.|
|amount|Gets or sets the payment amount.<br/>            <br/>            Valid values are between 0.01 and 999,999,999.99.|
|currency|Gets or sets the payment currency.<br/>            <br/>            Valid values are "CHF" and "EUR".|
|account|Gets or sets the creditor's account number.<br/>            <br/>            Account numbers must be valid IBANs of a bank of Switzerland or<br/>            Liechtenstein. Spaces are allowed in the account number.|
|creditor|Gets or sets the creditor address.|
|reference|Gets or sets the creditor payment reference.<br/>            <br/>            The reference is mandatory for SwissQR IBANs, i.e.IBANs in the range<br/>            CHxx30000xxxxxx through CHxx31999xxxxx.<br/>            <br/>            If specified, the reference must be either a valid SwissQR reference<br/>            (corresponding to ISR reference form) or a valid creditor reference<br/>            according to ISO 11649 ("RFxxxx"). Both may contain spaces for formatting.|
|debtor|Gets or sets the debtor address.<br/>            <br/>            The debtor is optional. If it is omitted, both setting this field to|
|unstructured_message|Gets or sets the additional unstructured message.|
|bill_information|Gets or sets the additional structured bill information.|
|alternative_schemes|Gets ors sets the alternative payment schemes.<br/>            <br/>            A maximum of two schemes with parameters are allowed.|
## Methods
| Name | Description |
| :- | :- |
|create_and_set_creditor_reference(raw_reference)|Creates and sets a ISO11649 creditor reference from a raw string by prefixing<br/>            the String with "RF" and the modulo 97 checksum.<br/>            <br/>            Whitespace is removed from the reference|
|equals(other)|Determines whether the specified object is equal to the current object.|

### See Also

* namespace [aspose.barcode.complexbarcode](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

