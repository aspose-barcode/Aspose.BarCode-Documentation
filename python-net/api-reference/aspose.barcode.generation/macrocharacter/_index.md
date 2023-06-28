---
title: MacroCharacter
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 590
url: /python-net/api-reference/aspose.barcode.generation/macrocharacter/
---

## MacroCharacter enumeration

Macro Characters 05 and 06 values are used to obtain more compact encoding in special modes.<br/>            05 Macro craracter is translated to "[)>\u001E05\u001D" as decoded data header and "\u001E\u0004" as decoded data trailer.<br/>            06 Macro craracter is translated to "[)>\u001E06\u001D" as decoded data header and "\u001E\u0004" as decoded data trailer.

## Members
| Member name | Description |
| :- | :- |
|NONE|None of Macro Characters are added to barcode data|
|MACRO05|05 Macro craracter is added to barcode data in first position.<br/>            GS1 Data Identifier ISO 15434<br/>            Character is translated to "[)>\u001E05\u001D" as decoded data header and "\u001E\u0004" as decoded data trailer.|
|MACRO06|06 Macro craracter is added to barcode data in first position.<br/>            ASC MH10 Data Identifier ISO 15434<br/>            Character is translated to "[)>\u001E06\u001D" as decoded data header and "\u001E\u0004" as decoded data trailer.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

