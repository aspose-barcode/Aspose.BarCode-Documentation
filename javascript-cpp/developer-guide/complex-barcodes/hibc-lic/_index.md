---
title: Generate and Read HIBC LIC Barcodes in JavaScript
linktitle: HIBC LIC
type: docs
feedback: BARCODECOM
weight: 50
url: /javascript-cpp/hibc-lic-barcodes/
---

## **Overview**
The HIBCC Licensed Identification Code (LIC) is a standardized identifier for tracking products, packages, and containers, primarily used in the healthcare industry. It was introduced by the Healthcare Industry Bar Code Council (HIBCC), a non-profit organization focused on developing and promoting standardized barcodes in healthcare. The HIBC LIC can encode data elements such as product identifier, lot number, expiration date, and more. Each field follows a specific format, with guidelines provided by HIBCC.

***Aspose.BarCode for JavaScript via C++*** offers tools to generate and read barcodes using the HIBC LIC standard. Main data can be encoded with types like Code 39, Code 128, Aztec Code, Data Matrix, or QR Code. The barcode type must be set using the [*BarcodeType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.generation/barcodegenerator/barcodetype/) property. To generate HIBC LIC barcodes, use the [*ComplexBarcodeGenerator*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/complexbarcodegenerator/) class along with specific HIBC LIC classes, including [*HIBCLICComplexCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/hibcliccomplexcodetext/), [*HIBCLICCombinedCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/hibcliccombinedcodetext/), [*HIBCLICPrimaryDataCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/hibcliccombinedcodetext/primarydata/), and [*HIBCLICSecondaryAndAdditionalDataCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/hibcliccombinedcodetext/secondaryandadditionaldata/).

{{% alert color="primary" %}}*For any clarifications, please reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/), ask questions at the [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13), or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Generate HIBC LIC Barcodes**
As per the HIBCC (Health Industry Business Communications Council) standards, HIBC barcodes can store both primary and secondary information. The following explains how to create HIBC LIC barcodes encoding primary data, secondary data, or both using the barcode library.

### **Primary Data**
Medical products must be labeled with barcodes containing information such as the labeler's identification code, product number or catalog identifier, and unit of measure. These data elements are crucial for tracking products, packages, and containers within the supply chain. To generate HIBC LIC barcodes with primary data, use the [*HIBCLICPrimaryDataCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/hibcliccombinedcodetext/primarydata/) class.

The following code sample demonstrates how to generate HIBC LIC barcodes and encode primary data.


<p align="center"><img src="hibclicprimary.png"></p>

