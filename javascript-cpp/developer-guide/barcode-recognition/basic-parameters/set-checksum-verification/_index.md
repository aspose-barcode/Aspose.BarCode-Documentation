---
title: Set Barcode Checksum Verification
linktitle: Set Checksum Verification
type: docs
description: "This article describes how to set checksum verification in Aspose.BarCode for JavaScript via C++"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcode JavaScript"
feedback: BARCODECOM
weight: 40
url: /javascript-cpp/set-checksum-verification/
---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
## **Overview**
In many 1D and postal symbologies, data integrity verification and decoding rely on checksum control mechanisms. The [*BarcodeSettings*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodesettings) class has the [*ChecksumValidation*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodesettings/properties/checksumvalidation) property for managing checksum settings for data validation and decoding. Barcode standards can generally be divided into two groups: those that require a checksum and those that have an optional checksum. The [*ChecksumValidation*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodesettings/properties/checksumvalidation) field can be set to different values, affecting the barcode recognition process based on the checksum settings.

## **Checksum Validation for Barcodes with Obligatory Checksum**
For symbologies with an obligatory checksum, checksum control is always performed when the [*ChecksumValidation*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodesettings/properties/checksumvalidation) property is set to *ChecksumValidation.Default* or *ChecksumValidation.On*. If set to *ChecksumValidation.Off*, checksum control is disabled, allowing data reading from incorrectly generated barcodes. However, this increases the likelihood of inaccurate recognition.

The following code snippet demonstrates how to configure checksum validation for symbologies with an obligatory checksum (e.g., the *Code 11* barcode image shown below).

 
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Create a Code 11 barcode
var gen = new BarCodeInstance.BarcodeGenerator("Code11", "123456");
gen.Parameters.Barcode.XDimension = "2px";
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

// Read barcode image with ChecksumValidation.Default being set
console.log("ReadChecksumCode11:");
console.log("ChecksumValidation: Default");
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "Code11");
reader.BarcodeSettings.ChecksumValidation = BarCodeInstance.ChecksumValidation.Default;
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`CodeType: ${result.CodeType}`);
    console.log(`CodeText: ${result.CodeText}`);
    console.log(`1D Value: ${result.Extended.OneD.Value}`);
    console.log(`1D CheckSum: ${result.Extended.OneD.CheckSum}`);
}

// Read barcode image with ChecksumValidation.Off being set
console.log("ChecksumValidation: Off");
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "Code11");
reader.BarcodeSettings.ChecksumValidation = BarCodeInstance.ChecksumValidation.Off;
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`CodeType: ${result.CodeType}`);
    console.log(`CodeText: ${result.CodeText}`);
    console.log(`1D Value: ${result.Extended.OneD.Value}`);
    console.log(`1D CheckSum: ${result.Extended.OneD.CheckSum}`);
}

gen.delete();
reader.delete();

```
  
<p align="center"><img src="code11.png"></p> 

## **Checksum Validation for Barcodes with Optional Checksum**
For symbologies with optional checksum control, the [*ChecksumValidation*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodesettings/properties/checksumvalidation) property can be set to enable checksum checking by using the value *ChecksumValidation.On*. If the property is set to *ChecksumValidation.Default* or *ChecksumValidation.Off*, checksum validation will be skipped.

The following code sample demonstrates how to configure barcode reading with optional checksum (a *Code 39* barcode image is used as an example).

  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Create a Code 39 Extended barcode
var gen = new BarCodeInstance.BarcodeGenerator("Code39FullASCII", "123456");
gen.Parameters.Barcode.XDimension = "2px";
gen.Parameters.Barcode.IsChecksumEnabled = BarCodeInstance.EnableChecksum.Yes;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

// Read barcode image with ChecksumValidation.Default being set
console.log("ReadChecksumCode39:");
console.log("ChecksumValidation: Default");
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "Code39FullASCII");
reader.BarcodeSettings.ChecksumValidation = BarCodeInstance.ChecksumValidation.Default;
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`CodeType: ${result.CodeType}`);
    console.log(`CodeText: ${result.CodeText}`);
    console.log(`1D Value: ${result.Extended.OneD.Value}`);
    console.log(`1D CheckSum: ${result.Extended.OneD.CheckSum}`);
}

// Read barcode image with ChecksumValidation.On being set
console.log("ChecksumValidation: On");
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "Code39FullASCII");
reader.BarcodeSettings.ChecksumValidation = BarCodeInstance.ChecksumValidation.On;
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`CodeType: ${result.CodeType}`);
    console.log(`CodeText: ${result.CodeText}`);
    console.log(`1D Value: ${result.Extended.OneD.Value}`);
    console.log(`1D CheckSum: ${result.Extended.OneD.CheckSum}`);
}

gen.delete();
reader.delete();

```
  
<p align="center"><img src="code39.png"></p>

