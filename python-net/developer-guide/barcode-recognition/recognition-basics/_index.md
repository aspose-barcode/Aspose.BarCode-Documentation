---
title: Barcode Reading Basics
type: docs
description: "This Article Describes How to Read Barcodes of Different Symbologies from Images or Stream and How to Recognize All 1D Barcodes Presented in an Image"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcodes in Python"
weight: 10
url: /python-net/read-barcodes/
---

## **Overview**
Class [*BarCodeReader*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/) in ***Aspose.BarCode for Python via .NET*** is the most important to implement barcode recognition for more than 60 symbologies. First, it is necessary to identify a barcode source that can be represented as a file, a stream, or a bitmap object. After that, target barcode types need to be specified using values from the [*DecodeType*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/decodetype/) enum. By default, the library uses the *DecodeType.ALL_SUPPORTED_TYPES* setting that implies iterating over all supported barcode types to check for their presence in the source image. In this case, barcode scanning and recognition take much more time. 


{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Main Recognition Parameters**
Barcode reading is performed according to the following steps:
-	Determine the barcode source (image file, stream, or bitmap), e.g. set the path to a source image
-	Select target barcode types. [*DecodeType*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/decodetype/) is set to *DecodeType.ALL_SUPPORTED_TYPES* by default meaning that the source image will be scanned to search for all supported barcode types; in this case, the time required to finish the barcode detection process will increase.  
  
Class [*BarCodeReader*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/) contains the *read_bar_codes()* method that returns the result of barcode reading in an array of the [*BarCodeResult*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/) type.  

<p align="center"><img src="multiple_codes.png" hight="50%" width="50%"></p>  

  
## **Get Recognition Results**
To load barcode recognition outputs, it is needed to call the *read_bar_codes()* method that gets an array of the [*BarCodeResult*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/) type. Moreover, the current recognition output can be accessed through the *found_bar_codes* property that enables fetching decoding results or the *found_count* property that returns the number of detected barcodes.  
   
## **Recognition Abortion**
Class [*BarCodeReader*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/) enables two ways to interrupt the recognition process if it becomes unfeasible to complete. The first one is to initialize the *time_out* property that defines a timeout value for the barcode reading process . By default, the *TimeOut* value is set to 0.  
  
The second way is to use the *abort()* method. This option is used if the recognition process has been launched in the other thread. This method does not stop the entire process and returns controls immediately.  

  