---
title: Generate Swiss Post Parcel Barcodes in JavaScript
linktitle: Swiss Post Parcel
type: docs
description: "Description of Swiss Post Parcel Barcode Type"
keywords: swisspost parcel barcode, create swiss post barcode, generate swiss post barcode, read swiss post barcode, recognize swiss post codes, swiss post parcel codes
weight: 100
feedback: BARCODECOM
url: /javascript-cpp/swiss-post-parcel-barcodes/
---
## **Overview**

*Swiss Post Parcel* is a barcode type used by the Swiss Post to manage mail sending and shipping. Each parcel is assigned with a unique barcode that serves as an identifier in automatic parcel processing. This type is based on *Code 128* (charsets B and C) and inherits its advantages, including obligatory checksum controls, high data density, and the support of laser scanning.  
  
## **Swiss Post Parcel Barcode Subtypes**

*Swiss Post Parcel* allows generating three types of barcodes:
- *Domestic Mail* - a shipping identifier used to process postal and cargo shipments inside Switzerland. It is defined as an 18-digit code that starts with 98 or 99 and includes only a standard Code 128 checksum, e.g., "98.34.123456.12345678". As seen, for convenience, codes are divided by dots into four fragments.
- *International Mail* - a shipping identifier used for transnational shipments. It has the following format: **LLXXXXXXXXCCH**, where L denotes an uppercase English letter; X – a numerical digit from 0 to 9; C – a control digit; CH – the standard addition of two letters that remains unchanged. As seen, the code is protected by an additional checksum used together with the standard Code 128 check digit, e.g., "RM999605013CH". The control checksum can be computed manually or automatically by the ***Aspose.BarCode for JavaScript via C++*** library.
- *Additional Service Codes* - different codes used to indicate additional services for a shipment and defined as 4-digit sets, e.g., "0327". One shipment may include from 1 to 10 service codes. The library supports the service codes described in the table below.  
  
|Service Name|Letter Abbreviation|Service Code Number|
|---|---|:--:|
|Business reply label|GAS|0203|
|Personal delivery|RMP|0322|
|Return receipt|AR|0327|
|Electronic return receipt|eAR|0328|
|Cash on delivery (obsolete)|-|0340|
|Electronic cash on delivery|BLN|0341|
|ID Check|ID+RMP|0470|
|Items for the blind|CEC|0610|
|Military mail|MIL|1007|
|Second attempted delivery on the following Saturday|-|2512|
  
## **Generate Swiss Post Parcel Barcodes**

The code examples provided further demonstrate how to generate and read *Swiss Post Parcel* barcodes using the ***Aspose.BarCode for JavaScript via C++*** library. 


### **Domestic Mail**

This example demonstrates how to generate *Swiss Post Parcel* barcodes for *Domestic Mail*. The *Domestic Mail* identifier can be passed in its original form or as an 18-digit code. Both options provide the same results for generation and recognition.  
  
|Domestic Mail Barcode|With Original Identifier|With 18-digit Code|
|:--:|:--:|:--:|
| |![Swiss Post Parcel Original](swisspostdomesticmailasis.png)|![Swiss Post Parcel Code](swisspostdomesticmailasdigits.png)|
  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript

//generate a Swiss Post Domestic Mail barcode with the original identifier
var gen = new BarCodeInstance.BarcodeGenerator("SwissPostParcel", "98.34.123456.12345678");
gen.Parameters.Barcode.XDimension = "2px";
gen.Parameters.Barcode.BarHeight = "40px";
document.getElementById("img").src = gen.GenerateBarCodeImage();

//read the current barcode value
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "SwissPostParcel");
reader.ReadBarCodes();
for(var i = 0; i < reader.FoundCount; i++)
{
    const result = reader.FoundBarCodes(i);
    console.log(`Barcode type:${result.CodeType}, Barcode Data:${result.CodeText}`);
}

gen.delete();
reader.delete();

