---
title: Pdf417Parameters
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 290
url: /python-net/api-reference/aspose.barcode.generation/pdf417parameters/
---

## Pdf417Parameters class

PDF417 parameters. Contains PDF417, MacroPDF417 and MicroPDF417 parameters.<br/>            MacroPDF417 requires two fields: Pdf417MacroFileID and Pdf417MacroSegmentID. All other fields are optional.<br/>            MicroPDF417 in Structured Append mode (same as MacroPDF417 mode) requires two fields: Pdf417MacroFileID and Pdf417MacroSegmentID. All other fields are optional.

The Pdf417Parameters type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|pdf_417_compaction_mode|Pdf417 symbology type of BarCode's compaction mode.<br/>            Default value: Pdf417CompactionMode.Auto.|
|pdf_417_error_level|Gets or sets Pdf417 symbology type of BarCode's error correction level<br/>            ranging from level0 to level8, level0 means no error correction info,<br/>            level8 means best error correction which means a larger picture.|
|pdf_417_truncate|Whether Pdf417 symbology type of BarCode is truncated (to reduce space). <br/>            Also known as CompactPDF417. Rigth row indicator and right stop pattern are removed in this mode.|
|columns|Columns count.|
|rows|Rows count.|
|aspect_ratio|Height/Width ratio of 2D BarCode module.|
|pdf_417_macro_file_id|MacroPdf417 barcode's file ID (Required field).<br/>            MicroPDF417 barcode's file ID (Required field for Structured Append mode)|
|pdf_417_macro_segment_id|MacroPdf417 barcode's segment ID (Required field), which starts from 0, to MacroSegmentsCount - 1.<br/>            MicroPDF417 barcode's segment ID (Required field for Structured Append mode)|
|pdf_417_macro_segments_count|MacroPdf417 barcode segments count (optional field).<br/>            MicroPDF417 barcode segments count (optional field for Structured Append mode)|
|pdf_417_macro_file_name|MacroPdf417 barcode file name (optional field).<br/>            MicroPDF417 barcode file name (optional field for Structured Append mode)|
|pdf_417_macro_time_stamp|MacroPdf417 barcode time stamp (optional field).<br/>            MicroPDF417 barcode time stamp (optional field for Structured Append mode)|
|pdf_417_macro_sender|MacroPdf417 barcode sender name (optional field).<br/>            MicroPDF417 barcode sender name (optional field for Structured Append mode)|
|pdf_417_macro_addressee|MacroPdf417 barcode addressee name (optional field).<br/>            MicroPDF417 barcode addressee name (optional field for Structured Append mode)|
|pdf_417_macro_file_size|MacroPdf417 file size (optional field).<br/>            MicroPDF417 file size (optional field for Structured Append mode)<br/>            The file size field contains the size in bytes of the entire source file.|
|pdf_417_macro_checksum|MacroPdf417 barcode checksum (optional field).<br/>            MicroPDF417 barcode checksum (optional field for Structured Append mode)<br/>            The checksum field contains the value of the 16-bit (2 bytes) CRC checksum using the CCITT-16 polynomial. x^16 + x^12 + x^5 + 1|
|code_text_encoding|Gets or sets the encoding of codetext.<br/>            Default value: UTF-8|
|pdf_417eci_encoding|Extended Channel Interpretation Identifiers. It is used to tell the barcode reader details<br/>            about the used references for encoding the data in the symbol. Not applied for Macro PDF417 text fields.<br/>            Current implementation consists all well known charset encodings.|
|pdf_417_macro_eci_encoding|Extended Channel Interpretation Identifiers. Applies for Macro PDF417 text fields.|
|pdf_417_macro_terminator|Used to tell the encoder whether to add Macro PDF417 Terminator (codeword 922) to the segment. <br/>            Applied only for Macro PDF417.|
|is_reader_initialization|Used to instruct the reader to interpret the data contained within the symbol<br/>            as programming for reader initialization.|
|code_128_emulation|Function codeword for Code 128 emulation. Applied for MicroPDF417 only.  Ignored for PDF417 and MacroPDF417 barcodes.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

