---
title: Basic Barcode Recognition Parameters
linktitle: Basic Reading Parameters
type: docs
description: "This Article Describes How Basic Recognition Parameters"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcode JavaScript"
feedback: BARCODECOM
weight: 10
---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can test the quality of ***Aspose.BarCode*** recognition functionality and view the results online.{{% /alert %}}

## **Overview**
***Aspose.BarCode for JavaScript via C++*** provides class [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) that enables barcode recognition from given images for more than 60 symbologies. In general, to perform barcode reading, first, it is necessary to specify the source of an image with barcodes to be detected as a file, a bitmap object, or a stream. Then, it is required to set target symbologies in the [*DecodeType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/decodetype) parameter; otherwise, barcode recognition will take more time, as using the default setting *DecodeType.AllSupportedTypes* implies looking over all supported symbologies to check for their presence in the source barcode image. In addition, developers can explicitly set the target region/regions in an image for barcode reading. It can be done using a .NET [*Rectangle*](https://docs.microsoft.com/dotnet/api/system.drawing.rectangle) object and allows avoiding the unnecessary search for barcodes in the image areas with no barcodes presented by default.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Basic Recognition Parameters**
To read barcodes presented in an image using ***Aspose.BarCode for JavaScript via C++***, the following steps need to be taken:
-	Specify the source to read barcodes (from an image file, a stream, or a bitmap), e.g. set the path to a source image
-	Select target symbologies for barcode recognition. By default, the [*DecodeType*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/decodetype) property is set to *DecodeType.AllSupportedTypes*; in this way, the barcode reading procedure will cover all supported barcode types. Such an approach leads to extra time costs required to complete barcode recognition.  
  
In ***Aspose.BarCode for JavaScript via C++***, barcode recognition is performed through the [*ReadBarCodes*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/readbarcodes) method that returns recognition results in an array of the [*BarCodeResult*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderesult) type.  
  
The following code snippet explains how to specify several target barcode types to be recognized in a single image, in this case, *PDF417*, *QR Code*, *Code 39*, and *Code 128*, as can be seen in the sample image provided below. As such, barcodes that do not correspond to the target symbologies (*DataMatrix* and *RM4SCC* barcodes in the given example) will be ignored.
  
```javascript
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadSimpleExample:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
```
  
<p align="center"><img src="multiple_codes.png" hight="50%" width="50%"></p>  


## **Get Recognition Results**
To get barcode recognition results, it is necessary to call the [*ReadBarCodes*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/readbarcodes) method that will output an array of the [*BarCodeResult*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcoderesult) type. At the same time, it is possible to get access to the current barcode reading output by using the [*FoundBarCodes*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/properties/foundbarcodes) property that stores recognition results or the [*FoundCount*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/properties/foundcount) parameter that returns the number of barcodes that have been processed.  
  
The following code sample illustrates how to load recognition results for the image provided above.
  
```javascript
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    //Read barcodes
    reader.ReadBarCodes();
    Console.WriteLine("ReadFoundBarCodes:");
    Console.WriteLine($"BarCodes count:{reader.FoundCount.ToString()}");
    foreach (BarCodeResult result in reader.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
```

## **Manual and Timeout Methods of Recognition Abortion**
Class [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) allows aborting the recognition process in case it is not further feasible. It can be done in two ways. The first option is to use the [*TimeOut*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/properties/timeout) property to interrupt the recognition process in case of exceeding the timeout value. By default, [*TimeOut*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/properties/timeout) is set to 0.  
  
The second way is to call the [*Abort*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader/methods/abort) method in case the recognition process has been launched in the other stream. This method does not block the entire process and returns control immediately.  
  
Both recognition abortion ways result in throwing an exception called [*RecognitionAbortedException*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/recognitionabortedexception) in the case when the recognition process has not been completed.
  
The following code snippet demonstrates an example of aborting the recognition process with the exception "*Recognition is aborted. Execution time: 342 ms*".
  
```javascript
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadWithTimeout:");
    reader.Timeout = 50;
    try
    {
        reader.ReadBarCodes();
    }
    catch(RecognitionAbortedException e)
    {
        Console.WriteLine(e.Message);
    }
}
```
