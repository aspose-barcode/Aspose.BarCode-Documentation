---
title: Barcode Recognition Basics
linktitle: Barcode Recognition Basics
type: docs
aliases:
 - /node/read-barcodes-with-aspose-barcode-apis/
description: "This Article Describes How to Read Barcodes of Different Symbologies from Images or Stream and How to Recognize All 1D Barcodes Presented in an Image"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcodes in Java"
weight: 10
url: /java/read-barcodes-with-aspose-barcode-apis/
---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can test the quality of ***Aspose.BarCode*** recognition functionality and view the results online.{{% /alert %}}

## **Overview**
In ***Aspose.BarCode for Java***, class [*BarCodeReader*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) is the main class used to perform barcode reading for over 60 barcode types. Generally, it is first required to determine the source of an image with barcodes. The source can be a file, a bitmap object, or a stream. Then, it is necessary to identify target barcode types using the [*DecodeType*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/DecodeType) enum. If this step is omitted, barcode detection and reading will require much more time as the *DecodeType.AllSupportedTypes* setting used by default requires checking all supported symbologies to verify their presence in the source image. Moreover, it is possible to explicitly determine the target area/areas in the source image to perform barcode scanning. This option avoids looking for barcodes in regions without any barcodes and can be enabled through a system object called [*Rectangle*](https://apireference.aspose.com/imaging/java/com.aspose.imaging.class-use/Rectangle).

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Basic Recognition Parameters**
***Aspose.BarCode for Java*** requires executing the following steps to perform barcode recognition:
-	Source determination (from an image file a bitmap, or a stream), e.g. setring the path to a source image
-	Target barcode type selection. By default, [*DecodeType*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/DecodeType) is initialized as *DecodeType.ALL_SUPPORTED_TYPES*. In this case, barcode scanning will be performed for all available symbologies. This approach will require additional time to complete the barcode recognition process.  
  
To read barcode images, ***Aspose.BarCode for Java*** provides the *ReadBarCodes* method of class [*BarCodeReader*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) that returns recognition results in an array of the [*BarCodeResult*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult) type.  
  
The following code sample shows how to determine target symbologies to be searched in one image (i.e. *PDF417*, *QR Code*, *Code 128*, and *Code 39*). In this case, barcodes of other barcode types (*DataMatrix* and *RM4SCC*) will not be decoded.
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadSimpleExample:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}
  
<p align="center"><img src="multiple_codes.png" hight="50%" width="50%"></p>  
  
## **Getting Recognition Results**
To load barcode recognition outputs, it is needed to call the *ReadBarCodes* method that provides a [*BarCodeResult*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeResult) array. Moreover, the current recognition output can be accessed through the *getFoundBarCodes* method that enables fetching decoding results or the *getFoundCount* method that returns the number of detected barcodes.  
  
The following code snippet explains how to obtain recognition results.
  
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
{{< /highlight >}}

## **Barcode Recognition Source**
***Aspose.BarCode for Java*** provides three options to determine a source for barcode detection: as an image file, a stream, or a bitmap. Barcode recognition from file sources supports five image formats: PNG, BMP, JPEG, GIF, or TIFF. Three possible modes to load source barcodes are discussed below. 

### **Reading Barcodes from File**
To read barcodes from an image file, it is required to determine the full or relative path to this source file in the *BarCodeReader()* constructor or call the *setBarCodeImage* method to pass the path to the already existing object of [*BarCodeReader*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader).  
  
The following code sample explains how to use a file as a barcode recognition source through setting the path to the target image.

{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadFromFile:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}
  
The following code snippet shows how to determine the path to the already existing recognition source object.
  
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
{{< /highlight >}}

### **Reading Barcodes from Bitmap**
***Aspose.BarCode for Java*** enables loading a barcode image in the form of a graphical object or a bitmap. Bitmap objects serve to work with images composed of pixel data. To use a bitmap as a barcode reading source, it is required to pass the existing bitmap object to the *BarCodeReader()* constructor or the *setBarCodeImage* method.
  
