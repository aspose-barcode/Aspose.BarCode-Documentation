---
title: Detection of Potential Barcode Regions
type: docs
description: "This article explains how barcode recognition can be optimized in terms of accuracy and speed using different automatic presets and setting various options"
keywords: "Improve Barcode Recognition, Optimize Barcode Reading, Optimized Scan for Barcode Recognition, Speed Up Barcode Reading, Image Processing for Barcode, Read Many Barcodes from One Image, Aspose.BarCode, Read Barcode C#"
weight: 50
url: /net/detect-barcode-regions/
---

# **Overview**

To perform barcode recognition, first, ***Aspose.BarCode for .NET*** launches image segmentation and detects regions with potential barcodes to start the recognition process using corresponding methods. The library utilizes two barcode region detectors: the one with customizable sensitivity that is managed through a group of properties called [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings) and the other one based on the previous detector implementation that allows successfully detecting approximately 97% of barcodes without additional settings. By default, the [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings) mode is used together with the quality parameter set to *NormalQuality*.

## **Barcode Detector with Customized Sensibility**
The [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings) property group allows flexibly setting the sensitivity of the barcode detector according to particular business needs. The higher is the detection sensitivity, the lower is recognition speed and the more accurate are the results of barcode region detection in complex images with multiple textual blocks and tables. In the case of 1D barcodes, [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings) provides the following modes for region detection sensitivity settings:
-	[*HighPerformance*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/highperformance)
-	[*NormalQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/normalquality)  
-	[*HighQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/highquality) 
-	[*MaxQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/maxquality)  
  
The following code sample illustrates how to work with [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings).
    
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
  
OneDDetectorSettings:  
- DetectorSettings: **HighPerformance**  
Barcodes read: 2  
Code128:Aspose Code 03  
Code128:Aspose Code 04  
- DetectorSettings: **MaxQuality**  
Barcodes read: 5  
Code128:Aspose Diag 01  
Code128:Aspose Code 02  
Code128:Aspose Code 03  
Code128:Aspose Code 01  
Code128:Aspose Code 04  
  
</details>

### **Old Version of Barcode Detector**
The [*UseOldBarcodeDetector*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/useoldbarcodedetector) property enables 1D barcode region detection through the use of the previous detector implementation without flexible sensitivity settings. This region detection mode approximately corresponds to the [*NormalQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/normalquality) and [*HighQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/highquality) settings of the new detector implemented in [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings).  
  
The following code snippet shows how to use the old version of the barcode detector. 

{{< highlight csharp>}}
Console.WriteLine("OneOldBarcodeDetector:");

//read barcode image with UseOldBarcodeDetector set to false
Console.WriteLine("UseOldBarcodeDetector: false");
using (BarCodeReader read = new BarCodeReader($"{path}many_code128.png", DecodeType.Code128))
{
    read.QualitySettings.UseOldBarcodeDetector = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with UseOldBarcodeDetector set to true
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
  
OneOldBarcodeDetector:  
- UseOldBarcodeDetector: false  
Barcodes read: 2  
Code128:Aspose Code 03  
Code128:Aspose Code 04  
- UseOldBarcodeDetector: true  
Barcodes read: 2  
Code128:Aspose Diag 01  
Code128:Aspose Code 02  
Code128:Aspose Code 03  
Code128:Aspose Code 04  
  
</details>

