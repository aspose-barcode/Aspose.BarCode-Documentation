---
title: Recognition Barcode Quality and Deconvolution Modes
type: docs
description: "This article explains how barcode recognition can be optimized in terms of accuracy and speed in case of various distortions"
keywords: "Improve Barcode Recognition, Read Barcodes with Gaussian Noise, Read Distorted QR Code, Read Corrupted Barcodes, Read Industrual DataMatrix, Aspose.BarCode, Read Barcode C#"
weight: 30
feedback: BARCODECOM
url: /net/recognition-barcode-quality-deconvolution/
aliases:
- /net/read-damaged-barcodes/
- /net/recognition-specifics/

---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can check the quality of Aspose.BarCode recognition and view the results online.{{% /alert %}}
## **Overview**
***Aspose.BarCode for .NET*** provides special modes which selects and enables methods to recognize barcode elements with low barcode or image quality. [*BarcodeQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/barcodequality) can enable methods which improve recognition quality of low quality barcodes. [*Deconvolution*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/deconvolution) enables image preprocessing methods which can improve image quality before the recognition. Both methods trade recognition speed to recognition quality.
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Barcode Quality Mode**
[*BarcodeQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/barcodequality) mode selects and enables methods to recognize barcode elements with the selected quality. Barcode elements with lower quality requires more heavy recognition methods which slow the recognition. Mode list is shown in the table below. 

|Barcode Quality Mode|Description|
|---|---|
|*High*| Enables recognition methods for High quality barcodes. Fastest mode |
|*Normal*| Enables recognition methods for Common (Normal) quality barcodes |
|*Low*| Enables recognition methods for Low quality barcodes. Slowest mode|

