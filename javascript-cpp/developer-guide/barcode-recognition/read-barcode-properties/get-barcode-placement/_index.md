---
title: Get Barcode Placement Region and Orientation Angle
linktitle: Get Placement Region and Orientation
type: docs
description: "This article describes how to read barcode parameters"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode JavaScript"
feedback: BARCODECOM
weight: 20
url: /javascript-cpp/get-placement-and-orientation/
---  
  
## **Get Barcode Placement and Orientation Information**

To retrieve information about the placement region and orientation angle of a source barcode, ***Aspose.BarCode for JavaScript via C++*** provides a group of properties called [*RegionParameters*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderegionparameters). This group stores the following details:

- **Quadrangle** – an object that bounds the barcode.
- **Rectangle** – an object that bounds the barcode.
- **Points** – an array of points that make up the barcode.
- **Angle** – the orientation angle in degrees.

The following code sample demonstrates how to retrieve information about the barcode placement region and orientation angle from a sample barcode image.


```javascript
var gen = new BarCodeInstance.BarcodeGenerator("Code128", "Aspose1234");
gen.Parameters.Barcode.XDimension.Pixels = 2;
document.getElementById("img").src = gen.GenerateBarCodeImage(); // Display barcode image

// Read Code 128 barcode with region information
var reader = new BarCodeInstance.BarCodeReader(gen.GenerateBarCodeImage(), "Code128");
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    var result = reader.FoundBarCodes(i);
    console.log(`CodeType: ${result.CodeType}`);
    console.log(`CodeText: ${result.CodeText}`);
    console.log(`Quadrangle: ${result.Region.Quadrangle.toString()}`);
    console.log(`Angle: ${result.Region.Angle.toString()}`);
    console.log(`Rectangle: ${result.Region.Rectangle.toString()}`);
    let ptStr = "";
    for(var j = 0; j < result.Region.PointsCount; j++)
    {
        var pt = result.Region.GetPoint(j);
        ptStr += pt.toString() + " ";
    }
    console.log(`Points: ${ptStr}`);
}

gen.delete();
reader.delete();

```
  
<p align="center"><img src="qr_code128.png" width="20%" height="20%"></p>

