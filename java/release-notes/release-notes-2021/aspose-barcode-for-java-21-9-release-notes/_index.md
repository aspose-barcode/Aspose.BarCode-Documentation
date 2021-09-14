---
title: Aspose.BarCode for Java 21.9 Release Notes
type: docs
weight: 920
url: /java/aspose-barcode-for-java-21-9-release-notes/
---

{{% alert color="primary" %}}

This page contains release notes information for [Aspose.BarCode for Java 21.9](https://downloads.aspose.com/barcode/java/new-releases/aspose.barcode-for-java-21.9/).

{{% /alert %}}
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37826|Refactor BarcodeReader interface in data unpacking area|Enhancement|
|BARCODENET-37851|Throw Exception on timeout exceeding|Enhancement|

## **Public API and Backward Incompatible Changes**

- Added method com.aspose.barcode.barcoderecognition.BarCodeReader.getBarcodeSettings():BarcodeSettings
- Added class com.aspose.barcode.barcoderecognition.BarcodeSettings
- Added method com.aspose.barcode.barcoderecognition.BarcodeSettings.getChecksumValidation():ChecksumValidation
- Added method com.aspose.barcode.barcoderecognition.BarcodeSettings.setChecksumValidation(ChecksumValidation):void
- Added method com.aspose.barcode.barcoderecognition.BarcodeSettings.getStripFNC():boolean
- Added method com.aspose.barcode.barcoderecognition.BarcodeSettings.setStripFNC(boolean):void
- Added method com.aspose.barcode.barcoderecognition.BarcodeSettings.getDetectEncoding():boolean
- Added method com.aspose.barcode.barcoderecognition.BarcodeSettings.setDetectEncoding(boolean):void
- Added method com.aspose.barcode.barcoderecognition.BarcodeSettings.getAustraliaPost():AustraliaPostSettings
- Added class com.aspose.barcode.barcoderecognition.AustraliaPostSettings
- Added method com.aspose.barcode.barcoderecognition.AustraliaPostSettings.#ctor
- Added method com.aspose.barcode.barcoderecognition.AustraliaPostSettings.#ctor(AustraliaPostSettings)
- Added method com.aspose.barcode.barcoderecognition.AustraliaPostSettings.getCustomerInformationInterpretingType():CustomerInformationInterpretingType
- Added method com.aspose.barcode.barcoderecognition.AustraliaPostSettings.setCustomerInformationInterpretingType(CustomerInformationInterpretingType):void
- Added method com.aspose.barcode.barcoderecognition.AustraliaPostSettings.getIgnoreEndingFillingPatternsForCTable():boolean
- Added method com.aspose.barcode.barcoderecognition.AustraliaPostSettings.setIgnoreEndingFillingPatternsForCTable(boolean):void
- Added method com.aspose.barcode.barcoderecognition.AustraliaPostSettings.getCustomerInformationDecoder():AustraliaPostCustomerInformationDecoder
- Added method com.aspose.barcode.barcoderecognition.AustraliaPostSettings.setCustomerInformationDecoder(AustraliaPostCustomerInformationDecoder):void
- Added interface com.aspose.barcode.barcoderecognition.AustraliaPostCustomerInformationDecoder
- Added method com.aspose.barcode.barcoderecognition.AustraliaPostCustomerInformationDecoder.decode(String):String;
- Added method com.aspose.barcode.barcoderecognition.BarCodeRecognitionException.#ctor()
- Added class com.aspose.barcode.barcoderecognition.RecognitionAbortedException
- Added method com.aspose.barcode.barcoderecognition.RecognitionAbortedException.#ctor
- Added method com.aspose.barcode.barcoderecognition.RecognitionAbortedException.#ctor(int)
- Added method com.aspose.barcode.barcoderecognition.RecognitionAbortedException.#ctor(String,int)
- Added method com.aspose.barcode.barcoderecognition.RecognitionAbortedException.getExecutionTime():int
- Added method com.aspose.barcode.barcoderecognition.RecognitionAbortedException.setExecutionTime(int):int
