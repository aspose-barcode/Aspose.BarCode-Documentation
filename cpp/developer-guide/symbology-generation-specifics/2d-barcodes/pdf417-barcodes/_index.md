---
title: Generate PDF417 Barcodes in C++
linktitle: PDF417
type: docs
feedback: BARCODECOM
description: "Aspose.BarCode for C++ can be used to generate different types of PDF417 barcodes"
keywords: "Generate PDF417 Barcode, Create Macro PDF417 Barcode, How to Generate PDF417 barcodes, Aspose.BarCode for C++"
ai_search_scope: "barcode_cpp_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 50
url: /cpp/pdf417-barcodes/
aliases:
- /cpp/pdf417-and-macropdf417-barcode/
---

{{% alert color="primary" %}}[Generate PDF417 Barcodes Online](https://products.aspose.app/barcode/generate/pdf417): You can test the quality of ***Aspose.BarCode*** generation for PDF417 barcodes and get the results online.{{% /alert %}}

## **Overview**
*PDF417* is a group of 2D variable-length stacked symbologies that are similar to matrix barcodes in terms of various parameters. This standard supports laser scanning for high-quality documents (except *Compact PDF417* that requires photo scanning). *PDF417* barcodes have data density that is lower than that of matrix symbologies but several times greater compared to basic 1D stacked barcode types. *PDF417* standards enable encoding both byte streams and Unicode symbols. Moreover, *PDF417* barcodes include additional information for data recovery through Reed-Solomon error correction.  
  
The other peculiarity of the *PDF417* barcode family is the extended format of representing metadata so that one file can be divided into several barcodes and then transmitted on a printed document indicating file date, name, checksum, and other information. However, metadata require additional space in a barcode image. The layout of *PDF417* barcodes includes rows and columns. The basic *PDF417* standard can encode up to 1,108 bytes or 1,850 alphanumeric (2,710 numerical) symbols in up to 30 columns and 90 rows while *Micro PDF417* is capable of encoding at most 150 bytes of data or 266 alphanumeric (366 numerical) characters in up to 4 columns and 44 rows.  
  
|<p align="center">**PDF417 Standard**</p>|<p align="center">**Description**</p>|
|---|---|
|[**Basic PDF417**](#pdf417)|Basic *PDF417* that is intended for work with documents of any quality and provides the possibility of laser scanning|
|[**Micro PDF417**](#micropdf417)|Specialized *PDF417* standard that allows saving print space and is intended for joint use with two-component barcodes based on GS1 composite symbologies or for work with high-quality documents|
|[**Macro PDF417**](#macropdf417)|*PDF417* barcode type with the possibility to add metainformation|
|[**Compact PDF417**](#compactpdf417)|*PDF417* standard that can be with or without metainformation and is intended to address space limitations; in such barcodes, the right-side block of metadata is omitted, and the stop pattern is removed. This barcode type does not support laser scanning (only photo scanning can be used) and requires high-quality documents for successful recognition|
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **PDF417 and Macro PDF417**
*PDF417* and *Macro PDF417* barcodes may contain from 1 to 30 columns with input data, 2 columns with auxiliary metainformation (such as row indicator, the number of rows and columns) and then, start and stop patterns. The number of rows can vary from 3 to 90. The main distinction between *Macro PDF417* and *Basic PDF417* is the possibility to encode additional metadata about barcode contents. This redundancy associated with auxiliary metadata allows reading such barcodes using laser scanners as well as reducing barcode image quality requirements. The specificities of using *Macro PDF417* in ***Aspose.BarCode for C++*** are discussed further in the corresponding [**subsection**](#macropdf417).
  
<p align="center"><img src="pdf417basic.png"></p>
  
## **Micro PDF417**
*Micro PDF417* can include from 1 to 4 columns and from 4 to 44 rows; the maximal and minimal numbers of rows depend on the number of columns according to the predefined combinations of rows, columns, and error correction codewords. In addition, each barcode contains two columns with metadata that serve as targets for barcode location in an image. In general, *Micro PDF417* is used for work with high-quality documents due to barcode recognition difficulties; at the same time, these barcodes can be read by laser scanners. 

<p align="center"><img src="micropdf417basic.png"></p>
  

## **Compact PDF417**
The specification of *Compact PDF417* is similar to those of *Basic PDF417* and *Macro PDF417*; however, the right-side metainformation column and the right-side stop pattern are removed to save space for small-sized barcodes. This symbology does not support laser scanning; moreover, due to the absence of metainformation redundancy, it has difficulties with low-quality barcode image recognition. To set the *Compact PDF417* generation mode in ***Aspose.BarCode for C++***, it is necessary to initialize the *Pdf417Truncate* property of class *Pdf417Parameters*.
  
<p align="center"><img src="compactpdf417basic.png"></p>
  

## **PDF417 Data Encoding Modes**
To select the data encoding mode in ***Aspose.BarCode for C++***, it is required to set the *Pdf417CompactionMode* property of class *Pdf417Parameters* that specifies data compaction regimes to be used during barcode generation. To encode Unicode symbols, two other properties, *Pdf417ECIEncoding* and *CodeTextEncoding*, can be used. Detailed explanations and code samples for these properties are provided further in the article.

### **ECI Encoding Mode**
Besides encoding Unicode characters into byte streams, the *Pdf417ECIEncoding* property allows setting the ECI identifier for the current encoding that can be read and correctly interpreted by decoders. In the case of setting this property using any value that differs from *ECIEncodings.NONE*, data processing is performed using the specified ECI encoding. The present library implementation includes all well-known charset encodings that are listed in the *ECIEncodings* enumeration.  
  
  
<p align="center"><img src="pdf417eciencoding.png"></p>
  
### **Compaction Mode**
As mentioned above, to select the required data compaction way, the *Pdf417CompactionMode* property needs to be initialized using one of the supported compaction modes are described below.
  
|Compaction Mode|Description|
|---|---|
|**Auto**|Encoding is performed in the most high-density data compaction mode that is selected automatically. In the case when *CodeText* contents include a digit greater than 255, data compaction is executed using the encoding specified in *CodeTextEncoding*|
|**Binary**|This mode is intended to encode binary byte streams with digits from 0 to 255. If *CodeText* contains a digit greater than 255, data compaction is performed using the encoding set in *CodeTextEncoding*|
|**Text**|Legacy mode to encode alphanumeric data. It is recommended to use the *Auto* mode|
|**Numeric**|Legacy mode to encode numerical digits. It is recommended to use the *Auto* mode|
  
Barcode images demonstrated below have been generated using different compaction mode settings.
  
|Compaction Mode|***Auto***|***Binary***|***Text***|***Numeric***|
| :-: | :-: | :-: | :-: | :-: |
| |<img src="pdf417compactionauto.png">|<img src="pdf417compactionbinary.png">|<img src="pdf417compactiontext.png">|<img src="pdf417compactionnumeric.png">|
  
    
### **Unicode Encoding Mode**
The *CodeTextEncoding* property can be used to encode Unicode characters in the *Binary* mode.
  
  
<p align="center"><img src="pdf417codetextencoding.png"></p>
  
### **Byte Stream Encoding in Binary Mode**
When it is needed to encode and transmit an array of bytes in a barcode, developers can use the *Binary* mode that can be set in ***Aspose.BarCode for C++*** using the *Pdf417CompactionMode* property of class *Pdf417Parameters*. To display the custom text under a barcode, the *TwoDDisplayText* property needs to be set.
  
  
<p align="center"><img src="pdf417bytesencoding.png"></p>
  
## **Barcode Layout Settings**
To set the number of rows and columns in *PDF417* barcodes, ***Aspose.BarCode for C++*** enables the corresponding properties of class *Pdf417Parameters* that are called *Rows* and *Columns*. *Basic PDF417*, *Macro PDF417*, and *Micro PDF417* standards allow arbitrarily set the number of columns from 1 to 30 and the number of rows from 3 to 90. The number of rows and columns can be set independently. In turn, *Micro PDF417* supports setting from 1 to 4 columns so that the maximal and minimal numbers of rows depend on the number of columns. In case if the barcode type capacity is insufficient to generate a barcode with the requested number of rows and columns, an exception will be thrown.  
  
*PDF417* barcode images provided below have been generated using different layout settings.

|Layout Settings|2 Columns|6 Rows|9 Rows and 6 Columns|
| :-: | :-: | :-: | :-: |
| |<img src="pdf417columns2.png">|<img src="pdf417row6.png">|<img src="pdf417row9columns4.png">|
  

## **Error Correction Level Settings**
The *PDF417* barcode family applies the Reed-Solomon error correction mechanism to perform data recovery and integrity check. In *Micro PDF417* barcodes, the amount of redundant recovery information is defined automatically. To set the error correction level for *Basic PDF417*, *Macro PDF417*, and *Compact PDF417* in ***Aspose.BarCode for C++***, developers can use the *Pdf417ErrorLevel* property of class *Pdf417Parameters*. Adding each two error correction (EC) codewords allows recovering one unknown error or two known character removals. The higher is the EC level, the larger is the number of EC codewords in a barcode and accordingly, the better is the result of data recovery for severely damaged barcode images. The maximal *Level8* implies that 265 errors can be corrected; at the same time, the barcode encoding capacity will be reduced by 614 bytes. All supported EC levels are listed below.  
  
|EC Level|Number of EC Codewords|Error Correction Level|Number of EC Codewords|
| :-: | :-: | :-: | :-: |
|**Level 0**|2 EC codewords|**Level 5**|64 EC codewords|
|**Level 1**|4 EC codewords|**Level 6**|128 EC codewords|
|**Level 2**|8 EC codewords|**Level 7**|256 EC codewords|
|**Level 3**|16 EC codewords|**Level 8**|512 EC codewords|
|**Level 4**|32 EC codewords| |
  
*PDF417* barcode images shown below have been created using different error correction level settings.  
  
|Error Correction Level|Is Set to 2|Is Set to 5|
| :-: | :-: | :-: |
| |<img src="pdf417errorlevel2.png">|<img src="pdf417errorlevel5.png">|
  
  
## **Aspect Ratio Settings**
*Aspect Ratio* is defined as the ratio between the barcode width and height. In ***Aspose.BarCode for C++***, to customize barcode proportions using the X and Y coordinates, the *AspectRatio* property of class *Pdf417Parameters* can be used. It is implemented as a relative coefficient to the value of the *XDimension* parameter. For *PDF417* barcodes, the value of *AspectRatio* should be set between 3 and 5.

*PDF417* barcodes demonstrated below have been created using different aspect ratio settings.  
  
|Aspect Ratio|Is Set to 2|Is Set to 5|
| :-: | :-: | :-: |
| |<img src="pdf417aspectratio2.png">|<img src="pdf417aspectratio5.png">|
  

## **PDF417 Metadata Encoding**
*Macro PDF417* and *Micro PDF417* standards enable encoding additional metainformation about data origins and identification. These metadata are encoded in barcodes along with main input information and occupy the same data blocks. Metadata can be classified into permanent and optional ones that are explained further.
<a name="macropdf417"></a>

### **Permanent Metadata Settings**
Permanent metadata that determine encoding the rest of the fields include the following parameters.

|Permanent Metadata Field|Description|
|---|---|
|*Pdf417MacroFileID*|Unique identifier of a barcode series or PDF417 file that is set manually|
|*Pdf417MacroSegmentID*|Current segment identifier that starts with 0 and often is accompanied with an optional field called *Pdf417MacroSegmentsCount* that specifies the number of barcodes in a series|


<p align="center"><img src="macropdf417permanent.png"></p>

### **Optional Metadata Settings**
Optional metadata include various fields that are listed in the table below.
  
|Optional Metadata Field|Description|
|---|---|
|*Pdf417MacroSegmentsCount*|Number of barcodes in a series|
|*Pdf417MacroFileName*|Name of a file|
|*Pdf417MacroChecksum*|Checksum of a file that is calculated using CCITT-16 polynomial|
|*Pdf417MacroFileSize*|Total size of bytes in a series|
|*Pdf417MacroTimeStamp*|Time of creating/sending the file|
|*Pdf417MacroAddressee*|Address of the file sender|
|*Pdf417MacroSender*|Name of the file sender|
    
<p align="center"><img src="macropdf417optional.png"></p>
  
### **Unicode Metadata Settings**
If required, it is possible to transmit optional metadata fields in the Unicode encoding by initializing the *Pdf417MacroECIEncoding* property that converts the data and sends it together with the corresponding encoding identifier. 
  
<p align="center"><img src="macropdf417eciencoding.png"></p>
  
## **PDF417 Special Parameters**
For the *PDF417* barcode family, ***Aspose.BarCode for C++*** allows encoding special control parameters, such as indicating hardware reader initialization and *Code 128* emulation. 

### **Hardware Reader Initialization**
To encode the special flag indicating that the barcode data is intended for hardware reader initialization, developers can use the *IsReaderInitialization* property. 

<p align="center"><img src="pdf417readerinitialization.png"></p>

### ***Code 128* Emulation**
To indicate that hardware readers must emulate the considered *Micro PDF417* barcode as the data read from a *Code 128* barcode, the *Code128Emulation* field needs to be initialized. 
  

<p align="center"><img src="pdf417code128emulation.png"></p>
