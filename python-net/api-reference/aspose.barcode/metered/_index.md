---
title: Metered
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
ai_search_scope: "barcode_python-net_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 30
url: /python-net/api-reference/aspose.barcode/metered/
---

## Metered class

Provides methods to set metered key.

The Metered type exposes the following members:
## Constructors
| Name | Description |
| :- | :- |
|Metered()|Initializes a new instance of the Metered class|
## Methods
| Name | Description |
| :- | :- |
|set_metered_key(public_key, private_key)|Sets metered public and private key.<br/>            If you purchase metered license, when start application, this API should be called, normally, this is enough. <br/>            However, if always fail to upload consumption data and exceed 24 hours, the license will be set to evaluation status, <br/>            to avoid such case, you should regularly check the license status, if it is evaluation status, call this API again.|
|get_consumption_quantity()|Gets consumption file size|
|get_consumption_credit()|Gets consumption credit|
|get_product_name()|Gets name of licensed product|
|is_metered_licensed()|Check whether metered is licensed|

### See Also

* namespace [aspose.barcode](/barcode/python-net/api-reference/aspose.barcode/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

