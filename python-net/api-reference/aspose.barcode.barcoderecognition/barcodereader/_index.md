---
title: BarCodeReader
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 40
url: /python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/
---

## BarCodeReader class

BarCodeReader encapsulates an image which may contain one or several barcodes, it then can perform ReadBarCodes operation to detect barcodes.

The BarCodeReader type exposes the following members:
## Constructors
| Name | Description |
| :- | :- |
|BarCodeReader()|Initializes a new instance of the [BarCodeReader](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/) class with default values.<br/>            Requires to set image (SetBitmapImage()) before to call ReadBarCodes() method.|
|BarCodeReader(image)|Initializes a new instance of the BarCodeReader class|
|BarCodeReader(image, decode_types)|Initializes a new instance of the BarCodeReader class|
|BarCodeReader(image, type)|Initializes a new instance of the BarCodeReader class|
|BarCodeReader(image, area, decode_types)|Initializes a new instance of the BarCodeReader class|
|BarCodeReader(image, area, type)|Initializes a new instance of the BarCodeReader class|
|BarCodeReader(image, areas, decode_types)|Initializes a new instance of the BarCodeReader class|
|BarCodeReader(image, areas, type)|Initializes a new instance of the BarCodeReader class|
|BarCodeReader(filename)|Initializes a new instance of the BarCodeReader class|
|BarCodeReader(filename, decode_types)|Initializes a new instance of the BarCodeReader class|
|BarCodeReader(filename, type)|Initializes a new instance of the BarCodeReader class|
|BarCodeReader(stream)|Initializes a new instance of the BarCodeReader class|
|BarCodeReader(stream, type)|Initializes a new instance of the BarCodeReader class|
|BarCodeReader(stream, decode_types)|Initializes a new instance of the BarCodeReader class|
## Properties
| Name | Description |
| :- | :- |
|processor_settings|Gets a settings of using processor cores.|
|timeout|Gets or sets the timeout of recognition process in milliseconds.|
|found_bar_codes|Gets recognized [BarCodeResult](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/)s array|
|found_count|Gets recognized barcodes count|
|quality_settings|QualitySettings allows to configure recognition quality and speed manually.<br/>            You can quickly set up QualitySettings by embedded presets: HighPerformance, NormalQuality, <br/>            HighQuality, MaxBarCodes or you can manually configure separate options.<br/>            Default value of QualitySettings is NormalQuality.|
|barcode_settings|The main BarCode decoding parameters. Contains parameters which make influence on recognized data.|
## Methods
| Name | Description |
| :- | :- |
|set_bar_code_image(value)|Sets bitmap image for recognition. <br/>            Must be called before ReadBarCodes() method.|
|set_bar_code_image(value, areas)|Sets bitmap image and areas for recognition. <br/>            Must be called before ReadBarCodes() method.|
|set_bar_code_image(value, area)|Sets bitmap image and areas for recognition. <br/>            Must be called before ReadBarCodes() method.|
|set_bar_code_image(filename)|Sets image file for recognition. <br/>            Must be called before ReadBarCodes() method.|
|set_bar_code_image(stream)|Sets image stream for recognition. <br/>            Must be called before ReadBarCodes() method.|
|set_bar_code_read_type(barcode_types)|Sets [SingleDecodeType](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/singledecodetype/) type array for recognition. <br/>            Must be called before ReadBarCodes() method.|
|set_bar_code_read_type(type)|Sets decode type for recognition. <br/>            Must be called before ReadBarCodes() method.|
|export_to_xml(xml_file)|Exports BarCode properties to the xml-file specified|
|export_to_xml(xml_stream)|Exports BarCode properties to the xml-stream specified|
|import_from_xml(xml_file)|Imports BarCode properties from the xml-file specified and applies them to the current BarCodeReader instance.|
|import_from_xml(xml_stream)|Imports BarCode properties from the xml-stream specified and applies them to the current BarCodeReader instance.|
|abort()|Function requests termination of current recognition session from other thread. Abort is unblockable method and returns control just after calling. <br/>            The method should be used when recognition process is too long.|
|read_bar_codes()|Reads [BarCodeResult](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/)s from the image.|

### See Also

* namespace [aspose.barcode.barcoderecognition](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

