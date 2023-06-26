---
title: Aspose.BarCode for Java 23.6 Release Notes
type: docs
weight: 960
url: /java/aspose-barcode-for-java-23-6-release-notes/
---

{{% alert color="primary" %}}

This page contains release notes information for [Aspose.BarCode for Java 23.6](https://downloads.aspose.com/barcode/java/new-releases/aspose.barcode-for-java-23.6/).

{{% /alert %}}
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODEJAVA-1459|Improve the engine for license files handling|Enhancement|
|BARCODENET-36989|Improve Datamatrix recognition engine|Enhancement|
|BARCODENET-38462|Add support of Han Xin Code to Aspose.Barcode|Enhancement|
|BARCODENET-38608|Generated PDF417 is not recognized with DataSymbol scanner|Bug|

## Public API changes and backwards compatibility

In this release:
 -improved DataMatrix recognition quality
 -introduced the support of new barcode symbology - Han Xin Code.

### Han Xin Code

- com.aspose.barcode.generation.HanXinEncodeMode enum was added to select allowed Han Xin encoding modes.
- com.aspose.barcode.generation.HanXinErrorLevel enum was added to select allowed Han Xin error correction levels from L1 to L4.
- com.aspose.barcode.generation.HanXinVersion enum was added to select allowed Han Xin versions, Auto and Version01 - Version84.
- com.aspose.barcode.generation.HanXinParameters enum was added
- methods getHanXin():HanXinParameters and setHanXin(HanXinParameters) were added to com.aspose.barcode.generation.BarcodeParameters.
- HanXinEncodeMode was added to HanXinParameters.
- HanXinErrorLevel was added to HanXinParameters.
- HanXinVersion was added to HanXinParameters.
- HanXinECIEncoding was added to HanXinParameters.
- HanXin and GS1HanXin were added to com.aspose.barcode.generation.EncodeTypes.
- HanXin and GS1HanXin were added to com.aspose.barcode.barcoderecognition.DecodeType.