//generate a Swiss Post Domestic Mail barcode with the 18-digit code
gen = new BarCodeInstance.BarcodeGenerator("SwissPostParcel", "983412345612345678");
gen.Parameters.Barcode.XDimension = "2px";
gen.Parameters.Barcode.BarHeight = "40px";
document.getElementById("img").src = gen.GenerateBarCodeImage();

//read the current barcode value
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "SwissPostParcel");
reader.ReadBarCodes();
for(var i = 0; i < reader.FoundCount; i++)
{
    const result = reader.FoundBarCodes(i);
    console.log(`Barcode type:${result.CodeType}, Barcode Data:${result.CodeText}`);
}

gen.delete();
reader.delete();

```


### **International Mail**

# Generating Swiss Post Parcel Barcodes for International Mail

The following example demonstrates how to generate **Swiss Post Parcel** barcodes for **International Mail**:

- If the postal shipping identifier contains an **invalid checksum**, the library will automatically correct it during barcode generation.
- If the shipping identifier does **not include a checksum digit**, the library will create and add it automatically to the barcode.

## Example Output

| **International Mail Barcode** | **With Correct Checksum** | **Without Checksum** | **With Erroneous Checksum** |
|:------------------------------:|:--------------------------:|:--------------------:|:---------------------------:|
|                                | ![Correct Checksum](swisspostinternationalmailasis.png) | ![Without Checksum](swisspostinternationalmailwithoutchecksum.png) | ![Erroneous Checksum](swisspostinternationalmailwithwrongchecksum.png) |

  
[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Generate a Swiss Post International Mail barcode with a correct checksum
var gen = new BarCodeInstance.BarcodeGenerator("SwissPostParcel", "RM999605013CH");
gen.Parameters.Barcode.XDimension = "2px";
gen.Parameters.Barcode.BarHeight = "40px";
document.getElementById("img").src = gen.GenerateBarCodeImage();

// Read the generated barcode
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "SwissPostParcel");
reader.ReadBarCodes();

for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`Barcode Type: ${result.CodeType}, Barcode Data: ${result.CodeText}`);
}

gen.delete();
reader.delete();

// Generate a Swiss Post International Mail barcode with an erroneous checksum
var gen = new BarCodeInstance.BarcodeGenerator("SwissPostParcel", "RM999605017CH");
gen.Parameters.Barcode.XDimension = "2px";
gen.Parameters.Barcode.BarHeight = "40px";
document.getElementById("img").src = gen.GenerateBarCodeImage();

// Read the generated barcode
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "SwissPostParcel");
reader.ReadBarCodes();

for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`Barcode Type: ${result.CodeType}, Barcode Data: ${result.CodeText}`);
}

gen.delete();
reader.delete();

// Generate a Swiss Post International Mail barcode without a checksum
var gen = new BarCodeInstance.BarcodeGenerator("SwissPostParcel", "RM99960501CH");
gen.Parameters.Barcode.XDimension = "2px";
gen.Parameters.Barcode.BarHeight = "40px";
document.getElementById("img").src = gen.GenerateBarCodeImage();

// Read the generated barcode
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "SwissPostParcel");
reader.ReadBarCodes();

for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`Barcode Type: ${result.CodeType}, Barcode Data: ${result.CodeText}`);
}

gen.delete();
reader.delete();

```


### **Additional Service Codes**

This example demonstrates how to generate *Swiss Post Parcel* barcodes for indicating *Additional Services* required for postal shipments. These barcodes can be created in the *Code 128* format. Additionally, a human-readable designation of the service can be manually added.

| Additional Service Barcode | As *Swiss Post Parcel* | As *Code 128* |
| :--: | :--: | :--: |
|  | ![Swiss Post Parcel Additional Service With Original Identifier](swisspostadditionalserviceasis.png) | ![Swiss Post Parcel Additional Service As Code 128](swisspostadditionalserviceascode128.png) |

