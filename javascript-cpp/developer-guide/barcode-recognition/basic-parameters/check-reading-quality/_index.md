---
title: Check Barcode Recognition Quality
linktitle: Check Recognition Quality
type: docs
description: "This article describes how to verify barcode recognition quality"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode JavaScript"
feedback: BARCODECOM
weight: 50
url: /javascript-cpp/check-recognition-quality/
---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**

In many cases, it is important to assess whether a barcode has been accurately recognized. In ***Aspose.BarCode for JavaScript via C++***, this can be done using the [*Confidence*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderesult/properties/confidence) and [*ReadingQuality*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderesult/properties/readingquality) properties of the [*BarCodeResult*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderesult) class.

## **Verify Barcode Reading Quality**

The [*Confidence*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderesult/properties/confidence) property returns a value from the [*BarCodeConfidence*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodeconfidence) enumeration, indicating the confidence level of the recognition. The [*BarCodeConfidence*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodeconfidence) enumeration has three possible values: *None*, *Moderate*, and *Strong*. The [*ReadingQuality*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderesult/properties/readingquality) property provides an estimate of recognition quality based on the confidence level: 0 for *None*; values from 1 to 99; and 100 for *Strong*.

|Confidence Level|Reading Quality Value|Description|
|---|---|---|
|None|0|A *None* confidence level indicates that the source barcode may be incorrect and its data may contain errors. However, the barcode type and orientation in the image can still be determined, and partial data decoding is possible.|
|Moderate|80|Returned for 1D and postal barcodes with weak or missing checksum settings. The [*ReadingQuality*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderesult/properties/readingquality) value should be analyzed. Even with high values (close to 80), absolute recognition accuracy is not guaranteed.|
|Strong|100|Returned for all 2D barcodes with Reed-Solomon error correction when the *QualitySettings.AllowIncorrectBarcodes* setting is not enabled. This indicates that the barcode text has been decoded correctly and the recognition process was successful.|

The following code snippet shows how to obtain the recognition quality estimate for a sample barcode image.

  
```javascript
// Recognize image
console.log("ReadExtQuality:");
var reader = new BarCodeInstance.BarCodeReader("img.png", "QR");
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`CodeType: ${result.CodeType}`);
    console.log(`CodeText: ${result.CodeText}`);
    console.log(`Confidence: ${result.Confidence}`);
    console.log(`ReadingQuality: ${result.ReadingQuality}`);
}

reader.delete();

```

  
