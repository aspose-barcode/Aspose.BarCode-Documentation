---
title: Get Barcode Type and Encoded Data
type: docs
description: "This article describes how to read barcode parameters"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode C++"
weight: 10
feedback: BARCODECOM
url: /cpp/get-barcode-type-and-data/
---
  
## **Decode Barcode Type and Data**
To get the data encoded in a barcode and identify its type, class [*BarCodeResult*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult) provides the two most important fields, [*CodeText*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/codetext) and [*CodeType*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/codetype), respectively. The other parameter [*CodeTypeName*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/codetypename) represents the text name of a barcode symbology.
  
<p align="center"><img src="qrcodetext.png"></p> 
  
## **Read Barcode Data as Byte Stream**
In cases when it is necessary to get the data encoded in a barcode in the form of a byte stream, it can be read from the specific field of class [*BarCodeResult*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult) that is called [*CodeBytes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/codebytes).  
  

<p align="center"><img src="extcodebytes.png"></p>

## **Decode Barcode Data in Unicode Format**
In cases when the barcode data is encoded using a particular Unicode encoding, it can be read by calling the [*GetCodeText*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/methods/getcodetext) method and specifying the required encoding.  
  

<p align="center"><img src="extunicodecodetext.png"></p>
   
  
