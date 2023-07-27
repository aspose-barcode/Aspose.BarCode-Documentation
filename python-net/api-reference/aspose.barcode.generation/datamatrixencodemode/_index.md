---
title: DataMatrixEncodeMode
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 500
url: /python-net/api-reference/aspose.barcode.generation/datamatrixencodemode/
---

## DataMatrixEncodeMode enumeration

DataMatrix encoder's encoding mode, default to Auto

## Members
| Member name | Description |
| :- | :- |
|AUTO|Automatically pick up the best encode mode for Datamatrix encoding|
|ASCII|Encodes one alphanumeric or two numeric characters per byte|
|BYTES|Encode 8 bit values|
|C40|Uses C40 encoding. Encodes Upper-case alphanumeric, Lower case and special characters|
|TEXT|Uses Text encoding. Encodes Lower-case alphanumeric, Upper case and special characters|
|EDIFACT|Uses EDIFACT encoding. Uses six bits per character, encodes digits, upper-case letters, and many punctuation marks, but has no support for lower-case letters.|
|ANSIX12|Uses ANSI X12 encoding.|
|EXTENDED_CODETEXT|ExtendedCodetext mode allows to manually switch encodation schemes and ECI encodings in codetext.<br/>        It is better to use DataMatrixExtCodetextBuilder for extended codetext generation.<br/>        Use Display2DText property to set visible text to removing managing characters.<br/>        ECI identifiers are set as single slash and six digits identifier "\000026" - UTF8 ECI identifier<br/>        All unicode characters after ECI identifier are automatically encoded into correct character codeset.<br/>        <br/>        <br/>        Encodation schemes are set in the next format : "\Encodation_scheme_name:text\Encodation_scheme_name:text".<br/>        Allowed encodation schemes are: EDIFACT, ANSIX12, ASCII, C40, Text, Auto.<br/>        <br/>        <br/>        All backslashes (\) must be doubled in text.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

