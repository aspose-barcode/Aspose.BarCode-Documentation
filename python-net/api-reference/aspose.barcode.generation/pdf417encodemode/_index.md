---
title: Pdf417EncodeMode
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
ai_search_scope: "barcode_python-net_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 720
url: /python-net/api-reference/aspose.barcode.generation/pdf417encodemode/
---

## Pdf417EncodeMode enumeration

Pdf417 barcode encode mode

## Members
| Member name | Description |
| :- | :- |
|AUTO|In Auto mode, the CodeText is encoded with maximum data compactness. <br/>            Unicode characters are re-encoded in the ECIEncoding specified encoding with the insertion of an ECI identifier.<br/>            If a character is found that is not supported by the selected ECI encoding, an exception is thrown.|
|BINARY|In Binary mode, the CodeText is encoded with maximum data compactness. <br/>            If a Unicode character is found, an exception is thrown.|
|ECI|In ECI mode, the entire message is re-encoded in the ECIEncoding specified encoding with the insertion of an ECI identifier.<br/>            If a character is found that is not supported by the selected ECI encoding, an exception is thrown.<br/>            Please note that some old (pre 2006) scanners may not support this mode.|
|EXTENDED|Extended mode which supports multi ECI modes.<br/>        It is better to use Pdf417ExtCodetextBuilder for extended codetext generation.<br/>        Use Display2DText property to set visible text to removing managing characters.<br/>        ECI identifiers are set as single slash and six digits identifier "\000026" - UTF8 ECI identifier<br/>        All unicode characters after ECI identifier are automatically encoded into correct character codeset.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

