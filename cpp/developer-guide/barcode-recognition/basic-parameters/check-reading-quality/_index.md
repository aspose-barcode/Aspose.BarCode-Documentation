---
title: Check Barcode Recognition Quality
linktitle: Check Recognition Quality
type: docs
description: "This article describes how to verify barcode recognition quality"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode C#"
weight: 50
url: /cpp/check-recognition-quality/
---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**

In many cases, it is necessary to estimate whether the barcode has been recognized accurately. In ***Aspose.BarCode for C++***, this can be done using two specific properties of class [*BarCodeResult*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult): [*Confidence*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/confidence) and [*ReadingQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/readingquality).  

## **Verify Barcode Reading Quality**

As a result of barcode reading, the [*Confidence*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/confidence) property returns a value from the [*BarCodeConfidence*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodeconfidence) enumeration that corresponds to the recognition confidence level. Possible values of the [*BarCodeConfidence*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodeconfidence) enumeration (*None*, *Moderate*, and *Strong*) are explained in the table below. The [*ReadingQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/readingquality) parameter returns the estimate of recognition quality according to the identified confidence level: 0 for *None*; from 1 to 99; 100 for *Strong*.
  
|Confidence Level|Reading Quality Value|Description|
|---|---|---|
|None|0|If the confidence level returns *None*, it usually means that the source barcode is incorrect and its input data has been decoded with errors. However, it is still possible to get its type and place orientation in the source image, as well as partially decode inputted data|
|Moderate|80|Is returned for 1D and postal barcodes with weak or missing checksum settings. In this case, it is required to analyze the value of [*ReadingQuality*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/readingquality); however, even in the case of high values (close to 80), the absolute correctness of barcode recognition is not guaranteed|
|Strong|100|Is returned for all 2D barcode types with Reed-Solomon error correction in case the quality setting has not been set to *QualitySettings.AllowIncorrectBarcodes*. When this confidence level is returned, it means that barcode text has been decoded correctly, and the recognition process has been completed successfully|
  
  
