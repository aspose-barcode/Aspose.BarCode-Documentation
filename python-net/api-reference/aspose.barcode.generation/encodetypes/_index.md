---
title: EncodeTypes
second_title: Aspose.BarCode for Python via .NET API Reference
description: 
type: docs
weight: 170
url: /python-net/api-reference/aspose.barcode.generation/encodetypes/
---

## EncodeTypes class

Specifies the type of barcode to encode.

The EncodeTypes type exposes the following members:
## Properties
| Name | Description |
| :- | :- |
|all_encode_types|Specifies that data will be checked with all available symbologies.|
|NONE|Unspecified encode type.|
|CODABAR|Specifies that the data should be encoded with CODABAR barcode specification|
|CODE11|Specifies that the data should be encoded with CODE 11 barcode specification|
|CODE_39_STANDARD|Specifies that the data should be encoded with Standard CODE 39 barcode specification|
|CODE_39_EXTENDED|Specifies that the data should be encoded with Extended CODE 39 barcode specification|
|CODE_93_STANDARD|Specifies that the data should be encoded with Standard CODE 93 barcode specification|
|CODE_93_EXTENDED|Specifies that the data should be encoded with Extended CODE 93 barcode specification|
|CODE128|Specifies that the data should be encoded with CODE 128 barcode specification|
|GS1_CODE_128|Specifies that the data should be encoded with GS1 Code 128 barcode specification. The codetext must contains parentheses for AI.|
|EAN8|Specifies that the data should be encoded with EAN-8 barcode specification|
|EAN13|Specifies that the data should be encoded with EAN-13 barcode specification|
|EAN14|Specifies that the data should be encoded with EAN14 barcode specification|
|SCC14|Specifies that the data should be encoded with SCC14 barcode specification|
|SSCC18|Specifies that the data should be encoded with SSCC18 barcode specification|
|UPCA|Specifies that the data should be encoded with UPC-A barcode specification|
|UPCE|Specifies that the data should be encoded with UPC-E barcode specification|
|ISBN|Specifies that the data should be encoded with ISBN barcode specification|
|ISSN|Specifies that the data should be encoded with ISSN barcode specification|
|ISMN|Specifies that the data should be encoded with ISMN barcode specification|
|STANDARD_2OF_5|Specifies that the data should be encoded with Standard 2 of 5 barcode specification|
|INTERLEAVED_2OF_5|Specifies that the data should be encoded with INTERLEAVED 2 of 5 barcode specification|
|MATRIX_2OF_5|Represents Matrix 2 of 5 BarCode|
|ITALIAN_POST25|Represents Italian Post 25 barcode.|
|IATA2OF_5|Represents IATA 2 of 5 barcode.IATA (International Air Transport Assosiation) uses this barcode for the management of air cargo.|
|ITF14|Specifies that the data should be encoded with ITF14 barcode specification|
|ITF6|Represents ITF-6  Barcode.|
|MSI|Specifies that the data should be encoded with MSI Plessey barcode specification|
|VIN|Represents VIN (Vehicle Identification Number) Barcode.|
|DEUTSCHE_POST_IDENTCODE|Represents Deutsch Post barcode, This Symbology is also known as Identcode,CodeIdentcode,German Postal 2 of 5 Identcode, <br/>            Deutsch Post AG Identcode, Deutsch Frachtpost Identcode,  Deutsch Post AG (DHL)|
|DEUTSCHE_POST_LEITCODE|Represents Deutsch Post Leitcode Barcode,also known as German Postal 2 of 5 Leitcode, CodeLeitcode, Leitcode, Deutsch Post AG (DHL).|
|OPC|Represents OPC(Optical Product Code) Barcode,also known as , VCA Barcode VCA OPC, Vision Council of America OPC Barcode.|
|PZN|Represents PZN barcode.This Symbology is also known as Pharmacy central number, Pharmazentralnummer|
|CODE_16K|Represents Code 16K barcode.|
|PHARMACODE|Represents Pharmacode barcode.|
|DATA_MATRIX|2D barcode symbology DataMatrix|
|QR|Specifies that the data should be encoded with QR Code barcode specification|
|AZTEC|Specifies that the data should be encoded with Aztec barcode specification|
|PDF417|Specifies that the data should be encoded with Pdf417 barcode specification|
|MACRO_PDF417|Specifies that the data should be encoded with MacroPdf417 barcode specification|
|GS1_DATA_MATRIX|2D barcode symbology DataMatrix with GS1 string format|
|MICRO_PDF417|Specifies that the data should be encoded with MicroPdf417 barcode specification|
|GS1QR|2D barcode symbology QR with GS1 string format|
|MAXI_CODE|Specifies that the data should be encoded with MaxiCode barcode specification|
|DOT_CODE|Specifies that the data should be encoded with DotCode barcode specification|
|AUSTRALIA_POST|Represents Australia Post Customer BarCode|
|POSTNET|Specifies that the data should be encoded with Postnet barcode specification|
|PLANET|Specifies that the data should be encoded with Planet barcode specification|
|ONE_CODE|Specifies that the data should be encoded with USPS OneCode barcode specification|
|RM4SCC|Represents RM4SCC barcode. RM4SCC (Royal Mail 4-state Customer Code) is used for automated mail sort process in UK.|
|MAILMARK|Represents Royal Mail Mailmark barcode.|
|DATABAR_OMNI_DIRECTIONAL|Specifies that the data should be encoded with GS1 Databar omni-directional barcode specification.|
|DATABAR_TRUNCATED|Specifies that the data should be encoded with GS1 Databar truncated barcode specification.|
|DATABAR_LIMITED|Represents GS1 Databar limited barcode.|
|DATABAR_EXPANDED|Represents GS1 Databar expanded barcode.|
|DATABAR_EXPANDED_STACKED|Represents GS1 Databar expanded stacked barcode.|
|DATABAR_STACKED|Represents GS1 Databar stacked barcode.|
|DATABAR_STACKED_OMNI_DIRECTIONAL|Represents GS1 Databar stacked omni-directional barcode.|
|SINGAPORE_POST|Specifies that the data should be encoded with Singapore Post Barcode barcode specification|
|AUSTRALIAN_POSTE_PARCEL|Specifies that the data should be encoded with Australian Post Domestic eParcel Barcode barcode specification|
|SWISS_POST_PARCEL|Specifies that the data should be encoded with Swiss Post Parcel Barcode barcode specification. Supported types: Domestic Mail, International Mail, Additional Services (new)|
|PATCH_CODE|Represents Patch code barcode|
|CODE32|Specifies that the data should be encoded with Code32 barcode specification|
|DATA_LOGIC_2OF_5|Specifies that the data should be encoded with DataLogic 2 of 5 barcode specification|
|DUTCH_KIX|Specifies that the data should be encoded with Dutch KIX barcode specification|
|UPCA_GS_1_CODE_128_COUPON|Specifies that the data should be encoded with UPC coupon with GS1-128 Extended Code barcode specification.<br/>            An example of the input string:<br/>            BarcodeGenerator.Codetext = "514141100906(8102)03",<br/>            where UPCA part is "514141100906", GS1Code128 part is (8102)03.|
|UPCA_GS_1_DATABAR_COUPON|Specifies that the data should be encoded with UPC coupon with GS1 DataBar addition barcode specification.<br/>            An example of the input string:<br/>            BarcodeGenerator.Codetext = "514141100906(8110)106141416543213500110000310123196000",<br/>            where UPCA part is "514141100906", Databar part is "(8110)106141416543213500110000310123196000".<br/>            To change the caption, use Parameters.CaptionAbove.Text = "company prefix + offer code";|
|CODABLOCK_F|Specifies that the data should be encoded with Codablock-F barcode specification.|
|GS1_CODABLOCK_F|Specifies that the data should be encoded with GS1 Codablock-F barcode specification. The codetext must contains parentheses for AI.|
|GS1_COMPOSITE_BAR|Specifies that the data should be encoded with GS1 Composite Bar barcode specification. The codetext must contains parentheses for AI. 1D codetext and 2D codetext must be separated with symbol '/'|
## Methods
| Name | Description |
| :- | :- |
|get_names()|Retrieves an array of the names of the encode types.|
|parse(parsing_type, result)|Converts the string representation of a BaseEncodeType to its instance.<br/>            A return value indicates whether the conversion succeeded or failed.|
|try_parse(parsing_type, result)|Converts the string representation of a BaseEncodeType to its instance.<br/>            A return value indicates whether the conversion succeeded or failed.|

### See Also

* namespace [aspose.barcode.generation](/barcode/python-net/api-reference/aspose.barcode.generation/)
* assembly [Aspose.BarCode](/barcode/python-net/api-reference/)
