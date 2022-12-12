---
title: Generate MaxiCode Barcodes
linktitle: MaxiCode
type: docs
weight: 80
url: /python-net/generate-maxicode-barcodes/
---
{{% alert color="primary" %}}[Generate MaxiCode Barcodes Online](https://products.aspose.app/barcode/generate/maxicode): You can test the quality of ***Aspose.BarCode*** generation for MaxiCode barcodes and view the results online.{{% /alert %}}

## **Overview**
*MaxiCode* is a 2D barcode type used to encode textual data and streams of bytes. *MaxiCode* barcodes contain special round bullseye finder patterns consisting of 3 circles, 6 orientation patterns, and 33 rows composed of 29 or 30 hexagonal modules. This barcode standard has been developed for postal services and is recommended for industrial tasks. Its encoding capacity may vary according to the properties of encoded information and may reach up to 60 bytes or 90 alphanumeric characters or 140 numerical digits. The *MaxiCode* symbology supports Reed-Solomon error correction.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Encoding Modes**
***Aspose.BarCode for Python via .NET*** supports several encoding modes for the *MaxiCode* type that can be managed using the *maxi_code_encode_mode* property of class [*MaxiCodeParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/maxicodeparameters/): 
- *Encoding Modes 2 and 3* - these specific industrial standards apply to the transportation industry and aim to encode shipping information
- *Encoding Modes 4 and 5* - these modes are used to encode arbitrary textual data or streams of bytes; they differ in terms of encoding capacity and the number of codewords reserved for error correction
- *Encoding Mode 6* - this mode is similar to *Encoding Mode 4*; however, barcode data is used only to program hardware readers

### **Encoding Modes 2 and 3**
To ensure appropriate barcode generation, input data for *Encoding Modes 2 and 3* needs to be organized using specific formats defined as follows:  
- <mark>Format1: “[)>(rs)01(gs)(Postal Code)(gs)(Country Code)(gs)(Service Category)(gs)(Secondary Message)(eot)”</mark>
- <mark>Format2: “(Postal Code 9 digits)(gs)(Country Code)(gs)(Service Category)(gs)(Secondary Message)(eot)”</mark>
  
The standard includes several special characters:
- Group separator Unicode symbol: (gs) - \u001d
- Record separator Unicode symbol: (rs) - \u001e
- End-of-transmission Unicode symbol: (eot) - \u0004
  
Following *MaxiCode* barcodes have been generated applying Formats 1 and 2 of *Encoding Mode 2*.
   
|Mode 2|Format 1|Format 2|
| :-: | :-: | :-: |
| |<img src="maxicodeencodemode2first.png" width="40%" height="40%">|<img src="maxicodeencodemode2second.png" width="40%" height="40%">|
  
  
### **Encoding Modes 4, 5, and 6**
*Encoding modes 4, 5, and 6* can be used to encode arbitrary textual data or streams of bytes.

<p align="center"><img src="maxicodeencodemode4.png" width="20%" height="20%"></p>

## **Aspect Ratio Settings**
*Aspect Ratio* is one of the most important parameters for barcode generation that is determined as the ratio between barcode height and width. The *aspect_ratio* property of class [*MaxiCodeParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/maxicodeparameters/) can be used to modify barcode proportions corresponding to X and Y coordinates. *Aspect Ratio* is defined as a relative coefficient to the *XDimension* value. For *MaxiCode* barcode generation, it is recommended to set the value of *Aspect Ratio* to 1. The following *MaxiCode* has been created with the *Aspect Ratio* equal to 0.5.
  
<p align="center"><img src="maxicodeaspectratio0.5.png" width="20%" height="20%"></p>
  
