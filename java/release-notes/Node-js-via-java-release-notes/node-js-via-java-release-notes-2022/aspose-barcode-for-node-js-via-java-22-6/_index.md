---
title: Aspose.BarCode for Node.js via Java 22.6
type: docs
weight: 950
url: /java/aspose-barcode-for-node-js-via-java-22-6/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Node.js via Java 22.6](https://downloads.aspose.com/barcode/nodejs/new-releases/aspose.barcode-for-node.js-via-java-22.6/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-38207|Implement GS1 Composite bar code generation|Enhancement|

## **Public API and Backward Incompatible Changes**

Added const Generation.EncodeTypes.GS_1_COMPOSITE_BAR

Added class Generation.TwoDComponentType
Added const Generation.TwoDComponentType.AUTO
Added const Generation.TwoDComponentType.CC_A
Added const Generation.TwoDComponentType.CC_B
Added const Generation.TwoDComponentType.CC_C

Added function Generation.BarcodeParameters.getGS1CompositeBar():GS1CompositeBarParameters
Added function Generation.BarcodeParameters.setGS1CompositeBar(GS1CompositeBarParameters):void
Added class Generation.GS1CompositeBarParameters
Added property Generation.GS1CompositeBarParameters.getLinearComponentType():number
Added property Generation.GS1CompositeBarParameters.setLinearComponentType(number):void
Added property Generation.GS1CompositeBarParameters.getTwoDComponentType():number
Added property Generation.GS1CompositeBarParameters.setTwoDComponentType(number):void
Added function Generation.GS1CompositeBarParameters.toString():string