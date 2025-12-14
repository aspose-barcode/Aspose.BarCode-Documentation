---
title: AztecParameters
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
ai_search_scope: "barcode_python-net_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 30
url: /python-net/api-reference/aspose.barcode.generation/aztecparameters/
---

## AztecParameters class

Aztec parameters.

The AztecParameters type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|aztec_encode_mode|Gets or sets a Aztec encode mode. <br/>            Default value: Auto.|
|eci_encoding|Gets or sets ECI encoding. Used when AztecEncodeMode is Auto.<br/>            Default value: ISO-8859-1|
|structured_append_barcode_id|Barcode ID for Structured Append mode of Aztec barcode. Barcode ID should be in range from 1 to barcodes count.<br/>            Default value: 0|
|structured_append_barcodes_count|Barcodes count for Structured Append mode of Aztec barcode. Barcodes count should be in range from 1 to 26.<br/>            Default value: 0|
|structured_append_file_id|File ID for Structured Append mode of Aztec barcode (optional field). File ID should not contain spaces.<br/>            Default value: empty string|
|aztec_error_level|Level of error correction of Aztec types of barcode.<br/>            Value should between 5 to 95.|
|aztec_symbol_mode|Gets or sets a Aztec Symbol mode.<br/>            Default value: AztecSymbolMode.Auto.|
|layers_count|Gets or sets layers count of Aztec symbol. Layers count should be in range from 1 to 3 for Compact mode and<br/>            in range from 1 to 32 for Full Range mode.<br/>            Default value: 0 (auto).|
|is_reader_initialization|Used to instruct the reader to interpret the data contained within the symbol<br/>            as programming for reader initialization.|
|aspect_ratio|Height/Width ratio of 2D BarCode module.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

