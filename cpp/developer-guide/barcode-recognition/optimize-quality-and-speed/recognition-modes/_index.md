---
title: Recognition Quality Modes
type: docs
description: "This article explains how barcode recognition can be optimized in terms of accuracy and speed using different automatic presets and setting various options"
keywords: "Improve Barcode Recognition, Optimize Barcode Reading, Optimized Scan for Barcode Recognition, Speed Up Barcode Reading, Image Processing for Barcode, Read Many Barcodes from One Image, Aspose.BarCode, Read Barcode C++"
weight: 10
url: /cpp/recognition-quality-modes/

---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can check the quality of Aspose.BarCode recognition and view the results online.{{% /alert %}}

## **Overview**
Barcode recognition is based on machine vision techniques and utilizes sophisticated mathematical algorithms for object detection and reading. Similar to other computer vision applications, converting an arbitrary image into a machine-readable code strongly depends on the quality of the source image. Namely, barcode images with low quality may be deemed unreadable according to accepted standards. Various methods can be used to recognize barcodes even with unacceptable quality; however, using these methods requires additional CPU computation time and leads to considerably increasing overall reading time.

***Aspose.BarCode for C++*** allows optimizing the barcode recognition process in terms of speed and quality depending on particular business needs and specificities. The library provides a special class called [*QualitySettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings) that can be used to implement flexible settings for barcode recognition and to reach the required trade-off between reading capacity and speed according to the quality of source barcode images.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Recognition Options**

### **Fast Detection for High-Quality Barcodes**
To read high-quality 1D barcode images generated using web-based tools, it is recommended to set [*AllowOneDFastBarcodesDetector*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowonedfastbarcodesdetector) and [*FastScanOnly*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/fastscanonly) recognition options. Both modes enable fast scanning of selected barcode image regions using lightweight recognition methods. The only difference between these two recognition options is that the [*FastScanOnly*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/fastscanonly) mode does not imply further barcode detection in cases when no barcodes have been identified using lightweight recognition methods.  
  

<p align="center"><img src="code128_hq.png" height="20%" width="20%"></p>


### **Regular Option for Barcodes without Distortions**
To read regular barcode labels with normal quality, ***Aspose.BarCode for C++*** suggests an option called [*AllowRegularImage*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowregularimage) that implies applying standard barcode recognition methods. It is recommended to keep this mode enabled in most cases as disabling it may result in recognition failures for regular barcodes.  
    
<p align="center"><img src="aztec_regular_inverse.png" width="20%" heigh="20%"></p>


## **Use Scan Gap for 1D and 2D Barcode Scanning**
To perform preliminary scanning of large 1D barcodes and some 2D barcodes, such as *PDF417*, *QR Code*, or *Aztec*, scanning with a gap of a few lines is usually applied. This approach allows avoiding excessively long scanning and speeding up the recognition process. In ***Aspose.BarCode for C++***, the scan gap can be set using a special parameter called [*AllowDetectScanGap*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowdetectscangap). However, in cases when large and small barcodes are placed close to each other, this setting can result in a refusal to read barcodes of smaller sizes. Disabling this parameter allows successfully reading such combinations of barcode labels albeit at the expense of recognition speed.  
  

<p align="center"><img src="code128_big_and_small.png" width="25%" height="25%"></p>

