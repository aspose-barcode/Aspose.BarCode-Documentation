---
title: aspose.barcode.barcoderecognition
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 20
url: /python-net/api-reference/aspose.barcode.barcoderecognition/
---


The Aspose.BarCode.BarCodeRecognition contains tools for the 1D/2D barcodes recognition.

## Classes
| Class | Description |
| :- | :- |
|[AustraliaPostCustomerInformationDecoder](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/australiapostcustomerinformationdecoder/)|Public interface for Customer Information Field decoding which is used in AustraliaPost symbology. Implementation should be provided by user.|
|[AustraliaPostSettings](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/australiapostsettings/)|AustraliaPost decoding parameters. Contains parameters which make influence on recognized data of AustraliaPost symbology.|
|[AztecExtendedParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/aztecextendedparameters/)|Stores special data of Aztec recognized barcode|
|[BarCodeExtendedParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodeextendedparameters/)|Stores extended parameters of recognized barcode|
|[BarCodeReader](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/)|BarCodeReader encapsulates an image which may contain one or several barcodes, it then can perform ReadBarCodes operation to detect barcodes.|
|[BarCodeRegionParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderegionparameters/)|Represents the recognized barcode's region and barcode angle|
|[BarCodeResult](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/)|Stores recognized barcode data like [SingleDecodeType](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/singledecodetype/) type, string codetext, <br/>            [BarCodeRegionParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderegionparameters/) region and other parameters|
|[BarcodeSettings](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodesettings/)|The main BarCode decoding parameters. Contains parameters which make influence on recognized data.|
|[BaseDecodeType](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/basedecodetype/)|Base class for MultyDecodeType and SingleDecodeType.|
|[BaseExtendedParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/baseextendedparameters/)|Basic class for extended parameters of recognized barcode storing|
|[Code128DataPortion](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/code128dataportion/)|Contains the data of subtype for Code128 type barcode|
|[Code128ExtendedParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/code128extendedparameters/)|Stores special data of Code128 recognized barcode|
|[DataBarExtendedParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/databarextendedparameters/)|Stores a DataBar additional information of recognized barcode|
|[DataMatrixExtendedParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/datamatrixextendedparameters/)|Stores special data of DataMatrix recognized barcode|
|[DecodeType](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/decodetype/)|Specify the type of barcode to read.|
|[DotCodeExtendedParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/dotcodeextendedparameters/)|Stores special data of DotCode recognized barcode|
|[GS1CompositeBarExtendedParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/gs1compositebarextendedparameters/)|Stores special data of GS1 Composite Bar recognized barcode|
|[MaxiCodeExtendedParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/maxicodeextendedparameters/)|Stores a MaxiCode additional information of recognized barcode|
|[MultyDecodeType](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/multydecodetype/)|Composite decode type.|
|[OneDExtendedParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/onedextendedparameters/)|Stores special data of 1D recognized barcode like separate codetext and checksum|
|[Pdf417ExtendedParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/pdf417extendedparameters/)|Stores a MacroPdf417 metadata information of recognized barcode|
|[QRExtendedParameters](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/qrextendedparameters/)|Stores a QR Structured Append information of recognized barcode|
|[Quadrangle](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/quadrangle/)|Stores a set of four s that represent a [Quadrangle](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/quadrangle/) region.|
|[QualitySettings](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/qualitysettings/)|QualitySettings allows to configure recognition quality and speed manually.<br/>            You can quickly set up QualitySettings with embedded presets: HighPerformance, NormalQuality, HighQuality, MaxQuality or you can manually configure separate options.<br/>            Default value of QualitySettings is NormalQuality.|
|[SingleDecodeType](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/singledecodetype/)|Single decode type. See decode type to get instance.|
## Enumerations
| Enumeration | Description |
| :- | :- |
|[BarCodeConfidence](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodeconfidence/)|Contains recognition confidence level|
|[BarcodeQualityMode](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodequalitymode/)|Mode which enables methods to recognize barcode elements with the selected quality. Barcode element with lower quality requires more hard methods which slows the recognition.|
|[ChecksumValidation](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/checksumvalidation/)|Enable checksum validation during recognition for 1D and Postal barcodes.<br/>        Default is treated as Yes for symbologies which must contain checksum, as No where checksum only possible.<br/>        Checksum never used: Codabar, PatchCode, Pharmacode, DataLogic2of5<br/>        Checksum is possible: Code39 Standard/Extended, Standard2of5, Interleaved2of5, ItalianPost25, Matrix2of5, MSI, ItalianPost25, DeutschePostIdentcode, DeutschePostLeitcode, VIN<br/>        Checksum always used: Rest symbologies|
|[Code128SubType](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/code128subtype/)|Contains types of Code128 subset|
|[ComplexBackgroundMode](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/complexbackgroundmode/)|Mode which enables or disables additional recognition of color barcodes on color images.|
|[DeconvolutionMode](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/deconvolutionmode/)|Deconvolution (image restorations) mode which defines level of image degradation. Originally deconvolution is a function which can restore image degraded <br/>            (convoluted) by any natural function like blur, during obtaining image by camera. Because we cannot detect image function which corrupt the image, <br/>            we have to check most well know functions like sharp or mathematical morphology.|
|[InverseImageMode](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/inverseimagemode/)|Mode which enables or disables additional recognition of barcodes on images with inverted colors (luminance).|
|[XDimensionMode](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/xdimensionmode/)|Recognition mode which sets size (from 1 to infinity) of barcode minimal element: matrix cell or bar.|
