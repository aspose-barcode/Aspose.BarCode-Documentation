---
title: DataMatrixEncodeMode
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 540
url: /python-net/api-reference/aspose.barcode.generation/datamatrixencodemode/
---

## DataMatrixEncodeMode enumeration

DataMatrix encoder's encoding mode, default to Auto

## Members
| Member name | Description |
| :- | :- |
|AUTO|In Auto mode, the CodeText is encoded with maximum data compactness. <br/>            Unicode characters are re-encoded in the ECIEncoding specified encoding with the insertion of an ECI identifier.<br/>            If a character is found that is not supported by the selected ECI encoding, an exception is thrown.|
|ASCII|Encodes one alphanumeric or two numeric characters per byte|
|BYTES|Encode 8 bit values|
|C40|Uses C40 encoding. Encodes Upper-case alphanumeric, Lower case and special characters|
|TEXT|Uses Text encoding. Encodes Lower-case alphanumeric, Upper case and special characters|
|EDIFACT|Uses EDIFACT encoding. Uses six bits per character, encodes digits, upper-case letters, and many punctuation marks, but has no support for lower-case letters.|
|ANSIX12|Uses ANSI X12 encoding.|
|EXTENDED_CODETEXT|ExtendedCodetext mode allows to manually switch encodation schemes and ECI encodings in codetext.<br/>        It is better to use DataMatrixExtCodetextBuilder for extended codetext generation.<br/>        Use Display2DText property to set visible text to removing managing characters.<br/>        ECI identifiers are set as single slash and six digits identifier "\000026" - UTF8 ECI identifier<br/>        All unicode characters after ECI identifier are automatically encoded into correct character codeset.<br/>        <br/>        <br/>        Encodation schemes are set in the next format : "\Encodation_scheme_name:text\Encodation_scheme_name:text".<br/>        Allowed encodation schemes are: EDIFACT, ANSIX12, ASCII, C40, Text, Auto.<br/>        <br/>        <br/>        All backslashes (\) must be doubled in text.|
|EXTENDED|ExtendedCodetext mode allows to manually switch encodation schemes and ECI encodings in codetext.<br/>        It is better to use DataMatrixExtCodetextBuilder for extended codetext generation.<br/>        Use Display2DText property to set visible text to removing managing characters.<br/>        ECI identifiers are set as single slash and six digits identifier "\000026" - UTF8 ECI identifier<br/>        All unicode characters after ECI identifier are automatically encoded into correct character codeset.<br/>        <br/>        <br/>        Encodation schemes are set in the next format : "\Encodation_scheme_name:text\Encodation_scheme_name:text".<br/>        Allowed encodation schemes are: EDIFACT, ANSIX12, ASCII, C40, Text, Auto.<br/>        <br/>        <br/>        All backslashes (\) must be doubled in text.|
|BASE256|Encode 8 bit values|
|BINARY|In Binary mode, the CodeText is encoded with maximum data compactness. <br/>            If a Unicode character is found, an exception is thrown.|
|ECI|In ECI mode, the entire message is re-encoded in the ECIEncoding specified encoding with the insertion of an ECI identifier.<br/>            If a character is found that is not supported by the selected ECI encoding, an exception is thrown.<br/>            Please note that some old (pre 2006) scanners may not support this mode.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

