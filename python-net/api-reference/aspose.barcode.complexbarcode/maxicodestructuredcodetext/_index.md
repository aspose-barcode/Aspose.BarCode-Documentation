---
title: MaxiCodeStructuredCodetext
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
ai_search_scope: "barcode_python-net_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 200
url: /python-net/api-reference/aspose.barcode.complexbarcode/maxicodestructuredcodetext/
---

## MaxiCodeStructuredCodetext class

Base class for encoding and decoding the text embedded in the MaxiCode code for modes 2 and 3.

The MaxiCodeStructuredCodetext type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|maxi_code_encode_mode|Gets or sets a MaxiCode encode mode. <br/>            Default value: Auto.|
|eci_encoding|Gets or sets ECI encoding. Used when MaxiCodeEncodeMode is Auto.<br/>            Default value: ISO-8859-1|
|postal_code|Identifies the postal code. Must be 9 digits in mode 2 or <br/>            6 alphanumeric symbols in mode 3.|
|country_code|Identifies 3 digit country code.|
|service_category|Identifies 3 digit service category.|
|second_message|Identifies second message of the barcode.|
## Methods
| Name | Description |
| :- | :- |
|get_mode()|Gets MaxiCode mode.|
|get_constructed_codetext()|Constructs codetext|
|init_from_string(constructed_codetext)|Initializes instance from constructed codetext.|
|get_barcode_type()|Gets barcode type.|

### See Also

* namespace [aspose.barcode.complexbarcode](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

