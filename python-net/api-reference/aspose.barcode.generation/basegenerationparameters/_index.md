---
title: BaseGenerationParameters
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 70
url: /python-net/api-reference/aspose.barcode.generation/basegenerationparameters/
---

## BaseGenerationParameters class

Barcode image generation parameters.

The BaseGenerationParameters type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|use_anti_alias|Gets or sets a value indicating whether is used anti-aliasing mode to render image|
|back_color|Background color of the barcode image.<br/>            Default value: Color.White.<br/>            See aspose.pydrawing.Color.|
|resolution|Gets or sets the resolution of the BarCode image.<br/>            One value for both dimensions.<br/>            Default value: 96 dpi.|
|rotation_angle|BarCode image rotation angle, measured in degree, e.g. RotationAngle = 0 or RotationAngle = 360 means no rotation.<br/>            If RotationAngle NOT equal to 90, 180, 270 or 0, it may increase the difficulty for the scanner to read the image.<br/>            Default value: 0.|
|caption_above|Caption Above the BarCode image. See [CaptionParameters](/barcode/python-net/api-reference/aspose.barcode.generation/captionparameters/).|
|caption_below|Caption Below the BarCode image. See [CaptionParameters](/barcode/python-net/api-reference/aspose.barcode.generation/captionparameters/).|
|image|Image parameters. See [ImageParameters](/barcode/python-net/api-reference/aspose.barcode.generation/imageparameters/).|
|auto_size_mode|Specifies the different types of automatic sizing modes.<br/>            Default value: AutoSizeMode.None.|
|image_height|BarCode image height when [auto_size_mode](/barcode/python-net/api-reference/aspose.barcode.generation/basegenerationparameters/) property is set to AutoSizeMode.Nearest or AutoSizeMode.Interpolation.|
|image_width|BarCode image width when [auto_size_mode](/barcode/python-net/api-reference/aspose.barcode.generation/basegenerationparameters/) property is set to AutoSizeMode.Nearest or AutoSizeMode.Interpolation.|
|barcode|Gets the [BarcodeParameters](/barcode/python-net/api-reference/aspose.barcode.generation/barcodeparameters/) that contains all barcode properties.|
|border|Gets the [BorderParameters](/barcode/python-net/api-reference/aspose.barcode.generation/borderparameters/) that contains all configuration properties for barcode border.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

