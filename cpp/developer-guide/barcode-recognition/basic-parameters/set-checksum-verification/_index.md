---
title: Set Barcode Checksum Verification
linktitle: Set Checksum Verification
type: docs
description: "This article describes how to set checksum verification in Aspose.BarCode for C++"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcode C++"
ai_search_scope: "barcode_cpp_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 40
feedback: BARCODECOM
url: /cpp/set-checksum-verification/
---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
In many 1D and postal symbologies, data integrity verification and decoding are based on checksum control mechanisms. Class *BarcodeSettings* provides the *ChecksumValidation* property that is used to manage checksum settings for data validation and decoding. In general, barcode standards can be divided into two groups: those with obligatory checksum and those with optional one. Depending on this, the *ChecksumValidation* field can take different values; hence, the barcode recognition process will change according to particular checksum settings.  

## **Checksum Validation for Barcodes with Obligatory Checksum**
Symbologies with obligatory checksum always require performing checksum control when the *ChecksumValidation* property is set to *ChecksumValidation.Default* or *ChecksumValidation.On*. Otherwise, this parameter can take the value *ChecksumValidation.Off* that disables checksum controls for barcode type with obligatory checksum and thus allows reading data from incorrectly generated barcodes. However, in this case, the probability of inaccurate recognition increases considerably.  
  
  
<p align="center"><img src="code11.png"></p> 

## **Checksum Validation for Barcodes with Optional Checksum**
For symbologies with optional checksum control, *ChecksumValidation* can be set in such a way to enable checksum checking, namely, it needs to take the value *ChecksumValidation.On*. Otherwise, when the values *ChecksumValidation.Default* and *ChecksumValidation.Off* are used, checksum validation is omitted.  
  
  
<p align="center"><img src="code39.png"></p>

