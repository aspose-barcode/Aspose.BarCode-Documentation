---
title: Specific Parameters for 2D Barcodes
type: docs
weight: 160
url: /net/managing-2d-barcodes/
---

## Hiding Barcode Text that Is Too Long to Display

Unlike one-dimensional barcodes, two-dimensional ones often contain a large amount of data as they have been introduced exactly to address such a need. This human-readable barcode text does not require to be printed out as it does not undergo machine scanning. Therefore, it may be necessary to hide the contents of the *CodeText* property for 2D barcodes in cases when it is too long to be displayed on a barcode label. 

### Hiding Barcode Text
The following code snippet demonstrates how to hide the contents of the *CodeText* property.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-HideBarcodeCodeText-HideBarcodeCodeText.cs" >}}

|**Hiding CodeText Contents**|
| :- |
|![todo:image_alt_text](managing-2d-barcodes_1.jpg)|

### Reducing the Font Size of CodeText
The code sample provided below illustrates how to reduce the font size of *CodeText* contents.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-ReduceCodeTextFontSize-ReduceCodeTextFontSize.cs" >}}

## Adjusting 2D Barcode Label Size
{{% alert color="primary" %}} 

The size of a barcode label depends on many factors. Mainly, the following settings affect the size of the resulting image:

- Metrics
- Resolution: higher resolution will lead to a larger image size on the same screen or printer
- *GraphicsUnit*: all settings can be based on millimeters or inches
- *AutoSize*: setting this property to "*False*" will result in fixing the size of image as *ImageWidth * ImageHeight*. In this case, an oversized barcode (in the case when *CodeText* contents are too long) will be out of the frame
- *ImageWidth*: only valid when *AutoSize* is set to "*False*"
- *ImageHeight*: only valid when *AutoSize* is set to "*False*"
- Margins: only valid when *AutoSize* is set to "*True*". It indicates the marginal area of a barcode label itself. This setting could be overridden by *CaptionAbove* and *CaptionBelow*. In this case, when *AutoSize* is set to "*True*", and the value of *Margins* is not large enough to display the contents of *CaptionAbove* or *CaptionBelow*, then the marginal area will expand automatically
- *CaptionAbove*: is based on the settings of CaptionAbove.Visible, CaptionAbove.Space, and CaptionAbove.Font
- *CaptionBelow*: is based on the settings of CaptionBelow.Visible, CaptionBelow.Space, and CaptionBeow.Font
- Core barcode label
- *XDimension*: each (1D) black bar's or (2D) module's width
- *Rows*: the number of (2D) module rows
- *Columns*: the number of (2D) module columns
- *AspectRatio*: the ratio of *YDimension/XDimension*
- *WideNarrowRatio*: the ratio of wide bars / narrow bars or wide spaces / narrow spaces for some types of barcodes
- *CodeText*: is based on the settings of *CodeLocation*, *CodeTextFont*, and *CodeTextSpace* properties

{{% /alert %}} 

Each specific barcode type may have different semantic demands; then it will override or ignore the above settings. E.g., *Data Matrix* is a square-based barcode type. The *AspectRatio* setting is not applicable to the *Data Matrix* symbology as it equals 1 for square modules. Accordingly, *BarcodeGenerator* will simply ignore those settings during the generation process.

## Aspect Ratio Settings
The *AspectRatio* property is the ratio between the height and width of a barcode. We can control these parameters by setting the value of *AspectRatio*. For example, *AspectRatio* equal to 3:2 means that the width of the generated barcode will be 1.5 times larger than the height. Below the *PDF417* barcode with the *AspectRatio* of 1.5 is demonstrated.

|**Aspect Ratio of 1.5**|
| :- |
|![todo:image_alt_text](managing-2d-barcodes_2.png)|
  
Setting the *AspectRatio* equal to 2 means that the width of the barcode is 2 times greater than its height. The PDF417 barcode with the *AspectRatio* of 2 is shown.

|**Aspect Ratio of 2**|
| :- |
|![todo:image_alt_text](managing-2d-barcodes_3.png)|
  
The code snippet given below demonstrates how to set the Aspect Ratio:

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-SetAspectRatio-SetAspectRatio.cs" >}}

## Detecting Unicode Encoding of Barcode
Aspose.BarCode API allows developers to detect the Unicode encoding. This flag works only for QR/Micro QR codes at the moment.

In this case, when the encoding detection flag is enabled, the barcode engine returns Unicode text while attempting to detect the encoding of a barcode. The barcode may be encoded using one of the following encodings:

- UTF8
- BOM_UTF8
- BOM_UTF16BE
- BOM_UTF16LE

The flag is enabled by default. In the case when the flag is disabled, the engine returns plain text without encoding detection.

The code example given below demonstrates how to get the plain text without encoding detection.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-DetectUnicodeEncoding-DetectUnicodeEncoding.cs" >}}
