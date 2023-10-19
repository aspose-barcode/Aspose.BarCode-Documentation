---
title: Detection of Potential Barcode Regions
type: docs
description: "This article explains how barcode recognition can be optimized in terms of accuracy and speed using different automatic presets and setting various options"
keywords: "Improve Barcode Recognition, Optimize Barcode Reading, Optimized Scan for Barcode Recognition, Speed Up Barcode Reading, Image Processing for Barcode, Read Many Barcodes from One Image, Aspose.BarCode, Read Barcode C#"
weight: 50
feedback: BARCODECOM
url: /cpp/detect-barcode-regions/
---

# **Overview**

To perform barcode recognition, first, ***Aspose.BarCode for C++*** launches image segmentation and detects regions with potential barcodes to start the recognition process using corresponding methods. The library utilizes two barcode region detectors: the one with customizable sensitivity that is managed through a group of properties called [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings) and the other one based on the previous detector implementation that allows successfully detecting approximately 97% of barcodes without additional settings. By default, the [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings) mode is used together with the quality parameter set to *NormalQuality*.

## **Barcode Detector with Customized Sensibility**
The [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings) property group allows flexibly setting the sensitivity of the barcode detector according to particular business needs. The higher is the detection sensitivity, the lower is recognition speed and the more accurate are the results of barcode region detection in complex images with multiple textual blocks and tables. In the case of 1D barcodes, [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings) provides the following modes for region detection sensitivity settings:
-	[*HighPerformance*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/highperformance)
-	[*NormalQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/normalquality)  
-	[*HighQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/highquality) 
-	[*MaxQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/maxquality)  
  

### **Old Version of Barcode Detector**
The [*UseOldBarcodeDetector*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/useoldbarcodedetector) property enables 1D barcode region detection through the use of the previous detector implementation without flexible sensitivity settings. This region detection mode approximately corresponds to the [*NormalQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/normalquality) and [*HighQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/properties/highquality) settings of the new detector implemented in [*DetectorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/detectorsettings).  
  
