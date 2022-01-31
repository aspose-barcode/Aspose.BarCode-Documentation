---
title: Barcode Recognition Basics
type: docs
aliases:
 - /node/read-barcodes-with-aspose-barcode-apis/
description: "This Article Describes how to Scan a Barcode from an Image, read barcode from a stream, use barcode symbologies, recognize all 1D barcodes presented in an Image, Detect Dot Peen Datamatrix Barcode, and Implement Barcode Recognition in a WPF Project."
keywords: "read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Barcode in WPF Project, Aspose.BarCode, Read Barcode C#"
weight: 10
url: /net/read-barcodes-with-aspose-barcode-apis/
---
{{% alert color="primary" %}}[Try online](https://products.aspose.app/barcode/recognize). You can test the quality of ***Aspose.BarCode*** recognition functionality and view the results online.{{% /alert %}}

## Overview
***Aspose.BarCode for .NET*** provides class [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) that enables barcode recognition from given images for more than 60 symbologies. In general, to perform barcode reading, it is necessary first to specify the source of an image with barcodes to be detected as a file, a bitmap object, or a stream. Then, it is required to set target symbologies in the [*DecodeType*]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/decodetype) parameter; otherwise, barcode recognition will take more time as using the default setting *DecodeType.AllSupportedTypes* implies looking over all supported symbologies to check for their presence in the source barcode image. In addition, developers can explicitly set the target region/regions in an image for barcode reading. It can be done using a [*https://docs.microsoft.com/dotnet/api/system.drawing.rectangle *]( https://docs.microsoft.com/dotnet/api/system.drawing.rectangle) object and allows avoiding the unnecessary search for barcodes in the image areas with no barcodes presented by default.

## Basic Recognition Parameters
To read barcodes presented in an image using ***Aspose.BarCode for .NET***, the following steps need to be taken:
-	Specify the source to read barcodes from (image file, stream, or bitmap), e.g. set the path to a source image
-	Select target symbologies for barcode recognition. By default the [*DecodeType*]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/decodetype) property is set to *DecodeType.AllSupportedTypes* meaning that the barcode reading procedure will cover all supported barcode types. This leads to extra time costs required to complete barcode recognition.  
  
In ***Aspose.BarCode for .NET***, barcode recognition is performed through the [*ReadBarCodes*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/readbarcodes) method that returns recognition results in array [*BarCodeResult*]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult).  
  
The following code snippet explains how to specify several target barcode types to be recognized in a single image, in this case, *PDF417*, *QR Code*, *Code 39*, and *Code 128* as can be seen in the sample image provided below. As such, barcodes that do not correspond to the target symbologies (*DataMatrix* and *RM4SCC* barcodes in the given example) will be ignored.
  
<p align="center"><img src="multiple_codes.png" hight="50%" width="50%"></p>  

{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadSimpleExample:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}
  
## Getting Recognition Results
As mentioned above, to get barcode recognition results, it is necessary to call the [*ReadBarCodes*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/readbarcodes) method that will output an array of the [*BarCodeResult*]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult) type. At the same time, it is possible to get access to the current barcode reading output by using the [*FoundBarCodes*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/properties/foundbarcodes) property that stores recognition results or the [*FoundCount*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/properties/foundcount) parameter that returns the number of barcodes that have been processed.  
  
The following code sample illustrates how to load recognition results for the image provided above.
  
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

## Setting Barcode Recognition Source
In ***Aspose.BarCode for .NET***, a source for barcode recognition can be defined in three different ways: as an image file, as a stream, or as a bitmap. Reading barcodes from files can be done using five supported image formats: BMP, PNG, JPEG, GIF, or TIFF. The implementation details for three possible modes are provided further. 

### Read from File

To set the barcode recognition source as an image file, it is necessary to specify the full or relative path to this file in the [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) constructor or, alternatively, call the [*SetBarCodeImage*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/setbarcodeimage/methods/4) method to pass the path to the already existing object of [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader).  
  
The following code snippet shows how to set the barcode reading source as a file by specifying the path to the required image.

{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadFromFile:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}
  
The code sample below illustrates how to define the path to the alread created recognition source object.
  
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

### Read from Bitmap
In ***Aspose.BarCode for .NET***, it is possible to get a barcode image for reading in the form of a graphical object, namely, a bitmap. IN the .NET framework, bitmap objects are used to process images composed of pixel data. To set the recognition source as a bitmap, it is necessary to pass the created bitmap object to the [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) constructor or to the [*SetBarCodeImage*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/setbarcodeimage/methods/4) method similary to the case of using a raster image file.
  
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

### Read from Stream
***Aspose.BarCode for .NET*** enables the possiblity to load the source barcode image from a stream (in a binary format) that is viewed as an abstraction of a byte sequence. In many cases, it may be convenient to set a recognition source as a stream object that is universal and can be accessed without a file system. In ***Aspose.BarCode for .NET***, the source stream for barcode recognition can be passed to the [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) constructor or the [*SetBarCodeImage*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/setbarcodeimage/methods/4) method.
  
