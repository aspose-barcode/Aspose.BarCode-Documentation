---
title: Barcode Reading Quality Options and Presets
type: docs
description: "This article explains how barcode recognition can be optimized in terms of accuracy and speed using different automatic presets and setting various options"
keywords: "Improve Barcode Recognition, Optimize Barcode Reading, Optimized Scan for Barcode Recognition, Speed Up Barcode Reading, Image Processing for Barcode, Read Many Barcodes from One Image, Aspose.BarCode, Read Barcodes in Python"
weight: 10
url: /python-net/barcode-reading-presets/
---

## **Overview**
Barcode reading relies on machine vision mechanisms and uses various mathematical algorithms for object detection. Same as in other computer vision tasks, source image quality is crucial to convert an arbitrary image to machine-readable code. Low-quality barcode images may result being unreadable depending on specific recognition standards. There are different approaches to read barcodes of unacceptable quality. However, running such methods takes extra CPU computation time and may lead to the considerable increase in recognition time.

***Aspose.BarCode for Python via .NET*** suggests optimizing the recognition process in terms of quality and speed in line with specific business needs. A special class called [*QualitySettings*](https://reference.aspose.com/barcode/python-net/aspose.barcode.barcoderecognition/qualitysettings/) provides flexible recognition settings to achieve the acceptable trade-off between reading acuracy and speed depending the quality of a source barcode image.

  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Recognition Speed and Quality Options and Presets**
***Aspose.BarCode for Python via .NET*** contains class [*QualitySettings*](https://reference.aspose.com/barcode/python-net/aspose.barcode.barcoderecognition/qualitysettings/) that is used to enable and disable various algorithms to read barcodes with damages or artifacts. See the article [**Special Barcode Reading Cases**](/barcode/python-net/special-barcode-reading-cases/) for additional information. In addition, class [*QualitySettings*](https://reference.aspose.com/barcode/python-net/aspose.barcode.barcoderecognition/qualitysettings/) allows customizing the trade-off between recognition quality and speed in common cases. Corresponding properties are grouped into dedicated presets that allow improving image recovery and barcode reading for various scenarios.

## **Recognition Presets**
In this section, supported recognition presets are described, including *high_performance*, *normal_quality*, *high_quality*, *max_bar_codes*, and others, as represented in the table below. By default, the *normal_quality* preset is enabled. 

|Recognition Preset|Description|
|---|---|
|*normal_quality*|Suitable for regular-quality barcode images|
|*high_quality*|Intended for low-quality barcode images. It allows scanning diagonal and severely damaged barcode images|
|*high_performance*|Used for high-quality barcode images|
|*high_quality_detection*|Same as *normal_quality* but setting the *detector_settings* property with the *HighQuality* value|
|*max_quality_detection*|Same as *normal_quality* but setting the *detector_settings* property with the *MaxQuality* value. It allows detecting diagonal and damaged barcode images|
|*max_bar_codes*|Allows scanning all barcodes possibly presented in an image, including invalid ones. It is recommended for debugging tasks only|
   
### **Universal Presets for All Barcode Types**
***Aspose.BarCode for Python via .NET*** suggests various universal recognition presets and corresponding properties to activate them, such as *high_performance*, *setNormalQuality*, and *setHighQuality*. These presets establish linear dependence between reading accuracy and speed for all barcode types. Generally, using the default *normal_quality* preset is sufficient for most of barcodes that have acceptable scanning quality. 
    
<p align="center"><img src="barcodes_different_quality.png" height="45%" width="45%"></p>

### **Presets for 1D Barcode Types**
To scan linear barcodes, the barcode library provides dedicated recognition presets suitable for barcodes of normal quality. These presets provide improved 1D barcode detection and decoding and are useful to work with barcodes of small dimensions or complex documents with multiple text blocks and tables. For example, compared with general recognition settings, *high_quality_detection* and *max_quality_detection* presets allow improving recognition results for 1D barcodes in complex documents. Alternatilvely, such imprment can be implemented using the *normal_quality* preset and tuning [*BarcodeSvmDetectorSettings*](https://reference.aspose.com/barcode/python-net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/) using the *detector_settings* property.  
  
The image shown below is a sample document with multiple barcodes that contains also text parts and figures. 

<p align="center"><img src="many_code128.png" height="45%" width="45%"></p>


### **Using ***MaxBarCodes*** Preset for Debugging**
To detect all possible barcodes in an image including invalid ones, ***Aspose.BarCode for Python via .NET*** contains a special preset called *max_bar_codes*. This preset allows restoring up to 1% more barcodes (severely damaged or incorrectly generated) in comparison with the results that can be reached by the *NormalQuality* preset. Similar reading settings can be implemented using the *allow_incorrect_barcodes* property.
The *MaxBarCodes* preset may be used to scan even unreadable barcodes; however, it is intended for debugging tasks only as it may result in considerably augmenting the time needed to complete the reading process and providing invalid decoding outputs. This preset is suggested only for advanced users of the barcode library. 


## **Recognition Options**

### **Fast Detection for High-Quality Barcode Images**
To recognize high-quality 1D barcodes created through web-based applications, it is suggested to use *allow_one_d_fast_barcodes_detector* and *fast_scan_only* properties. They enable fast scanning of target image areas through lightweight scanning techniques. The difference between these two options is that the *fast_scan_only* property does not enable further barcode search after the failure to idetify more barcodes through lightweight scanning methods.  
  
<p align="center"><img src="code128_hq.png" height="20%" width="20%"></p>

### **Regular Recognition of Barcode Images without Damage**
To decode regular norma-quality barcode images, ***Aspose.BarCode for Python via .NET*** provides the *allow_regular_image* property that enables standard recognition techniques. This mode is suggested to be applied to most cases, as its deactivation may lead to decoding failures for regular barcode images.  
 
<p align="center"><img src="aztec_regular_inverse.png" width="20%" heigh="20%"></p>


## **Detection of Areas with Potential Barcodes**
To read barcodes, ***Aspose.BarCode for Python via .NET*** first performs the segmentation of a source image and finds areas with potential barcodes. Two barcode region detectors are available: the one with flexible sensitivity implemented in a class called [*BarcodeSvmDetectorSettings*](https://reference.aspose.com/barcode/python-net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/) and the other one that relies on the previous detector version that allows correctly identifying about 97% of barcodes without the need in additional settings. [*BarcodeSvmDetectorSettings*](https://reference.aspose.com/barcode/python-net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/barcodesvmdetectorsettings/) is used by default together with using the "normal_quality* preset.

### **Barcode Detector with Flexible Sensibility**
[*BarcodeSvmDetectorSettings*](https://reference.aspose.com/barcode/python-net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/) allows adjusting the sensitivity of the barcode detector in a flexible manner according to specific needs. The better is the detector sensitivity, the lower is reading speed and the better are the results of barcode region detection in complex source images with many text blocks and tables. For 1D barcodes, [*BarcodeSvmDetectorSettings*](https://reference.aspose.com/barcode/python-net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/) supports the following sensitivity settings:
-	*NormalQuality* 
-	*HighQuality* 
-	*HighPerformance*
-	*MaxQuality*  

### **Previous Version of Barcode Detector**
The *use_old_barcode_detector* property allows performing barcode region detection for 1D barcodes using the previous detector version that does not support flexible sensitivity settings. This region detection mode is close to *NormalQuality* and *HighQuality* modes of the new detector implemented in [*BarcodeSvmDetectorSettings*](https://reference.aspose.com/barcode/python-net/aspose.barcode.barcoderecognition/barcodesvmdetectorsettings/).  

## **Managing Scan Gap during 1D and 2D Barcode Scanning**
To conduct preliminary detection of large-sized 1D and some 2D types, such as *QR Code*, *PDF417*, or *Aztec Code*, barcode scanning can be applied with a gap of several lines. This option is intended to avoid unaccaptably long scanning and allows speeding up the decoding process. The barcode library contains the *allow_detect_scan_gap* to enable the scan gap. However, if large-sized and tiny barcodes are displayed in an image close to each other, applying this recognition option can lead to a failure to read smaller-sized barcode. When this option is not enabled, reading such combinations of barcodes can be executed successfully at the expense of recognition speed.  
  
<p align="center"><img src="code128_big_and_small.png" width="25%" height="25%"></p>

