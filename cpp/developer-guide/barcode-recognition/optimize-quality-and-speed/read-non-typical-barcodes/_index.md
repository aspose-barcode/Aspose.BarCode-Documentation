---
title: Read Non-typical Barcodes
type: docs
description: "This article explains how barcode recognition can be optimized in terms of accuracy and speed in case of various distortions"
keywords: "Improve Barcode Recognition, Read Barcodes with Gaussian Noise, Read Inverted Barcodes, Read Colored Barcode, Read Distorted QR Code, Read Corrupted Barcodes, Read Industrual DataMatrix, Aspose.BarCode, Read Barcode C++"
weight: 40
feedback: BARCODECOM
url: /cpp/read-non-typical-barcodes/

---
 
## **Read Inverted Barcode Images**
***Aspose.BarCode for C++*** enables reading barcode images with inverted colors. To do this, it is required to enable a special parameter called [*AllowInvertImage*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowinvertimage). 

<p align="center"><img src="aztec_regular_inverse.png" width="20%" height="20%"></p>


## **Read Colored Barcodes on Colored Background**
To read colored barcodes on a colored background, ***Aspose.BarCode for C++*** provides a special parameter called [*AllowComplexBackground*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowcomplexbackground) that attempts to distinguish the colored background from barcode labels through color quantization and then subtract it. It should be noted that enabling this parameter results in considerable deceleration of recognition speed and thus should be used in special cases only. 
  
<p align="center"><img src="qr_color.png" width="15%" height="15%"></p>



## **Read Industrial Data Matrix Barcodes**
Industrial *Data Matrix* barcodes often have dotted patterns or other decoration elements and are placed onto metallic surfaces, in this way, creating embossed indelible barcode labels. To facilitate the recognition of such barcodes, it is possible to enable a special parameter called [*AllowDatamatrixIndustrialBarcodes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowdatamatrixindustrialbarcodes) that allows reading dashed labels in a slow mode. 
  
<p align="center"><img src="datamatrix_industrial.png" width="30%" height="30%"></p>

