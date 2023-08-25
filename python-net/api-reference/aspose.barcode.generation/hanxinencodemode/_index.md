---
title: HanXinEncodeMode
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 560
url: /python-net/api-reference/aspose.barcode.generation/hanxinencodemode/
---

## HanXinEncodeMode enumeration

Han Xin Code encoding mode. It is recommended to use Auto with ASCII / Chinese characters or Unicode for Unicode characters.

## Members
| Member name | Description |
| :- | :- |
|AUTO|Sequence of Numeric, Text, ECI, Binary Bytes and 4 GB18030 modes changing automatically.|
|BINARY|Binary byte mode encodes binary data in any form and encodes them in their binary byte. Every byte in <br/>            Binary Byte mode is represented by 8 bits.|
|ECI|Extended Channel Interpretation (ECI) mode|
|UNICODE|Unicode mode designs a way to represent any text data reference to UTF8 encoding/charset in Han Xin Code.|
|URI|URI mode indicates the data represented in Han Xin Code is Uniform Resource Identifier (URI)<br/>            reference to RFC 3986.|
|EXTENDED|Extended mode allow combinations of internal modes: Auto, Binary, Text, Numeric, URI, Unicode, ECI, Common Chinese Region One,<br/>            Common Chinese Region Two, GB18030 Two Byte, GB18030 Four Byte.<br/>            Codetext can be built manually with prefixes and doubled backslashes, e.g.: @"\auto:abc\000009:ΑΒΓΔΕ\auto:ab\\c" or using the HanXinExtCodetextBuilder.<br/>            If the codetext contains an ECI fragment, then only the following modes can be in that codetext after ECI fragment:<br/>            Auto, Binary, Text, Numeric, URI, ECI.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

