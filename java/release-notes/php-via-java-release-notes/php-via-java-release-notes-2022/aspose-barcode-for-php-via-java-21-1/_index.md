---
title: Aspose.BarCode for PHP via Java 22.1
type: docs
weight: 30
url: /java/aspose-barcode-for-php-via-java-22-1/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for PHP via Java 22.1](https://downloads.aspose.com/barcode/phpjava/new-releases/aspose.barcode-for-php-via-java-22.1/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37974|Fix array out of bounds issue|Bug|
|BARCODENET-37962|Fix bug with incorrect text wrapping with current EMF encoder|Bug|
|BARCODENET-37963|Fix SwissQR codetext serialization issue|Bug|
|BARCODEPHP-396|Implement the possibility to import barcode images from http resource|Enhancement|
|BARCODEPHP-397|Implement the possibility to deserialize BarCodeReader from xml file located in file system or http resource|Enhancement|
|BARCODEPHP-398|Implement the possibility to deserialize BarcodeGenerator from xml file located in file system or http resource|Enhancement|
|BARCODEPHP-387|Correct the function $generator->getBarcodeType()|Bug|
|BARCODEPHP-392|Implement the generation of the images in TIFF and SVG formats|Bug|


## **Public API and Backward Incompatible Changes**
- Added function Generation->BarcodeGenerator->exportToXml($file)
- Added function Generation->BarcodeGenerator->importFromXml($resource)
- Added function Recognition->BarCodeReader->importFromXml($resource)
- Added const Generation->BarCodeImageFormat->TIFF
- Added const Generation->BarCodeImageFormat->TIFF_IN_CMYK
- Added const Generation->BarCodeImageFormat->SVG

Upcoming API changes:
- Code 39 standard and Code 39 extended symbologies will be merged into Code 39
- Code 93 standard and Code 93 extended symbologies will be merged into Code 93