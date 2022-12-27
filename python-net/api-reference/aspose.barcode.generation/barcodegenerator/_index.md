---
title: BarcodeGenerator
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 30
url: /python-net/api-reference/aspose.barcode.generation/barcodegenerator/
---

## BarcodeGenerator class

BarcodeGenerator for backend barcode images generation.<br/>            <br/>            supported symbologies:<br/>            1D:<br/>            Codabar, Code11, Code128, Code39Standard, Code39Extended<br/>            Code93Standard, Code93Extended, EAN13, EAN8, Interleaved2of5,<br/>            MSI, Standard2of5, UPCA, UPCE, ISBN, GS1Code128, Postnet, Planet<br/>            EAN14, SCC14, SSCC18, ITF14, SingaporePost ...<br/>            2D:<br/>            Aztec, DataMatrix, PDf417, QR code ...

The BarcodeGenerator type exposes the following members:
## Constructors
| Name | Description |
| :- | :- |
|BarcodeGenerator(type)|Initializes a new instance of the BarcodeGenerator class|
|BarcodeGenerator(type, code_text)|Initializes a new instance of the BarcodeGenerator class|
## Properties
| Name | Description |
| :- | :- |
|parameters|Generation parameters.|
|barcode_type|Barcode symbology type.|
|code_text|Text to be encoded.|
## Methods
| Name | Description |
| :- | :- |
|save(stream, format)|Save barcode image to stream in specific format.|
|save(filename, format)|Save barcode image to specific file in specific format.|
|save(filename)|Save barcode image to specific file in specific format.|
|export_to_xml(xml_file)|Exports BarCode properties to the xml-file specified|
|export_to_xml(xml)|Exports BarCode properties to the xml-stream specified|
|import_from_xml(xml_file)|Imports BarCode properties from the xml-file specified and creates BarcodeGenerator instance.|
|import_from_xml(xml)|Imports BarCode properties from the xml-stream specified and creates BarcodeGenerator instance.|
|generate_bar_code_image()|Generate the barcode image under current settings.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