## **Deconvolution Mode**
[*Deconvolution*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/deconvolution) mode defines level of image degradation. Originally deconvolution is a function which can restore image degraded (convoluted) by any natural function like blur, during obtaining image by camera. Because we cannot detect image function which corrupt the image, we have to check most well-known functions like [sharp](https://en.wikipedia.org/wiki/Kernel_(image_processing)) or [mathematical morphology](https://en.wikipedia.org/wiki/Mathematical_morphology). Image preprocessing algorithms require additional time and can slow the recognition. Mode list is shown in the table below.

|Deconvolution Mode|Description|
|---|---|
|*Fast*| Enables fast deconvolution methods for high quality images without any image distortions |
|*Normal*| Enables normal deconvolution methods for common images with light image distortions like light noise or blur |
|*Slow*| Enables heavy deconvolution methods for low quality highly corrupted images with huge image distortions |

## **Using Barcode Quality and Deconvolution Modes**
The following table shows difference in recognition quality, depends on [*BarcodeQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/barcodequality) and [*Deconvolution*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/deconvolution) settings.

<p align="center"><img src="manybarcodes_quality_deconvolution.png" height="45%" width="45%"></p>

| Barcode Quality | Deconvolution | Recognized barcodes | 
|---|---|---|
| **High** | **Fast** | **4** |
| **Normal** | **Normal** | **6** |
| **Low** | **Normal** | **9** |
| **Normal** | **Slow** | **7** |
| **Low** | **Slow** | **10** |

``` csharp
Console.WriteLine("ReadBarcodeQualityDeconvolutionDocument:");
//recognize image with BarcodeQualityMode High, DeconvolutionMode Fast
Console.WriteLine("BarcodeQualityMode: High, DeconvolutionMode: Fast");
using (BarCodeReader read = new BarCodeReader($"{path}manybarcodes_quality_deconvolution.png", DecodeType.Code128, DecodeType.Code39Extended, DecodeType.Planet, DecodeType.QR, DecodeType.MicroQR, DecodeType.DataMatrix))
{
    read.QualitySettings.BarcodeQuality = BarcodeQualityMode.High;
    read.QualitySettings.Deconvolution = DeconvolutionMode.Fast;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//recognize image with BarcodeQualityMode Normal, DeconvolutionMode Normal
Console.WriteLine("BarcodeQualityMode: Normal, DeconvolutionMode: Normal");
using (BarCodeReader read = new BarCodeReader($"{path}manybarcodes_quality_deconvolution.png", DecodeType.Code128, DecodeType.Code39Extended, DecodeType.Planet, DecodeType.QR, DecodeType.MicroQR, DecodeType.DataMatrix))
{
    read.QualitySettings.BarcodeQuality = BarcodeQualityMode.Normal;
    read.QualitySettings.Deconvolution = DeconvolutionMode.Normal;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//recognize image with BarcodeQualityMode Low, DeconvolutionMode Normal
Console.WriteLine("BarcodeQualityMode: Low, DeconvolutionMode: Normal");
using (BarCodeReader read = new BarCodeReader($"{path}manybarcodes_quality_deconvolution.png", DecodeType.Code128, DecodeType.Code39Extended, DecodeType.Planet, DecodeType.QR, DecodeType.MicroQR, DecodeType.DataMatrix))
{
    read.QualitySettings.BarcodeQuality = BarcodeQualityMode.Low;
    read.QualitySettings.Deconvolution = DeconvolutionMode.Normal;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//recognize image with BarcodeQualityMode Normal, DeconvolutionMode Slow
Console.WriteLine("BarcodeQualityMode: Normal, DeconvolutionMode: Slow");
using (BarCodeReader read = new BarCodeReader($"{path}manybarcodes_quality_deconvolution.png", DecodeType.Code128, DecodeType.Code39Extended, DecodeType.Planet, DecodeType.QR, DecodeType.MicroQR, DecodeType.DataMatrix))
{
    read.QualitySettings.BarcodeQuality = BarcodeQualityMode.Normal;
    read.QualitySettings.Deconvolution = DeconvolutionMode.Slow;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//recognize image with BarcodeQualityMode Low, DeconvolutionMode Slow
Console.WriteLine("BarcodeQualityMode: Low, DeconvolutionMode: Slow");
using (BarCodeReader read = new BarCodeReader($"{path}manybarcodes_quality_deconvolution.png", DecodeType.Code128, DecodeType.Code39Extended, DecodeType.Planet, DecodeType.QR, DecodeType.MicroQR, DecodeType.DataMatrix))
{
    read.QualitySettings.BarcodeQuality = BarcodeQualityMode.Low;
    read.QualitySettings.Deconvolution = DeconvolutionMode.Slow;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
```

<details>  
<summary>View the results of code execution</summary>

```text  
ReadBarcodeQualityDeconvolutionDocument:
BarcodeQualityMode: High, DeconvolutionMode: Fast
Barcodes read: 4
Code128:Aspose Code 04
Code39Extended:/YYAD25HL
Code39Extended:0058
MicroQR:FV50CE
BarcodeQualityMode: Normal, DeconvolutionMode: Normal
Barcodes read: 6
Code128:Aspose Code 04
Code39Extended:/YYAD25HL
Code39Extended:0058
Planet:990000837284
DataMatrix:D19-WQ9-F91046-0811
MicroQR:FV50CE
BarcodeQualityMode: Low, DeconvolutionMode: Normal
Barcodes read: 9
Code128:Aspose Code 04
Code128:JJBEA129955634111200235
Code39Extended:0058
Planet:990000837284
DataMatrix:250623022021032007010300
DataMatrix:StarDatamatrix
DataMatrix:87918-1023
DataMatrix:D19-WQ9-F91046-0811
MicroQR:FV50CE
BarcodeQualityMode: Normal, DeconvolutionMode: Slow
Barcodes read: 7
Code128:Aspose Code 04
Code39Extended:/YYAD25HL
Code128:EASYAPANEXO
Code39Extended:0058
Planet:990000837284
DataMatrix:D19-WQ9-F91046-0811
MicroQR:FV50CE
BarcodeQualityMode: Low, DeconvolutionMode: Slow
Barcodes read: 10
Code128:Aspose Code 04
Code128:JJBEA129955634111200235
Code128:EASYAPANEXO
Code39Extended:0058
Planet:990000837284
DataMatrix:250623022021032007010300
DataMatrix:StarDatamatrix
DataMatrix:87918-1023
DataMatrix:D19-WQ9-F91046-0811
MicroQR:FV50CE
```

</details>
