---
title: Set Barcode Checksum Controls in JavaScript
linktitle: Set Barcode Checksum Controls
type: docs
weight: 80
feedback: BARCODECOM
description: How to Set Checksum for 1D Barcodes in JavaScript API"
keywords: Generate Barcodes, Barcode Checksum in Aspose.BarCode for JavaScript via C++, Generate Barcodes in Aspose.BarCode, Convert Barcode Size in Aspose.BarCode, Customized Barcode Checksum, Set Barcode Check Digit, Checksum Settings Aspose.BarCode
url: /javascript-cpp/set-checksum-controls/
---

## **Overview**
The **checksum** (or *check digit*) is an error detection mechanism used to verify the accuracy and integrity of information encoded in 1D barcodes. Checksums ensure that barcode data has not been corrupted or lost and that the barcode reading process has been completed correctly. Typically, a checksum is the last symbol in a barcode sequence, encoded as a standard character supported by the corresponding barcode type. 1D barcodes may include a checksum as an optional feature or as a mandatory part calculated using a specific algorithm. Barcode scanners calculate the checksum by performing mathematical operations on the digits preceding the checksum and comparing the result to the checksum value.

Some symbologies without an obligatory checksum use self-checking characters. Self-checking barcodes are resistant to errors since any modification in a character is detected, making the barcode unreadable. Two conflicting changes made simultaneously in a character and a scan line may result in an incorrect read, known as a substitution error. This can be avoided by implementing checksum controls.

