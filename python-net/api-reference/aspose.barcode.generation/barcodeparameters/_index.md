---
title: BarcodeParameters
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 50
url: /python-net/api-reference/aspose.barcode.generation/barcodeparameters/
---

## BarcodeParameters class

Barcode generation parameters.

The BarcodeParameters type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|x_dimension|x-dimension is the smallest width of the unit of BarCode bars or spaces.<br/>            Increase this will increase the whole barcode image width.<br/>            Ignored if [auto_size_mode](/barcode/python-net/api-reference/aspose.barcode.generation/basegenerationparameters/) property is set to AutoSizeMode.Nearest or AutoSizeMode.Interpolation.|
|bar_height|Height of 1D barcodes' bars in [Unit](/barcode/python-net/api-reference/aspose.barcode.generation/unit/) value.<br/>            Ignored if [auto_size_mode](/barcode/python-net/api-reference/aspose.barcode.generation/basegenerationparameters/) property is set to AutoSizeMode.Nearest or AutoSizeMode.Interpolation.|
|bar_color|Bars color.<br/>            Default value: Color.Black.|
|padding|Barcode paddings.<br/>            Default value: 5pt 5pt 5pt 5pt.|
|checksum_always_show|Always display checksum digit in the human readable text for Code128 and GS1Code128 barcodes.|
|is_checksum_enabled|Enable checksum during generation 1D barcodes.<br/>        Default is treated as Yes for symbology which must contain checksum, as No where checksum only possible.<br/>        Checksum is possible: Code39 Standard/Extended, Standard2of5, Interleaved2of5, Matrix2of5, ItalianPost25, DeutschePostIdentcode, DeutschePostLeitcode, VIN, Codabar<br/>        Checksum always used: Rest symbology|
|enable_escape|Indicates whether explains the character "\" as an escape character in CodeText property. Used for Pdf417, DataMatrix, Code128 only<br/>            If the EnableEscape is true, "\" will be explained as a special escape character. Otherwise, "\" acts as normal characters.|
|throw_exception_when_code_text_incorrect|Only for 1D barcodes.<br/>            If codetext is incorrect and value set to true - exception will be thrown. Otherwise codetext will be corrected to match barcode's specification.<br/>            Exception always will be thrown for: Databar symbology if codetext is incorrect.<br/>            Exception always will not be thrown for: AustraliaPost, SingapurePost, Code39Extended, Code93Extended, Code16K, Code128 symbology if codetext is incorrect.|
|wide_narrow_ratio|Wide bars to Narrow bars ratio.<br/>            Default value: 3, that is, wide bars are 3 times as wide as narrow bars.<br/>            Used for ITF, PZN, PharmaCode, Standard2of5, Interleaved2of5, Matrix2of5, ItalianPost25, IATA2of5, VIN, DeutschePost, OPC, Code32, DataLogic2of5, PatchCode, Code39Extended, Code39Standard|
|code_text_parameters|Codetext parameters.|
|filled_bars|Gets or sets a value indicating whether bars filled.<br/>            Only for 1D barcodes.<br/>            Default value: true.|
|bar_width_reduction|Get or sets bars reduction value that is used to compensate ink spread while printing.<br/>            Default value: 0|
|postal|Postal parameters. Used for Postnet, Planet.|
|patch_code|PatchCode parameters.|
|australian_post|AustralianPost barcode parameters.|
|data_bar|Databar parameters.|
|gs1_composite_bar|GS1 Composite Bar parameters.|
|codablock|Codablock parameters.|
|data_matrix|DataMatrix parameters.|
|code_16k|Code16K parameters.|
|dot_code|DotCode parameters.|
|itf|ITF parameters.|
|pdf417|PDF417 parameters.|
|qr|QR, MicroQR and RectMicroQR parameters.|
|supplement|Supplement parameters. Used for Interleaved2of5, Standard2of5, EAN13, EAN8, UPCA, UPCE, ISBN, ISSN, ISMN.|
|maxi_code|MaxiCode parameters.|
|aztec|Aztec parameters.|
|code128|Code128 parameters.|
|codabar|Codabar parameters.|
|coupon|Coupon parameters. Used for UpcaGs1DatabarCoupon, UpcaGs1Code128Coupon.|
|han_xin|HanXin parameters.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)

