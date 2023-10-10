---
title: Read Barcode Properties
type: docs
description: "This article describes how to read barcode parameters"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode C#"
notoc: true
weight: 30
url: /java/read-barcode-properties/
---

***Aspose.BarCode for Java*** not only enables reading information encoded in a barcode but also provides a possibility to analyze its technical properties, including symbology, orientation angle, position, and metadata. This data is stored in objects of class [*BarCodeResult*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult) and can be fetched using special methods described further in this section.  
  
The articles listed below describe how to get the required information about barcode properties using the functionality of ***Aspose.BarCode for Java***.

|Article|Description|
|---|---|
|[Get Barcode Placement Region and Orientation Angle](/barcode/java/get-placement-and-orientation/)|Explains how to get information about barcode coordinates and rotation angle|
|[Get Barcode Type and Encoded Data](/barcode/java/get-barcode-type-and-data/)|Demostrates how to fetch the barcode type and data stored in this barcode|
|[Get Barcode Metadata](/barcode/java/read-barcode-metadata/)|Describes how to retrieve barcode metadata|



<!--The following code snippet illustrates how to get contents of the [*BarCodeResult*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult) instance.
 
 BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Code128, "12345");
 generator.save("c:\\test.png");
 BarCodeReader reader = new BarCodeReader("c:\\test.png", DecodeType.CODE_39_STANDARD, DecodeType.CODE_128);
 for(BarCodeResult result : reader.readBarCodes())
 {
     System.out.println("BarCode Type: " + result.getCodeTypeName());
     System.out.println("BarCode CodeText: " + result.getCodeText());
     System.out.println("BarCode Confidence: " + result.getConfidence());
     System.out.println("BarCode ReadingQuality: " + result.getReadingQuality());
     System.out.println("BarCode Angle: " + result.getRegion().getAngle());
 }-->  


