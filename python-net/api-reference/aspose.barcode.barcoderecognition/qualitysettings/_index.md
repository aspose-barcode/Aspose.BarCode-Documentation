---
title: QualitySettings
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 240
url: /python-net/api-reference/aspose.barcode.barcoderecognition/qualitysettings/
---

## QualitySettings class

QualitySettings allows to configure recognition quality and speed manually.<br/>            You can quickly set up QualitySettings with embedded presets: HighPerformance, NormalQuality, HighQuality, MaxQuality or you can manually configure separate options.<br/>            Default value of QualitySettings is NormalQuality.

The QualitySettings type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|high_performance|HighPerformance recognition quality preset. High quality barcodes are recognized well in this mode.|
|normal_quality|NormalQuality recognition quality preset. Suitable for the most of barcodes|
|high_quality|HighQuality recognition quality preset. This preset is developed for low quality barcodes. Allows to detect highly damaged barcodes.|
|max_quality|MaxQuality recognition quality preset. This preset is developed to recognize all possible barcodes, even incorrect barcodes.|
|x_dimension|Recognition mode which sets size (from 1 to infinity) of barcode minimal element: matrix cell or bar.|
|minimal_x_dimension|Minimal size of XDimension in pixels which is used with UseMinimalXDimension.|
|barcode_quality|Mode which enables methods to recognize barcode elements with the selected quality. Barcode element with lower quality requires more hard methods which slows the recognition.|
|deconvolution|Deconvolution (image restorations) mode which defines level of image degradation. Originally deconvolution is a function which can restore image degraded <br/>            (convoluted) by any natural function like blur, during obtaining image by camera. Because we cannot detect image function which corrupt the image, <br/>            we have to check most well know functions like sharp or mathematical morphology.|
|inverse_image|Mode which enables or disables additional recognition of barcodes on images with inverted colors (luminance).|
|complex_background|Mode which enables or disables additional recognition of color barcodes on color images.|
|allow_incorrect_barcodes|Allows engine to recognize barcodes which has incorrect checksumm or incorrect values. Mode can be used to recognize damaged barcodes with incorrect text.|

### See Also

* namespace [aspose.barcode.barcoderecognition](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

