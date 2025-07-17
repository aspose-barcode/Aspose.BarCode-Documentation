---
title: Barcode Recognition Basics
linktitle: Barcode Recognition Basics
type: docs
description: "This Article Describes How to Read Barcodes of Different Symbologies from Images or Stream and How to Recognize All 1D Barcodes Presented in an Image"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcodes in Python"
ai_search_scope: "barcode_python-java_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 10
url: /python-java/basic-barcode-recognition/
---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can test the quality of ***Aspose.BarCode*** recognition functionality and view the results online.{{% /alert %}}

## **Overview**
Class [*BarCodeReader*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.recognition.bar_code_reader/) in ***Aspose.BarCode for Python via Java*** is the most important to implement barcode recognition for more than 60 symbologies. First, it is necessary to indentify a barcode source that can be represented as a file, a stream, or a bitmap object. After that, target symbologies needs to be specified using values from the [*DecodeType*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.recognition.decode_type/) enum. By default, the library uses the *DecodeType.ALL_SUPPORTED_TYPES* setting that implies iterating over all supported barcode types to check for their presence in the source image. In this case, barcode scanning and recognition takes much more time. Developers can specify explicitly not only the desired symbologies but also a target region or regions in the source image. This allows optimizing the scanning process by avoiding areas without barcodes. Target regions can be determined using a system class called [*Rectangle*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.assist.rectangle/).

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Main Recognition Parameters**
In ***Aspose.BarCode for Python via Java***, barcode reading is performed according to the following steps:
-	Determine the barcode source (image file, stream, or bitmap), e.g. set the path to a source image
-	Select target barcode types. [*DecodeType*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.recognition.decode_type/) is set to *DecodeType.ALL_SUPPORTED_TYPES* by default meaning that the sources image will be scanned to search for all supported barcode types; in this case, time required to finish the barcode detection process will increase.  
  
***Aspose.BarCode for Python*** contains the *ReadBarCodes* method of class [*BarCodeReader*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.recognition.bar_code_reader/) that returns the result of barcode reading in an array of the [*BarCodeResult*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.recognition.bar_code_result/) type.  
  
<!--The following code snippet expplains how to specify target barcode types (i.e. *PDF417*, *QR Code*, *Code 128*, and *Code 39*). In this example, other barcodes (*DataMatrix* and *RM4SCC*) will be omitted.
  
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
  
## **Getting Recognition Results**
To load barcode recognition outputs, it is needed to call the *ReadBarCodes* method that provides a [*BarCodeResult*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.recognition.bar_code_result/) array. Moreover, the current recognition output can be accessed through the *getFoundBarCodes* method that enables fetching decoding results or the *getFoundCount* method that returns the number of detected barcodes.  
  
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

## **Barcode Recognition Source**
In ***Aspose.BarCode for Python via Java***, there are three ways to set the barcode recognition source: from an image file, from a bitmap, or from a stream. The following five raster image formats are supported: PNG, JPEG, BMP, TIFF, or GIF. Three options to set the source for barcodes reading are explained further. 

### **Read Barcodes from Files**
First of all, barcodes can be scanned and recognized from image files. The full or relative path to the source needs to be specified in the *BarCodeReader* constructor. Alternatively, the *setBarCodeImage* method can be used to pass the path to the existing object of class [*BarCodeReader*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.recognition.bar_code_reader/).  
  
<!--The following code snippet shows how to read barcodes from a file by specifying the path to the source image.

