---
title: Read Damaged Barcodes
type: docs
description: "This article explains how barcode recognition can be optimized in terms of accuracy and speed in case of various distortions in Node.js via Java"
keywords: "Improve Barcode Recognition, Read Barcodes with Gaussian Noise, Read Inverted Barcodes, Read Colored Barcode, Read Distorted QR Code, Read Corrupted Barcodes, Read Industrial Data Matrix, Aspose.BarCode, Read Barcodes in Node.js"
ai_search_scope: "barcode_nodejsjava_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 20
url: /nodejsjava/read-damaged-barcodes/
---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can check the quality of Aspose.BarCode recognition and view the results online.{{% /alert %}}

## **Barcode Images with Gaussian Noise**
Gaussian noise is one of the most common damages that may deteriorate the quality of a source barcode. Most of difficulties correspond to the cases when barcode images have the monochrome color scheme or the distortion grain is considerably bigger than the minimal element of a barcode. To cope with these effects, median filtering mechanisms suitable for both 1D and 2D types can be applied. Median filtering mechanisms also affect image quality due to the possible removal of some barcode elements together with noise; however, they still may be helpful in improving readability of key barcode modules.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/nodejsjava/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

### **Median Filtering for 2D Barcodes**
In ***Aspose.BarCode for Node.js via Java***, median filtering can be implemented using the *setAllowMedianSmoothing* method of class [*QualitySettings*](https://reference.aspose.com/barcode/nodejs/QualitySettings) and setting the median filtering window using the *setMedianSmoothingWindowSize* method. Unlike 1D barcodes, automated selection of a suitable median filtering window is not supported for 2D types. 

``` java

let reader = new BarCodeReader("test.png", null,  [ DecodeType.CODE_39_STANDARD, DecodeType.CODE_128 ]);

reader.getQualitySettings().setAllowMedianSmoothing(true);
reader.getQualitySettings().setMedianSmoothingWindowSize(5);
reader.readBarCodes().forEach(function(result, i, results)
{
    console.log("BarCode CodeText: " + result.getCodeText());
});
```
    
<p align="center"><img src="datamatrix_noised.png" width="15%" height="15%"></p>

### **Median Filtering for 1D Barcodes**
One-dimensional filtering for linear barcodes can be set using the *setAllowSaltAndPaperFiltering* method of class [*QualitySettings*](https://reference.aspose.com/barcode/nodejs/QualitySettings). The filtering window size is selected automatically.  
  
<p align="center"><img src="saltandpaper.png" width="30%" height="30%"></p>

### **Median Filtering for Postal Barcodes**
One-dimensional median filtering for postal barcode types can be performed using the *AllowMicroWhiteSpotsRemoving* method of class [*QualitySettings*](https://reference.aspose.com/barcode/nodejs/QualitySettings). The size of the filtering window is set automatically.  
  
<p align="center"><img src="planet_noised.png" width="40%" height="40%"></p>

### **Filtering Out White Spots**
The presence of white spots in barcode images is a frequent problem that appears while sending documents with barcodes through fax transmission. To mitigate this issue, it is possible to use the *setAllowWhiteSpotsRemoving* method of class [*QualitySettings*](https://reference.aspose.com/barcode/nodejs/QualitySettings) that allows filtering out not all Gaussian noise but only white spots.  
  
<p align="center"><img src="code128_whitespots.png" width="30%" height="30%"></p>

## **Reducing Barcode Image Size to Eliminate Visual Artifacts**
In some cases, distortions caused by excessive scaling of a barcode image can be mitigated by reducing the scale space. It can be done using the *setAllowDecreasedImage* method of class [*QualitySettings*](https://reference.aspose.com/barcode/nodejs/QualitySettings). It aims to reduce the size of an image and in this way, to facilitate barcode reading by eliminating visual artifacts.   
  
<p align="center"><img src="datamatrix_waved.png" width="20%" height="20%"></p>

## **Reading Inverted Barcode Images**
The barcode library enables reading barcode images with inverted colors. To do this, it is required to enable a special method called *setAllowInvertImage*. 

<p align="center"><img src="aztec_regular_inverse.png" width="20%" height="20%"></p>

## **Detecting Colored Barcodes on Colored Background**
To read colored barcodes on a colored background, it is necessary to use a method called *setAllowComplexBackground* that attempts to distinguish the colored background from barcode images through color quantization and then subtract it. It should be noted that enabling this parameter results in considerable deceleration of recognition speed and thus should be used in special cases only. 
  
<p align="center"><img src="qr_color.png" width="15%" height="15%"></p>

## **Reading Barcodes with Erased or Displaced Bars**
While scanning or sending barcode images using fax transmission, the problem of displaced or erased bars in 1D barcode labels often appears, especially, in those printed out using ink-jet printers. To resolve this issue, the barcode library provides two methods of class [*QualitySettings*](https://reference.aspose.com/barcode/nodejs/QualitySettings) that are called *setAllowOneDWipedBarsRestoration* and *setCheckMore1DVariants*. They enable selecting the most suitable reading option according to the checksum value and other barcode elements. However, it should be noted that enabling these settings may result in incorrect recognition of 1D barcodes.  
  
<p align="center"><img src="code128_wipedbars.png" width="40%" height="40%"></p>

## **Reading Evidently Incorrect Barcodes**
In cases when it is necessary just to detect the presence of barcodes regardless of their validity and corresponding recognition correctness, it is possible to enable two special settings called *setAllowIncorrectBarcodes* and *setReadTinyBarcodes*. The first one is used to attempt performing partial barcode recognition even if the reading process has provided incorrect results; in this case, the barcode data is decoded with [*BarCodeConfidence*](https://reference.aspose.com/barcode/nodejs/global#BarCodeConfidence) being set to *NONE*, which means that the correctness of recognition is not guaranteed.  
  
The *setReadTinyBarcodes* method facilitates reading small barcode labels in large images. It is ignored if the *setAllowIncorrectBarcodes* method is called passing the *True* value. However, enabling this parameter may result in recognizing false barcodes in place of actual text or tables.  
  
<p align="center"><img src="pdf417_qr_corrupted.png" width="30%" height="30%"></p>

## **Reading Severely Distorted QR Codes and Micro QR Codes**
The barcode library allows reading severely damages *QR Code* and *Micro QR Code* images. This can be enabled by setting the *setAllowQRMicroQrRestoration* parameter. 

<p align="center"><img src="microqr_3d_distorted.png"></p>

## **Reading Industrial Data Matrix Barcodes**
Industrial *Data Matrix* barcodes often have dotted patterns or other decoration elements and are placed onto metallic surfaces, in this way, creating embossed indelible barcode labels. To facilitate the recognition of such barcodes, the barcode library provides the *setAllowDatamatrixIndustrialBarcodes* method of class of class [*QualitySettings*](https://reference.aspose.com/barcode/nodejs/QualitySettings) that allows reading dashed labels in a slow mode. 

<p align="center"><img src="datamatrix_industrial.png" width="30%" height="30%"></p>



