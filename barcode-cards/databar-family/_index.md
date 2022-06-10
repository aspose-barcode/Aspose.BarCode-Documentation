---
title: DataBar Family
description: "Overview of the DataBar Barcode Family"
keywords: "DataBar, data bar barcode, databar barcode type, Create databar barcodes, databar stacked, Read databar codes, what is databar, databar stacked barcodes, generate databar barcode, matrix barcodes, 1D barcodes, stacked linear barcodes, gs1, gs1 barcodes, gs1 databar, databar generator, databar reader, recognise data bar codes, scan databar barcode, databar family, databar expanded, databar limited, databar truncated"
type: docs
weight: 70
url: /info-cards/databar-family/
---

The DataBar barcode group was introduced at the beginning of the 2000s as a part of the GS1 group of standards. Its purpose was to mitigate the problems associated with the use of linear barcode types developed in the 70s. It was also necessary to keep the most important feature of 1D barcodes, namely, laser scanning capability.
DataBar is intended to store trade identification codes, i.e., Global Trade Item Number (GTIN), and allows producing barcode labels that are over 50% more compact compared with UPC and EAN barcodes.  
DataBar has been introduced to encode GS1 identification codes for trade items (i.e. Application Identifiers, see more in [GS1 Barcodes](/barcode/net/generating-barcodes-using-new-barcode-generation-api/)). As it can encode large amounts of information in relatively compact barcode labels, this barcode specification is often applied to the tasks of tracking small items in various industries, such as healthcare, food, retail, and pharmaceutical. DataBar barcode types can be classified into two main groups: continuous and stacked. DataBar subtypes differ from each other in terms of space-saving approaches, encoding capacity, and structure.

The DataBar specification includes the following subtypes: 
- [DataBar Omnidirectional / DataBar Stacked Omnidirectional](/barcode/info-cards/databar-omnidirectional/)
- [DataBar Truncated / DataBar Stacked](/barcode/info-cards/databar-truncated/)
- [DataBar Expanded / DataBar Expanded Stacked](/barcode/info-cards/databar-expanded/)
- [DataBar Limited](/barcode/info-cards/databar-limited/)
  
All DataBar subtypes except DataBar Limited can be generated both using two-row or multiple-row (up to 10 rows) configurations. This feature allows customizing the barcode layout in the case of limited horizontal space. DataBar can be applied to encode trade identifiers defined as Global Trade Item Number (GTIN) in GTIN-12, GTIN-13, and GTIN-14 digital formats using the 14-digit data structure (with the exception of DataBar Expanded and Expanded Stacked that support any of GTIN formats). DataBar barcodes can store GS1 Application Identifiers, which represent supplementary information, such as serial numbers, expiration dates, and others. The improved capacity together with the capability to store additional information enables creating item tracking solutions to facilitate product identification, tracking, quality management, and the development of loyalty programs.  
The specification for the DataBar group is provided in standard ISO/IEC 24724. 

|DataBar Examples| | | |
| :-: | :-: | :-: | :-: |
| |<img src="databaraspectratio15.png" alt="DataBar Barcode Sample 1">|<img src="databarrows3.png" alt="DataBar Barcode Sample 2">|
  
{{% alert color="primary" %}}You can find the detailed description of classes and properties that are used in ***Aspose.BarCode*** for DataBar generation and recognition:
- [**DataBar in Aspose.BarCode for .NET**](/barcode/net/databar-barcodes/)
