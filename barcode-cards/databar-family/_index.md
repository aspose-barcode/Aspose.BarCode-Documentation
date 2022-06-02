---
title: DataBar Family
description: ""
key words: ""
type: docs
weight: 70
url: /databar-barcode-cards/
---

The DataBar symbology group was introduced at the beginning of the 2000s as a part of the GS1 group of standards. Its purpose was to mitigate the problems associated with the use of linear barcode types developed in the 70s. It was also necessary to keep the most important feature of 1D barcodes, namely, laser scanning capability.
The GS1 DataBar can carry all 14 digits of a manufacture’s GTIN and is more than 50% smaller than the currently used UPC and EAN symbols. This makes it particularly useful for identifying small/hard-to-mark items such as produce and pharmaceutical items. DataBar barcode types can be divided into two main groups: continuous and stacked. DataBar subtypes differ from each another in terms of space-saving strategies, encoding capacity, and barcode structure.

The DataBar standard includes the following barcode types: 
- [DataBar Omnidirectional / DataBar Stacked Omnidirectional](/barcode/databar-omnidirectional-card/)
- [DataBar Truncated / DataBar Stacked](/barcode/databar-truncated-card/)
- [DataBar Expanded / DataBar Expanded Stacked](/barcode/databar-expanded-card/)
- [DataBar Limited](/barcode/databar-limited-card/)
  
All DataBar barcode types except DataBar Limited can be generated both in two-row or multiple-row (up to 10 rows) configurations. This feature serves to customize the barcode layout in the case of limited horizontal space. DataBar has been introduced to encode GS1 identification codes for trade items (i.e. Application Identifiers, see more in [GS1 Barcodes](/barcode/net/generating-barcodes-using-new-barcode-generation-api/)). As they can encode large amounts of information in small barcode labels, these symbologies are often used for small item tracking, i.e. in retail, healthcare, food, and pharmaceutical industries. 
  
DataBar can be used to encode trade identifiers defined as Global Trade Item Number (GTIN) using GTIN12, GTIN13, and GTIN14 digital formats using the 14-digit data structure (with the exception of DataBar Expanded and Expanded Stacked that can use any of GTIN formats). Additionally, the GS1 DataBar symbol can carry GS1 Application Identifiers which allow additional information such as serial numbers, lot numbers, and expiration dates to be encoded. The greater dimensional efficiency combined with the ability to encode additional data opens the doors for creating trade solutions that greater support product identification, traceability, quality control, and more flexible coding for coupon applications.  
The specification for the DataBar group is provided in standard ISO/IEC 24724. 
  
|DataBar Examples| | | |
| :-: | :-: | :-: | :-: |
| |<img src="databaraspectratio15.png">|<img src="databarrows3.png">|