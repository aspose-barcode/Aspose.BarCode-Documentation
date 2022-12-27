---
title: Barcode Reading Basics
type: docs
description: "This Article Describes How to Read Barcodes of Different Symbologies from Images or Stream and How to Recognize All 1D Barcodes Presented in an Image"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcodes in Python"
weight: 10
url: /python-net/read-barcodes/
---

## **Overview**
Class [*BarCodeReader*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/) in ***Aspose.BarCode for Python via .NET*** is the most important to implement barcode recognition for more than 60 symbologies. First, it is necessary to identify a barcode source that can be represented as a file, a stream, or a bitmap object. After that, target barcode types need to be specified using values from the [*DecodeType*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/decodetype/) enum. By default, the library uses the *DecodeType.ALL_SUPPORTED_TYPES* setting that implies iterating over all supported barcode types to check for their presence in the source image. In this case, barcode scanning and recognition take much more time. Developers can specify explicitly not only the desired types but also a target region or regions in the source image. This allows optimizing the scanning process by avoiding areas without barcodes. Target regions can be determined using a class called [*Quadrangle*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/quadrangle/).


{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Main Recognition Parameters**
Barcode reading is performed according to the following steps:
-	Determine the barcode source (image file, stream, or bitmap), e.g. set the path to a source image
-	Select target barcode types. [*DecodeType*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/decodetype/) is set to *DecodeType.ALL_SUPPORTED_TYPES* by default meaning that the source image will be scanned to search for all supported barcode types; in this case, the time required to finish the barcode detection process will increase.  
  
Class [*BarCodeReader*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/) contains the *read_bar_codes()* method that returns the result of barcode reading in an array of the [*BarCodeResult*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/) type.  

<p align="center"><img src="multiple_codes.png" hight="50%" width="50%"></p>  

  
## **Getting Recognition Results**
To load barcode recognition outputs, it is needed to call the *read_bar_codes()* method that gets an array of the [*BarCodeResult*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/) type. Moreover, the current recognition output can be accessed through the *found_bar_codes* property that enables fetching decoding results or the *found_count* property that returns the number of detected barcodes.  
  

## **Barcode Recognition Source**
There are three ways to set the barcode recognition source: from an image file, a bitmap, or a stream. The following five raster image formats are supported: PNG, JPEG, BMP, TIFF, or GIF. Three options to set the barcode reading source are explained further. 


### **Read Barcodes from Files**
First of all, barcodes can be scanned and recognized from image files. The full or relative path to the source needs to be specified in the *BarCodeReader* constructor. Alternatively, the *set_bar_code_image* method can be used to pass the path to the existing object of class [*BarCodeReader*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/).  


### **Read Barcodes from Bitmap Objects**
It is possible to use a graphical object or a bitmap as a source for barcode reading. Bitmap objects allow working with images consisting of pixel data. To read barcodes from a bitmap, the created bitmap object needs to be passed to the *BarCodeReader()* constructor or the *set_bar_code_image* method. 

### **Read Barcodes from Streams**
In ***Aspose.BarCode for Python via .NET***, a stream (in a binary format) can be also used as a source for barcode recognition. This option can be useful in some situations owing to its versatility and accessibility without file systems. A stream to read barcodes from needs to be passed to the *BarCodeReader()* constructor or the *set_bar_code_image* method.

## **Setting Target Barcode Types**
***Aspose.BarCode for Python via .NET*** supports barcode recognition for 60+ various barcode types. To improve the efficiency of the recognition process and optimize its timing, it is recommended to set target symbologies in advance. Otheriwise, the *ALL_SUPPORTED_TYPES* setting of the [*DecodeType*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/decodetype/) enum will be used by default meaning that the library will look over all supported barcode types to check for their presence in the source image. Using this setting will increase the time needed to complete barcode recognition. 

### **Listing Target Barcode Types in DecodeType**
Target barcode types can be specified by grouping them in a list and passing it to the *BarCodeReader()* constructor or the *set_bar_code_read_type* method.  

### Using ***MultyDecodeType* Mode**
The other way to specify target barcode types is to determine them using a constructor of class [*MultyDecodeType*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/multydecodetype/) and then pass it to class [*BarCodeReader*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/) or the *set_bar_code_read_type* method.  

### **Using Predefined Barcode Type Sets**
Class [*DecodeType*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/decodetype/) provides the following symbology sets for barcode reading:
-	*ALL_SUPPORTED_TYPES* - all available barcode types
-	*TYPES_1D* - all supported 1D types
-	*TYPES_2D* - all supported 2D types
-	*POSTAL_TYPES* - all available postal types
-	*MOST_COMMON_TYPES* - a set of most widespread barcode types defined according to Aspose recommendations

The required set can be specified in the *BarCodeReader* constructor or passed to the *bar_code_read_type* property.
  
## **Recognition Abortion**
Class [*BarCodeReader*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/) enables two ways to interrupt the recognition process if it becomes unfeasible to complete. The first one is to initialize the *time_out* property that defines a timeout value for the barcode reading process . By default, the *TimeOut* value is set to 0.  
  
The second way is to use the *abort()* method. This option is used if the recognition process has been launched in the other thread. This method does not stop the entire process and returns controls immediately.  

  