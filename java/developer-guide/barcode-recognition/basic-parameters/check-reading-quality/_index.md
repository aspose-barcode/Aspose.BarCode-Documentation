---
title: Check Barcode Recognition Quality
linktitle: Check Recognition Quality
type: docs
feedback: BARCODECOM
description: "This article describes how to verify barcode recognition quality"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode C#"
weight: 50
url: /java/check-recognition-quality/
---

Developers may need to check whether barcode reading outputs are accurate and complete. For this purpose, ***Aspose.BarCode for Java*** provides two specific methods of class [*BarCodeResult*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult): *getConfidence* and *getReadingQuality*.  
Depending of the quality of barcode reading results, the *getConfidence* method returns a instance of the [*BarCodeConfidence*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeConfidence) enum that denotes the recognition confidence level. This enumeration contains values *STRONG*, *NONE*, and *MODERATE* that are discussed below. The *getReadingQuality* method returns an estimate of recognition quality corresponding to the confidence level, as explained in the table below.
  
|Confidence Level|Quality Value|Description|
|---|---|---|
|*NONE*|0|If the confidence level is *None*, it indicates that the barcode is invalid and its information has been read with errors. If required, it is possible to get its symbology and position in the image and decode barcode information partially|
|*MODERATE*|80|This confidence level may be returned for linear and postal barcode types with weak or absent checksum controls. Furthermore, it is necessary to analyze the result of the *getReadingQuality* method. The absolute correctness of barcode reading results is not assured|
|*STRONG*|100|This confidence level is returned for all 2D symbologies with Reed-Solomon error correction. It means that barcode text has been recognized accurately|
  
<!--The following code sample shows how to obtain the recognition quality estimate.
  
{{< highlight java>}}
//recognize image
Console.WriteLine("ReadExtQuality:");
using (BarCodeReader read = new BarCodeReader($"{path}qr_code128.png", DecodeType.QR, DecodeType.Code128))
{
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine($"Confidence:{result.Confidence.ToString()}");
        Console.WriteLine($"ReadingQuality:{result.ReadingQuality.ToString()}");
    }
}
{{< /highlight >}}-->
