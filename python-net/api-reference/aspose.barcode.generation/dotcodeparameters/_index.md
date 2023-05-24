---
title: DotCodeParameters
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 180
url: /python-net/api-reference/aspose.barcode.generation/dotcodeparameters/
---

## DotCodeParameters class

DotCode parameters.

The DotCodeParameters type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|aspect_ratio|Height/Width ratio of 2D BarCode module.|
|dot_code_encode_mode|Identifies DotCode encode mode. <br/>            Default value: Auto.|
|is_reader_initialization|Indicates whether code is used for instruct reader to interpret the following data as instructions for initialization or reprogramming of the bar code reader.<br/>            Default value is false.|
|dot_code_structured_append_mode_barcode_id|Identifies the ID of the DotCode structured append mode barcode. ID starts from 1 and must be less or equal to barcodes count. Default value is -1.|
|dot_code_structured_append_mode_barcodes_count|Identifies DotCode structured append mode barcodes count. Default value is -1. Count must be a value from 1 to 35.|
|eci_encoding|Identifies ECI encoding. Used when DotCodeEncodeMode is Auto.<br/>            Default value: ISO-8859-1|
|rows|Identifies rows count. Sum of the number of rows plus the number of columns of a DotCode symbol must be odd. Number of rows must be at least 5.<br/>            Default value: -1|
|columns|Identifies columns count. Sum of the number of rows plus the number of columns of a DotCode symbol must be odd. Number of columns must be at least 5.<br/>            Default value: -1|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

