---
title: BarcodeSvmDetectorSettings
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 80
url: /python-net/api-reference/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/
---

## BarcodeSvmDetectorSettings class

Barcode detector settings.

The BarcodeSvmDetectorSettings type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|scan_window_sizes|Scan window sizes in pixels.<br/>            <br/>            Allowed sizes are 10, 15, 20, 25, 30.<br/>            Scanning with small window size takes more time and provides more accuracy but may fail in detecting very big barcodes.<br/>            Combining of several window sizes can improve detection quality.|
|similarity_coef|Similarity coefficient depends on how homogeneous barcodes are.<br/>            <br/>            Use high value for for clear barcodes.<br/>            Use low values to detect barcodes that ara partly damaged or not lighten evenly.<br/>            Similarity coefficient must be between [0.5, 0.9]|
|region_likelihood_threshold_percent|Sets threshold for detected regions that may contain barcodes.<br/>            <br/>            Value 0.7 means that bottom 70% of possible regions are filtered out and not processed further.<br/>            Region likelihood threshold must be between [0.05, 0.9]<br/>            Use high values for clear images with few barcodes.<br/>            Use low values for images with many barcodes or for noisy images.<br/>            Low value may lead to a bigger recognition time.|
|skip_diagonal_search|Allows detector to skip search for diagonal barcodes.<br/>            <br/>            Setting it to false will increase detection time but allow to find diagonal barcodes that can be missed otherwise.<br/>            Enabling of diagonal search leads to a bigger detection time.|
|high_performance|High performance detection preset.<br/>            <br/>            Default for [None](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition.qualitysettings/presettype/)|
|normal_quality|Normal quality detection preset.<br/>            <br/>            Default for [None](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition.qualitysettings/presettype/)|
|high_quality|High quality detection preset.<br/>            <br/>            Default for [None](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition.qualitysettings/presettype/) and [None](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition.qualitysettings/presettype/)|
|max_quality|Max quality detection preset.<br/>            <br/>            Default for [None](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition.qualitysettings/presettype/) and [None](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition.qualitysettings/presettype/)|

### See Also

* namespace [aspose.barcode.barcoderecognition](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

