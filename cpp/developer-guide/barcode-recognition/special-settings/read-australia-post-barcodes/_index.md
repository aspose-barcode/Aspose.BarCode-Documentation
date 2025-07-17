---
title: Read Australia Post Barcodes
type: docs
description: "This article describes how to decode Australia Post barcodes in Aspose.BarCode for C++"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcode C++"
ai_search_scope: "barcode_cpp_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 30
feedback: BARCODECOM
url: /cpp/read-australia-post/
---

{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can test the quality of ***Aspose.BarCode*** recognition functionality and view the results online.{{% /alert %}}
  
## **Overview**
*Australia Post* is a 4-state postal symbology used in the Australian Post. In this barcode standard, input messages include specific 2-digit format control code (FCC) fields and 8-digit sorting code (SC) fields. FCC fields are used to indicate one of three available barcode types with different fixed lengths: 37, 52, or 67 bars. Depending on FCC, barcodes may contain a customer information (CI) field that identifies one of the encoding types that support numerical or alphanumeric symbols. Customer information can occupy 16 bars in 52-length barcodes or 31 bars in 67-length ones. The Australia Post standard contains a checksum and information used for Reed-Solomon data recovery.  
*See more details about this symbology [here](/barcode/net/postal-barcodes/#australia-post-symbology)*.  
  
Due to the possibility to add customer information in barcode input data, barcode recognition for *Australia Post* barcodes has some specifics. In ***Aspose.BarCode for C++***, developers can use class [*AustraliaPostSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/australiapostsettings) to customize recognition parameters for this barcode standard according to particular requirements. Further, the main properties of class [*AustraliaPostSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/australiapostsettings) are explained in detail.

## **Decode Customer Information in Standard Formats**
The *Australia Post* symbology allows encoding additional customer information in three different formats; automatic recognition of the format used for encoding is not possible. In ***Aspose.BarCode for C++***, the required decoding format can be set in the [*CustomerInformationInterpretingType*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/australiapostsettings/properties/customerinformationinterpretingtype) field that can take the following values as explained in the table below.
  
|Australia Post Encoding Table|Supported Symbols|
|---|---|
|CTable|Numerical digits, English letters, space symbol, and #|
|NTable|Numerical digits|
|Other|0, 1, 2, and 3 that correspond to H, A, D, and T states, respectively|
  
**CTable**  
    
<p align="center"><img src="australiapostctable.png"></p>

**NTable**  
  
  
<p align="center"><img src="australiapostntable.png"></p>

**Other**  
  
  
<p align="center"><img src="australiapostother.png"></p>

## **Remove Filling Patterns**
The *Australia Post* standard imposes using fixed size for each subtype. When barcode decoding is performed in the *CTable* format, the data filling empty space in the input message is decoded as symbol “z”. To avoid such a result, it is necessary to set the [*IgnoreEndingFillingPatternsForCTable*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/australiapostsettings/properties/ignoreendingfillingpatternsforctable) property to *True*.  
  
  
<p align="center"><img src="australiapostctableignoreending.png"></p>

## **Decode Customer Information in Custom Format**
***Aspose.BarCode for C++*** allows developers to decode customer information in their own format. For this purpose, the library provides a special interface called [*CustomerInformationDecoder*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/australiapostsettings/properties/customerinformationdecoder). In such a way, decoding of barcode data is performed using this interface; the properties [*CustomerInformationInterpretingType*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/australiapostsettings/properties/customerinformationinterpretingtype
) and [*IgnoreEndingFillingPatternsForCTable*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/australiapostsettings/properties/ignoreendingfillingpatternsforctable) are ignored.  
  
  
<p align="center"><img src="australiapostcustomerinformationdecoder.png"></p>
