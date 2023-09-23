---
title: Recognition Quality Presets
type: docs
description: "This article explains how barcode recognition can be optimized in terms of accuracy and speed using different automatic presets and setting various options"
keywords: "Improve Barcode Recognition, Optimize Barcode Reading, Optimized Scan for Barcode Recognition, Speed Up Barcode Reading, Image Processing for Barcode, Read Many Barcodes from One Image, Aspose.BarCode, Read Barcode C#"
weight: 20
url: /net/recognition-quality-presets/

---

## **Manage Reading Speed and Quality Using Presets**
***Aspose.BarCode for .NET*** provides class [*QualitySettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings) that allows enabling and disabling various algorithms for image recovery to read barcodes with distortions or artifacts. See the article [**Recognition Specifics**](/barcode/net/recognition-specifics/) for more information about special cases of barcode recognition. Moreover, class [*QualitySettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings) provides special parameters to customize the trade-off between reading speed and quality in regular situations. Such parameters are grouped into several presets that facilitate image recovery and barcode reading for different recognition scenarios.

## **Supported Presets**
This section provides detailed information about supported recognition presets, including *NormalQuality*, *HighPerformance*, *HighQuality*, *MaxBarCodes*, manually configured options, and others, as listed in the table below. By default, [*QualitySettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings) uses the *NormalQuality* preset. 

|Recognition Preset|Description|
|---|---|
|[*NormalQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/normalquality)|Suitable for the most of barcodes with regular quality|
|[*HighQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highquality)|Intended for work with low-quality barcodes; it allows reading and decoding diagonal and severely corrupted barcodes|
|[*HighPerformance*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highperformance)|Suggested for high-quality barcode images|
|[*HighQualityDetection*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highqualitydetection)|Similar to the *NormalQuality* one but has the [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings) parameter set to [*HighQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/highquality)|
|[*MaxQualityDetection*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/maxqualitydetection)|Similar to the *NormalQuality* one but with the [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings) set to [*MaxQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/maxquality). It is applicable to detect diagonal and damaged barcodes|
|[*MaxBarcodes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/maxbarcodes)|Allows reading all potential barcodes in an image, even incorrect ones. It is recommended for use for debugging purposes only|
  
### **Universal Presets for All Barcode Types**
***Aspose.BarCode for .NET*** provides several universal recognition quality setting presets, such as [*HighPerformance*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highperformance), [*NormalQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/normalquality), and [*HighQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highquality). These presets allow establishing linear dependence between recognition quality and speed for all barcode types, including 1D, 2D, and postal symbologies. In most cases, the [*NormalQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/normalquality) preset used by default is sufficient for the majority of barcodes that provide normal scanning quality. 
  
The following code snippet illustrates how to apply universal recognition presets to the sample image provided below.
  
<p align="center"><img src="barcodes_different_quality.png" height="45%" width="45%"></p>
  
{{< highlight csharp>}}
Console.WriteLine("QualityPresetsMain:");

