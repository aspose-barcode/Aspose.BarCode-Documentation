---
title: Read Non-typical Barcodes
type: docs
feedback: BARCODECOM
description: "This article explains how barcode recognition can be optimized in terms of accuracy and speed in case of various distortions"
keywords: "Improve Barcode Recognition, Read Barcodes with Gaussian Noise, Read Inverted Barcodes, Read Colored Barcode, Read Distorted QR Code, Read Corrupted Barcodes, Read Industrual DataMatrix, Aspose.BarCode, Read Barcode Java"
weight: 40
url: /java/read-non-typical-barcodes/
---
 
## **Reading Inverted Barcode Images**
***Aspose.BarCode for Java*** enables reading barcode images with inverted colors. To do this, it is required to enable a special method called *setAllowInvertImage*. 
<!--The following code snippet shows how to do that considering the provided barcode image as an example.-->

<p align="center"><img src="aztec_regular_inverse.png" width="20%" height="20%"></p>

<!--{{< highlight csharp>}}
Console.WriteLine("InvertImage:");

//read barcode image with AllowInvertImage set to false
Console.WriteLine("AllowInvertImage: false");
using (BarCodeReader read = new BarCodeReader($"{path}aztec_regular_inverse.png", DecodeType.Aztec))
{
    read.QualitySettings.AllowInvertImage = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with AllowInvertImage set to true
Console.WriteLine("AllowInvertImage: true");
using (BarCodeReader read = new BarCodeReader($"{path}aztec_regular_inverse.png", DecodeType.Aztec))
{
    read.QualitySettings.AllowInvertImage = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

## **Detecting Colored Barcodes on Colored Background**
To read colored barcodes on a colored background, ***Aspose.BarCode for Java*** provides a special method called *setAllowComplexBackground* that attempts to distinguish the colored background from barcode labels through color quantization and then subtract it. It should be noted that enabling this parameter results in considerable deceleration of recognition speed and thus should be used in special cases only. 
<!--The following code sample explains how to implement subtraction of a colored barcode from the colored background, as demonstrated in the source image given below.-->
  
<p align="center"><img src="qr_color.png" width="15%" height="15%"></p>

<!--{{< highlight csharp>}}
Console.WriteLine("ComplexBackground:");

//read barcode image with AllowComplexBackground set to false
Console.WriteLine("AllowComplexBackground: false");
using (BarCodeReader read = new BarCodeReader($"{path}qr_color.png", DecodeType.QR))
{
    read.QualitySettings.AllowComplexBackground = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with AllowComplexBackground set to true
Console.WriteLine("AllowComplexBackground: true");
using (BarCodeReader read = new BarCodeReader($"{path}qr_color.png", DecodeType.QR))
{
    read.QualitySettings.AllowComplexBackground = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->


## **Read Industrial Data Matrix Barcodes**
Industrial *Data Matrix* barcodes often have dotted patterns or other decoration elements and are placed onto metallic surfaces, in this way, creating embossed indelible barcode labels. To facilitate the recognition of such barcodes, it is possible to enable a special parameter called *setAllowDatamatrixIndustrialBarcodes* that allows reading dashed labels in a slow mode. 
<!--The following code snippet explains how to read sample industrial *Data Matrix* barcodes that are shown in the image below.-->

<p align="center"><img src="datamatrix_industrial.png" width="30%" height="30%"></p>

<!--{{< highlight csharp>}}
Console.WriteLine("DatamatrixIndustrialBarcodes:");

//read barcode image with AllowDatamatrixIndustrialBarcodes set to false
Console.WriteLine("AllowDatamatrixIndustrialBarcodes: false");
using (BarCodeReader read = new BarCodeReader($"{path}datamatrix_industrial.png", DecodeType.DataMatrix))
{
    read.QualitySettings.AllowDatamatrixIndustrialBarcodes = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with AllowDatamatrixIndustrialBarcodes set to true
Console.WriteLine("AllowDatamatrixIndustrialBarcodes: true");
using (BarCodeReader read = new BarCodeReader($"{path}datamatrix_industrial.png", DecodeType.DataMatrix))
{
    read.QualitySettings.AllowDatamatrixIndustrialBarcodes = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->



