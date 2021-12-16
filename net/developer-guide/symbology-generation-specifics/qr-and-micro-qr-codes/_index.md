---
title: QR and Micro QR Codes
type: docs
aliases:
 - /.net/qr-and-micro-qr-barcode/
description: "Aspose.BarCode for .NET allows generating QR and Micro QR Barcode more simply."
keywords: "QR Code, Micro QR Barcode, Generate QR Code, Generate Micro QR Barcode, Create QR Code, Aspose.BarCode, C#"
weight: 110
url: /net/qr-and-micro-qr-barcode/
---

## **Create QR or Micro QR Barcode**
QR is a two-dimensional barcode symbology invented in Japan. QR barcodes have the following features:
- High data encoding capacity (up to 7,000 numeric digits or 4,000 alphanumeric symbols)
- Dirt and damage resistance (at maximum, 30% of codewords can be restored)
- Readability from all directions

The new [QR](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/properties/qr) property has been added to class [*BarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) as [*BarcodeParameter*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters) to serve as a QR / MicroQR selector. This property should be set as *ForceQR* (default) for standard QR symbols or *Auto* for MicroQR.

In addition, the following QR parameters can be initialized:

1. **QrECIEncoding** – defines Extended Channel Interpretation Identifiers. It is used to store information about the references used for encoding data in a symbol. The current implementation includes all widely used charset encodings. At present, this property is applicable only to QR barcodes.
2. **QrEncodeMode** - denotes a QR symbology type. The default mode is set to Auto.
3. **QrEncodeType** - sets a QR / MicroQR selector mode. *ForceQR* is to be set for standard QR symbols, and *Auto* is for MicroQR ones.
4. **QrErrorLevel** - defines the level of the Reed-Solomon error correction for QR barcodes. It can range from low to high: LevelL, LevelM, LevelQ, and LevelH.
5. **QrVersion** - identifies the version of *QR Code*: from Version1 to Version40 for QR codes, and from M1 to M4 for MicroQr. The default value is set to *QRVersion.Auto*.