//read barcode image with QualitySettings set to HighPerformance
Console.WriteLine("QualitySettings: HighPerformance");
using (BarCodeReader read = new BarCodeReader($"{path}barcodes_different_quality.png", DecodeType.Code128, 
    DecodeType.Code39Extended, DecodeType.Planet, DecodeType.QR, DecodeType.MicroQR, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.Aztec))
{
    read.QualitySettings = QualitySettings.HighPerformance;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with QualitySettings set to NormalQuality
Console.WriteLine("QualitySettings: NormalQuality");
using (BarCodeReader read = new BarCodeReader($"{path}barcodes_different_quality.png", DecodeType.Code128,
    DecodeType.Code39Extended, DecodeType.Planet, DecodeType.QR, DecodeType.MicroQR, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.Aztec))
{
    read.QualitySettings = QualitySettings.NormalQuality;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with QualitySettings set to HighQuality
Console.WriteLine("QualitySettings: HighQuality");
using (BarCodeReader read = new BarCodeReader($"{path}barcodes_different_quality.png", DecodeType.Code128,
    DecodeType.Code39Extended, DecodeType.Planet, DecodeType.QR, DecodeType.MicroQR, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.Aztec))
{
    read.QualitySettings = QualitySettings.HighQuality;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}
  
<details>  
<summary>View the results of code execution</summary>
  
QualityPresetsMain:  
- QualitySettings: **HighPerformance**  
Barcodes read: 2  
Code128:Aspose Code 04  
Aztec:Aspose Regular  
- QualitySettings: **NormalQuality**  
Barcodes read: 6  
Code128:Aspose Code 04  
Aztec:Aspose Regular  
Code39Extended:/YYAD25HL  
DataMatrix:D19-WQ9-F91046-0811  
Code39Extended:0058  
Planet:990000837284  
- QualitySettings: **HighQuality**  
Barcodes read: 8  
Code128:Aspose Code 04  
Aztec:Aspose Regular  
Aztec:Aspose Inverse  
Code128:JJBEA129955634111200235  
MicroQR:FV50CE  
DataMatrix:D19-WQ9-F91046-0811  
Code39Extended:0058  
Planet:990000837284  
  
</details>

### **Presets for 1D Barcode Types**
To read 1D barcodes, ***Aspose.BarCode for .NET*** provides special quality setting presets that are intended for working with normal quality barcodes and at the same time, enable improved parameters for the detection and recognition of 1D barcodes. These presets can be particularly useful in cases when it is necessary to scan barcodes of small dimensions that are difficult for detecting and recognizing from complex documents with many textual blocks and tables. Specifically, using [*HighQualityDetection*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highqualitydetection) and [*MaxQualityDetection*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/maxqualitydetection) presets allows getting much better recognition results for 1D barcodes in complex documents compared with basic settings. Similar improvements can be achieved by using the [*NormalQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/normalquality) preset and specifying the appropriate settings in [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings).  
  
The image below illustrates an example of a document with various barcodes presented in this document along with textual parts and illustrations. 

<p align="center"><img src="many_code128.png" height="45%" width="45%"></p>
  
The following code snippet explains how to set recognition quality parameters to ensure accurate detection and decoding of all 1D barcodes of target symbologies. 

{{< highlight csharp>}}
Console.WriteLine("QualityPresetsOneD:");

//read barcode image with QualitySettings set to NormalQuality
Console.WriteLine("QualitySettings: NormalQuality");
using (BarCodeReader read = new BarCodeReader($"{path}many_code128.png", DecodeType.Code128))
{
    read.QualitySettings = QualitySettings.NormalQuality;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with QualitySettings set to HighQualityDetection
Console.WriteLine("QualitySettings: HighQualityDetection");
using (BarCodeReader read = new BarCodeReader($"{path}many_code128.png", DecodeType.Code128))
{
    read.QualitySettings = QualitySettings.HighQualityDetection;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with QualitySettings set to MaxQualityDetection
Console.WriteLine("QualitySettings: MaxQualityDetection");
using (BarCodeReader read = new BarCodeReader($"{path}many_code128.png", DecodeType.Code128))
{
    read.QualitySettings = QualitySettings.MaxQualityDetection;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
  
QualityPresetsOneD:  
- QualitySettings: **NormalQuality**  
Barcodes read: 2  
Code128:Aspose Code 03  
Code128:Aspose Code 04  
- QualitySettings: **HighQualityDetection**  
Barcodes read: 4  
Code128:Aspose Diag 01  
Code128:Aspose Code 02  
Code128:Aspose Code 03  
Code128:Aspose Code 04  
- QualitySettings: **MaxQualityDetection**  
Barcodes read: 5  
Code128:Aspose Diag 01  
Code128:Aspose Code 02  
Code128:Aspose Code 03  
Code128:Aspose Code 01  
Code128:Aspose Code 04  
  
</details>

### **Preset ***MaxBarCodes*** for Debugging**
To read all barcodes potentially presented in an image including incorrect ones, ***Aspose.BarCode for .NET*** provides a special preset called [*MaxBarCodes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/maxbarcodes). This preset applies recognition quality settings that allow recovering up to 1% more barcodes (severely corrupted or erroneous ones) compared with the results achievable using the [*NormalQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/normalquality) preset. Similar recognition quality settings can be enabled using the [*AllowIncorrectBarcodes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowincorrectbarcodes) property.
Although the [*MaxBarCodes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/maxbarcodes) mode may be useful to decode barcodes that otherwise are unreadable, it should be used for debugging purposes only, as applying this parameter may lead to notably increasing the time required to complete the recognition process and producing incorrect recognition outputs. This preset is recommended for use only for advanced users of the ***Aspose.BarCode*** library. 
  
The following code snippet explains how to work with the [*MaxBarCodes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/maxbarcodes) preset.

{{< highlight csharp>}}
Console.WriteLine("MaxBarCodesPreset:");

//read barcode image with QualitySettings set to MaxBarCodes
Console.WriteLine("QualitySettings: MaxBarCodes");
using (BarCodeReader read = new BarCodeReader($"{path}barcodes_different_quality.png", DecodeType.Code128,
    DecodeType.Code39Extended, DecodeType.Planet, DecodeType.QR, DecodeType.MicroQR, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.Aztec))
{
    read.QualitySettings = QualitySettings.MaxBarCodes;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
  
MaxBarCodesPreset:  
- QualitySettings: MaxBarCodes  
Barcodes read: 11  
Code128:Aspose Code 04  
Code128:Aspose Code 01  
Aztec:Aspose Regular  
Aztec:Aspose Inverse  
Code128:JJBEA129955634111200235  
MicroQR:FV50CE  
QR:Aspose QR  
DataMatrix:D19-WQ9-F91046-0811  
Pdf417:Aspose Pdf417  
Code39Extended:0058  
Planet:990000837284  
  
</details>

