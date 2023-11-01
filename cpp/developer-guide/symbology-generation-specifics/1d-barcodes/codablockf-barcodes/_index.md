---
title: Generate Codablock-F Barcodes in C++
linktitle: Codablock-F
type: docs
weight: 20
feedback: BARCODECOM
url: /cpp/codablockf-barcodes/
---
{{% alert color="primary" %}}[Generate Codablock-F Barcodes Online](https://products.aspose.app/barcode/generate/codablock?type=codablockf): You can check the quality of ***Aspose.BarCode*** generation for Codablock-F barcodes and view the results online.{{% /alert %}}

## **Overview**
*Codablock-F* is a multiple-row stacked symbology that allows generating barcodes composed of several *Code128* barcode labels. Using this symbology, it is possible to encode up to 2,725 characters setting the required number rows (from 2 to 44) so that each of them can contain from 4 to 62 digits. *Codablock-F* has two main advantages over basic *Code128*. First, it allows utilizing horizontal and vertical space more efficiently owing to flexible settings of barcode layout (the number of rows and columns). Second, it provides two check digits (based on the modulo 86 algorithm) for an entire message encoded in a *Codablock-F* barcode in addition to obligatory checksums that are calculated for each row composed of *Code128* barcodes. Moreover, *Codablock-F* can be read by laser scanners.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
  
## **Barcode Height Settings**
In ***Aspose.BarCode for C++***, developers can set the height of each row in a stacked barcode by initializing the *AspectRatio* property of class *CodablockParameters*. This parameter is defined as a relative coefficient to the value of the *XDimension* property. It is recommended to set the value of *AspectRatio* greater than 10.  
  
Barcode labels demonstrated below have been generated with different aspect ratio settings. 
  
|Aspect Ratio|Is Set to 15|Is Set to 30|
| :-: | :-: | :-: |
| |<img src="codablockfaspectratio15.png">|<img src="codablockfaspectratio30.png">|
    

## **Layout Settings**
To set the layout of *Codablock-F* barcodes by defining the number of rows and columns, it is necessary to initialize *Columns* and *Rows* properties of class *CodablockParameters* where the former is the most significant parameter. The maximal values of these properties are limited to 62 and 44 for *Columns* and *Rows*, respectively.  
  
The barcode images provided below have been generated with different layout settings.
  
|Layout Settings|4 Columns|4 Rows|6 Rows and 4 Columns|
| :-: | :-: | :-: | :-: | :-: |
| |<img src="codablockfcol4.png">|<img src="codablockfrow4.png">|<img src="codablockfrow6col4.png">|
  
