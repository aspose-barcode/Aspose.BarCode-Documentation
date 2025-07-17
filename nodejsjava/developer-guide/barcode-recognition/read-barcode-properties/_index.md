---
title: Read Barcode Properties and Metadata
type: docs
description: "This article describes how to read barcode parameters and encoded metadata"
keywords: Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcodes in Node.js
ai_search_scope: "barcode_nodejsjava_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 40
url: /nodejsjava/read-barcode-properties/

---

{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can test the quality of ***Aspose.BarCode*** recognition functionality and view the results online.{{% /alert %}}
  
## **Overview**
***Aspose.BarCode for Node.js via Java*** not only enables reading information encoded in a barcode but also provides a possibility to analyze its technical properties, including symbology, orientation angle, position, and metadata. This data is stored in objects of class [*BarCodeResult*](https://reference.aspose.com/barcode/nodejs/BarCodeResult) and can be fetched using special methods described further in this article.  


{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/nodejsjava/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Barcode Type and Encoded Data**
To obtain input barcode data and its symbology, *getCodeText* and *getCodeType* methods of class [*BarCodeResult*](https://reference.aspose.com/barcode/nodejs/BarCodeResult) can be used. The other method called *getCodeTypeName* returns the text name of the barcode type.
  
``` java
//This sample shows how to obtain BarCodeResult.
let generator = new BarcodeGenerator(EncodeTypes.Code128, "12345");
generator.save("test.png");
let reader = new BarCodeReader("test.png", null,  [ DecodeType.CODE_39_STANDARD, DecodeType.CODE_128 ]);
reader.readBarCodes().forEach(function(result, i, results)
{
    console.log("BarCode Type: " + result.getCodeTypeName());
    console.log("BarCode CodeText: " + result.getCodeText());
    console.log("BarCode Confidence: " + result.getConfidence());
    console.log("BarCode ReadingQuality: " + result.getReadingQuality());
    console.log("BarCode Angle: " + result.getRegion().getAngle());
});
```

<p align="center"><img src="qrcodetext.png"></p> 
  
## **Read Barcode Data as Byte Stream**
It is possible to load barcode data as a byte stream using a special method of class [*BarCodeResult*](https://reference.aspose.com/barcode/nodejs/BarCodeResult) that is called *getCodeBytes*. 

<p align="center"><img src="extcodebytes.png"></p>

## **Decode Barcode Text in Unicode**
For barcodes in which the barcode data is encoded in a Unicode encoding, the library provides the *getCodeText* method that can be used to enable the required encoding.  
  
<p align="center"><img src="extunicodecodetext.png"></p>
   
## **Quality Check of Barcode Reading Results**
Developers may need to check whether barcode reading outputs are accurate and complete. For this purpose, ***Aspose.BarCode for Node.js via Java*** provides two specific methods of class [*BarCodeResult*](https://reference.aspose.com/barcode/nodejs/BarCodeResult): *getConfidence* and *getReadingQuality*.  
Depending of the quality of barcode reading results, the *getConfidence* method returns a instance of the [*BarCodeConfidence*](https://reference.aspose.com/barcode/nodejs/global#BarCodeConfidence) global property that denotes the recognition confidence level. It contains values *STRONG*, *NONE*, and *MODERATE* that are discussed below. The *getReadingQuality* method returns an estimate of recognition quality corresponding to the confidence level, as explained in the table below.
  
|Confidence Level|Quality Value|Description|
|---|---|---|
|*NONE*|0|If the confidence level is *None*, it indicates that the barcode is invalid and its information has been read with errors. If required, it is possible to get its symbology and position in the image and decode barcode information partially|
|*MODERATE*|80|This confidence level may be returned for linear and postal barcode types with weak or absent checksum controls. Furthermore, it is necessary to analyze the result of the *getReadingQuality* method. The absolute correctness of barcode reading results is not assured|
|*STRONG*|100|This confidence level is returned for all 2D types with Reed-Solomon error correction. It means that barcode text has been recognized accurately|
    
``` java
//This sample shows how to set BarCodeConfidence
//Moderate confidence
let generator = new BarcodeGenerator(EncodeTypes.CODE_128, "12345");
generator.save("test.png");
let reader = new BarCodeReader("test.png", null,  [DecodeType.CODE_39_STANDARD, DecodeType.CODE_128]);
reader.readBarCodes().forEach(function(result, i, results)
{
   console.log("BarCode Type: " + result.getCodeTypeName());
   console.log("BarCode CodeText: " + result.getCodeText());
   console.log("BarCode Confidence: " + result.getConfidence());
   console.log("BarCode ReadingQuality: " + result.getReadingQuality());
});
//Strong confidence
let generator = new BarcodeGenerator(EncodeTypes.QR, "12345");
generator.save("test.png");
let reader = new BarCodeReader("test.png", null,  [DecodeType.CODE_39_STANDARD, DecodeType.QR]);
reader.readBarCodes().forEach(function(result, i, results)
{
    console.log("BarCode Type: " + result.getCodeTypeName());
    console.log("BarCode CodeText: " + result.getCodeText());
    console.log("BarCode Confidence: " + result.getConfidence());
    console.log("BarCode ReadingQuality: " + result.getReadingQuality());
});
```

## **Barcode Position and Orientation Angle**
To obtain the position of a source barcode and its orientation angle, methods class [*BarCodeRegionParameters*](https://reference.aspose.com/barcode/nodejs/BarCodeRegionParameters) can be used. This class allows getting the information about the barcode region in the following forms:
-	Quadrangle – a quadrangle object that bounds a barcode
-	Rectangle - a rectangle object that bounds a barcode
-	Points – an array of points constituting a barcode
-	Angle – an orientation angle in degrees

``` java
//This sample shows how to get barcode angle and bounding quadrangle values
let generator = new BarcodeGenerator(EncodeTypes.Code128, "12345");
generator.save("test.png");
let reader = new BarCodeReader("test.png", null,  [ DecodeType.CODE_39_STANDARD, DecodeType.CODE_128 ]);
reader.readBarCodes().forEach(function(result, i, results)
{
   console.log("BarCode CodeText: " + result.getCodeText());
   console.log("BarCode Angle: " + result.getRegion().getAngle());
   console.log("BarCode Quadrangle: " + result.getRegion().getQuadrangle());
});
```

<p align="center"><img src="qr_code128.png" width="20%" height="20%"></p>

## **Barcode Metadata**

### **Read Macro PDF417 and Macro PDF417 Metadata**
Metadata from *PDF417* barcodes can be obtained using methods of class [*Pdf417ExtendedParameters*](https://reference.aspose.com/barcode/nodejs/Pdf417ExtendedParameters) listed below.
  
|PDF417 Metadata Method|Description|
|---|---|
|*getPdf417MacroFileID*|Gets the unique identifier of a barcode series or a PDF417 file|
|*getPdf417MacroSegmentID*|Gets the current identifier of a segment|
|*getPdf417MacroSegmentsCount*|Returns the number of barcodes in a series|
|*getPdf417MacroFileName*|Returns the name of a file|
|*getPdf417MacroChecksum*|Gets the checksum value computed using CCITT-16 polynomial|
|*getPdf417MacroFileSize*|Returs the total size of bytes in a series|
|*getPdf417MacroTimeStamp*|Returns the time spent to generate/send the file|
|*getPdf417MacroAddressee*|Gets the address of the file sender|
|*getPdf417MacroSender*|Returns the name of the file sender|
    

``` java
//This sample shows how to get MacroPdf417 metadata
let generator = new BarcodeGenerator(EncodeTypes.MacroPdf417, "12345");
generator.getParameters().getBarcode().getPdf417().setPdf417MacroFileID(10);
generator.getParameters().getBarcode().getPdf417().setPdf417MacroSegmentsCount(2);
generator.getParameters().getBarcode().getPdf417().setPdf417MacroSegmentID(1);
generator.save("test.png");
let reader = new BarCodeReader("test.png", null,  DecodeType.MACRO_PDF_417);
reader.readBarCodes().forEach(function(result, i, results)
{
    console.log("BarCode Type: " + result.getCodeTypeName());
    console.log("BarCode CodeText: " + result.getCodeText());
    console.log("Macro Pdf417 FileID: " + result.getExtended().getPdf417().getMacroPdf417FileID());
    console.log("Macro Pdf417 Segments: " + result.getExtended().getPdf417().getMacroPdf417SegmentsCount());
    console.log("Macro Pdf417 SegmentID: " + result.getExtended().getPdf417().getMacroPdf417SegmentID());
});
```
    
<p align="center"><img src="extpdf417meta.png"></p>  

### **Read Barcode Metadata from QR Codes with Structured Append**
To fetch metadata from *QR Code* barcodes with structured append, the barcode library provides the [*QRExtendedParameters*](https://reference.aspose.com/barcode/nodejs/QRExtendedParameters) class. Methods of this class enable reading the information from structured append that is used to combine several *QR Code* barcode into one. This data can be obtained using the following methods:

- *getQRStructuredAppendModeBarCodeIndex* - returns the sequence number of the current barcode (starting from 0)
- *getQRStructuredAppendModeBarCodesQuantity* - returns the number of barcodes in a composite *QR Code* barcode taht can take values from 2 to 16
- *getQRStructuredAppendModeParityData* - returns the checksum identifier byte that is usually computed as *XOR* of all bytes in which UTF16BE characters are encoded in two bytes  
  
``` java
//This sample shows how to get QR Structured Append data

let reader = new BarCodeReader("test.png", null,  DecodeType.QR);
reader.readBarCodes().forEach(function(result, i, results)
{
   console.log("BarCode Type: " + result.getCodeTypeName());
   console.log("BarCode CodeText: " + result.getCodeText());
   console.log("QR Structured Append Quantity: " + result.getExtended().getQR().getQRStructuredAppendModeBarCodesQuantity());
   console.log("QR Structured Append Index: " + result.getExtended().getQR().getQRStructuredAppendModeBarCodeIndex());
   console.log("QR Structured Append ParityData: " + result.getExtended().getQR().getQRStructuredAppendModeParityData());
});
```

<p align="center"><img src="extqrmeta.png"></p>
  
### **Read Barcode Metadata from DataBar with 2D Components**
Metadata from *DataBar* barcodes with 2D components can be obtained using class called [*DataBarExtendedParameters*](https://reference.aspose.com/barcode/nodejs/DataBarExtendedParameters) that provides a special method called *is2DCompositeComponent*. This methods allows enabling or disabling a 2D component in *DataBar* barcodes.  

``` java
let reader = new BarCodeReader("c:\\test.png", DecodeType.DATABAR_OMNI_DIRECTIONAL);
reader.readBarCodes().forEach(function(result, i, results)
{
   console.log("BarCode Type: " + result.getCodeTypeName());
   console.log("BarCode CodeText: " + result.getCodeText());
   console.log("QR Structured Append Quantity: " + result.getExtended().getQR().getQRStructuredAppendModeBarCodesQuantity());
});
```
  
<p align="center"><img src="extdatabarmeta.png"></p>

### **Read Metadata from 1D Barcodes**
Some 1D barcode types, i.e. *EAN-13*, allow separating barcode input information itself from the checksum value. To do this, class [*OneDExtendedParameters*](https://reference.aspose.com/barcode/nodejs/OneDExtendedParameters) provides the *getValue* method that allows getting 1D barcode text and the *getCheckSum* method that returns the result of checksum computation.

``` java
//This sample shows how to get 1D barcode value and checksum
let generator = new BarcodeGenerator(EncodeTypes.EAN_13, "1234567890128");
generator.save("test.png");
let reader = new BarCodeReader("test.png", null,  DecodeType.EAN_13);
reader.readBarCodes().forEach(function(result, i, results)
{
   console.log("BarCode Type: " + result.getCodeTypeName());
   console.log("BarCode CodeText: " + result.getCodeText());
   console.log("BarCode Value: " + result.getExtended().getOneD().getValue());
   console.log("BarCode Checksum: " + result.getExtended().getOneD().getCheckSum());
});
```  
 
<p align="center"><img src="ean13.png"></p>
  
### **Get Raw Data from Code 128 Barcodes**
Input data stored in *Code 128* barcodes can be encoded in three ways: A, B, or C. Class [*Code128ExtendedParameters*](https://reference.aspose.com/barcode/nodejs/Code128ExtendedParameters) provides the *getCode128DataPortions* method that returns decoded parts of barcode input information and the encoding mode.

``` java
//This sample shows how to get Code128 raw values
let generator = new BarcodeGenerator(EncodeTypes.Code128, "12345");
generator.save("test.png");
let reader = new BarCodeReader("test.png", null,  DecodeType.CODE_128);
reader.readBarCodes().forEach(function(result, i, results)
{
   console.log("BarCode Type: " + result.getCodeTypeName());
   console.log("BarCode CodeText: " + result.getCodeText());
   console.log("Code128 Data Portions: " + result.getExtended().getCode128());
});
```

<p align="center"><img src="code128.png"></p>
