---
title: Set Barcode Checksum Verification
linktitle: Set Checksum Verification
type: docs
description: "This article describes how to set checksum verification in Aspose.BarCode for Java"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcode in Java"
weight: 40
url: /python-net/set-checksum-verification/
---

## **Overview**
Various 1D and postal types include checksum control mechanisms for data integrity verification. To adjust checksum settings for data validation purposes, class [*BarcodeSettings*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarcodeSettings) contains the [*ChecksumValidation*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/ChecksumValidation) enum. Generally, barcode types can be classified according to the following types: with obligatory checksum controls and with optional ones. The [*ChecksumValidation*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/ChecksumValidation) enum suggests different options for these two groups. The barcode recognition procedure varies in line with checksum settings.  

## **Checksum Validation for Barcodes with Obligatory Checksum**
Barcoded types with obligatory checksum controls require performing compulsive checksum validation when [*ChecksumValidation*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/ChecksumValidation) is initialized using *ChecksumValidation.DEFAULT* or *ChecksumValidation.ON* values. Alternatively, setting the *ChecksumValidation.Off* value turns off checksum verification and in this way, allows decoding information from invalid barcodes. This option increases the probability of incorrect recognition.  
  
  
<p align="center"><img src="code11.png"></p> 

## **Checksum Validation for Barcodes with Optional Checksum**
[*ChecksumValidation*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/ChecksumValidation) allows enabling and disabling checksum controls for barcode standards with optional checksum verification. To request checksum validation, the following setting should be used: *ChecksumValidation.ON*. When other options *ChecksumValidation.DEFAULT* and *ChecksumValidation.OFF* are enabled, checksum controls are disabled.  
  
  
<p align="center"><img src="code39.png"></p>
