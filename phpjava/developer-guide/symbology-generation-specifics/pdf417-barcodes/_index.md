---
title: Generate PDF417 Barcodes
type: docs
description: "Generate different types of PDF417 barcodes using Aspose.BarCode for PHP via Java"
keywords: "Generate PDF417 Barcodes, Create Macro PDF417 Barcode, How to Generate PDF417 barcodes, Aspose.BarCode for PHP"
ai_search_scope: "barcode_phpjava_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 50
url: /phpjava/generate-pdf417/
---
{{% alert color="primary" %}}[Generate PDF417 Barcodes Online](https://products.aspose.app/barcode/generate/pdf417): You can test the quality of ***Aspose.BarCode*** generation for PDF417 barcodes and get the results online.{{% /alert %}}

## **Overview**
*PDF417* is a family of 2D variable-length stacked barcode standards that enables laser scanning for documents of high quality (with the exception of *Compact PDF417*, which supports only photo scanning). The *PDF417* type provides smaller data density compared with matrix barcode types. However, it is several times larger than the data density of conventional 1D stacked barcode standards. *PDF417* barcodes can be used to encode streams of bytes or Unicode characters and contain recovery data required for Reed-Solomon error correction.  
  
One of the main specificities of *PDF417* types is that they support the special format of encoding metadata. This allows dividing a single document into several parts marked with barcode labels indicating file name, creation date, checksum control, and some other additional information. Thereafter, these parts can be transmitted one by one and reassembled together according to barcode markers. Adding metadata to barcodes occupies extra barcode capacity.  
  
The *PDF417* layout configuration is composed of multiple rows and columns. Basic *PDF417* can be used to encode at most 1,850 alphanumeric characters or 2,710 numerical digits or 1,108 bytes with the maximal configuration including 90 rows and 30 columns. In turn, the *Micro PDF417* type can encode up to 266 alphanumeric characters or 366 numerical digits or 150 bytes with the maximal configuration of 44 rows and 4 columns.  
  
|PDF417 Standard|Description|
|---|---|
|[**Basic PDF417**](#pdf417)|Can be used to work with documents of any quality and supports laser scanning|
|[**Micro PDF417**](#micropdf417)|Allows minimizing the barcode area and can be used as an add-on for GS1 composite symbologies or applied to high-quality documents|
|[**Macro PDF417**](#macropdf417)|Provides increased encoding capacity and supports metainformation|
|[**Compact PDF417**](#compactpdf417)|Supports optional metainformation and can be useful in cases of limited printing space. It suggests omitting the right-side block of metadata and removing the stop pattern is removed. Laser scanning is not supported; only photo scanning is available. It is applicable to high-quality documents only|
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/phpjava/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Basic PDF417 and Macro PDF417 Types**
*Basic PDF417* and *Macro PDF417* support the following configuration: from 1 to 30 columns to encode information; 2 columns to store metainformation (i.e. row indicator, layout information); start and stop patterns. It is possible to add from 3 to 90 rows. The key difference between *Basic PDF417* and *Macro PDF417* is that the latter supports metadata.
  
<p align="center"><img src="pdf417basic.png"></p>
  
<a name="pdf417"></a>
  
## **Micro PDF417 Type**
The layout of *Micro PDF417* supports adding from 4 to 44 rows and from 1 to 4 columns. Layout options are strictly predefined in terms of maximum and minimum numbers of rows and columns, as well as error correction codewords. Moreover, barcodes include two columns with metadata. Commonly, *Micro PDF417* is suggested for use in high-quality documents to ensure correct recognition. However, this type supports laser scanning. 

<p align="center"><img src="micropdf417basic.png"></p>
  
<a name="micropdf417"></a>

## **Compact PDF417 Symbology**
*Compact PDF417* has a specification like *Basic PDF417* and *Macro PDF417*. The difference is that in *Compact PDF417* barcodes, the right-side metainformation column and the corresponding stop pattern are eliminated to decrease barcode size. This is the only barcode type in the *PDF417* family that does not support laser scanning. It should be also noted that reading low-quality barcode images may have issues due to the lack of metainformation redundancy. To enable the *Compact PDF417* mode, developers can use the *setPdf417Truncate* function of class [*Pdf417Parameters*](https://reference.aspose.com/barcode/php/classPdf417Parameters).
  
<p align="center"><img src="compactpdf417basic.png"></p>
  
<a name="compactpdf417"></a>

## **PDF417 Encoding Modes**
To enable the required encoding mode for *PDF417* generation, it is necessary to call the *setPdf417CompactionMode* function of class [*Pdf417Parameters*](https://reference.aspose.com/barcode/php/classPdf417Parameters) that is intended to manage data compaction regimes. Two other functions, i.e. *setPdf417ECIEncoding* and *setCodeTextEncoding*, can be used to enable encoding modes suitable for Unicode symbols. In this article, it is described how to work with different encoding modes.

### **ECI Encoding Mode**
The *setPdf417ECIEncoding* function of class [*Pdf417Parameters*](https://reference.aspose.com/barcode/php/classPdf417Parameters) can be used to encode Unicode symbols to streams of bytes. Moreover, it allows determining an ECI identifier for the present encoding that can be detected and interpreted by decoders. When this function is called passing any value from the [*ECIEncodings*](https://reference.aspose.com/barcode/php/classECIEncodings) class besides *ECIEncodings.NONE*, information is processed using the determined ECI encoding. At present, ***Aspose.BarCode*** supports all widely used charset encodings included in the [*ECIEncodings*](https://reference.aspose.com/barcode/php/classECIEncodings) class.  
    
<p align="center"><img src="pdf417eciencoding.png"></p>
 
### **Compaction Mode**
Developers can enable the desired data compaction mode through the *setPdf417CompactionMode* function passing the value from the [*Pdf417CompactionMode*](https://reference.aspose.com/barcode/php/classPdf417CompactionMode) class.
  
|Compaction Mode|Description|
|---|---|
|**AUTO**|Automatically selects the data compaction mode with the highest data density. If barcode data contains a digit greater than 255, data compaction is performed with the specified encoding|
|**BINARY**|Encodes binary streams of bytes with digits from 0 to 255. If barcode data has a digit greater than 255, data compaction is conducted using the specified encoding|
|**NUMERIC**|Legacy mode for numerical digits. Using the *AUTO* mode is recommended|
|**TEXT**|Legacy mode for alphanumeric characters. Using the *AUTO* mode is recommended|

Following barcodes have been created applying various compaction modes.
  
|Compaction Mode|AUTO|BINARY|TEXT|NUMERIC|
| :-: | :-: | :-: | :-: | :-: |
| |<img src="pdf417compactionauto.png">|<img src="pdf417compactionbinary.png">|<img src="pdf417compactiontext.png">|<img src="pdf417compactionnumeric.png">|
  
   
### **Unicode Encoding Mode**
Unicode characters can be encoded using the *setCodeTextEncoding* function. 
  
<p align="center"><img src="pdf417codetextencoding.png"></p>
  
### **Encoding Streams of Bytes in Binary Mode**
Developers can encode and transmit an array of bytes through the *BINARY* mode that can be enabled through the *setPdf417CompactionMode* function of class [*Pdf417Parameters*](https://reference.aspose.com/barcode/php/classPdf417Parameters). To show the text line under a barcode, the *setTwoDDisplayText* function must be called. 
  
<p align="center"><img src="pdf417bytesencoding.png"></p>
  
## **Layout Configuration Settings**
Developers can define the required layout configuration for *PDF417* generation using dedicated function of class [*Pdf417Parameters*](https://reference.aspose.com/barcode/php/classPdf417Parameters), i.e. *setRows* and *setColumns*. All *PDF417* standards besides *Micro PDF417* may have the following configuration settings: from 1 to 30 columns and from 3 to 90 rows. The number of rows and columns can be defined separately. The layout of *Micro PDF417* allows adding from 1 to 4 columns.  
  
Following *PDF417* barcodes have different layout configurations.

|Layout Configuration|2 Columns|6 Rows|9 Rows and 6 Columns|
| :-: | :-: | :-: | :-: |
| |<img src="pdf417columns2.png">|<img src="pdf417row6.png">|<img src="pdf417row9columns4.png">|
  

## **Managing Error Correction Level**
The *PDF417* barcode family supports Reed-Solomon error correction to provide data recovery and integrity check. *Micro PDF417* enables determining the size of redundant recovery data automatically. Other *PDF417* standards allow customizing the error correction level through the *setPdf417ErrorLevel* function of class [*Pdf417Parameters*](https://reference.aspose.com/barcode/php/classPdf417Parameters). Each additional pair of error correction codewords serves to recover one unknown error or two known missing digits. A higher error correction level requires storing more codewords and enables more efficient data recovery for damaged barcodes. The maximal level of error correction, i.e. *Level8*, means that 265 errors can be corrected. However, data encoding capacity will decrease by 614 bytes. Available error correction levels are represented in the following table.  
  
|Error Correction Level**|Number of Codewords|Error Correction Level|Number of Codewords|
| :-: | :-: | :-: | :-: |
|**Level 0**|2 codewords|**Level 5**|64 codewords|
|**Level 1**|4 codewords|**Level 6**|128 codewords|
|**Level 2**|8 codewords|**Level 7**|256 codewords|
|**Level 3**|16 codewords|**Level 8**|512 codewords|
|**Level 4**|32 codewords| |
  
Following *PDF417* barcodes have different error correction levels.  
  
|Error Correction Level|Is Set to 2|Is Set to 5|
| :-: | :-: | :-: |
| |<img src="pdf417errorlevel2.png">|<img src="pdf417errorlevel5.png">|
  
 
## **Aspect Ratio Settings**
*Aspect Ratio* is one of the main parameters used to manage barcode proportions along X and Y coordinates. *Aspect Ratio* can be determined as the ratio between barcode height and width or as the relative coefficient to the *XDimension* value. Its value can be modified through the *setAspectRatio* function of class [*Pdf417Parameters*](https://reference.aspose.com/barcode/php/classPdf417Parameters). To generate *PDF417* barcodes, it is recommended to select the value of *AspectRatio* between 3 and 5.

Following *PDF417* barcodes have been generated with different aspect ratio values.  
  
|Aspect Ratio|Is Set to 2|Is Set to 5|
| :-: | :-: | :-: |
| |<img src="pdf417aspectratio2.png">|<img src="pdf417aspectratio5.png">|
  
## **Working withPDF417 Metadata**
*Micro PDF417* and *Macro PDF417* allow adding special metainformation about barcode data. Such metadata can be encoded together with main barcode information sharing the same blocks of data. It is possible to classify barcode metadata into permanent data and optional data as clarified further. All functions mentioned below correspond to class [*Pdf417Parameters*](https://reference.aspose.com/barcode/php/classPdf417Parameters).

<a name="macropdf417"></a>

### **Permanent Metadata**
Permanent metadata can be used to encode different special parameters using the functions listed below.
  
|Permanent Metadata Functins|Description|
|---|---|
|*setPdf417MacroFileID*|Manually adjusted unique identifier used for a series of barcodes or a PDF417 file|
|*setPdf417MacroSegmentID*|Identifier of the current barcode segment starting from 0. It is often used together with the *setPdf417MacroSegmentsCount* function that allows setting the number of barcodes in a series|
  
<p align="center"><img src="macropdf417permanent.png"></p>

### **Optional Metadata**
Optional metadata are used to store information about various data properties that can be encoded through special functions described below.
  
|Optional Metadata Functions|Description|
|---|---|
|*setPdf417MacroSegmentsCount*|Amount of barcodes in a series|
|*setPdf417MacroFileName*|File name|
|*setPdf417MacroChecksum*|Barcode checksum ocomputed based on the CCITT-16 polynomial|
|*setPdf417MacroFileSize*|Overall size of bytes in a barcode series|
|*setPdf417MacroTimeStamp*|Time spent to generate/send a file|
|*setPdf417MacroAddressee*|File sender address|
|*setPdf417MacroSender*|File sender name|
  
<p align="center"><img src="macropdf417optional.png"></p>
  
### **Unicode Metadata**
In ***Aspose.BarCode for PHP via Java***, it is possible to re-encode optional metadata using the Unicode encoding through the *setPdf417MacroECIEncoding* function of class [*Pdf417Parameters*](https://reference.aspose.com/barcode/php/classPdf417Parameters). This function is intended to perform the conversion of metadata and send it along with the related encoding identifier. 

<p align="center"><img src="macropdf417eciencoding.png"></p>
  
## **Setting Special Parameters**
The barcode library allows encoding specific control parameters for *PDF417* barcodes, i.e. hardware reader initialization and emulation for the *Code 128* type. 

### **Hardware Reader Initialization**
The *setReaderInitialization* function of class [*Pdf417Parameters*](https://reference.aspose.com/barcode/php/classPdf417Parameters) that allows encoding the special flag used to indicate that barcode data will serve for hardware reader initialization. 

<p align="center"><img src="pdf417readerinitialization.png"></p>

### ***Code 128* Emulation**
In some cases, it may be necessary to make hardware readers emulate information encoded in *Micro PDF417* barcodes in the format of *Code 128* barcode data. This can be done by calling the *setCode128Emulation* function of class [*Pdf417Parameters*](https://reference.aspose.com/barcode/php/classPdf417Parameters) and passing the required value from the [*Code128Emulation*](https://reference.aspose.com/barcode/php/classCode128Emulation) class. This function is applicable to *Micro PDF417* barcodes only. 

<p align="center"><img src="pdf417code128emulation.png"></p>
