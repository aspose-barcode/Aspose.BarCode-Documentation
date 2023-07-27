---
title: QREncodeMode
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 670
url: /python-net/api-reference/aspose.barcode.generation/qrencodemode/
---

## QREncodeMode enumeration

Encoding mode for QR barcodes. It is recommended to Use Auto with CodeTextEncoding = Encoding.UTF8 for Latin symbols or digits and Utf8BOM for Unicode symbols.

## Members
| Member name | Description |
| :- | :- |
|AUTO|Encode codetext as is non-Unicode charset. If there is any Unicode character, the codetext will be encoded with value which is set in CodeTextEncoding.|
|BYTES|Encode codetext as plain bytes. If it detects any Unicode character, the character will be encoded as two bytes, lower byte first.|
|UTF_8BOM|Encode codetext with UTF8 encoding with first ByteOfMark character.|
|UTF_16BEBOM|Encode codetext with UTF8 encoding with first ByteOfMark character. It can be problems with some barcode scanners.|
|ECI_ENCODING|Encode codetext with value set in the ECIEncoding property. It can be problems with some old (pre 2006) barcode scanners.|
|EXTENDED_CODETEXT|Extended Channel mode which supports FNC1 first position, FNC1 second position and multi ECI modes.<br/>        It is better to use QrExtCodetextBuilder for extended codetext generation.<br/>        Use Display2DText property to set visible text to removing managing characters.<br/>        Encoding Principles:<br/>        All symbols "\" must be doubled "\\" in the codetext.<br/>        FNC1 in first position is set in codetext as as "<FNC1>"<br/>        FNC1 in second position is set in codetext as as "<FNC1(value)>". The value must be single symbols (a-z, A-Z) or digits from 0 to 99.<br/>        Group Separator for FNC1 modes is set as 0x1D character '\\u001D' <br/>        If you need to insert "<FNC1>" string into barcode write it as "<\FNC1>" <br/>        ECI identifiers are set as single slash and six digits identifier "\000026" - UTF8 ECI identifier<br/>        To disable current ECI mode and convert to default JIS8 mode zero mode ECI indetifier is set. "\000000"<br/>        All unicode characters after ECI identifier are automatically encoded into correct character codeset.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

