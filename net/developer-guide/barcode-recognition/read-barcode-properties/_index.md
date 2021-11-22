---
title: Read Barcode Properties
type: docs
description: "This article explains how to read the image and get all barcode regions.  Getting Barcode Recognition Quality in Percentage, Detect an Unreadable Barcode on the Image and Detect Orientation of a Barcode."
keywords: "read barcode properties, read barcode regions, Detect Unreadable Barcode, Barcode orientation, Detect Orientation of Barcode, Aspose.BarCode, Read Barcode C#"
weight: 30
url: /net/read-barcode-properties/
---
{{% alert color="primary" %}}[Try online](https://products.aspose.app/barcode/recognize). You can check the quality of Aspose.BarCode recognition and view the results online.{{% /alert %}}
## **Getting Barcode Region Information from Image**
In this section, we will read the image and get all the barcode regions, for all the recognized barcodes in the image. The barcode region is the part of the image that only contains the barcode itself. In a large image, there may be other texts or images along with the barcode. Getting the barcode region will separate the barcodes from other text/objects in the image by detecting their edges. 

First, we will read the Barcodes in the image using the [BarCodeReader.ReadBarCodes()(https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/methods/readbarcodes) method. Then, we will get the region of the barcode using [BarCodeResult.Region](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderegionparameters) , which will return the recognized barcode's region and barcode angle. We can then get the X and Y coordinates of the barcode.
### **Getting Barcode Coordinate with Points**
{{< highlight csharp>}}
// Create an instance of BarCodeReader class and read barcode file
using (BarCodeReader barCodeReader = new BarCodeReader(dataDir + "Region.png", DecodeType.Code39Standard))
    foreach (BarCodeResult result in barCodeReader.ReadBarCodes())
    {
        // Display x and y coordinates of barcode detected
        Console.WriteLine("Top left coordinates: X = " + result.Region.Points[0].X + ", Y = " + result.Region.Points[0].Y);
        Console.WriteLine("Top right coordinates: X = " + result.Region.Points[1].X + ", Y = " + result.Region.Points[1].Y);
        Console.WriteLine("Bottom right coordinates: X = " + result.Region.Points[2].X + ", Y = " + result.Region.Points[2].Y);
        Console.WriteLine("Bottom left coordinates: X = " + result.Region.Points[3].X + ", Y = " + result.Region.Points[3].Y);
        //codetext
        Console.WriteLine("Codetext: " + result.CodeText);
    }
{{< /highlight >}}
{{% alert color="primary" %}}**[GetBarCodeRegionInformationfromImage.cs](https://github.com/aspose-barcode/Aspose.BarCode-for-.NET/blob/master/Examples/CSharp/ManageAndOptimizeBarcodeRecognition/GetBarCodeRegionInformationfromImage.cs) as a source of code example, hosted by GitHub**{{% /alert %}}

### **Getting Barcode Coordinate with Quadrangle**
{{< highlight csharp>}}
// Create an instance of BarCodeReader class and read barcode file
using (BarCodeReader barCodeReader = new BarCodeReader(dataDir + "Region.png", DecodeType.Code39Standard))
    foreach (BarCodeResult result in barCodeReader.ReadBarCodes())
    {
        // Display x and y coordinates of barcode detected
        Console.WriteLine("Top left coordinates: X = " + result.Region.Quadrangle.LeftTop.X + ", Y = " + result.Region.Quadrangle.LeftTop.Y);
        Console.WriteLine("Top right coordinates: X = " + result.Region.Quadrangle.RightTop.X + ", Y = " + result.Region.Quadrangle.RightTop.Y);
        Console.WriteLine("Bottom right coordinates: X = " + result.Region.Quadrangle.RightBottom.X + ", Y = " + result.Region.Quadrangle.RightBottom.Y);
        Console.WriteLine("Bottom left coordinates: X = " + result.Region.Quadrangle.LeftBottom.X + ", Y = " + result.Region.Quadrangle.LeftBottom.Y);
        //codetext
        Console.WriteLine("Codetext: " + result.CodeText);
    }
{{< /highlight >}}
{{% alert color="primary" %}}**[GetBarCodeRegionInformationfromImage.cs](https://github.com/aspose-barcode/Aspose.BarCode-for-.NET/blob/master/Examples/CSharp/ManageAndOptimizeBarcodeRecognition/GetBarCodeRegionInformationfromImage.cs) as a source of code example, hosted by GitHub**{{% /alert %}}

### **Getting Barcode Coordinate with Rectangle**
{{< highlight csharp>}}
// Create an instance of BarCodeReader class and read barcode file
using (BarCodeReader barCodeReader = new BarCodeReader(dataDir + "Region.png", DecodeType.Code39Standard))
    foreach (BarCodeResult result in barCodeReader.ReadBarCodes())
    {
        // Display region rectangle
        Console.WriteLine("Barcode Rectangle: " + result.Region.Rectangle.ToString());
        //codetext
        Console.WriteLine("Codetext: " + result.CodeText);
    }
{{< /highlight >}}
{{% alert color="primary" %}}**[GetBarCodeRegionInformationfromImage.cs](https://github.com/aspose-barcode/Aspose.BarCode-for-.NET/blob/master/Examples/CSharp/ManageAndOptimizeBarcodeRecognition/GetBarCodeRegionInformationfromImage.cs) as a source of code example, hosted by GitHub**{{% /alert %}}

## **Detect Orientation of the Barcode**
[BarCodeReader](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) allows developers to detect the orientation of a detected bar code by reading [BarCodeResult.Region.Angle](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderegionparameters/properties/angle) . The following code snippet shows you how to detect the orientation of a barcode.
{{< highlight csharp>}}
// Instantiate BarCodeReader object
using (BarCodeReader reader = new BarCodeReader(dataDir + "rotatedbarcode.jpg", DecodeType.Code128))
    // Read Code128 bar code and Detect bar code orientation
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine("Rotaion Angle: " + result.Region.Angle);
{{< /highlight >}}
{{% alert color="primary" %}}**[DetectOrientationOfBarCode.cs](https://github.com/aspose-barcode/Aspose.BarCode-for-.NET/blob/master/Examples/CSharp/ManageAndOptimizeBarcodeRecognition/DetectOrientationOfBarCode.cs) as a source of code example, hosted by GitHub**{{% /alert %}}

## **Getting Barcode Recognition Quality and Confidence**
The [BarCodeResult](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult) provides the [ReadingQuality](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/readingquality) and [Confidence](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/confidence) properties. Confidence assures in recognition result because some barcodes even with moderate ReadingQuality could be recognized wrong. ReadingQuality shows quality of the barcode image and used only for 1D and postal barcodes.
{{< highlight csharp>}}
// Initialize the BarCodeReader object and Call read method
using (BarCodeReader reader = new BarCodeReader(dataDir + "Barcode2.png", DecodeType.AllSupportedTypes))
{
    foreach (BarCodeResult result in reader.ReadBarCodes())
    {
        Console.WriteLine("Type: " + result.CodeType);
        Console.WriteLine("Codetext: " + result.CodeText);
        Console.WriteLine("Confidence: " + result.Confidence.ToString());
        Console.WriteLine("Reading Quality: " + result.ReadingQuality.ToString("F0"));
    }
}
{{< /highlight >}}
{{% alert color="primary" %}}**[GetBarCodeRecognitionQuality.cs](https://github.com/aspose-barcode/Aspose.BarCode-for-.NET/blob/master/Examples/CSharp/ManageAndOptimizeBarcodeRecognition/GetBarCodeRecognitionQuality.cs) as a source of code example, hosted by GitHub**{{% /alert %}}

## **Reading Byte Array as Recognition Result**
[BarCodeReader](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) allows to directly read byte array as barcode result and use this data for internal use.
{{< highlight csharp>}}
// Load barcode image and Read barcode
using (BarCodeReader reader = new BarCodeReader(dataDir + "Chinese.png", DecodeType.Pdf417))
{
    foreach (BarCodeResult result in reader.ReadBarCodes())
    {
        var t = result.CodeBytes;
        var encodingValue = Encoding.GetEncoding(1254).GetString(t);
        Console.WriteLine("CodeText: " + encodingValue);
    }
}
{{< /highlight >}}
{{% alert color="primary" %}}**[RecognizeBarcodeWithChineseCharacters.cs](https://github.com/aspose-barcode/Aspose.BarCode-for-.NET/blob/master/Examples/CSharp/ManageBarCodes/RecognizeBarcodeWithChineseCharacters.cs) as a source of code example, hosted by GitHub**{{% /alert %}}

## **Reading MacroPDF417 metadata**
We can recognize Macro Pdf417 barcodes which is PDF417 barcodes with extended metadata. [BarCodeReader](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) class. can recognize these metadatas and store them in [Pdf417ExtendedParameters](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/pdf417extendedparameters) structure. The BarCodeReader class can recognize the Segment ID, File ID, Segment ID, Segment Count, File Size, Sender, Addressee, Date and Checksum metadatas.In the lower code example we show how to read Macro Pdf417 metadatas with barcode data.
{{< highlight csharp>}}
// Create array for storing multiple bar codes file names
string[] files = new string[] { "MacroPdf417_0.png", "MacroPdf417_1.png" };

// Iiterate through the bar code image files
for (int i = 0; i < files.Length; ++i)
{
    // Create instance of BarCodeReader class and set symbology
    using (BarCodeReader reader = new BarCodeReader(dataDir + files[i], DecodeType.MacroPdf417))
    {
        foreach (BarCodeResult result in reader.ReadBarCodes())
        {
            // Get code text, file id, segment id and segment count
            Console.WriteLine("File Name: " + files[i] + " Code Text: " + result.CodeText);
            Console.WriteLine("File ID: " + result.Extended.Pdf417.MacroPdf417FileID);
            Console.WriteLine("Segment ID: " + result.Extended.Pdf417.MacroPdf417SegmentID);
            Console.WriteLine("Segment Count: " + result.Extended.Pdf417.MacroPdf417SegmentsCount);
            Console.WriteLine("File Size: " + result.Extended.Pdf417.MacroPdf417FileSize);
            Console.WriteLine("Sender: " + result.Extended.Pdf417.MacroPdf417Sender);
            Console.WriteLine("Addressee: " + result.Extended.Pdf417.MacroPdf417Addressee);
            Console.WriteLine("Date: " + result.Extended.Pdf417.MacroPdf417TimeStamp.ToString());
            Console.WriteLine("Checksum: " + result.Extended.Pdf417.MacroPdf417Checksum);
        }
        Console.WriteLine();
    }
}
{{< /highlight >}} 
{{% alert color="primary" %}}**[ReadMultipleMacroPdf417Barcodes.cs](https://github.com/aspose-barcode/Aspose.BarCode-for-.NET/blob/master/Examples/CSharp/ManageAndOptimizeBarcodeRecognition/ReadMultipleMacroPdf417Barcodes.cs) as a source of code example, hosted by GitHub**{{% /alert %}}

## **Reading 1D Barcode parameters**
{{< highlight csharp>}}
// Instantiate BarCodeReader object
using (BarCodeReader reader = new BarCodeReader(dataDir + "EAN13_EAN5.png", DecodeType.EAN13, DecodeType.Supplement))
    // Read Code128 bar code and Detect bar code orientation
    foreach (BarCodeResult result in reader.ReadBarCodes())
    {
        Console.WriteLine("Type: " + result.CodeTypeName);
        Console.WriteLine("CodeText: " + result.CodeText);
        Console.WriteLine("Value: " + result.Extended.OneD.Value);
        Console.WriteLine("CheckSum: " + result.Extended.OneD.CheckSum);
    }
{{< /highlight >}} 
{{% alert color="primary" %}}**[ReadOneDBarcodes.cs](https://github.com/aspose-barcode/Aspose.BarCode-for-.NET/blob/master/Examples/CSharp/ManageAndOptimizeBarcodeRecognition/ReadOneDBarcodes.cs) as a source of code example, hosted by GitHub**{{% /alert %}}

## **Reading Code128 Barcode parameters**
{{< highlight csharp>}}
// Instantiate BarCodeReader object
using (BarCodeReader reader = new BarCodeReader(dataDir + "rotatedbarcode.jpg", DecodeType.Code128))
    // Read Code128 bar code and Detect bar code orientation
    foreach (BarCodeResult result in reader.ReadBarCodes())
    {
        Console.WriteLine("Type: " + result.CodeTypeName);
        Console.WriteLine("CodeText: " + result.CodeText);
        Console.WriteLine("Portions: ");
        foreach (Code128DataPortion portion in result.Extended.Code128.Code128DataPortions)
            Console.WriteLine("Subtype:" + portion.Code128SubType.ToString() + "Data:" + portion.Data);
    }
{{< /highlight >}} 
{{% alert color="primary" %}}**[ReadCode128Barcodes.cs](https://github.com/aspose-barcode/Aspose.BarCode-for-.NET/blob/master/Examples/CSharp/ManageAndOptimizeBarcodeRecognition/ReadCode128Barcodes.cs) as a source of code example, hosted by GitHub**{{% /alert %}}

## **Reading QR Barcode parameters**
{{< highlight csharp>}}
// Instantiate BarCodeReader object
using (BarCodeReader reader = new BarCodeReader(dataDir + "QRStructuredAppend.png", DecodeType.QR))
    // Read Code128 bar code and Detect bar code orientation
    foreach (BarCodeResult result in reader.ReadBarCodes())
    {
        Console.WriteLine("Type: " + result.CodeTypeName);
        Console.WriteLine("CodeText: " + result.CodeText);
        Console.WriteLine("BarCodes Quantity: " + result.Extended.QR.QRStructuredAppendModeBarCodesQuantity);
        Console.WriteLine("BarCode Index: " + result.Extended.QR.QRStructuredAppendModeBarCodeIndex);
        Console.WriteLine("Parity Data: " + result.Extended.QR.QRStructuredAppendModeParityData);
    }
{{< /highlight >}} 
{{% alert color="primary" %}}**[ReadQRBarcodes.cs](https://github.com/aspose-barcode/Aspose.BarCode-for-.NET/blob/master/Examples/CSharp/ManageAndOptimizeBarcodeRecognition/ReadQRBarcodes.cs) as a source of code example, hosted by GitHub**{{% /alert %}}

## **Reading Databar Barcode parameters**
{{< highlight csharp>}}
// Instantiate BarCodeReader object
using (BarCodeReader reader = new BarCodeReader(dataDir + "Databar.png", DecodeType.DatabarExpanded, DecodeType.DatabarExpandedStacked))
    // Read Code128 bar code and Detect bar code orientation
    foreach (BarCodeResult result in reader.ReadBarCodes())
    {
        Console.WriteLine("Type: " + result.CodeTypeName);
        Console.WriteLine("CodeText: " + result.CodeText);
        Console.WriteLine("Is DataBar has 2D component: " + result.Extended.DataBar.Is2DCompositeComponent.ToString());
    }
{{< /highlight >}} 
{{% alert color="primary" %}}**[ReadDatabarBarcodes.cs](https://github.com/aspose-barcode/Aspose.BarCode-for-.NET/blob/master/Examples/CSharp/ManageAndOptimizeBarcodeRecognition/ReadDatabarBarcodes.cs) as a source of code example, hosted by GitHub**{{% /alert %}}