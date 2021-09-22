---
title: Aspose.BarCode for Cpp 21.9 Release Notes
type: docs
weight: 10
url: /cpp/aspose-barcode-for-cpp-21-9-release-notes/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for C++ 21.9](https://downloads.aspose.com/barcode/cpp/new-releases/aspose.barcode-for-c---21.9/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37855|Optimize SVG numbers precision|Enhancement|
|BARCODENET-37880|Swiss-QR-Code Encoding Problems|Enhancement|
|BARCODENET-37889|Implement FastScanOnly setting for 1D recognition|Enhancement|
|BARCODECPP-465|Erroneous character observed while working with Swiss code|Bug|

## **Public API and Backward Incompatible Changes**
- Added property getter bool Aspose.BarCode.BarCodeRecognition.QualitySettings.get_FastScanOnly()
- Added property setter Aspose.BarCode.BarCodeRecognition.QualitySettings.set_FastScanOnly(bool)

|**Class**|**Moved from**|**Moved to**|
| :- | :- | :- |
|Aspose::BarCode::Generation::AztecSymbolMode|Generation/AztecSymbolMode.h|BarCode.Generation/GenerationParameters/AztecSymbolMode|
|Aspose::BarCode::Generation::BarCodeImageFormat|Generation/BarCodeImageFormat.h|BarCode.Generation/GenerationParameters/BarCodeImageFormat|
|Aspose::BarCode::Generation::BorderDashStyle|Generation/BorderDashStyle.h|BarCode.Generation/GenerationParameters/BorderDashStyle|
|Aspose::BarCode::Generation::CodabarChecksumMode|Generation/CodabarChecksumMode.h|BarCode.Generation/GenerationParameters/CodabarChecksumMode|
|Aspose::BarCode::Generation::CodabarSymbol|Generation/CodaBarSymbol.h|BarCode.Generation/GenerationParameters/CodaBarSymbol|
|Aspose::BarCode::Generation::DataMatrixEccType|Generation/DataMatrixEccType.h|BarCode.Generation/GenerationParameters/DataMatrixEccType|
|Aspose::BarCode::Generation::DataMatrixEncodeMode|Generation/DataMatrixEncodeMode.h|BarCode.Generation/GenerationParameters/DataMatrixEncodeMode|
|Aspose::BarCode::Generation::ECIEncodings|Generation/ECIEncodings.h|BarCode.Generation/GenerationParameters/ECIEncodings|
|Aspose::BarCode::Generation::EnableChecksum|Generation/EnableChecksum.h|BarCode.Generation/GenerationParameters/EnableChecksum|
|Aspose::BarCode::Generation::ITF14BorderType|Generation/ITF14BorderType.h|BarCode.Generation/GenerationParameters/ITF14BorderType|
|Aspose::BarCode::Generation::MacroCharacter|Generation/MacroCharacter.h|BarCode.Generation/GenerationParameters/MacroCharacter|
|Aspose::BarCode::Generation::MacroCharacterValues|Generation/MacroCharacter.h|BarCode.Generation/GenerationParameters/MacroCharacter|
|Aspose::BarCode::Generation::Pdf417CompactionMode|Generation/Pdf417CompactionMode.h|BarCode.Generation/GenerationParameters/Pdf417CompactionMode|
|Aspose::BarCode::Generation::Pdf417ErrorLevel|Generation/Pdf417ErrorLevel.h|BarCode.Generation/GenerationParameters/Pdf417ErrorLevel|
|Aspose::BarCode::Generation::QREncodeMode|Generation/QREncodeMode.h|BarCode.Generation/GenerationParameters/QREncodeMode|
|Aspose::BarCode::Generation::QREncodeType|Generation/QREncodeType.h|BarCode.Generation/GenerationParameters/QREncodeType|
|Aspose::BarCode::Generation::QRErrorLevel|Generation/QRErrorLevel.h|BarCode.Generation/GenerationParameters/QRErrorLevel|
|Aspose::BarCode::Generation::QRVersion|Generation/QRVersion.h|BarCode.Generation/GenerationParameters/QRVersion|
|Aspose::BarCode::Generation::BarcodeClassifications|Generation/EncodeTypes/BarcodeClassifications.h|BarCode.Generation/EncodeTypes/BarcodeClassifications|
|Aspose::BarCode::Generation::BarcodeClassifications|Generation/EncodeTypes/BarcodeClassifications.h|BarCode.Generation/EncodeTypes/BarcodeClassifications|
|Aspose::BarCode::Generation::EncodeTypes|Generation/EncodeTypes/EncodeTypes.h|BarCode.Generation/EncodeTypes/EncodeTypes|
|Aspose::BarCode::Generation::SymbologyEncodeType|Generation/EncodeTypes/SymbologyEncodeType.h|BarCode.Generation/EncodeTypes/SymbologyEncodeType|