---
title: DataMatrixParameters
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
ai_search_scope: "barcode_python-net_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 190
url: /python-net/api-reference/aspose.barcode.generation/datamatrixparameters/
---

## DataMatrixParameters class

DataMatrix parameters.

The DataMatrixParameters type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|data_matrix_ecc|Gets or sets a Datamatrix ECC type.<br/>            Default value: DataMatrixEccType.Ecc200.|
|data_matrix_version|Gets or sets a Datamatrix symbol size.<br/>            Default value: DataMatrixVersion.Auto.|
|data_matrix_encode_mode|Encode mode of Datamatrix barcode.<br/>            Default value: DataMatrixEncodeMode.Auto.|
|structured_append_barcode_id|Barcode ID for Structured Append mode of Datamatrix barcode.<br/>            Default value: 0|
|structured_append_barcodes_count|Barcodes count for Structured Append mode of Datamatrix barcode.<br/>            Default value: 0|
|structured_append_file_id|File ID for Structured Append mode of Datamatrix barcode.<br/>            Default value: 0|
|is_reader_programming|Used to instruct the reader to interpret the data contained within the symbol<br/>            as programming for reader initialization.<br/>            Default value: false|
|macro_characters|Macro Characters 05 and 06 values are used to obtain more compact encoding in special modes.<br/>            Can be used only with DataMatrixEccType.Ecc200 or DataMatrixEccType.EccAuto.<br/>            Cannot be used with EncodeTypes.GS1DataMatrix<br/>            Default value: MacroCharacters.None.|
|columns|Columns count.|
|rows|Rows count.|
|aspect_ratio|Height/Width ratio of 2D BarCode module.|
|eci_encoding|Gets or sets ECI encoding. Used when DataMatrixEncodeMode is Auto.<br/>            Default value: ISO-8859-1|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

