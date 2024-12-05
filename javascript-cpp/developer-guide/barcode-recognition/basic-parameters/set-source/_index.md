---
title: Set Barcode Source
type: docs
description: "This Article Describes How to Set Barcode Source for Recognition"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcode JavaScript"
feedback: BARCODECOM
weight: 10
url: /javascript-cpp/set-barcode-source/

---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**

In ***Aspose.BarCode for JavaScript via C++***, a source for barcode recognition can be defined in three different ways: as an image file, as a stream, or as a bitmap. Reading barcodes from files can be done using five supported image formats: BMP, PNG, JPEG, GIF, or TIFF. The implementation details for three possible modes are provided further. 

## **Read Barcodes from File**
To set the barcode recognition source as an image file, it is necessary to specify the full or relative path to this file in the [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) constructor or call the [*SetBarCodeImage*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition.barcodereader/setbarcodeimage/methods/4) method to pass the path to the already existing object of [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader).  
  
The following code snippet shows how to set the barcode reading source as a file by specifying the path to the required image.

```javascript
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadFromFile:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeType}:{result.CodeText}");
}
```
  
The code sample below illustrates how to define the path to the already created recognition source object.
  
```javascript
using (BarCodeReader reader = new BarCodeReader())
{
    //set path to image
    reader.SetBarCodeImage($"{path}multiple_codes.png");
    reader.SetBarCodeReadType(DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR, DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC);
    Console.WriteLine("ReadSetBarCodeImageFromFile:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeType}:{result.CodeText}");
}
```

## **Read Barcodes from Bitmap**
In ***Aspose.BarCode for JavaScript via C++***, it is possible to get a barcode image for reading in the form of a graphical object, namely, a bitmap. IN the .NET framework, bitmap objects are used to process images composed of pixel data. To set the recognition source as a bitmap, it is necessary to pass the created bitmap object to the [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) constructor or the [*SetBarCodeImage*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition.barcodereader/setbarcodeimage/methods/4) method similarly to the case of using a raster image file.
  
```javascript
using (Bitmap bmp = new Bitmap($"{path}multiple_codes.png"))
using (BarCodeReader reader = new BarCodeReader(bmp, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadFromBitmap:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeType}:{result.CodeText}");
}
```

## **Read Barcodes from Stream**
***Aspose.BarCode for JavaScript via C++*** enables the possibility to load the source barcode image from a stream (in a binary format) that is viewed as an abstraction of a byte sequence. In many cases, it may be convenient to set a recognition source as a stream object that is universal and can be accessed without a file system. In ***Aspose.BarCode for JavaScript via C++***, the source stream for barcode recognition can be passed to the [*BarCodeReader*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/barcodereader) constructor or the [*SetBarCodeImage*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition.barcodereader/setbarcodeimage/methods/4) method.
  
The following code snippet explains how to set a source stream for barcode recognition.

```javascript
using (Stream stream = new FileStream($"{path}multiple_codes.png", FileMode.Open, FileAccess.Read))
using (BarCodeReader reader = new BarCodeReader(stream, DecodeType.Pdf417, DecodeType.DataMatrix, DecodeType.QR,
    DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC))
{
    Console.WriteLine("ReadFromStream:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeType}:{result.CodeText}");
}
```

