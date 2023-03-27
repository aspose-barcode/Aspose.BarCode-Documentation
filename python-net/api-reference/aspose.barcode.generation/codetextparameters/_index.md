---
title: CodetextParameters
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 120
url: /python-net/api-reference/aspose.barcode.generation/codetextparameters/
---

## CodetextParameters class

Codetext parameters.

The CodetextParameters type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|two_d_display_text|Text that will be displayed instead of codetext in 2D barcodes.<br/>            Used for: Aztec, Pdf417, DataMatrix, QR, MaxiCode, DotCode|
|font_mode|Specify FontMode. If FontMode is set to Auto, font size will be calculated automatically based on xDimension value.<br/>            It is recommended to use FontMode.Auto especially in AutoSizeMode.Nearest or AutoSizeMode.Interpolation.<br/>            Default value: FontMode.Auto.|
|font|Specify the displaying CodeText's font.<br/>            Default value: Arial 5pt regular.<br/>            Ignored if FontMode is set to FontMode.Auto.|
|space|Space between the CodeText and the BarCode in [Unit](/barcode/python-net/api-reference/aspose.barcode.generation/unit/) value.<br/>            Default value: 2pt.<br/>            Ignored for EAN8, EAN13, UPCE, UPCA, ISBN, ISMN, ISSN, UpcaGs1DatabarCoupon.|
|alignment|Gets or sets the alignment of the code text.<br/>            Default value: StringAlignment.Center.|
|color|Specify the displaying CodeText's Color.<br/>            Default value: Color.Black.|
|location|Specify the displaying CodeText Location, set to CodeLocation.None to hide CodeText.<br/>            Default value: CodeLocation.Below for 1D barcodes and CodeLocation.None for 2D barcodes.|
|no_wrap|Specify word wraps (line breaks) within text.<br/>            Default value: false.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

