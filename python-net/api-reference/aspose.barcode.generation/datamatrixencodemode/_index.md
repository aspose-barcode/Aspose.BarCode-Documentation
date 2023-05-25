---
title: DataMatrixEncodeMode
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 480
url: /python-net/api-reference/aspose.barcode.generation/datamatrixencodemode/
---

## DataMatrixEncodeMode enumeration

DataMatrix encoder's encoding mode, default to Auto

## Members
| Member name | Description |
| :- | :- |
|AUTO|Automatically pick up the best encode mode for Datamatrix encoding|
|ASCII|Encodes one alphanumeric or two numeric characters per byte|
|FULL|Encode 8 bit values|
|CUSTOM|Encode with the encoding specified in BarcodeGenerator.Parameters.Barcode.DataMatrix.CodeTextEncoding|
|C40|Uses C40 encoding. Encodes Upper-case alphanumeric, Lower case and special characters|
|TEXT|Uses Text encoding. Encodes Lower-case alphanumeric, Upper case and special characters|
|EDIFACT|Uses EDIFACT encoding. Uses six bits per character, encodes digits, upper-case letters, and many punctuation marks, but has no support for lower-case letters.|
|ANSIX12|Uses ANSI X12 encoding.|
|EXTENDED_CODETEXT|ExtendedCodetext mode allows to manually switch encodation schemes in codetext.<br/>        Format : "\Encodation_scheme_name:text\Encodation_scheme_name:text".<br/>        Allowed encodation schemes are: EDIFACT, ANSIX12, ASCII, C40, Text, Auto.<br/>        Extended codetext example: @"\ansix12:ANSIX12TEXT\ascii:backslash must be \\ doubled\edifact:EdifactEncodedText"<br/>        All backslashes (\) must be doubled in text.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

