---
title: Generate Codabar Barcodes in C++
linktitle: Codabar
type: docs
ai_search_scope: "barcode_cpp_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 10
feedback: BARCODECOM
url: /cpp/codabar-barcodes/
---
{{% alert color="primary" %}}[Generate Codabar Barcodes Online](https://products.aspose.app/barcode/generate/codabar): You can test the quality of ***Aspose.BarCode*** generation for Codabar barcodes and get the results online.{{% /alert %}}

## **Overview**
***Aspose.BarCode for C++*** enables generating barcode labels according to the *Codabar* standard that supports encoding numerical digits and six punctuation signs. The number of digits to be encoded in a barcode is unlimited. A *Codabar* barcode may contain four optional alphabet characters (usually, A, B, C, or D) that are used as start and stop digits. In this way, the symbology provides four types of start characters and four types of stop ones. Accordingly, for the same information to be encoded, it allows generating 16 barcodes with different service sets of start and stop characters.  
  
Input text in *Codabar* barcodes has the following format:  
<p align="center"><mark>[Start Character "A/B/C/D"] [Data Digits from the charset: "0-9" and "–$./:+"] [Stop Character "A/B/C/D"]</mark></p>
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
  
## **Start and Stop Symbols**
The library allows encoding start and stop characters independently with any of four supported formats: A, B, C, or D. To set the required format, it is necessary to initiate *CodabarStartSymbol* and *CodabarStopSymbol* properties included in the *Codabar* group of parameters of class *BarcodeParameters*.  
By default, start and stop characters are set to "A".  
  
Sample barcode labels demonstrated below have been generated with different settings for start and stop characters.
  
|Start and Stop Characters|A+A|B+B|C+C|D+D|
| :-: | :-: | :-: | :-: | :-: |
| |<img src="codabarstartastopa.png">|<img src="codabarstartbstopb.png">|<img src="codabarstartcstopc.png">|<img src="codabarstartdstopd.png">|
  
  
## **Checksum Settings**
By default, the *Codabar* symbology does not require using an obligatory checksum; however, it supports two checksum calculation algorithms: Mod10 and Mod16 (the most widely used one). The pseudocode provided below illustrates how these two checksum standards can be implemented.  
  
To enable a checksum for this barcode type, it is necessary to initialize the *IsChecksumEnabled* property by setting the mode *EnableChecksum.Yes* and define the required checksum algorithm in the *CodabarChecksumMode* property. By default, the *Mod16* checksum is applied.  
  
*Codabar* barcode images provided below have been created with different checksum calculation settings.

|Checksum Calculation|Is Set to *None*|Is Set to *Mod10*|Is Set to *Mod16*|
| :-: | :-: | :-: | :-: |
| |<img src="codabarchecksumnone.png">|<img src="codabarchecksummod10.png">|<img src="codabarchecksummod16.png">|
  
