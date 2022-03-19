---
title: Working with Barcode Recognition State in XML
type: docs
description: "This Article Describes How to Save or Load Barcode Recognition State in the XML format"
keywords: "Read barcode in XML, Barcode XML Serialization, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Barcode in WPF Project, Aspose.BarCode, Read Barcode C#"
weight: 50
url: /net/barcode-reading-in-xml/
---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can check the quality of Aspose.BarCode recognition and view the results online.{{% /alert %}}

## **Overview**
In addition to barcode recognition functionality, class [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) allows performing the serialization of the barcode recognition state and uploading it in the XML format. The recognition state can be saved both to a file [*ExportToXml(String)*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/exporttoxml/methods/1) or a stream [*ExportToXml(Stream)*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/exporttoxml). Moreover, it can be imported in the XML format from a file or a stream using functions [*ImportFromXml(String)*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/importfromxml/methods/1) and [*ImportFromXml(Stream)*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/importfromxml). 
  
It should be noted that the serialization of the information about a barcode image, the link to a source image file, or the image itself cannot be performed automatically. In the case of such a need, this functionality has to be set explicitly using the family of functions called [*SetBarCodeImage*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/setbarcodeimage/index).    

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Saving Barcode Recognition State to XML**
***Aspose.BarCode for .NET*** provides two ways to obtain the current state of class [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader): to an XML file through the [*ImportToXml(String)*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/importfromxml/methods/1) function or a stream using the [*ImportToXml(Stream)*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/importfromxml) function. The code snippet below illustrates how to perform the serialization of the barcode recognition state to an XML file.   

{{< highlight csharp>}}
//init barcode reader
using (BarCodeReader read = new BarCodeReader())
{
    read.SetBarCodeReadType(DecodeType.Pdf417);
    read.BarcodeSettings.StripFNC = true;
    read.QualitySettings.MedianSmoothingWindowSize = 5;
    ////serialize BarCodeReader to file
    read.ExportToXml($"{path}readerPdf417.xml");
}
{{< /highlight >}}

## **Loading Barcode Recognition State from XML**
The current state of class [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) can be loaded from an XML file through the [*ImportFromXml(String)*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/importfromxml/methods/1) function or from a stream through the [*ImportFromXml(Stream)*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/importfromxml) function. The target barcode image needs to be specified using the group of properties called [*SetBarCodeImage*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/setbarcodeimage/index). The following code snippet explains how to load the state of a [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) object from an XML file. 

{{< highlight csharp>}}
//load BarCodeReader from file
Console.WriteLine("BarCodeReaderSerialization:");
using (BarCodeReader read = BarCodeReader.ImportFromXml($"{path}readerPdf417.xml"))
{
    //set the recognized file because it is not stored
    read.SetBarCodeImage($"{recpath}many_pdf417.png");
    //initialized data
    Console.WriteLine($"StripFNC:{read.BarcodeSettings.StripFNC}");
    Console.WriteLine($"MedianSmoothingWindowSize:{read.QualitySettings.MedianSmoothingWindowSize}");
    //read
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}


## **Loading and Saving Barcode Recognition State from Stream**
***Aspose.BarCode for .NET*** enables saving the barcode recognition state or loading it from streams using special functions [*ExportToXml(Stream)*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/exporttoxml) and [*ImportFromXml(Stream)*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/importfromxml), respectively. The target barcode image needs to be set explicitly using the group of properties called [*SetBarCodeImage*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/setbarcodeimage/index). The following code snippet demonstrates how to save the barcode recognition state and load it from a stream. 

{{< highlight csharp>}}
//stream 
MemoryStream ms = new MemoryStream();

//init barcode reader
using (BarCodeReader read = new BarCodeReader())
{
    read.SetBarCodeReadType(DecodeType.Pdf417);
    read.BarcodeSettings.StripFNC = true;
    read.QualitySettings.MedianSmoothingWindowSize = 5;
    ////serialize BarCodeReader to stream
    read.ExportToXml(ms);
    ms.Position = 0;
}

//load an instance of BarCodeReader from stream
Console.WriteLine("BarCodeReaderStreamSerialization:");
using (BarCodeReader read = BarCodeReader.ImportFromXml(ms))
{
    //set the recognized file because it is not stored
    read.SetBarCodeImage($"{recpath}many_pdf417.png");
    //initialized data
    Console.WriteLine($"StripFNC:{read.BarcodeSettings.StripFNC}");
    Console.WriteLine($"MedianSmoothingWindowSize:{read.QualitySettings.MedianSmoothingWindowSize}");
    //read
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}