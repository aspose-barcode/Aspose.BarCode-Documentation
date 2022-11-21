---
title: Aspose.BarCode for PHP via Java 22.11
type: docs
weight: 14
url: /java/aspose-barcode-for-php-via-java-22-11/
---

{{% alert color="primary" %}}
This page contains release notes information for [Aspose.BarCode for PHP via Java 22.11](https://downloads.aspose.com/barcode/php/new-releases/aspose.barcode-for-php-via-java-22.11/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37546|Improve MaxiCode decoder|Enhancement|

## **Public API and Backward Incompatible Changes**

- Added class Generation->MaxiCodeEncodeMode
- Added const Generation->MaxiCodeEncodeMode::AUTO
- Added const Generation->MaxiCodeEncodeMode::BYTES
- Added const Generation->MaxiCodeEncodeMode::EXTENDED_CODETEXT
- Added class Generation->MaxiCodeMode
- Added const Generation->MaxiCodeMode::MODE_2
- Added const Generation->MaxiCodeMode::MODE_3
- Added const Generation->MaxiCodeMode::MODE_4
- Added const Generation->MaxiCodeMode::MODE_5
- Added const Generation->MaxiCodeMode::MODE_6
- Added class Generation->MaxiCodeExtCodetextBuilder
- Added function Generation->MaxiCodeExtCodetextBuilder->getExtendedCodetext():string
- Added function Generation->MaxiCodeParameters->getMaxiCodeMode():int
- Added function Generation->MaxiCodeParameters->setMaxiCodeMode(int):void
- Added function Generation->MaxiCodeParameters->getMaxiCodeEncodeMode():int
- Added function Generation->MaxiCodeParameters->setMaxiCodeEncodeMode(int)
- Added function Generation->MaxiCodeParameters->getECIEncoding():int
- Added function Generation->MaxiCodeParameters->setECIEncoding(int):void
- Added function Generation->MaxiCodeParameters->getMaxiCodeStructuredAppendModeBarcodeId():int
- Added function Generation->MaxiCodeParameters->setMaxiCodeStructuredAppendModeBarcodeId(int):void
- Added function Generation->MaxiCodeParameters->getMaxiCodeStructuredAppendModeBarcodesCount():int
- Added function Generation->MaxiCodeParameters->setMaxiCodeStructuredAppendModeBarcodesCount(int):void
- Added function Generation->MaxiCodeParameters->getAspectRatio():float
- Added function Generation->MaxiCodeParameters->setAspectRatio(float):void
- Added function ComplexBarcode->ComplexCodetextReader::tryDecodeMaxiCode(int,string):MaxiCodeCodetext
- Added class ComplexBarcode->MaxiCodeCodetext
- Added function ComplexBarcode->MaxiCodeCodetext->getMaxiCodeEncodeMode():MaxiCodeEncodeMode
- Added function ComplexBarcode->MaxiCodeCodetext->setMaxiCodeEncodeMode(MaxiCodeEncodeMode)
- Added function ComplexBarcode->MaxiCodeCodetext->getECIEncoding():int
- Added function ComplexBarcode->MaxiCodeCodetext->setECIEncoding(int):void
- Added function ComplexBarcode->MaxiCodeCodetext->getMode():nt
- Added function ComplexBarcode->MaxiCodeCodetext->initFromString(string)
- Added function ComplexBarcode->MaxiCodeCodetext->getBarcodeType():int
- Added class ComplexBarcode->MaxiCodeStructuredCodetext
- Added function ComplexBarcode->MaxiCodeStructuredCodetext->getPostalCode():string
- Added function ComplexBarcode->MaxiCodeStructuredCodetext->getCountryCode():int
- Added function ComplexBarcode->MaxiCodeStructuredCodetext->setCountryCode(int):void
- Added function ComplexBarcode->MaxiCodeStructuredCodetext->getServiceCategory():int
- Added function ComplexBarcode->MaxiCodeStructuredCodetext->setServiceCategory(int):void
- Added function ComplexBarcode->MaxiCodeStructuredCodetext->getSecondMessage():MaxiCodeSecondMessage
- Added function ComplexBarcode->MaxiCodeStructuredCodetext->setSecondMessage(MaxiCodeSecondMessage):vod
- Added function ComplexBarcode->MaxiCodeStructuredCodetext->getConstructedCodetext():string
- Added function ComplexBarcode->MaxiCodeStructuredCodetext->initFromString(string)
- Added function ComplexBarcode->MaxiCodeStructuredCodetext->equals(object)
- Added function ComplexBarcode->MaxiCodeStructuredCodetext->getHashCode()
- Added abstract class ComplexBarcode->MaxiCodeSecondMessage
- Added function ComplexBarcode->MaxiCodeSecondMessage->getMessage():string
- Added class ComplexBarcode->MaxiCodeStandartSecondMessage
- Added function ComplexBarcode->MaxiCodeStandartSecondMessage->setMessage(string)
- Added function ComplexBarcode->MaxiCodeStandartSecondMessage->getMessage():string
- Added function ComplexBarcode->MaxiCodeStandartSecondMessage->equals(object)
- Added function ComplexBarcode->MaxiCodeStandartSecondMessage->getHashCode()
- Added class ComplexBarcode->MaxiCodeStructuredSecondMessage
- Added function ComplexBarcode->MaxiCodeStructuredSecondMessage->getYear():int
- Added function ComplexBarcode->MaxiCodeStructuredSecondMessage->setYear(int):void
- Added function ComplexBarcode->MaxiCodeStructuredSecondMessage->getIdentifiers():List<string>
- Added function ComplexBarcode->MaxiCodeStructuredSecondMessage->add(string):void
- Added function ComplexBarcode->MaxiCodeStructuredSecondMessage->clear()
- Added function ComplexBarcode->MaxiCodeStructuredSecondMessage->getMessage():string
- Added function ComplexBarcode->MaxiCodeStructuredSecondMessage->equals(object)
- Added function ComplexBarcode->MaxiCodeStructuredSecondMessage->getHashCode()
- Added class ComplexBarcode->MaxiCodeCodetextMode2
- Added function ComplexBarcode->MaxiCodeCodetextMode2->getMode()
- Added class ComplexBarcode->MaxiCodeCodetextMode3
- Added function ComplexBarcode->MaxiCodeCodetextMode3->getMode()
- Added class ComplexBarcode->MaxiCodeStandardCodetext
- Added function ComplexBarcode->MaxiCodeStandardCodetext->setMode(int)
- Added function ComplexBarcode->MaxiCodeStandardCodetext->getMode():int
- Added function ComplexBarcode->MaxiCodeStandardCodetext->getMessage():string
- Added function ComplexBarcode->MaxiCodeStandardCodetext->setMessage(string):void
- Added function ComplexBarcode->MaxiCodeStandardCodetext->getConstructedCodetext():string
- Added function ComplexBarcode->MaxiCodeStandardCodetext->initFromString(string)
- Added function ComplexBarcode->MaxiCodeStandardCodetext->equals(object)
- Added function ComplexBarcode->MaxiCodeStandardCodetext->getHashCode()
- Added function Recognition->BarCodeExtendedParameters->getMaxiCode():MaxiCodeExtendedParameters
- Added class Recognition->MaxiCodeExtendedParameters
- Added function Recognition->MaxiCodeExtendedParameters->getMaxiCodeMode():int
- Added function Recognition->MaxiCodeExtendedParameters->setMaxiCodeMode(int):void
- Added function Recognition->MaxiCodeExtendedParameters->getMaxiCodeStructuredAppendModeBarcodeId():int
- Added function Recognition->MaxiCodeExtendedParameters->setMaxiCodeStructuredAppendModeBarcodeId(int):void
- Added function Recognition->MaxiCodeExtendedParameters->getMaxiCodeStructuredAppendModeBarcodesCount():int
- Added function Recognition->MaxiCodeExtendedParameters->setMaxiCodeStructuredAppendModeBarcodesCount(int):void
- Added function Recognition->MaxiCodeExtendedParameters->equals(object)
- Added function Recognition->MaxiCodeExtendedParameters->getHashCode()
- Added function Recognition->MaxiCodeExtendedParameters->toString()
