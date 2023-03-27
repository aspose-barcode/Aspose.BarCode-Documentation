---
title: Mailmark2DCodetext
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 120
url: /python-net/api-reference/aspose.barcode.complexbarcode/mailmark2dcodetext/
---

## Mailmark2DCodetext class

Class for encoding and decoding the text embedded in the Royal Mail 2D Mailmark code.

The Mailmark2DCodetext type exposes the following members:
## Constructors
| Name | Description |
| :- | :- |
|Mailmark2DCodetext()|Initializes a new instance of the Mailmark2DCodetext class|
## Properties
| Name | Description |
| :- | :- |
|upu_country_id|Identifies the UPU Country ID.Max length: 4 characters.|
|information_type_id|Identifies the Royal Mail Mailmark barcode payload for each product type.|
|version_id|Identifies the  barcode version as relevant to each Information Type ID.|
|klass|Identifies the class of the item.|
|supply_chain_id|Identifies the unique group of customers involved in the mailing.<br/>            Max value: 9999999.|
|item_id|Identifies the unique item within the Supply Chain ID.<br/>            Every Mailmark barcode is required to carry an ID<br/>            so it can be uniquely identified for at least 90 days.<br/>            Max value: 99999999.|
|destination_post_code_and_dps|Contains the Postcode of the Delivery Address with DPS<br/>            If inland the Postcode/DP contains the following number of characters.<br/>            Area (1 or 2 characters) District(1 or 2 characters)<br/>            Sector(1 character) Unit(2 characters) DPS (2 characters).<br/>            The Postcode and DPS must comply with a valid PAF® format.|
|rts_flag|Flag which indicates what level of Return to Sender service is being requested.|
|return_to_sender_post_code|Contains the Return to Sender Post Code but no DPS.<br/>            The PC(without DPS) must comply with a PAF® format.|
|customer_content|Optional space for use by customer.|
|customer_content_encode_mode|Encode mode of Datamatrix barcode.<br/>            Default value: DataMatrixEncodeMode.C40.|
|data_matrix_type|2D Mailmark Type defines size of Data Matrix barcode.|
## Methods
| Name | Description |
| :- | :- |
|get_constructed_codetext()|Construct codetext from Mailmark data.|
|init_from_string(constructed_codetext)|Initializes Mailmark data from constructed codetext.|
|get_barcode_type()|Gets barcode type.|

### See Also

* namespace [aspose.barcode.complexbarcode](/barcode/python-net/api-reference/aspose.barcode.complexbarcode/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

