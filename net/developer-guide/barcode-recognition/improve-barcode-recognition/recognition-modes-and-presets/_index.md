---
title: Recognition Options and Presets
type: docs
description: "This article explains how barcode recognition can be optimized in terms of accuracy and speed."
keywords: "Improve Barcode Recognition, Optimize Barcode Reading, Optimized Scan for Barcode Recognition, Speed Up Barcode Reading, Image Processing for Barcode, Improve Barcode Recognition, Read Many Barcodes from One Image, Aspose.BarCode, Read Barcode C#"
weight: 10
url: /net/recognition-modes-and-presets/
---
{{% alert color="primary" %}}[Read barcodes online](https://products.aspose.app/barcode/recognize). You can check the quality of Aspose.BarCode recognition and view the results online.{{% /alert %}}

## Overview
Barcode recognition is based on machine vision techniques and utilizes sophisticated mathematical algorithms for object detection and reading. Similar as for other computer vision applications, converting an arbitrary image into a machine-readable code strongly depends on the quality of the source image. Namely, barcode images with low quality may be deemed unreadable according to accepted standards. There are various methods that allow recognizing barcodes even with unacceptable quality; however, using these methods requires additional CPU computation time and leads to considerably increasing overall reading time. 

***Aspose.BarCode for .NET** allows optimizing the barcode recognition process in terms of speed and quality depending on particular business needs and specificities. The library provides a special class called [*QualitySettings*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings) that can be used to implement flexible settings for barcode recognition and to reach the required trade-off between reading capacity and speed according to the quality of source barcode images.

## Recognition Options and Presets for Managing Speed and Quality
As mentioned above, ***Aspose.BarCode for .NET*** provides class [*QualitySettings*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings) that allows enabling and disabling various algorithms for image recovery to read barcodes with distortions or artifacts. See article [**Recognition Specifics**](/barcode/net/recognition-specifics/) for more information about special cases of barcode recognition. Moreover, this class provides special parameters to customize the trade-off between reading speed and quality in more simple case. Such parameters are grouped into several presets that facilitate image recovery and barcode reading for different recognition scenarios.

## Recognition Presets
This section provides the detailed information about supported recognition presets, including *NormalQuality*, *HighPerformance*, *HighQuality*, *MaxBarCodes*, manually configured options, and others, as listed in the table below. By default, [*QualitySettings*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings) uses the *NormalQuality* preset. 

|Recognition Preset|Description|
|---|---|
|[*NormalQuality*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/normalquality)| |
|[*HighQuality*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highquality)| |
|[*HighPerformance*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highperformance)| |
|[*HighQualityDetection*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highqualitydetection)| |
|[*MaxQualityDetection*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/maxqualitydetection)| |
|[*MaxBarcodes*]()| |
  
### Universal Presets for All Barcode Types
***Aspose.BarCode for .NET*** provides several universal recognition quality setting presets, such as [*HighPerformance*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highperformance), [*NormalQuality*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/normalquality), and [*HighQuality*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highquality). These presets establish linear depence between recognition quality and speed for all barcode types, including 1D, 2D, and postal symbologies. In most cases, the [*NormalQuality*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/normalquality) preset used by default is sufficient for the majority of barcodes that provide normal scanning quality. 

<p align="center"><img src="barcodes_different_quality.png" height="75%" width="75%"></p>

The following code snippet illustrates how to work with universal recognition presets.

{{< highlight csharp>}}
Console.WriteLine("QualityPresetsMain:");

//recognize image with QualitySettings HighPerformance
Console.WriteLine("QualitySettings: HighPerformance");
using (BarCodeReader read = new BarCodeReader($"{path}barcodes_different_quality.png", DecodeType.Code128, 
    DecodeType.Code39Extended, DecodeType.Planet, DecodeType.QR, DecodeType.MicroQR, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.Aztec))
{
    read.QualitySettings = QualitySettings.HighPerformance;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//recognize image with QualitySettings NormalQuality
Console.WriteLine("QualitySettings: NormalQuality");
using (BarCodeReader read = new BarCodeReader($"{path}barcodes_different_quality.png", DecodeType.Code128,
    DecodeType.Code39Extended, DecodeType.Planet, DecodeType.QR, DecodeType.MicroQR, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.Aztec))
{
    read.QualitySettings = QualitySettings.NormalQuality;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//recognize image with QualitySettings HighQuality
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
</details>

### Presets for 1D Barcode Types
To read 1D barcodes, ***Aspose.BarCode for .NET*** provides special quality setting presets that are intended for working with normal quality barcodes and at the same time, enable improved parameters for the detection and recognition of 1D barcodes. These presets can be particularly useful in cases when it is necessary to scan barcodes of small dimensions that are difficult for detecting and recognizing from complex documents with many textual blocks and tables. Specifically, using [*HighQualityDetection*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highqualitydetection) and [*MaxQualityDetection*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings) presets allows getting much better recognition results for 1D barcodes in complex documents compared with basic settings. Similar improvements can be achieved by using the [*NormalQuality*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/normalquality) preset and imposing the appropriate settings in [*DetectorSettings*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings).   

<p align="center"><img src="many_code128.png" height="75%" width="75%""></p>

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
</details>

### Preset ***MaxBarCodes*** for Setups
To read all barcodes potentially presented in an image including incorrect ones, ***Aspose.BarCode for .NET*** suggest using a special preset called [*MaxBarCodes*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/maxbarcodes). This preset applies recognition quality settings that allow recovering up to 1% of data contained in severely corrupted or erroneous barcodes. Similar recognition quality settings can be enabled using the [*AllowIncorrectBarcodes*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowincorrectbarcodes) property.
Although the [*MaxBarCodes*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/maxbarcodes) mode may be useful to decode barcodes that otherwise are unreadable, it should be used for setup purposes only, as applying this parameter may lead to considerably increasing the time required to complete the recognition process and producing incorrect recognition outputs.

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
</details>

## Recognition Options

### Fast Detection for High-Quality Barcodes
To read high-quality 1D barcode images generated using web-based tools, it is recommended to set [*AllowOneDFastBarcodesDetector*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowonedfastbarcodesdetector) and [*FastScanOnly*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/fastscanonly) recognition options. Both modes enable fast scanning of selected barcode image regions using lightweight recognition methods. The only difference between these two recognition options is that the [*FastScanOnly*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/fastscanonly) mode does not imply further barcode detection in cases when no barcodes have been identified using lightweight recognition methods.

<p align="center"><img src="code128_hq.png" height="20%" width="20%"></p>

{{< highlight csharp>}}
Console.WriteLine("FastScan:");

//read barcode image with FastScan options disabled
Console.WriteLine("FastScan: disabled");
using (BarCodeReader read = new BarCodeReader($"{path}code128_hq.png", DecodeType.Code128))
{
    read.QualitySettings.FastScanOnly = false;
    read.QualitySettings.AllowOneDFastBarcodesDetector = false;
    Stopwatch watch = new Stopwatch();
    watch.Start();
    read.ReadBarCodes();
    watch.Stop();
    Console.WriteLine($"Barcodes read: {read.FoundCount}, Recognition time:{(int)watch.ElapsedMilliseconds} ms");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with FastScan options enabled
Console.WriteLine("FastScan: enabled");
using (BarCodeReader read = new BarCodeReader($"{path}code128_hq.png", DecodeType.Code128))
{
    read.QualitySettings.FastScanOnly = true;
    read.QualitySettings.AllowOneDFastBarcodesDetector = true;
    Stopwatch watch = new Stopwatch();
    watch.Start();
    read.ReadBarCodes();
    watch.Stop();
    Console.WriteLine($"Barcodes read: {read.FoundCount}, Recognition time:{(int)watch.ElapsedMilliseconds} ms");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
</details>

### Regular Recognition of Barcodes without Distortions
To read regular barcode labels with normal quality, ***Aspose.BarCode for .NET*** suggests an option called [*AllowRegularImage*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowregularimage) that implies applying standard barcode recognition methods. It is recommended to keep this mode enabled in most cases as disabling it may result in recognition failures for regular barcodes.

<p align="center"><img src="aztec_regular_inverse.png"></p>

{{< highlight csharp>}}
Console.WriteLine("RegularImage:");

//recognize image with AllowRegularImage false
Console.WriteLine("AllowRegularImage: false");
using (BarCodeReader read = new BarCodeReader($"{path}aztec_regular_inverse.png", DecodeType.Aztec))
{
    read.QualitySettings = QualitySettings.HighPerformance;
    read.QualitySettings.AllowRegularImage = false;
    read.QualitySettings.AllowInvertImage = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//recognize image with AllowRegularImage true
Console.WriteLine("AllowRegularImage: true");
using (BarCodeReader read = new BarCodeReader($"{path}aztec_regular_inverse.png", DecodeType.Aztec))
{
    read.QualitySettings = QualitySettings.HighPerformance;
    read.QualitySettings.AllowRegularImage = true;
    read.QualitySettings.AllowInvertImage = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
</details>

## Detection of Potential Barcode Regions
To perform barcode recognition, first, ***Aspose.BarCode for .NET*** launches image segmentation and highlights regions with potential barcodes to start the recognition process using corresponding methods. The library utilizes two barcode region detectors: the one with customizable sensitivity that is managed through a group of properties called [*DetectorSettings*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings) and the other one based on the previous detector implementation that allows successfully detecting approximately 97% of barcodes without additional settings. By default, the [*DetectorSettings*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings) mode is used together with the quality parameter set to *NormalQuality*.

### Barcode Detector with Customized Sensibility
The [*DetectorSettings*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings) property group allows flexibly setting the sensitivity of the barcode detector according to particular business needs. The higher is the detection sensitivity, the lower is recognition speed and the more accurate are the results of barcode region detection in complex images with multiple textual blocks and tables. In case of 1D barcodes, [*DetectorSettings*] provides the following modes for region detection sensitivity settings:
-	[*HighPerformance](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/highperformance)
-	[*NormalQuality*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/normalquality)  
-	[*HighQuality*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/highquality) 
-	[*MaxQuality*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/maxquality)  

{{< highlight csharp>}}
Console.WriteLine("OneDDetectorSettings:");

//read barcode image with DetectorSettings set to HighPerformance
Console.WriteLine("DetectorSettings: HighPerformance");
using (BarCodeReader read = new BarCodeReader($"{path}many_code128.png", DecodeType.Code128))
{
    read.QualitySettings.DetectorSettings = BarcodeSvmDetectorSettings.HighPerformance;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with DetectorSettings set to MaxQuality
Console.WriteLine("DetectorSettings: MaxQuality");
using (BarCodeReader read = new BarCodeReader($"{path}many_code128.png", DecodeType.Code128))
{
    read.QualitySettings.DetectorSettings = BarcodeSvmDetectorSettings.MaxQuality;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
</details>

### Old Version of Barcode Detector
The [*UseOldBarcodeDetector*]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/useoldbarcodedetector) property enables 1D barcode region detection through the use of the previous detector implementation without flexible sensitivity settings. This region detection mode approximately corresponds to the [*NormalQuality*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/normalquality) and [*HighQuality*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/highquality) settings of the new detector implemented in [*DetectorSettings*]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings).

<p align="center"><img src=""></p>

{{< highlight csharp>}}
Console.WriteLine("OneOldBarcodeDetector:");

//recognize image with UseOldBarcodeDetector false
Console.WriteLine("UseOldBarcodeDetector: false");
using (BarCodeReader read = new BarCodeReader($"{path}many_code128.png", DecodeType.Code128))
{
    read.QualitySettings.UseOldBarcodeDetector = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//recognize image with UseOldBarcodeDetector true
Console.WriteLine("UseOldBarcodeDetector: true");
using (BarCodeReader read = new BarCodeReader($"{path}many_code128.png", DecodeType.Code128))
{
    read.QualitySettings.UseOldBarcodeDetector = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
</details>

## Using Scan Gap for 1D and 2D Barcode Scanning
To perform preliminary scanning of large 1D barcodes and some 2D barcodes, such as *PDF417*, *QR Code*, or *Aztec*, scanning with a gap of few lines is usually applied. This approach allows avoiding excessively long scanning and speeding up the recognition process. In ***Aspose.BarCode for .NET**, the scan gap can be set using a special parameter called [*AllowDetectScanGap*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowdetectscangap). However, in cases when large and small barcodes are placed close to each other, this setting can result in refusal to read the barcode of smaller sizes. Disabling this parameter allows successfully reading such combinations of barcode labels albeit at the expense of recognition speed. 
<p align="center"><img src="code128_big_and_small.png"></p>

{{< highlight csharp>}}
Console.WriteLine("DetectScanGap:");

//recognize image with AllowDetectScanGap true
Console.WriteLine("AllowDetectScanGap: true");
using (BarCodeReader read = new BarCodeReader($"{path}code128_big_and_small.png", DecodeType.Code128))
{
    read.QualitySettings.AllowDetectScanGap = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//recognize image with AllowDetectScanGap false
Console.WriteLine("AllowDetectScanGap: false");
using (BarCodeReader read = new BarCodeReader($"{path}code128_big_and_small.png", DecodeType.Code128))
{
    read.QualitySettings.AllowDetectScanGap = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
</details>






