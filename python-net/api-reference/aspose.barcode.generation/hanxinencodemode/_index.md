---
title: HanXinEncodeMode
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 600
url: /python-net/api-reference/aspose.barcode.generation/hanxinencodemode/
---

## HanXinEncodeMode enumeration

Han Xin Code encoding mode. It is recommended to use Auto with ASCII / Chinese characters or Unicode for Unicode characters.

## Members
| Member name | Description |
| :- | :- |
|AUTO|In Auto mode, the CodeText is encoded with maximum data compactness. <br/>            Unicode characters are encoded using GB18030 encoding according to HanXin barcode specification.|
|BINARY|In Binary mode, the CodeText is encoded with maximum data compactness. <br/>            If a Unicode character is found, an exception is thrown.|
|ECI|In ECI mode, the entire message is re-encoded in the ECIEncoding specified encoding with the insertion of an ECI identifier.<br/>            If a character is found that is not supported by the selected ECI encoding, an exception is thrown.<br/>            Please note that some old (pre 2006) scanners may not support this mode.|
|UNICODE|Unicode mode designs a way to represent any text data reference to UTF8 encoding/charset in Han Xin Code.|
|URI|URI mode indicates the data represented in Han Xin Code is Uniform Resource Identifier (URI)<br/>            reference to RFC 3986.|
|EXTENDED|Extended mode allow combinations of internal modes: Auto, Binary, Text, Numeric, URI, Unicode, ECI, Common Chinese Region One,<br/>            Common Chinese Region Two, GB18030 Two Byte, GB18030 Four Byte.<br/>            Codetext can be built manually with prefixes and doubled backslashes, e.g.: @"\auto:abc\000009:ΑΒΓΔΕ\auto:ab\\c" or using the HanXinExtCodetextBuilder.<br/>            If the codetext contains an ECI fragment, then only the following modes can be in that codetext after ECI fragment:<br/>            Auto, Binary, Text, Numeric, URI, ECI.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

