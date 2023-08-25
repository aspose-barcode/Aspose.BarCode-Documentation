---
title: Recognition Quality Presets
type: docs
description: "This article explains how barcode recognition can be optimized in terms of accuracy and speed using different automatic presets and setting various options"
keywords: "Improve Barcode Recognition, Optimize Barcode Reading, Optimized Scan for Barcode Recognition, Speed Up Barcode Reading, Image Processing for Barcode, Read Many Barcodes from One Image, Aspose.BarCode, Read Barcode C++"
weight: 20
url: /cpp/recognition-quality-presets/

---

## **Manage Reading Speed and Quality Using Presets**
***Aspose.BarCode for C++*** provides class [*QualitySettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings) that allows enabling and disabling various algorithms for image recovery to read barcodes with distortions or artifacts. See the article [**Recognition Specifics**](/barcode/net/recognition-specifics/) for more information about special cases of barcode recognition. Moreover, class [*QualitySettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings) provides special parameters to customize the trade-off between reading speed and quality in regular situations. Such parameters are grouped into several presets that facilitate image recovery and barcode reading for different recognition scenarios.

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
***Aspose.BarCode for C++*** provides several universal recognition quality setting presets, such as [*HighPerformance*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highperformance), [*NormalQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/normalquality), and [*HighQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highquality). These presets allow establishing linear dependence between recognition quality and speed for all barcode types, including 1D, 2D, and postal symbologies. In most cases, the [*NormalQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/normalquality) preset used by default is sufficient for the majority of barcodes that provide normal scanning quality. 
    
<p align="center"><img src="barcodes_different_quality.png" height="45%" width="45%"></p>
  

### **Presets for 1D Barcode Types**
To read 1D barcodes, ***Aspose.BarCode for C++*** provides special quality setting presets that are intended for working with normal quality barcodes and at the same time, enable improved parameters for the detection and recognition of 1D barcodes. These presets can be particularly useful in cases when it is necessary to scan barcodes of small dimensions that are difficult for detecting and recognizing from complex documents with many textual blocks and tables. Specifically, using [*HighQualityDetection*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/highqualitydetection) and [*MaxQualityDetection*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/maxqualitydetection) presets allows getting much better recognition results for 1D barcodes in complex documents compared with basic settings. Similar improvements can be achieved by using the [*NormalQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/normalquality) preset and specifying the appropriate settings in [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings).  
  
The image below illustrates an example of a document with various barcodes presented in this document along with textual parts and illustrations. 

<p align="center"><img src="many_code128.png" height="45%" width="45%"></p>
  

### **Preset ***MaxBarCodes*** for Debugging**
To read all barcodes potentially presented in an image including incorrect ones, ***Aspose.BarCode for C++*** provides a special preset called [*MaxBarCodes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/maxbarcodes). This preset applies recognition quality settings that allow recovering up to 1% more barcodes (severely corrupted or erroneous ones) compared with the results achievable using the [*NormalQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/normalquality) preset. Similar recognition quality settings can be enabled using the [*AllowIncorrectBarcodes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowincorrectbarcodes) property.
Although the [*MaxBarCodes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/maxbarcodes) mode may be useful to decode barcodes that otherwise are unreadable, it should be used for debugging purposes only, as applying this parameter may lead to notably increasing the time required to complete the recognition process and producing incorrect recognition outputs. This preset is recommended for use only for advanced users of the ***Aspose.BarCode*** library. 
  