{{% alert color="primary" %}}*For any clarifications, reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/). You can ask questions at the [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Definition of Checksum**
Most 1D barcode standards, developed in the 1970s, define the checksum as a simple sum of all preceding characters modulo the maximum index of the encoded characters. In contrast, the *DataBar* group of barcode standards, introduced in the early 2000s, uses a more complex checksum verification algorithm similar to modern data transmission protocols.

In ***Aspose.BarCode for JavaScript via C++***, enabling checksum for 1D barcodes helps verify barcodes with minor damages. However, if a barcode is significantly corrupted, the likelihood of incorrect reading increases.

Examples of checksum calculations and settings for *Code 39* and *Code 128* symbologies are provided below.

**Code 39 Checksum**

In *Code 39*, the checksum is optional. The checksum is calculated as the sum of encoded digits modulo 43, as the maximum number of characters to be encoded is 43. The following code snippet demonstrates how to compute the checksum for *Code 39*.

  
```javascript

for (var i = 0; i < encodedCodetext.length; i++) {
    checkSum = (checkSum + encodedCodetext[i]) % 43;
}


```
  
**Code 128 Checksum**

The *Code 128* standard uses an advanced algorithm for checksum calculation compared to *Code 39*. In this method, each digit in the barcode is weighted by its position index. The following code sample demonstrates how to perform checksum calculation for *Code 128*.

  
```javascript

for (var pos = 0; pos < encodedCodetext.length; ++pos) {
    checkSum = (checkSum + encodedCodetext[pos] * (pos + 1)) % 103;
}

``` 
  
## **Barcode Checksum Settings**
Different barcode types have varying checksum requirements, which can be either optional or mandatory. Additionally, different barcode standards may use different checksum types. When a checksum is required, the library applies the most commonly used checksum type for the specific barcode type. The checksum digit is generated as the last character of the barcode. The [*IsChecksumEnabled*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodeparameters/properties/ischecksumenabled) property of the [*BarcodeParameters*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodeparameters) class is used to control checksum calculation for 1D barcodes. By default, this property is set to *Yes* for barcode types that require a checksum and *No* for those with an optional checksum.

Below are the lists of barcode standards with optional and mandatory checksum settings.

|Checksum Requirements|1D Symbologies|
|---|---|
|**Optional**|Codabar, Code39, Italian Post 25, Interleaved 2 of 5, Matrix 2 of 5, MSI, Pharmacode, PatchCode, PZN, Standard 2 of 5|
|**Mandatory**|CodablockF, Code11, Code128, Code16K, Code32, Code93, Databar Expanded Stacked, Databar Expanded, Databar OmniDirectional, Databar Stacked OmniDirectional, Databar Stacked, DatabarLimited, DatabarTruncated, EAN13, EAN14, EAN2, EAN5, EAN8, GS1 CodablockF, GS1 Code128, IATA 2 of 5, ISBN, ISMN, ISSN, ITF14, ITF6, OPC, SSCC14, SSCC18, UPCA, UPCE, UpcaGs1DatabarCoupon, VIN|

### **Optional Checksum Controls**
By default, 1D barcodes with optional checksum do not require the calculation of a check digit. For these barcodes, the [*IsChecksumEnabled*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodeparameters/properties/ischecksumenabled) property of the [*BarcodeParameters*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodeparameters) class can be set as follows:
- *EnableChecksum.Default* and *EnableChecksum.No*: Disables checksum calculation.
- *EnableChecksum.Yes*: The library generates the checksum using the most appropriate type for the given barcode symbology.

|Checksum Settings|Checksum Enabled|Checksum Disabled|
| :-: | :-: | :-: |
| |<img src="onecscode39withchecksum.png">|<img src="onecscode39withoutchecksum.png">|

The following code snippet demonstrates how to enable and disable checksum for *Code 39* barcodes.

  
```javascript

// Create a Code39FullASCII barcode generator with no checksum
var gen = new BarCodeInstance.BarcodeGenerator("Code39FullASCII", "CODE");
gen.Parameters.Barcode.IsChecksumEnabled = BarCodeInstance.EnableChecksum.No;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

// Set checksum to enabled and generate another barcode
gen.Parameters.Barcode.IsChecksumEnabled = BarCodeInstance.EnableChecksum.Yes;
document.getElementById("img2").src = gen.GenerateBarCodeImage(); // Display barcode image with checksum

// Cleanup
gen.delete();


``` 
### **Obligatory Checksum Controls**
For barcodes with mandatory checksum control, the [*IsChecksumEnabled*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodeparameters/properties/ischecksumenabled) property of the [*BarcodeParameters*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodeparameters) class can be configured as follows:
- *EnableChecksum.Default* and *EnableChecksum.Yes*: The checksum calculation is performed using the specific algorithm for the barcode type.
- *EnableChecksum.No*: Depending on the symbology, the library either throws an exception or disregards this setting.

The following image demonstrates a barcode label generated with obligatory checksum settings.     
<p align="center"><img src="onecscode93withchecksum.png"></p>

The code snippet below shows how to set checksum options for *Code 39*. If the *EnableChecksum* property is set to "*No*", the following exception is raised: "*Unable to use Code93Extended symbology without checksum*".


```javascript

// Create a Code93 barcode generator with checksum enabled
var gen = new BarCodeInstance.BarcodeGenerator("Code93", "CODE");
gen.Parameters.Barcode.IsChecksumEnabled = BarCodeInstance.EnableChecksum.Yes;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

// Attempt to set checksum to disabled and generate an image
try {
    gen.Parameters.Barcode.IsChecksumEnabled = BarCodeInstance.EnableChecksum.No;
    document.getElementById("img").src = gen.GenerateBarCodeImage(); // This line should not execute
} catch (e) {
    console.log(e.message); // Log the error message
}

// Cleanup
gen.delete();


```
## **Display Checksum for Code 128**
For *Code 128* and *GS1 Code 128* symbologies, the library includes the [*ChecksumAlwaysShow*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodeparameters/properties/checksumalwaysshow) setting in the [*BarcodeParameters*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodeparameters) class. When enabled, this setting adds the checksum digit to the *CodeText* field, displaying it as human-readable barcode text.

|Checksum Visibility|Displayed|Hidden|
| :-: | :-: | :-: |
| |<img src="onecscode128showchecksum.png">|<img src="onecscode128notshowchecksum.png">|

The following code snippet demonstrates how to enable and disable the *ChecksumAlwaysShow* property.

  
```javascript

// Create a Code128 barcode generator with checksum display settings
var gen = new BarCodeInstance.BarcodeGenerator("Code128", "CODE");

// Do not display checksum
gen.Parameters.Barcode.ChecksumAlwaysShow = false;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image without checksum

// Display checksum
gen.Parameters.Barcode.ChecksumAlwaysShow = true;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image with checksum

// Cleanup
gen.delete();


``` 
