---
title: Aspose.BarCode for Android via Java 21.6
type: docs
weight: 830
url: /java/aspose-barcode-for-android-via-java-21-6/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Android via Java 21.6](https://downloads.aspose.com/barcode/androidjava/new-releases/aspose.barcode-for-android-via-java-21.6/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODEANDROID-454|Investigate and find solution for the large images processing|Enhancement|
|BARCODENET-37797|Remove Databar14 split pattern generation code|Enhancement|
|BARCODENET-37789|Generated DataBar Expanded images are not recognized by other engines|Bug|
|BARCODENET-37783|Cannot read QR code image in the PDF file|Bug|
|BARCODENET-37778|The QR code recognition of certain image throws Exception|Bug|
|BARCODENET-37784|Certain image cannot be recognized|Bug|

## **Public API and Backward Incompatible Changes**
- Added method com.aspose.barcode.barcoderecognition.QualitySettings.setImageScalingMode(ImageScalingMode) 
- Added method com.aspose.barcode.barcoderecognition.QualitySettings.getImageScalingMode():ImageScalingMode 
- Added enum ImageScalingMode
- Added enum  values
  ImageScalingMode.WITHOUT_SCALE
  ImageScalingMode.SCALE_800x600
  ImageScalingMode.SCALE_1280x720
  ImageScalingMode.SCALE_1920x1080
   