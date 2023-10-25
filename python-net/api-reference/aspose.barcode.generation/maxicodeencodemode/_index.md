---
title: MaxiCodeEncodeMode
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 620
url: /python-net/api-reference/aspose.barcode.generation/maxicodeencodemode/
---

## MaxiCodeEncodeMode enumeration

Encoding mode for MaxiCode barcodes.

## Members
| Member name | Description |
| :- | :- |
|AUTO|Encode codetext with value set in the ECIEncoding property.|
|BYTES|Encode codetext as plain bytes. If it detects any Unicode character, the character will be encoded as two bytes, lower byte first.|
|EXTENDED_CODETEXT|Extended mode which supports multi ECI modes.<br/>        It is better to use MaxiCodeExtCodetextBuilder for extended codetext generation.<br/>        Use Display2DText property to set visible text to removing managing characters.<br/>        ECI identifiers are set as single slash and six digits identifier "\000026" - UTF8 ECI identifier<br/>        All unicode characters after ECI identifier are automatically encoded into correct character codeset.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

