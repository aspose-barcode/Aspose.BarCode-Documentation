---
title: Barcode Reading Settings
type: docs
description: "This article describes how to adjust various barcode recognition settings in Aspose.BarCode for Python according to business needs"
keywords: Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcodes in Python
ai_search_scope: "barcode_python-net_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 20
url: /python-net/barcode-reading-settings/
---
 
## **Overview**
In the barcode recognition process implemented in ***Aspose.BarCode for Python via .NET***, barcode data decoding is initiated according to the special protocol after scanning the raw data from a graphical representation. Some linear and postal barcode types have passed standardization after their wide implementation, and therefore, it has led to the presence of incompatible decoding formats. To resolve possible conflicts, class [*BarCodeReader*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/) provides a special class called [*BarcodeSettings*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodesettings/) used to manage barcode decoding settings.


{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Checksum Verification**
Various 1D and postal types include checksum control mechanisms for data integrity verification. To adjust checksum settings for data validation purposes, class [*BarcodeSettings*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/) contains the [*ChecksumValidation*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/checksumvalidation/) enum. Generally, barcode types can be classified according to the following types: with obligatory checksum controls and with optional ones. The [*ChecksumValidation*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/checksumvalidation/) enum suggests different options for these two groups. The barcode recognition procedure varies in line with checksum settings.  

### **Checksum Validation for Barcodes with Obligatory Checksum**
Barcoded types with obligatory checksum controls require performing compulsive checksum validation when [*ChecksumValidation*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/checksumvalidation/) is initialized using *ChecksumValidation.DEFAULT* or *ChecksumValidation.ON* values. Alternatively, setting the *ChecksumValidation.OFF* value turns off checksum verification and in this way, allows decoding information from invalid barcodes. This option increases the probability of incorrect recognition.  

### **Checksum Validation for Barcodes with Optional Checksum**
[*ChecksumValidation*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/checksumvalidation/) allows enabling and disabling checksum controls for barcode standards with optional checksum verification. To request checksum validation, the following setting should be used: *ChecksumValidation.ON*. When other options *ChecksumValidation.DEFAULT* and *ChecksumValidation.OFF* are enabled, checksum controls are disabled.  

## **Managing Barcodes with Unicode Encodings**
***Aspose.BarCode for Python via .NET*** provides class [*BarcodeSettings*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodesettings/) that contains the *detect_encoding* that enables the automatic recognition of UTF8 and UTF16 Unicode encodings for 2D types and allows re-encoding barcode information into a string with Unicode characters. If this recognition mode is turned off, barcode information can be scanned and decoded manually based on the desired encoding.  

## **FNC Symbols**
The GS1 association suggests using FNC characters to decode some barcode types, including *Code 128* and *Code 128*. Four types of FNC symbols (FNC1-4) are supported. FNC1 is the most widely used one that is intended for GS1 Application Identifier (AI) marking. When a barcode does not relate to any of GS1 types (e.g. *Code 128* or *GS1 Code 128*), the decoder processes FNC symbols as *<FNC#>*. These symbols can be removed from decoding results by passing the *False* value to the *strip_fnc* property.  

## **Australia Post Barcodes**
*Australia Post* is a 4-state postal barcode type implemented by the Australian Post. This type requires special two-digit format control code (FCC) fields and eight-digit sorting code (SC) fields as barcode information. FCC fields are intended to set one of three supported types with various fixed numbers of bars: 37, 52, or 67 bars. For some FCC, barcodes may comprise a customer information (CI) field that indicates one of the encoding types supporting numerical or alphanumeric characters. Customer information can take 31 bars in 67-length barcodes or 16 bars in 52-length ones. *Australia Post* barcodes have checksum controls and supports Reed-Solomon error correction.  
  
Because of the possible presence of customer information in barcode information for *Australia Post*, the recognition process has some peculiarities. ***Aspose.BarCode for Python via .NET*** provides class [*AustraliaPostSettings*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/australiapostsettings/) to manage recognition parameters according to specific industrial needs. 

### **Decoding Customer Information in Standard Formats**
The *Australia Post* standard enables encoding additional customer data in three formats; automatic detection of the used format is not supported. The desired decoding format can be enabled through the *customer_information_interpreting_type* property that can take different values explained in the table below.
  
|Australia Post Encoding Table|Supported Symbols|
|---|---|
|CTable|Numerical digits, English letters, space symbol, and #|
|NTable|Numerical digits|
|Other|0, 1, 2, and 3 that correspond to H, A, D, and T states|
  
### **Removal of Fill Patterns**
*Australia Post* barcodes require setting a fixed size for each subtype. When the *CTable* format is enabled, the empty space included in the input message is decoded as “z”. To disable this property, the *ignore_ending_filling_patterns_for_c_table* property needs to be called.  

### **Decoding Customer Information in Custom Format**
***Aspose.BarCode for Python via .NET*** allows decoding customer data in various specific formats. To do this, a special interface called [*AustraliaPostCustomerInformationDecoder*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/australiapostcustomerinformationdecoder/) is available. In this case, barcode data decoding is processed according to this interface; *customer_information_interpreting_type* and *ignore_ending_filling_patterns_for_c_table* settings are ignored.  
