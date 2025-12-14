---
title: Barcode Reading Basics
type: docs
description: "This Article Describes How to Read Barcodes of Different Symbologies from Images or Stream and How to Recognize All 1D Barcodes Presented in an Image"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcodes in Node.js"
ai_search_scope: "barcode_nodejsjava_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 10
url: /nodejsjava/barcode-reading-basics/

---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can test the quality of ***Aspose.BarCode*** recognition functionality and view the results online.{{% /alert %}}

## **Overview**
Class [*BarCodeReader*](https://reference.aspose.com/barcode/nodejs/BarCodeReader) in ***Aspose.BarCode for Node.js via Java*** is the most important to implement barcode recognition for more than 60 symbologies. First, it is necessary to indentify a barcode source that can be represented as a file, a stream, or a bitmap object. After that, target symbologies needs to be specified using values from the [*DecodeType*](https://reference.aspose.com/barcode/nodejs/global#DecodeType) global property. By default, the library uses the *DecodeType.ALL_SUPPORTED_TYPES* setting that implies iterating over all supported barcode types to check for their presence in the source image. In this case, barcode scanning and recognition takes much more time. Developers can specify explicitly not only the desired symbologies but also a target region or regions in the source image. This allows optimizing the scanning process by avoiding areas without barcodes. Target regions can be determined using class [*Rectangle*](https://reference.aspose.com/barcode/nodejs/Rectangle).

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/nodejsjava/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Main Recognition Parameters**
In ***Aspose.BarCode for Node.js via Java***, barcode reading is performed according to the following steps:
-	Determine the barcode source (image file, stream, or bitmap), e.g. set the path to a source image
-	Select target barcode types. [*DecodeType*](https://reference.aspose.com/barcode/nodejs/global#DecodeType) is set to *DecodeType.ALL_SUPPORTED_TYPES* by default meaning that the sources image will be scanned to search for all supported barcode types; in this case, time required to finish the barcode detection process will increase.  
  
The library contains the *ReadBarCodes* method of class [*BarCodeReader*](https://reference.aspose.com/barcode/nodejs/BarCodeReader) that returns the result of barcode reading in an array of the [*BarCodeResult*](https://reference.aspose.com/barcode/nodejs/BarCodeResult) type.  

<p align="center"><img src="multiple_codes.png" hight="50%" width="50%"></p>  

``` java
//This sample shows how to detect and read Code39 and Code128 barcodes
let reader = new BarCodeReader("test.png", null,  [DecodeType.CODE_39_STANDARD, DecodeType.CODE_128]);
reader.readBarCodes().forEach(function(result, i, results)
{
   console.log("BarCode Type: " + result.getCodeTypeName());
   console.log("BarCode CodeText: " + result.getCodeText());
});
```
  
## **Get Barcode Reading Results**
To load barcode reading results, it is needed to call the *ReadBarCodes* method that provides a [*BarCodeResult*](https://reference.aspose.com/barcode/nodejs/BarCodeResult) array. The current output can be accessed using the *getFoundBarCodes* method that enables getting decoding results or the *getFoundCount* method that returns the number of detected barcodes.  

``` java
//This sample shows how to obtain the barcode reading result
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

``` java
//This sample shows how to read barcodes with BarCodeReader
let reader = new BarCodeReader("test.png", null,  [ DecodeType.CODE_39_STANDARD, DecodeType.CODE_128 ]);
reader.readBarCodes();
for(let i = 0; reader.getFoundCount() > i; ++i)
   console.log("BarCode CodeText: " +  reader.getFoundBarCodes()[i].getCodeText());
```

``` java
//This sample shows how to read barcodes with BarCodeReader
let reader = new BarCodeReader("test.png", null,  [ DecodeType.CODE_39_STANDARD, DecodeType.CODE_128 ]);
reader.readBarCodes();
for(let i = 0; reader.getFoundCount() > i; ++i)
   console.log("BarCode CodeText: " + reader.getFoundBarCodes()[i].getCodeText());
Value: The recognized barcodes count
```

## **Set Source Barcode**
In ***Aspose.BarCode for Node.js via Java***, there are three ways to set the barcode recognition source: from an image file, from a bitmap, or from a stream. The following five raster image formats are supported: PNG, JPEG, BMP, TIFF, or GIF. Three options to set the source for barcodes reading are explained further. 

### **Read Barcodes from Files**
First of all, barcodes can be scanned and recognized from image files. The full or relative path to the source needs to be specified in the *BarCodeReader* constructor. Alternatively, the *setBarCodeImage* method can be used to pass the path to the existing object of class [*BarCodeReader*](https://reference.aspose.com/barcode/nodejs/BarCodeReader).  
  
### **Read Barcodes from Bitmap Objects**
In ***Aspose.BarCode for Node.js via Java***, it is possible to use a graphical object or a bitmap as a source for barcode reading. Bitmap objects allow working with images consisting of pixel data. To read barcodes from a bitmap, the created bitmap object needs to be passed to the *BarCodeReader()* constructor or the *setBarCodeImage* method.  


### **Read Barcodes from Streams**
In ***Aspose.BarCode for Node.js via Java***, a stream (in a binary format) can be also used as a source for barcode recognition. This option can be useful in some situations owing to its versatility and accessibility without file systems. A stream to read barcodes from needs to be passed to the *BarCodeReader()* constructor or the *setBarCodeImage* method.


## **Setting Target Barcode Types**
***Aspose.BarCode for Node.js via Java*** supports barcode recognition for 60+ various barcode types. To improve the efficiency of the recognition process and optimize its timing, it is recommended to set target symbologies in advance. Otheriwse, the *DecodeType.ALL_SUPPORTED_TYPES* setting of the [*DecodeType*](https://reference.aspose.com/barcode/nodejs/global#DecodeType) global property will be used by default meaning that the library will look over all supported barcode types to check for their presence in the source image. Using this setting will increase the time needed to complete barcode recognition. 

### **Listing Target Barcode Types in DecodeType**
Target barcode types can be specified by grouping them in a list and passing it to the *BarCodeReader()* constructor or the *setBarCodeReadType* method.  


### **Using Predefined Sets for Barcode Types**
The [*DecodeType*](https://reference.aspose.com/barcode/nodejs/global#DecodeType) global property enables the following options for barcode reading:
-	*ALL_SUPPORTED_TYPES* - all available barcode types
-	*TYPES_1D* - all supported 1D types
-	*TYPES_2D* - all supported 2D types
-	*POSTAL_TYPES* - all available postal types
-	*MOST_COMMON_TYPES* - a set of most widespread barcode types defined according to Aspose recommendations

The required set can be specified in the *BarCodeReader* constructor or passed to the *setBarCodeReadType* method.

``` java
//This sample shows how to detect 1D barcodes
let reader = new BarCodeReader("test.png", null,  [DecodeType.TYPES_1D]);
reader.readBarCodes().forEach(function(result, i, results)
{
   console.log("BarCode Type: " + result.getCodeTypeName());
   console.log("BarCode CodeText: " + result.getCodeText());
});
```

## **Setting Target Barcode Regions**
In ***Aspose.BarCode for Node.js via Java***, it is possible to specify target areas for barcode detection by creating one or several objects of class [*Rectangle*](https://reference.aspose.com/barcode/nodejs/Rectangle). Setting target regions allows improving recognition efficiency and avoiding the regions without any barcodes. Target areas have to be determined accurately as the Aspose library apply heuristic approaches to identify target barcode detection areas. Focusing on too many image regions can lead to recognition efficiency deterioration.

### **Unique Target Region**
To set one target area for barcode recognition, it is necessary to create an object of class [*Rectangle*](https://reference.aspose.com/barcode/nodejs/Rectangle) and then pass it to the *BarCodeReader* constructor or the *setBarCodeImage* method.  
  

### **Several Target Regions**
It is also possible to set several target areas for barcode detection within the one source image. This can be done in the same way as described above for one target region, i.e., using the *BarCodeReader* constructor or the *setBarCodeImage* method.  
  


## **Recognition Abortion Using Manual and Timeout Methods**
Class [*BarCodeReader*](https://reference.aspose.com/barcode/nodejs/BarCodeReader) enables a method to interrupt the barcode reading process if it becomes unfeasible to complete. This method is called *setTimeOut* and is aimed to interrupt the barcode reading process immediately after the timeout value gets exceeded. By default, the *TimeOut* value is set to 0. It throws an exception called [*RecognitionAbortedException*](https://reference.aspose.com/barcode/nodejs/RecognitionAbortedException) if the recognition process could not be completed successfully.
  