[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
//create a HIBC LIC barcode
// Create HIBC LIC Primary Data Codetext
var complexCodetext = new BarCodeInstance.HIBCLICPrimaryDataCodetext();
complexCodetext.BarcodeType = "HIBCQRLIC"; // Set barcode type

// Specify primary data
complexCodetext.Data = new BarCodeInstance.PrimaryData();
complexCodetext.Data.ProductOrCatalogNumber = "12345";
complexCodetext.Data.LabelerIdentificationCode = "A999";
complexCodetext.Data.UnitOfMeasureID = 1;

// Encode HIBC LIC data
var gen = new BarCodeInstance.ComplexBarcodeGenerator(complexCodetext);
gen.Parameters.Barcode.XDimension.Pixels = 10;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display HIBC LIC barcode

gen.delete();

```

### **Secondary Data**
HIBC LIC barcodes can also encode additional data fields as secondary information, such as expiration date, product quantity, lot number, serial number, and date of manufacture. This type of auxiliary information can be included in the barcode using the [*HIBCLICSecondaryAndAdditionalDataCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/hibcliccombinedcodetext/secondaryandadditionaldata/) class to format the data as needed.

The following code sample shows how to generate HIBC LIC barcodes and encode secondary data.


<p align="center"><img src="hibclicsecondary.png"></p>

[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Create HIBC LIC Secondary and Additional Data Codetext
var complexCodetext = new BarCodeInstance.HIBCLICSecondaryAndAdditionalDataCodetext();
complexCodetext.BarcodeType = "HIBCQRLIC"; // Set barcode type

// Create secondary data
complexCodetext.Data = new BarCodeInstance.SecondaryAndAdditionalData();
complexCodetext.Data.ExpiryDate = new Date(); // Current date as expiry date
complexCodetext.Data.ExpiryDateFormat = BarCodeInstance.HIBCLICDateFormat.MMDDYY;
complexCodetext.Data.Quantity = 30;
complexCodetext.Data.LotNumber = "LOT123";
complexCodetext.Data.SerialNumber = "SERIAL123";
complexCodetext.Data.DateOfManufacture = new Date(); // Current date as date of manufacture
complexCodetext.LinkCharacter = 'S'; // Set link character

// Encode HIBC LIC Code
var gen = new BarCodeInstance.ComplexBarcodeGenerator(complexCodetext);
gen.Parameters.Barcode.XDimension.Pixels = 10;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display HIBC LIC barcode

gen.delete();

```

### **Combined Data**
The barcode library allows for encoding both primary and secondary data in a single HIBC LIC barcode. This can be achieved using the [*HIBCLICCombinedCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/hibcliccombinedcodetext/) class.

The following code sample illustrates how to generate HIBC LIC barcodes with combined primary and secondary data.

<p align="center"><img src="hibcliccombined.png"></p>

[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Create HIBC LIC Combined Codetext
var complexCodetext = new BarCodeInstance.HIBCLICCombinedCodetext();
complexCodetext.BarcodeType = "HIBCQRLIC"; // Set barcode type

// Create primary data
complexCodetext.PrimaryData = new BarCodeInstance.PrimaryData();
complexCodetext.PrimaryData.ProductOrCatalogNumber = "12345";
complexCodetext.PrimaryData.LabelerIdentificationCode = "A999";
complexCodetext.PrimaryData.UnitOfMeasureID = 1;

// Create secondary data
complexCodetext.SecondaryAndAdditionalData = new BarCodeInstance.SecondaryAndAdditionalData();
complexCodetext.SecondaryAndAdditionalData.ExpiryDate = new Date(); // Current date as expiry date
complexCodetext.SecondaryAndAdditionalData.ExpiryDateFormat = BarCodeInstance.HIBCLICDateFormat.MMDDYY;
complexCodetext.SecondaryAndAdditionalData.Quantity = 30;
complexCodetext.SecondaryAndAdditionalData.LotNumber = "LOT123";
complexCodetext.SecondaryAndAdditionalData.SerialNumber = "SERIAL123";
complexCodetext.SecondaryAndAdditionalData.DateOfManufacture = new Date(); // Current date as date of manufacture

// Encode HIBC LIC Combined Code
var gen = new BarCodeInstance.ComplexBarcodeGenerator(complexCodetext);
gen.Parameters.Barcode.XDimension.Pixels = 10;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display HIBC LIC combined barcode

gen.delete();

```


## Read and Decode HIBC LIC Barcodes
To decode HIBC LIC barcodes, start by creating an instance of the [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/) class and setting the appropriate value for the [*DecodeType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/decodetype/) property. Next, process the obtained barcode type by calling the [*TryDecodeHIBCLIC*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/complexcodetextreader/trydecodehibclic/) method from the [*ComplexCodetextReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/complexcodetextreader/) class. This method returns an instance of the [*HIBCLICComplexCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/hibcliccomplexcodetext/) class. This object can be further converted to instances of [*HIBCLICPrimaryDataCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/hibclicprimarydatacodetext/), [*HIBCLICSecondaryAndAdditionalDataCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/hibclicsecondaryandadditionaldatacodetext/), or [*HIBCLICCombinedCodetext*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.complexbarcode/hibcliccombinedcodetext/), based on the format of the encoded data.

The following code sample illustrates how to read HIBC LIC barcodes.


[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Recognize a HIBC LIC Combined barcode
var reader = new BarCodeInstance.BarCodeReader(`${path}HIBCLICCombined.png`, "HIBCQRLIC");
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    var codetext = BarCodeInstance.ComplexCodetextReader.TryDecodeHIBCLIC(result.CodeText);
    var combinedCodetext = codetext instanceof BarCodeInstance.HIBCLICCombinedCodetext ? codetext : null;
    if (!combinedCodetext) continue;

    console.log(`Product or catalog number: ${combinedCodetext.PrimaryData.ProductOrCatalogNumber}`);
    console.log(`Labeler identification code: ${combinedCodetext.PrimaryData.LabelerIdentificationCode}`);
    console.log(`Unit of measure ID: ${combinedCodetext.PrimaryData.UnitOfMeasureID}`);
    console.log(`Expiry date: ${combinedCodetext.SecondaryAndAdditionalData.ExpiryDate}`);
    console.log(`Quantity: ${combinedCodetext.SecondaryAndAdditionalData.Quantity}`);
    console.log(`Lot number: ${combinedCodetext.SecondaryAndAdditionalData.LotNumber}`);
    console.log(`Serial number: ${combinedCodetext.SecondaryAndAdditionalData.SerialNumber}`);
    console.log(`Date of manufacture: ${combinedCodetext.SecondaryAndAdditionalData.DateOfManufacture}`);
}

reader.delete();

```