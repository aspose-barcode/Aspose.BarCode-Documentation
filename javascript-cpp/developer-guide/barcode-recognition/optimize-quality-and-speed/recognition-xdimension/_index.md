---
title: Recognition XDimension Mode
type: docs
description: "This article explains how barcode recognition can be optimized for different bercode sizes and scan resolutions"
keywords: "Improve Barcode Recognition, Optimize Barcode Reading, Optimized Scan for Barcode Recognition, Barcode Resolution, Speed Up Barcode Reading, Image Processing for Barcode, Read Many Barcodes from One Image, Aspose.BarCode, Read Barcode JavaScript"
weight: 20
feedback: BARCODECOM
url: /javascript-cpp/recognition-xdimension/
---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can check the quality of Aspose.BarCode recognition and view the results online.{{% /alert %}}
## **Overview**
***Aspose.BarCode for JavaScript via C++*** provides a specialized mode that leverages the minimal element of a barcode (such as a matrix cell or bar). This mode, configured using the [*XDimension*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension) and [*UseMinimalXDimension*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/xdimensionmode/) properties from the [*QualitySettings*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings) class, enhances performance by filtering out noise, text, and non-barcode elements. Additionally, the [*MinimalXDimension*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings/properties/minimalxdimension) property can be used to set the minimum barcode element size.

{{% alert color="primary" %}}
*Need assistance? Reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/) via the [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or the [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*
{{% /alert %}}

---

## **XDimension Mode**
Below are the details of the [*XDimension*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension) and [*UseMinimalXDimension*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/xdimensionmode/) properties, along with the supported modes:

| **XDimension Mode** | **Description** |
|----------------------|-----------------|
| **Auto**            | Currently equivalent to *Normal*. Future updates may include AI-based detection. |
| **Small**           | Detects barcodes with a minimal [*XDimension*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension) of 1 pixel or more. |
| **Normal**          | Detects barcodes with a base [*XDimension*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension) of 2-5 pixels or more. The exact value depends on the barcode type. |
| **Large**           | Detects barcodes with large [*XDimension*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension), typically captured by high-resolution cameras. |
| **UseMinimalXDimension** | Detects barcodes using the [*XDimension*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension) specified in the [*UseMinimalXDimension*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/xdimensionmode/) property. |
## **Using XDimension with 1D Barcode Types**
The table below illustrates the impact of different [*XDimension*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension) settings on recognition quality.

<p align="center"><img src="many_code128.png" height="45%" width="45%"></p>

| **XDimension Normal** | **XDimension Small** | **XDimension UseMinimalXDimension** |
|------------------------|-----------------------|-------------------------------------|
| **Recognized barcodes: 2** | **Recognized barcodes: 5** | **Recognized barcodes: 5** |


```javascript
// Recognize image with XDimension Normal
console.log("XDimensionMode: Normal");
var readerNormal = new BarCodeInstance.BarCodeReader(`${path}many_code128.png`, "Code128");
readerNormal.QualitySettings.XDimension = BarCodeInstance.XDimensionMode.Normal;
readerNormal.ReadBarCodes();
console.log(`Barcodes read: ${readerNormal.FoundCount}`);
for (var i = 0; i < readerNormal.FoundCount; i++) {
    const result = readerNormal.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}
readerNormal.delete();

// Recognize image with XDimension Small
console.log("XDimensionMode: Small");
var readerSmall = new BarCodeInstance.BarCodeReader(`${path}many_code128.png`, "Code128");
readerSmall.QualitySettings.XDimension = BarCodeInstance.XDimensionMode.Small;
readerSmall.ReadBarCodes();
console.log(`Barcodes read: ${readerSmall.FoundCount}`);
for (var i = 0; i < readerSmall.FoundCount; i++) {
    const result = readerSmall.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}
readerSmall.delete();

// Recognize image with XDimension UseMinimalXDimension
console.log("XDimensionMode: UseMinimalXDimension");
var readerMinimal = new BarCodeInstance.BarCodeReader(`${path}many_code128.png`, "Code128");
readerMinimal.QualitySettings.XDimension = BarCodeInstance.XDimensionMode.UseMinimalXDimension;
readerMinimal.QualitySettings.MinimalXDimension = 1;
readerMinimal.ReadBarCodes();
console.log(`Barcodes read: ${readerMinimal.FoundCount}`);
for (var i = 0; i < readerMinimal.FoundCount; i++) {
    const result = readerMinimal.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}
readerMinimal.delete();

```

<p align="center"><img src="code128_big_and_small.png" width="25%" height="25%"></p>

| **XDimension Normal**        | **XDimension Small**       |
|-------------------------------|----------------------------|
| **Recognized barcodes: 2**   | **Recognized barcodes: 3** |


```javascript

// Recognize image with XDimension Normal
console.log("XDimensionMode: Normal");
var readerNormal = new BarCodeInstance.BarCodeReader(`${path}code128_big_and_small.png`, "Code128");
readerNormal.QualitySettings.XDimension = BarCodeInstance.XDimensionMode.Normal;
readerNormal.ReadBarCodes();
console.log(`Barcodes read: ${readerNormal.FoundCount}`);
for (var i = 0; i < readerNormal.FoundCount; i++) {
    const result = readerNormal.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}
readerNormal.delete();

// Recognize image with XDimension Small
console.log("XDimensionMode: Small");
var readerSmall = new BarCodeInstance.BarCodeReader(`${path}code128_big_and_small.png`, "Code128");
readerSmall.QualitySettings.XDimension = BarCodeInstance.XDimensionMode.Small;
readerSmall.ReadBarCodes();
console.log(`Barcodes read: ${readerSmall.FoundCount}`);
for (var i = 0; i < readerSmall.FoundCount; i++) {
    const result = readerSmall.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}
readerSmall.delete();

```