{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadFromFile:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->
  
<!--The following code snippet shows how to determine the path to the already existing recognition source object.
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader())
{
    //set path to image
    reader.SetBarCodeImage($"{path}multiple_codes.png");
    reader.SetBarCodeReadType(DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR, DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC);
    Console.WriteLine("ReadSetBarCodeImageFromFile:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

### **Read Barcodes from Bitmap Objects**
In ***Aspose.BarCode for Python via Java***, it is possible to use a graphical object or a bitmap as a source for barcode reading. Bitmap objects allow working with images consisting of pixel data. To read barcodes from a bitmap, the created bitmap object needs to be passed to the *BarCodeReader()* constructor or the *setBarCodeImage* method.  
  
<!--The following code sample demonstrates how to set a bitmap object for barcode reading.
  
{{< highlight csharp>}}
using (Bitmap bmp = new Bitmap($"{path}multiple_codes.png"))
using (BarCodeReader reader = new BarCodeReader(bmp, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadFromBitmap:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

### **Read Barcodes from Streams**
In ***Aspose.BarCode for Python via Java***, a stream (in a binary format) can be also used as a source for barcode recognition. This option can be useful in some situations owing to its versatility and accessibility without file systems. A stream to read barcodes from needs to be passed to the *BarCodeReader()* constructor or the *setBarCodeImage* method.
  
<!--The following code sample shows how to specify a source stream for barcode recognition.

{{< highlight csharp>}}
using (Stream stream = new FileStream($"{path}multiple_codes.png", FileMode.Open, FileAccess.Read))
using (BarCodeReader reader = new BarCodeReader(stream, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadFromStream:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

## **Setting Target Barcode Types**
***Aspose.BarCode for Python via Java*** supports barcode recognition for 60+ various barcode types. To improve the efficiency of the recognition process and optimize its timing, it is recommended to set target symbologies in advance. Otheriwse, the *DecodeType.ALL_SUPPORTED_TYPES* setting of the [*DecodeType*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.recognition.decode_type/) enum will be used by default meaning that the library will look over all supported barcode types to check for their presence in the source image. Using this setting will increase the time needed to complete barcode recognition. 

### **Listing Target Barcode Types in DecodeType**
Target barcode types can be specified by grouping them in a list and passing it to the *BarCodeReader* constructor or the *setBarCodeReadType* method.  
  
<!--The following code snippet shows how to determine target barcode types (i.e. *Code 128*,*Code 39*, and *RM4SCC*) using [*DecodeType*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.recognition.decode_type/).
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png"))
{
    reader.SetBarCodeReadType(DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC);
    Console.WriteLine("ReadDecodeTypeList:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

### **Using Predefined Sets for Barcode Types**
Class [*DecodeType*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.recognition.decode_type/) provides the following symbology setsfor barcode reading:
-	*ALL_SUPPORTED_TYPES* - all available barcode types
-	*TYPES_1D* - all supported 1D types
-	*TYPES_2D* - all supported 2D types
-	*POSTAL_TYPES* - all available postal types
-	*MOST_COMMON_TYPES* - a set of most widespread barcode types defined according to Aspose recommendations

The required set can be specified in the *BarCodeReader* constructor or passed to the *setBarCodeReadType* method.
  
<!--The following code snippet shows how to work with the *TYPES_2D* set.
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Types2D))
{
    Console.WriteLine("ReadTypes2D:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

## **Setting Target Barcode Regions**
In ***Aspose.BarCode for Python via Java***, it is possible to specify target areas for barcode detection by creating one or several objects of the [*Rectangle*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.assist.rectangle/) type. Setting target regions allows improving recognition efficiency and avoiding the regions without any barcodes. Target areas have to be determined accurately as the Aspose library apply heuristic approaches to identify target barcode detection areas. Focusing on too many image regions can lead to recognition efficiency deterioration.

### **Unique Target Region**
To set one target area for barcode recognition, it is necessary to create an object of the [*Rectangle*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.assist.rectangle/) type and then pass it to the *BarCodeReader* constructor or the *setBarCodeImage* method.  
  
<!--The following code samples explain how to specify one target region in the source image.

**Setting Target Region Using Class BarCodeReader**

{{< highlight csharp>}}
//specify the rectangle of a 2D barcode in the source image
Rectangle rect2D = new Rectangle(0, 0, 430, 440);
using (Bitmap bmp = new Bitmap($"{path}multiple_codes.png"))
using (BarCodeReader reader = new BarCodeReader(bmp, rect2D, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadWithRegion:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

**Setting Target Region Using SetBarCodeImage Method**
{{< highlight csharp>}}
//specify the rectangle of a 2D barcode in the source image
Rectangle rect2D = new Rectangle(0, 0, 430, 440);
using (Bitmap bmp = new Bitmap($"{path}multiple_codes.png"))
using (BarCodeReader reader = new BarCodeReader())
{
    reader.SetBarCodeImage(bmp, rect2D);
    reader.SetBarCodeReadType(DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR, DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC);
    Console.WriteLine("ReadSetBarCodeRegion:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

### **Several Target Regions**
It is also possible to set several target areas for barcode detection within the one source image. This can be done in the same way as described above for one target region, i.e., using the *BarCodeReader* constructor or the *setBarCodeImage* method.  
  
<!--The following code snippet shows how to specify several target regions in the source image.
  
{{< highlight csharp>}}
using (Bitmap bmp = new Bitmap($"{path}multiple_codes.png"))
using (BarCodeReader reader = new BarCodeReader())
{
    //detecting the rectangle of a 2D barcode in the source image
    Rectangle rect2D = new Rectangle(0, 0, 430, 440);
    //rectangle of Code128 barcode in the source image
    Rectangle rectCode128 = new Rectangle(460, 111, 360, 150);
    reader.SetBarCodeImage(bmp, new Rectangle[] { rect2D, rectCode128 });
    reader.SetBarCodeReadType(DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR, DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC);
    Console.WriteLine("ReadMultipleRegions:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

## **Recognition Abortion through Manual and Timeout Methods**
Class [*BarCodeReader*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.recognition.bar_code_reader/) enables two special methods to stop the recognition process if it becomes unfeasible to complete. The first one is the *setTimeOut* method that can be called to interrupt the barcode reading process immediately after the timeout value gets exceeded. By default, the *TimeOut* value is set to 0.  
  
The second way is to use the *abort()* method. This option is used if the recognition process has been launched in the other thread. This method does not stop the entire process and returns controls immediately.  
  
Both aforementioned methods throw an exception called [*RecognitionAbortedException*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.recognition.recognition_aborted_exception/) if the recognition process could not be finished successfully.
  
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
