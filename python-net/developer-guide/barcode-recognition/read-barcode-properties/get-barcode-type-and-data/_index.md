---
title: Get Barcode Type and Encoded Data
type: docs
description: "This article describes how to read barcode parameters"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcode C#"
ai_search_scope: "barcode_python-net_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 10
url: /python-net/get-barcode-type-and-data/
---
  
## **Get Barcode Type and Encoded Data**
To obtain input barcode data and its type, *code_text* and *code_type* properties of class [*BarCodeResult*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/) can be used. The other property called *code_type_name* returns the text name of the barcode type.


<p align="center"><img src="qrcodetext.png"></p> 
  
## **Get Barcode Data as Byte Stream**
It is possible to load barcode data as a byte stream using a property of class [*BarCodeResult*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/) that is called *code_bytes*. 

<p align="center"><img src="extcodebytes.png"></p>

## **Decode Barcode Text in Unicode**
For barcodes in which the barcode data is encoded in a Unicode encoding, the barcode library provides the *get_code_text(encoding)* method that can be used to enable the required encoding.  

<p align="center"><img src="extunicodecodetext.png"></p>
