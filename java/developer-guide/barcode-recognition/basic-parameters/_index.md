---
title: Basic Barcode Recognition Parameters
linktitle: Basic Reading Parameters
type: docs
description: "This Article Describes How Basic Recognition Parameters"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Barcode in WPF Project, Aspose.BarCode, Read Barcode Java"
weight: 10
feedback: BARCODECOM
url: /java/basic-recognition-parameters/
aliases: 
- /java/barcode-recognition-basics/
- /node/read-barcodes-with-aspose-barcode-apis/

---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can test the quality of ***Aspose.BarCode*** recognition functionality and view the results online.{{% /alert %}}

## **Overview**
Class [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) in ***Aspose.BarCode for Java*** is the most important to implement barcode recognition for more than 60 symbologies. First, it is necessary to identify a barcode source that can be represented as a file, a stream, or a bitmap object. After that, target barcode types need to be specified using values from the [*DecodeType*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/DecodeType) enum. By default, the library uses the *DecodeType.ALL_SUPPORTED_TYPES* setting that implies iterating over all supported barcode types to check for their presence in the source image. In this case, barcode scanning and recognition take much more time. Developers can specify explicitly not only the desired types but also a target region or regions in the source image. This allows optimizing the scanning process by avoiding areas without barcodes. Target regions can be determined using a system class called [*Rectangle*](https://reference.aspose.com/imaging/java/com.aspose.imaging/Rectangle).  
  
In the barcode recognition process implemented in ***Aspose.BarCode for Java***, barcode data decoding is initiated according to the special protocol after scanning the raw data from a graphical representation. Some linear and postal barcode types have passed standardization after their wide implementation, and therefore, it has led to the presence of incompatible decoding formats. To resolve possible conflicts, class [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) provides a special class called [*BarcodeSettings*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarcodeSettings) used to manage barcode decoding settings.


{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Basic Recognition Parameters**
In ***Aspose.BarCode for Java***, barcode reading is performed according to the following steps:
-	Determine the barcode source (image file, stream, or bitmap), e.g. set the path to a source image
-	Select target barcode types. [*DecodeType*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/DecodeType) is set to *DecodeType.ALL_SUPPORTED_TYPES* by default meaning that the source image will be scanned to search for all supported barcode types; in this case, the time required to finish the barcode detection process will increase.  
  
***Aspose.BarCode for Java*** contains the *ReadBarCodes* method of class [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) that returns the result of barcode reading in an array of the [*BarCodeResult*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult) type.  
  
<!--The following code snippet explains how to specify target barcode types (i.e. *PDF417*, *QR Code*, *Code 128*, and *Code 39*). In this example, other barcodes (*DataMatrix* and *RM4SCC*) will be omitted.
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadSimpleExample:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->
  
<p align="center"><img src="multiple_codes.png" hight="50%" width="50%"></p>  
  
## **Get Recognition Results**
To load barcode recognition outputs, it is needed to call the *ReadBarCodes* method that provides a [*BarCodeResult*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult) array. Moreover, the current recognition output can be accessed through the *getFoundBarCodes* method that enables fetching decoding results or the *getFoundCount* method that returns the number of detected barcodes.  
  
<!--The following code snippet explains how to obtain recognition results.
  
{{< highlight csharp>}}
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
{{< /highlight >}}-->

## **Abort Barcode Reading using Manual and Timeout Methods**
Class [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) enables two special methods to stop the recognition process if it becomes unfeasible to complete. The first one is the *setTimeOut* method that can be called to interrupt the barcode reading process immediately after the timeout value gets exceeded. By default, the *TimeOut* value is set to 0.  
  
The second way is to use the *abort()* method. This option is used if the recognition process has been launched in the other thread. This method does not stop the entire process and returns controls immediately.  
  
Both aforementioned methods throw an exception called [*RecognitionAbortedException*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/RecognitionAbortedException) if the recognition process could not be finished successfully.
  
<!--The following code snippet shows how to interrupt the recognition process.
  
{{< highlight csharp>}}
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
{{< /highlight >}}-->

