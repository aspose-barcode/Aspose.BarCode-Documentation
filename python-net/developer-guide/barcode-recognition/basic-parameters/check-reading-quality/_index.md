---
title: Check Barcode Recognition Quality
linktitle: Check Recognition Quality
type: docs
description: "This article describes how to verify barcode recognition quality"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode C#"
weight: 50
url: /python-net/check-recognition-quality/
---

## **Quality Check of Barcode Reading Results**
Developers may need to check whether barcode reading outputs are accurate and complete. For this purpose, class [*BarCodeResult*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/) contains two properties: *confidence* and *reading_quality*.  
Depending of the quality of barcode reading results, the *confidence* property returns a instance of the [*BarCodeConfidence*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodeconfidence/) enum that denotes the recognition confidence level. This enumeration contains values *STRONG*, *NONE*, and *MODERATE* that are discussed below. The *reading_quality* property returns an estimate of recognition quality corresponding to the confidence level, as explained in the table below.
  
|Confidence Level|Quality Value|Description|
|---|---|---|
|*NONE*|0|If the confidence level is *None*, it indicates that the barcode is invalid and its information has been read with errors. If required, it is possible to get its type and position in the image and decode barcode information partially|
|*MODERATE*|80|This confidence level may be returned for linear and postal barcode types with weak or absent checksum controls. Furthermore, it is necessary to analyze the result of the *reading_quality* property. The absolute correctness of barcode reading results is not assured|
|*STRONG*|100|This confidence level is returned for all 2D types with Reed-Solomon error correction. It means that barcode text has been recognized accurately|
  

