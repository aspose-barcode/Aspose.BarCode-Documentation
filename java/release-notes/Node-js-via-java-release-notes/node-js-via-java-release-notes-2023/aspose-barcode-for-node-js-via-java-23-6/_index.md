---
title: Aspose.BarCode for Node.js via Java 23.6
type: docs
weight: 950
url: /java/aspose-barcode-for-node-js-via-java-23-6/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Node.js via Java 23.6](https://downloads.aspose.com/barcode/nodejs/new-releases/aspose.barcode-for-node.js-via-java-23.6/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODEJS-411|Improve the engine for license files handling|Enhancement|
|BARCODENET-36989|Improve Datamatrix recognition engine|Enhancement|
|BARCODENET-38462|Add support of Han Xin Code to Aspose.Barcode|Enhancement|
|BARCODENET-38608|Generated PDF417 is not recognized with DataSymbol scanner|Bug|

## Public API changes and backwards compatibility

In this release:
-improved DataMatrix recognition quality
-introduced the support of new barcode symbology - Han Xin Code.

### Han Xin Code

- Generation.HanXinEncodeMode class was added to select allowed Han Xin encoding modes.
- Generation.HanXinErrorLevel class was added to select allowed Han Xin error correction levels from L1 to L4.
- Generation.HanXinVersion class was added to select allowed Han Xin versions, Auto and Version01 - Version84.
- Generation.HanXinParameters class was added
- functions getHanXin():HanXinParameters and setHanXin(HanXinParameters) were added to Generation.BarcodeParameters.
- functions getHanXinEncodeMode():int and setHanXinEncodeMode(int) were added to Generation.HanXinParameters.
- functions getHanXinErrorLevel():int and setHanXinErrorLevel(int) were added to Generation.HanXinParameters.
- functions getHanXinVersion():int and setHanXinVersion(int) were added to Generation.HanXinParameters.
- functions getHanXinECIEncoding():int and setHanXinECIEncoding(int) were added to Generation.HanXinParameters.
- constants HAN_XIN and GS_1_HAN_XIN constants were added to Generation.EncodeTypes.
- constants HAN_XIN and GS_1_HAN_XIN values were added to Recognition.DecodeType.