[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Additional Service codes:
// Personal delivery (RMP) 0322
// Return receipt (AR) 0327
// Cash on delivery (currently obsolete) 0340
// Electronic cash on delivery (BLN) 0341
// Items for the blind (CEC) 0610
// Military mail (MIL) 1007
// Second attempted delivery on the following Saturday 2512
// Electronic return receipt (eAR) 0328
// ID check (ID+RMP) 0470
// Business reply label (GAS) 0203

// Generate a Swiss Post Additional Service barcode
var gen = new BarCodeInstance.BarcodeGenerator("SwissPostParcel", "0327");
gen.Parameters.Barcode.XDimension = "2px";
gen.Parameters.Barcode.BarHeight = "40px";
gen.Parameters.Barcode.CodeTextParameters.Location = BarCodeInstance.CodeLocation.None; // No code text display
gen.Parameters.CaptionAbove.Visible = true;
gen.Parameters.CaptionAbove.Alignment = BarCodeInstance.TextAlignment.Left; // Align text to the left
gen.Parameters.CaptionAbove.Text = "AR"; // Display "AR" above the barcode
gen.Parameters.CaptionAbove.Font.Size = "24px";
gen.Parameters.CaptionAbove.Font.Style = BarCodeInstance.FontStyle.Bold;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

// Read the current barcode value
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "SwissPostParcel");
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`Barcode Type: ${result.CodeType}, Barcode Data: ${result.CodeText}`);
}

gen.delete();
reader.delete();
```

[How to get *BarCodeInstance*](/barcode/javascript-cpp/get-barcode-module-instance/)
```javascript
// Additional Service codes:
// Personal delivery (RMP) 0322
// Return receipt (AR) 0327
// Cash on delivery (currently obsolete) 0340
// Electronic cash on delivery (BLN) 0341
// Items for the blind (CEC) 0610
// Military mail (MIL) 1007
// Second attempted delivery on the following Saturday 2512
// Electronic return receipt (eAR) 0328
// ID check (ID+RMP) 0470
// Business reply label (GAS) 0203

// Generate a Swiss Post Additional Service barcode
var gen = new BarCodeInstance.BarcodeGenerator("SwissPostParcel", "0327");
gen.Parameters.Barcode.XDimension = "2px";
gen.Parameters.Barcode.BarHeight = "40px";
gen.Parameters.Barcode.CodeTextParameters.Location = BarCodeInstance.CodeLocation.None; // No code text display
gen.Parameters.CaptionAbove.Visible = true;
gen.Parameters.CaptionAbove.Alignment = BarCodeInstance.TextAlignment.Left; // Align text to the left
gen.Parameters.CaptionAbove.Text = "AR"; // Display "AR" above the barcode
gen.Parameters.CaptionAbove.Font.Size = "24px";
gen.Parameters.CaptionAbove.Font.Style = BarCodeInstance.FontStyle.Bold;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

// Read the current barcode value
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "SwissPostParcel");
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`Barcode Type: ${result.CodeType}, Barcode Data: ${result.CodeText}`);
}

gen.delete();
reader.delete();

// Generate a Swiss Post Additional Service barcode in the form of Code 128
var gen = new BarCodeInstance.BarcodeGenerator("Code128", "0327");
gen.Parameters.Barcode.XDimension = "2px";
gen.Parameters.Barcode.BarHeight = "40px";
gen.Parameters.Barcode.CodeTextParameters.Location = BarCodeInstance.CodeLocation.None; // No code text display
gen.Parameters.CaptionAbove.Visible = true;
gen.Parameters.CaptionAbove.Alignment = BarCodeInstance.TextAlignment.Left; // Align text to the left
gen.Parameters.CaptionAbove.Text = "AR"; // Display "AR" above the barcode
gen.Parameters.CaptionAbove.Font.Size = "24px";
gen.Parameters.CaptionAbove.Font.Style = BarCodeInstance.FontStyle.Bold;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

// Read the current barcode value
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "SwissPostParcel");
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`Barcode Type: ${result.CodeType}, Barcode Data: ${result.CodeText}`);
}

gen.delete();
reader.delete();
```