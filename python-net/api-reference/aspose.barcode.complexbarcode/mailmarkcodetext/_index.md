---
title: MailmarkCodetext
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 130
url: /python-net/api-reference/aspose.barcode.complexbarcode/mailmarkcodetext/
---

## MailmarkCodetext class

Class for encoding and decoding the text embedded in the 4-state Royal Mailmark code.

The MailmarkCodetext type exposes the following members:
## Constructors
| Name | Description |
| :- | :- |
|MailmarkCodetext()|Initializes a new instance of the MailmarkCodetext class|
## Properties
| Name | Description |
| :- | :- |
|format|"0" – Null or Test<br/>            "1" – Letter<br/>            "2" – Large Letter|
|version_id|Currently "1" – For Mailmark barcode (0 and 2 to 9 and A to Z spare for future use)|
|klass|"0" - Null or Test<br/>            "1" - 1C (Retail)<br/>            "2" - 2C (Retail)<br/>            "3" - 3C (Retail)<br/>            "4" - Premium (RetailPublishing Mail) (for potential future use)<br/>            "5" - Deferred (Retail)<br/>            "6" - Air (Retail) (for potential future use)<br/>            "7" - Surface (Retail) (for potential future use)<br/>            "8" - Premium (Network Access)<br/>            "9" - Standard (Network Access)|
|supply_chain_id|Maximum values are 99 for Barcode C and 999999 for Barcode L.|
|item_id|Maximum value is 99999999.|
|destination_post_code_and_dps|The PC and DP must comply with a PAF format.<br/>            Nine character string denoting international "XY11     " (note the 5 trailing spaces) or a pattern<br/>            of characters denoting a domestic sorting code.<br/>            A domestic sorting code consists of an outward postcode, an inward postcode, and a Delivery Point Suffix.|
## Methods
| Name | Description |
| :- | :- |
|get_constructed_codetext()|Construct codetext from Mailmark data.|
|init_from_string(constructed_codetext)|Initializes Mailmark data from constructed codetext.|
|get_barcode_type()|Gets barcode type.|

### See Also

* namespace [aspose.barcode.complexbarcode](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