The following code snippet explains how to set a source stream for barcode recognition.

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

## Selecting Target Symbologies
***Aspose.BarCode for .NET*** supports more than 60 barcode types for recognition. To minimize the time required to complete recognition and avoid attempts to recognize outdated barcodes that are still used as a legacy of some industrial systems, it is recommended to select target barcode symbologies that will be considered for recognition. However, in the case when there is no information about precise symbologies that can be presented in a source image, it is possible to use the default setting *DecodeType.AllSupportedTypes* for the [*DecodeType*]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/decodetype) property so that the source image will be checked for the presence of all supported barcode types. This setting results in increased time required to complete barcode recognition. 

### Listing Barcode Types Defined in DecodeType
Target symbologies for barcode recognition can be specified as a list and passed to the [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) constructor or to the [*SetBarCodeReadType*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/setbarcodereadtype/methods/1) method.  
  
The following code snippet demonstrates how to set target symbologies (*Code 39*, *Code 128*, and *RM4SCC*) using *DecodeType*.
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png"))
{
    reader.SetBarCodeReadType(DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC);
    Console.WriteLine("ReadDecodeTypeList:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

### ***MultyDecodeType*** Mode
The other way to set target symbologies for recognition is to list the required barcode types in a constructor of class [*MultyDecodeType*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/multydecodetype) and then to pass an instance of this class to the [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) constructor or to [*SetBarCodeReadType*]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/setbarcodereadtype/methods/1) method.  
  
The following code sample explains how to define target symbologies for barcode reading (in this case, *Code 39*, *Code 128*, and *RM4SCC*) through *MultyDecodeType*.
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png"))
{
    reader.SetBarCodeReadType(new MultyDecodeType(DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC));
    Console.WriteLine("ReadMultyDecodeType:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

### Predefined Sets of Symbologies
Class [*DecodeTypes*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/decodetype) contains various predefined sets of symbologies for recognition, including the following ones:
-	*AllSupportedTypes* - all supported barcode types
-	*Types1D* - all supported 1D symbologies
-	*Types2D* - all supported 2D symbologies
-	*PostalTypes* - all supported postal symbologies that are mainly used by postal services
-	*MostCommonTypes* - a set of most widely used barcode standards defined according to the Aspose recommendations

 The required symbology set can be defined in the [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) constructor or to [SetBarCodeReadType]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/setbarcodereadtype/methods/1) method.
  
The following code snippet illustrates how to specify target barcode types using the predefined set called *Types2D*.
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Types2D))
{
    Console.WriteLine("ReadTypes2D:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

## Specifying Target Regions for Recognition
***Aspose.BarCode for .NET*** enables setting one or many objects of the *Rectangle* type to limit target areas for barcode detection. This property allows improving recognition efficiency and avoiding the recognition of irrelevant barcodes placed in the areas out of interest. At the same time, it is necessary to select target regions justifiably because the Aspose library applies heuristic methods to localize regions for barcode recognition; hence, simply enumerating multiple areas can deteriorate reading efficiency.

### Single Region
To set a target region for barcode recognition, it is necessary to define an object of the *Rectangle* type using the [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) constructor or the [*SetBarCodeImage*]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/setbarcodeimage/methods/1) method.  
  
The following code samples illustrate how to set a target recognition region in the source image using two ways mentioned above.

**Setting Target Region for Recognition Using Class BarCodeReader**

{{< highlight csharp>}}
//rectangle of 2D barcode in the source image
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

**Setting Target Region for Recognition Using  SetBarCodeImage Method**
{{< highlight csharp>}}
//rectangle of 2D barcode on our image
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

### Multiple Regions
In cases when it is required to specify several regions for barcode reading in the same source image, developers can define target areas in the same way as for the single region, namely, using the [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) constructor or the [*SetBarCodeImage *]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/setbarcodeimage/methods/1) method.  
  
The following code snippet explains how to multiple target areas for barcode reading in the source image.
  
{{< highlight csharp>}}
using (Bitmap bmp = new Bitmap($"{path}multiple_codes.png"))
using (BarCodeReader reader = new BarCodeReader())
{
    //rectangle of 2D barcode in the source image
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

## Manual and Timeout Methods of Recognition Abortion
Class [*BarCodeReader *](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) allows aborting the recognition process in case it is not further feasible. It can be done in two ways. The first option is to use the [*TimeOut*]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/properties/timeout) property so as to stop the recognition process in case of exceeding the timeout value.  By default, [*TimeOut*]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/properties/timeout) is set to 0.  
  
The second way is to call the [*Abort*]( https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/abort) method in case if the recognition process has been launched in the other stream. This method does not block the entire process and return control immediately.  
  
Both recognition abortion ways result in throwing an exception called [*RecognitionAbortedException*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/recognitionabortedexception) in case when the recognition process has not been completed.
  
The following code snippet demonstrates an example of aborting the recognition process with the exception "*Recognition is aborted. Execution time: 342 ms*".
  
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