{{< highlight csharp>}}
using (Bitmap bmp = new Bitmap($"{path}multiple_codes.png"))
using (BarCodeReader reader = new BarCodeReader(bmp, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadFromBitmap:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

### **Reading Barcodes from Stream**
***Aspose.BarCode for Java*** allows loading the source image from a stream (in a binary format) that can be considered as an abstraction of byte sequences. Setting a recognition source as a stream object can be convenient in some cases as it is universal and accessible without the need to use a file system. A source stream for barcode recognition can be passed to the *BarCodeReader()* constructor or the *setBarCodeImage* method.
  
The following code sample shows how to specify a source stream for barcode recognition.

{{< highlight csharp>}}
using (Stream stream = new FileStream($"{path}multiple_codes.png", FileMode.Open, FileAccess.Read))
using (BarCodeReader reader = new BarCodeReader(stream, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadFromStream:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

## **Selecting Target Symbologies**
***Aspose.BarCode for Java*** enables reading over 60 various symbologies. To decrease the time needed to complete the barcode reading process, target barcode types should be specified. However, if no information about symbologies that can be found in a source image is available, the default setting *DecodeType.ALL_SUPPORTED_TYPES* of the [*DecodeType*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/DecodeType) enum can be applied so that the source image will be searched for all supported symbologies. Leaving this setting enabled may lead incresaing the time needed to complete barcode recognition. 

### **Listing Symbologies Defined in DecodeType**
To determine target symbologies for barcode reading, they can be grouped in a list and passed to the *BarCodeReader()* constructor or the *setBarCodeReadType* method.  
  
The following code sample explains how to enable target barcode types (i.e. *Code 128*,*Code 39*, and *RM4SCC*) using [*DecodeType*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/DecodeType).
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png"))
{
    reader.SetBarCodeReadType(DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC);
    Console.WriteLine("ReadDecodeTypeList:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

### ***MultyDecodeType* Mode**
The other option to determine target barcode types is to list them in a constructor of class [*MultyDecodeType*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/MultyDecodeType) and then pass this object to class [*BarCodeReader*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) or the *setBarCodeReadType* method.  
  
The following code snippet shows how to set target barcode types (i.e., *Code 39*, *Code 128*, and *RM4SCC*) through [*MultyDecodeType*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/MultyDecodeType).
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png"))
{
    reader.SetBarCodeReadType(new MultyDecodeType(DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC));
    Console.WriteLine("ReadMultyDecodeType:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

### **Predefined Sets of Barcode Types**
Class [*DecodeType*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/DecodeType) suggests using several predefined symbology sets, including the following ones:
-	*ALL_SUPPORTED_TYPES* - all available symbologies
-	*TYPES_1D* - all supported 1D standards
-	*TYPES_2D* - all supported 2D barcode types
-	*POSTAL_TYPES* - all available postal symbologies
-	*MOST_COMMON_TYPES* - a set of most widespread symbologies defined according to the Aspose recommendations

The desired symbology set can be specified in the *BarCodeReader()* constructor or passed to the *setBarCodeReadType* method.
  
The following code sample explains how to enable the predefined set called *Types2D*.
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Types2D))
{
    Console.WriteLine("ReadTypes2D:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

## **Setting Target Barcode Regions for Recognition**
***Aspose.BarCode for Java*** allows determining one or several objects of the [*Rectangle*](https://apireference.aspose.com/imaging/java/com.aspose.imaging.class-use/Rectangle) type to specify target regions for barcode detection and scanning. It allows increasing reading efficiency and avoiding the scanning of irrelevant barcodes presented in the regions out of interest. It is important to select target areas wisely as the Aspose library uses heuristic methods to determine regions for barcode detection; therefore, targeting multiple image areas can result in decreasing recognition efficiency.

### **Single Region**
To specify a single target area for barcode reading, an object of the [*Rectangle*](https://apireference.aspose.com/imaging/java/com.aspose.imaging.class-use/Rectangle) type needs to be created using the *BarCodeReader()* constructor or the *setBarCodeImage*() method.  
  
The following code snippets show how to determine a target barcode detection area in the source image through the two modes outlined above.

**Setting Target Reading Area Using Class BarCodeReader**

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

**Setting Target Reading Area Using SetBarCodeImage Method**
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
{{< /highlight >}}

### **Several Reading Regions**
When it is needed to determine various areas for barcode detection within the same source image, this can be done similarly as for the case of one target region, i.e., through the *BarCodeReader()* constructor or the *setBarCodeImage* method.  
  
The following code sample demonstrates how to determine several target areas in the source image.
  
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
{{< /highlight >}}

## **Manual and Timeout Methods of Recognition Abortion**
Class [*BarCodeReader*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) provides two options to abort the reading procedure if it becomes unfeasible to continue. The first way is to call the *setTimeOut* method that will interrupt recognition as soon as the timeout value is exceeded. *TimeOut* is set to 0 by default.  
  
The second option is to call the *abort()* method in case when the reading process has been started in the other stream. This method does not interrupt the entire procedure and returns control immediately.  
  
Both recognition abortion options result in throwing an exception called [*RecognitionAbortedException*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/RecognitionAbortedException) if the reading procedure has not been completed.
  
The following code sample illustrates an example of aborting the recognition process.
  
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
{{< /highlight >}}