[*Enum QREncodeType*](https://apireference.aspose.com/barcode/net/aspose.barcode/qrencodetype):

1. **Auto** - initiates barcode version negotiation from MicroQR V1
2. **ForceQR** – starts barcode version negotiation from QR V1
3. **ForceMicroQR** - performs barcode version negotiation from MicroQR V1 to V4. If data cannot be encoded using MicroQR, an exception is thrown.

The following changes have been added to Enum [*QREncodeMode*](https://apireference.aspose.com/barcode/net/aspose.barcode/qrencodemode):

1. **Auto** - encodes *CodeText* using the non-Unicode charset. If there is a Unicode character, *CodeText* is encoded with the value that is set in *CodeTextEncoding*
2. **Bytes** - encodes *CodeText* as plain bytes. If a Unicode character is detected, it is encoded as two bytes, the lower byte first
3. **Utf8BOM** - encodes *CodeText* using UTF8 encoding with the first *ByteOfMark* character
4. **Utf16BEBOM** - encodes *CodeText* with UTF8 encoding with the first *ByteOfMark* character. It may cause problems with some barcode scanners
<!--which kind of problems?-->
5. **ECIEncoding** - encodes *CodeText* with the value set stored in the ECIEncoding property. It may lead to problems with some old (pre-2006) barcode scanners
6. **ExtendedCodetext** - encodes *CodeText* in the Extended Channel mode that supports the FNC1 first position, the FNC1 second position, and multi-ECI modes.

### **Encoding QR and Micro QR Barcodes**
Micro QR code is a more compact version of the QR code standard used in applications where symbol size is limited. There are four different versions (corrrsponding to various sizes) of Micro QR codes: the smallest is 11×11 modules; the largest can contain up to 35 numeric characters.

### **Error correction**
QR barcodes can be decoded successfully even in case of certain damages and distortions of an image. This capability is specified by setting the error correction level during encoding. There are four levels of error correction, from low to high:

- **LevelL**: permits recovering 7% of the code text
- **LevelM**: permits recovering 15% of the code text
- **LevelQ**: permits recovering 25% of the code text
- **LevelH**: permits recovering 30% of the code text

### **How to Encode QR Codes**
To generate a QR code, it is necessary to instantiate a *BarcodeGenerator* class object and set its *EncodeType* to QR. Then, it is required to set its *CodeText property*, *QREncodeMode* to "Auto", *QREncodeType* to "ForceQR", and specify the error correction level. The code sample provided below demonstrates how to generate a QR barcode.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-EncodeQRCode-EncodeQRCode.cs" >}}

### **How to set QR version**
***Aspose.BarCode for .NET*** allows developers to specify the version of the QR barcode type while generating barcodes. To implement this possibility, property *QR.Version* has been introduced to *BarcodeGenerator* class. The following code snippet illustrates how to set the QR version before generating a barcode label.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-SettingQRVersion-SettingQRVersion.cs" >}}

### **How to Encode MicroQR Code**
To create a MicriQR code, it is required to instantiate a *BarcodeGenerator* class object and set its *EncodeType* to QR. Then, you need to set its *CodeText* property,*QREncodeMode* to "Auto", *QREncodeType* to "Auto", and define the error correction level. The following code snippet shows how to generate a MicroQR barcode.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-EncodeMicroQRCode-EncodeMicroQRCode.cs" >}}


## **QR Code Encoding in the ECI Mode**
The extended channel interpretation (ECI) mode enables QR codes to encode multiple character sets (e.g. Arabic, Cyrillic, Greek, Hebrew, etc.) and represent other data interpretations or industry-specific requirements into one QR code symbol.

The new property *ECIEncoding* has been added to [*BarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) class. It includes information about the references used to encode data in the symbol using ECI identifiers. The current implementation supports all widely used charset encodings only for QR codes.

Enum ECIEncodings:

1. **ISO_8859_1** - ISO/IEC 8859-1 Latin alphabet No. 1 encoding. ECI Id:"\000003".
2. **ISO_8859_2** - ISO/IEC 8859-2 Latin alphabet No. 2 encoding. ECI Id:"\000004".
3. **ISO_8859_3** - ISO/IEC 8859-3 Latin alphabet No. 3 encoding. ECI Id:"\000005".
4. **ISO_8859_4** - ISO/IEC 8859-4 Latin alphabet No. 4 encoding. ECI Id:"\000006".
5. **ISO_8859_5** - ISO/IEC 8859-5 Latin/Cyrillic alphabet encoding. ECI Id:"\000007".
6. **ISO_8859_6** - ISO/IEC 8859-6 Latin/Arabic alphabet encoding. ECI Id:"\000008".
7. **ISO_8859_7** - ISO/IEC 8859-7 Latin/Greek alphabet encoding. ECI Id:"\000009".
8. **ISO_8859_8** - ISO/IEC 8859-8 Latin/Hebrew alphabet encoding. ECI Id:"\000010".
9. **ISO_8859_9** - ISO/IEC 8859-9 Latin alphabet No. 5 encoding. ECI Id:"\000011".
10. **ISO_8859_10** - ISO/IEC 8859-10 Latin alphabet No. 6 encoding. ECI Id:"\000012".
11. **ISO_8859_11** - ISO/IEC 8859-11 Latin/Thai alphabet encoding. ECI Id:"\000013".
12. **ISO_8859_13** - ISO/IEC 8859-13 Latin alphabet No. 7 (Baltic Rim) encoding. ECI Id:"\000015".
13. **ISO_8859_14** - ISO/IEC 8859-14 Latin alphabet No. 8 (Celtic) encoding. ECI Id:"\000016".
14. **ISO_8859_15** - ISO/IEC 8859-15 Latin alphabet No. 9 encoding. ECI Id:"\000017".
15. **ISO_8859_16** - ISO/IEC 8859-16 Latin alphabet No. 10 encoding. ECI Id:"\000018".
16. **Shift_JIS** - Shift JIS (JIS X 0208 Annex 1 + JIS X 0201) encoding. ECI Id:"\000020".
17. **Win1250** - Windows 1250 Latin 2 (Central Europe) encoding. ECI Id:"\000021".
18. **Win1251** - Windows 1251 Cyrillic encoding. ECI Id:"\000022".
19. **Win1252** - Windows 1252 Latin 1 encoding. ECI Id:"\000023".
20. **Win1256** - Windows 1256 Arabic encoding. ECI Id:"\000024".
21. **UTF16BE** - ISO/IEC 10646 UCS-2 (High order byte first) encoding. ECI Id:"\000025".
22. **UTF8** - ISO/IEC 10646 UTF-8 encoding. ECI Id:"\000026".
23. **US_ASCII** - ISO/IEC 646:1991 International Reference Version of ISO 7-bit coded character set encoding. ECI Id:"\000027".
24. **Big5** - Big 5 (Taiwan) Chinese Character Set encoding. ECI Id:"\000028".
25. **GB18030** - GB (PRC) Chinese Character Set encoding. ECI Id:"\000029".
26. **EUC_KR** - Korean Character Set encoding. ECI Id:"\000030".

### **QR Code Encoding in the ECI Mode**
To generate a QT code in the ECI mode, it is necessary to instantiate a [*BarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) class object. Thne, it is required to set its *EncodeType* to QR, define *CodeText* property, set [*QREncodeMode*](https://apireference.aspose.com/barcode/net/aspose.barcode/qrencodemode) to "ECIEncoding", [*QREncodeType*](https://apireference.aspose.com/barcode/net/aspose.barcode/qrencodetype) to "ForceQR", *ECIEncoding* to UTF8, and specify the error correction level. The following code example demonstrates how to generate a QR barcode in this mode.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-EncodeQRCodEInECIMode-EncodeQRCodEInECIMode.cs" >}}


## **Encode multi-ECI and FNC1 Symbols in QR Code**
The *ExtendedCodetext* mode allows developers to encode multi-ECI and FNC1 symbols into QR codes. The extended channel mode supports the FNC1 first position, the FNC1 second position, and multi-ECI modes.

### **QR Code Encoding in the Extended Code Text Mode**
***Aspose.BarCode APIs*** use [*QrExtCodetextBuilder*](https://apireference.aspose.com/barcode/net/aspose.barcode/qrextcodetextbuilder) class to implement extended code text generation. It it required to define [*Display2DText*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/codetextparameters/properties/twoddisplaytext) property of [*BarcodeGenerator*](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) class to set text being visible and remove the display to manage characters.

In this mode, encoding principles are defined as follows:

- All symbols "\" must be doubled in *CodeText*
- FNC1 in the first position is set in *CodeText* as "<FNC1>"
- FNC1 in the second position is set in *CodeText* as "<FNC1(value)>". The value must be a single symbol (a-z, A-Z) or a digit from 0 to 99
- *Group Separator* for FNC1 modes is set to a 0x1D character '\u001D'
- If you need to insert the "<FNC1>" string into a barcode, denote it as "<\FNC1>".
- ECI identifiers are set as an identifier composed of a single slash and six digits (e.g. "\000026") - a UTF8 ECI identifier.
- To disable the current ECI mode and switch to the default JIS8 mode, the zero-mode ECI identifier is set to "\000000".
- All Unicode characters are automatically encoded into the correct character codeset after applying the ECI identifier.

[*QrExtCodetextBuilder*](https://apireference.aspose.com/barcode/net/aspose.barcode/qrextcodetextbuilder) class inlcudes the following methods:

- **Clear()** method - clears extended code text items.
- **AddPlainCodetext(System.String)** method - adds plain code text to extended code text items.
- **AddECICodetext(Aspose.BarCode.ECIEncodings,System.String)** method - adds code text with ECI.
- **AddFNC1FirstPosition()** method - adds FNC1 in the first position to extended code text items.
- **AddFNC1SecondPosition(System.String)** method - adds FNC1 in the second position to extended code text items.
- **AddFNC1GroupSeparator()** method - adds Group Separator (GS - '\u001D') to extended code text items.
- **GetExtendedCodetext()** method - generates extended code text from the list of generated items.

### **Use multi ECI Mode in Extended Mode**

To instantiate a [*QrExtCodetextBuilder*](https://apireference.aspose.com/barcode/net/aspose.barcode/qrextcodetextbuilder) class object, it is required to call [*AddECICodetext*](https://apireference.aspose.com/barcode/net/aspose.barcode/extcodetextbuilder/methods/addecicodetext) method multiple times to add code text with ECI and then call [*AddPlainCodetext*](https://apireference.aspose.com/barcode/net/aspose.barcode/extcodetextbuilder/methods/addplaincodetext) method to add plain code text to extended code text items.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-MultiECIModeInExtendedMode-MultiECIModeInExtendedMode.cs" >}}

MicroQR does not support ECI and FNC1 modes. Therefore, if you want to generate MicroQR code you need use the standard modes of *QREncodeMode*: Auto, Bytes, Utf8BOM, and Utf16BEBOM.
