---
title: Working with Barcode Recognition State using XML in Java
linktitle: Barcode Reading State in XML
type: docs
description: "This Article Describes How to Save or Load Barcode Recognition State in the XML format"
keywords: "Read barcode in XML, Barcode XML Serialization, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Barcode in WPF Project, Aspose.BarCode, Read Barcodes in Java"
weight: 50
url: /java/barcode-in-xml/
---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can check the quality of Aspose.BarCode recognition and view the results online.{{% /alert %}}

## **Overview**
***Aspose.BarCode for Java*** provides class [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) that enables serializing the current barcode recognition state and saving it using the XML format to a file through the *exportToXml(java.lang.String xmlFile)* method or a stream through the *exportToXml(java.io.OutputStream xmlStream)* method. In addition, it is possible to import the barcode state in the XML format from a file or a stream using corresponding methods *importFromXml(java.lang.String xmlFile)* and *importFromXml(java.io.InputStream xmlStream)*. 
  
However, serializing cannot be implemented automatically for some barcode data, including the barcode image itself and the link to the source file. If needed, this can be done through the *setBarCodeImage()* method.    

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Outputting Barcode Recognition State in XML Format**
In ***Aspose.BarCode for Java***, there are two options to save the current state of class [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader): to an XML file using the *exportToXml(java.lang.String xmlFile)* method or a stream using the *exportToXml(java.io.OutputStream xmlStream)* method. 
<!--The following code sample explains how to output the barcode recognition state to an XML file.   

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
{{< /highlight >}}-->

## **Loading Barcode Recognition State from XML**
The current barcode recognition state corresponding to an object of class [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) can be loaded from an XML file through the *importFromXml(java.lang.String xmlFile)* method or a stream through the *importFromXml(java.io.InputStream xmlStream)* method. The source barcode image needs to be determined using the *setBarCodeImage* method. 
<!--The following code sample shows how to get the state of a [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) object from an XML file. 

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
{{< /highlight >}}-->


## **Loading and Saving Barcode Recognition State from Stream**
In ***Aspose.BarCode for Java***, it is possible to save or load the barcode reading state from a stream using special methods *exportToXml(java.io.OutputStream xmlStream)* and *importFromXml(java.io.InputStream xmlStream)*. The source barcode image needs to be specified explicitly using the *setBarCodeImage()* method. 
<!--The following code sample shows how to save or load the barcode recognition state from a stream. 

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
{{< /highlight >}}-->