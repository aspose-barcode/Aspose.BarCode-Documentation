---
title: Special Barcode Recognition Cases
type: docs
description: "This article explains how barcode recognition can be optimized in terms of accuracy and speed in case of various distortions"
keywords: "Improve Barcode Recognition, Read Barcodes with Gaussian Noise, Read Inverted Barcodes, Read Colored Barcode, Read Distorted QR Code, Read Corrupted Barcodes, Read Industrual Data Matrix, Aspose.BarCode, Read Barcodes in Android"
ai_search_scope: "barcode_androidjava_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 20
url: /androidjava/special-recognition-cases/
---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can check the quality of Aspose.BarCode recognition and view the results online.{{% /alert %}}

## **Barcode Images with Gaussian Noise**
Gaussian noise is one of the most common damages that may deteriorate the quality of a source barcode. Most of difficulties correspond to the cases when barcode images have the monochrome color scheme or the distortion grain is considerably bigger than the minimal element of a barcode. To cope with these effects, median filtering mechanisms suitable for both 1D and 2D symbologies can be applied. Median filtering mechanisms also affect image quality due to the possible removal of some barcode elements together with noise; however, they still may be helpful in improving readability of key barcode modules.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

### **Median Filtering for 2D Barcodes**
In ***Aspose.BarCode for Android via Java***, median filtering can be implemented using a special method called *setAllowMedianSmoothing* and setting the median filtering window using the *setMedianSmoothingWindowSize* method. Unlike 1D barcodes, automated selection of a suitable median filtering window is not supported for 2D types.  
  
<!--The following code snippet illustrates how to perform median filtering for the sample barcode image given below.-->
  
<p align="center"><img src="datamatrix_noised.png" width="15%" height="15%"></p>

<!--{{< highlight java>}}
Console.WriteLine("MedianSmoothing:");

//read barcode image with AllowMedianSmoothing set to false
Console.WriteLine("AllowMedianSmoothing: false");
using (BarCodeReader read = new BarCodeReader($"{path}datamatrix_noised.png", DecodeType.DataMatrix))
{
    read.QualitySettings.AllowMedianSmoothing = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with AllowMedianSmoothing set to true
Console.WriteLine("AllowMedianSmoothing: true");
using (BarCodeReader read = new BarCodeReader($"{path}datamatrix_noised.png", DecodeType.DataMatrix))
{
    read.QualitySettings.AllowMedianSmoothing = true;
    read.QualitySettings.MedianSmoothingWindowSize = 4;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

### **Median Filtering for 1D Barcodes**
One-dimensional filtering for linear barcodes can be set using a method called *setAllowSaltAndPaperFiltering*. In this case, the filtering window size is selected automatically.  
  
<!--The following code sample explains how to apply median filtering to 1D barcodes, such as, for example, the barcode image shown further.--> 

<p align="center"><img src="saltandpaper.png" width="30%" height="30%"></p>

<!--{{< highlight java>}}
Console.WriteLine("SaltAndPaperFiltering:");

//read barcode image with AllowSaltAndPaperFiltering set to false
Console.WriteLine("AllowSaltAndPaperFiltering: false");
using (BarCodeReader read = new BarCodeReader($"{path}saltandpaper.png", DecodeType.Code39Standard, DecodeType.Code39Extended))
{
    read.QualitySettings.AllowSaltAndPaperFiltering = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with AllowSaltAndPaperFiltering set to true
Console.WriteLine("AllowSaltAndPaperFiltering: true");
using (BarCodeReader read = new BarCodeReader($"{path}saltandpaper.png", DecodeType.Code39Standard, DecodeType.Code39Extended))
{
    read.QualitySettings.AllowSaltAndPaperFiltering = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

### **Median Filtering for Postal Barcodes**
One-dimensional median filtering for postal symbologies can be performed using the *AllowMicroWhiteSpotsRemoving* method. The size of the filtering window is set automatically.  
  
<!--The following code snippet demonstrates how to perform medial filtering in the case of postal barcodes (as the sample *Planet* barcode given below).-->

<p align="center"><img src="planet_noised.png" width="40%" height="40%"></p>

<!--{{< highlight java>}}
Console.WriteLine("MicroWhiteSpotsRemoving:");

//read barcode image with AllowMicroWhiteSpotsRemoving set to False
Console.WriteLine("AllowMicroWhiteSpotsRemoving: false");
using (BarCodeReader read = new BarCodeReader($"{path}planet_noised.png", DecodeType.Planet))
{
    read.QualitySettings.AllowMicroWhiteSpotsRemoving = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with AllowMicroWhiteSpotsRemoving set to True
Console.WriteLine("AllowMicroWhiteSpotsRemoving: true");
using (BarCodeReader read = new BarCodeReader($"{path}planet_noised.png", DecodeType.Planet))
{
    read.QualitySettings.AllowMicroWhiteSpotsRemoving = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

### **Filtering Out White Spots**
The presence of white spots in barcode images is a frequent problem that appears while sending documents with barcodes through fax transmission. To mitigate this issue in ***Aspose.BarCode for Android via Java***, it is possible to use a special method called *setAllowWhiteSpotsRemoving* that allows filtering out not all Gaussian noise but only white spots.  
  
<!--The following code sample illustrates how to filter out white spot artifacts from the source barcode image demonstrated below.-->

<p align="center"><img src="code128_whitespots.png" width="30%" height="30%"></p>

<!--{{< highlight java>}}
Console.WriteLine("WhiteSpotsRemoving:");

//read barcode image with AllowWhiteSpotsRemoving set to false
Console.WriteLine("AllowWhiteSpotsRemoving: false");
using (BarCodeReader read = new BarCodeReader($"{path}code128_whitespots.png", DecodeType.Code128))
{
    read.QualitySettings.AllowWhiteSpotsRemoving = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with AllowWhiteSpotsRemoving set to true
Console.WriteLine("AllowWhiteSpotsRemoving: true");
using (BarCodeReader read = new BarCodeReader($"{path}code128_whitespots.png", DecodeType.Code128))
{
    read.QualitySettings.AllowWhiteSpotsRemoving = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

## **Reducing Barcode Image Size to Eliminate Visual Artifacts**
In some cases, distortions caused by excessive scaling of a barcode image can be mitigated by reducing the scale space. In ***Aspose.BarCode for Android via Java***, it can be done using a special method called *setAllowDecreasedImage*. Its purpose is to reduce the size of an image and in this way, to facilitate barcode reading by eliminating visual artifacts.   
  
<!--The following code snippet explains how to the size of the source barcode image shown below can be reduced to improve recognition quality.-->

<p align="center"><img src="datamatrix_waved.png" width="20%" height="20%"></p>

<!--{{< highlight java>}}
Console.WriteLine("DecreasedImage:");

//read barcode image with AllowDecreasedImage false
Console.WriteLine("AllowDecreasedImage: false");
using (BarCodeReader read = new BarCodeReader($"{path}datamatrix_waved.png", DecodeType.DataMatrix))
{
    read.QualitySettings.AllowDecreasedImage = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with AllowDecreasedImage true
Console.WriteLine("AllowDecreasedImage: true");
using (BarCodeReader read = new BarCodeReader($"{path}datamatrix_waved.png", DecodeType.DataMatrix))
{
    read.QualitySettings.AllowDecreasedImage = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

## **Reading Inverted Barcode Images**
***Aspose.BarCode for Android via Java*** enables reading barcode images with inverted colors. To do this, it is required to enable a special method called *setAllowInvertImage*. 
<!--The following code snippet shows how to do that considering the provided barcode image as an example.-->

<p align="center"><img src="aztec_regular_inverse.png" width="20%" height="20%"></p>

<!--{{< highlight java>}}
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
To read colored barcodes on a colored background, ***Aspose.BarCode for Android via Java*** provides a special method called *setAllowComplexBackground* that attempts to distinguish the colored background from barcode labels through color quantization and then subtract it. It should be noted that enabling this parameter results in considerable deceleration of recognition speed and thus should be used in special cases only. 
<!--The following code sample explains how to implement subtraction of a colored barcode from the colored background, as demonstrated in the source image given below.-->
  
<p align="center"><img src="qr_color.png" width="15%" height="15%"></p>

<!--{{< highlight java>}}
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

## **Reading Barcodes with Erased or Displaced Bars**
While scanning or sending barcode images using fax transmission, the problem of displaced or erased bars in 1D barcode labels often appears, especially, in those printed out using ink-jet printers. To resolve this issue, ***Aspose.BarCode for Android via Java*** provides two methods called *setAllowOneDWipedBarsRestoration* and *setCheckMore1DVariants* that allow selecting the most suitable recognition option according to the checksum value and other barcode elements. However, it should be noted that enabling these settings may result in incorrect recognition of 1D barcodes.  
  
<!--The following code snippet shows how to work with a barcode image having displaced bars as in the example provided below.-->  

<p align="center"><img src="code128_wipedbars.png" width="40%" height="40%"></p>

<!--{{< highlight java>}}
Console.WriteLine("OneDWipedBarsRestoration:");

//read barcode image with AllowQRMicroQrRestoration and CheckMore1DVariants set to False
Console.WriteLine("AllowQRMicroQrRestoration and CheckMore1DVariants: false");
using (BarCodeReader read = new BarCodeReader($"{path}code128_wipedbars.png", DecodeType.Code128))
{
    read.QualitySettings.AllowOneDWipedBarsRestoration = false;
    read.QualitySettings.CheckMore1DVariants = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with AllowQRMicroQrRestoration and CheckMore1DVariants set to True
Console.WriteLine("AllowQRMicroQrRestoration and CheckMore1DVariants: true");
using (BarCodeReader read = new BarCodeReader($"{path}code128_wipedbars.png", DecodeType.Code128))
{
    read.QualitySettings.AllowOneDWipedBarsRestoration = true;
    read.QualitySettings.CheckMore1DVariants = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

## **Reading Evidently Incorrect Barcodes**
In cases when it is necessary just to detect the presence of barcodes regardless of their validity and corresponding recognition correctness, it is possible to enable two special settings called *setAllowIncorrectBarcodes* and *setReadTinyBarcodes*. The first one is used to attempt performing partial barcode recognition even if the reading process has provided incorrect results; in this case, the barcode data is decoded with [*BarCodeConfidence*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.barcoderecognition/BarCodeConfidence) being set to *NONE*, which means that the correctness of recognition is not guaranteed.  
  
The *setReadTinyBarcodes* method facilitates reading small barcode labels in large images. It is ignored if the *setAllowIncorrectBarcodes* method is called passing the *True* value. However, enabling this parameter may result in recognizing false barcodes in place of actual text or tables.  
  
<!--The following code snippet explains how to force the recognition of the barcode known as unreadable (given below).-->

<p align="center"><img src="pdf417_qr_corrupted.png" width="30%" height="30%"></p>

<!--{{< highlight java>}}
Console.WriteLine("IncorrectBarcodes:");

//read barcode image with AllowIncorrectBarcodes set to False
Console.WriteLine("AllowIncorrectBarcodes: false");
using (BarCodeReader read = new BarCodeReader($"{path}pdf417_qr_corrupted.png", DecodeType.Pdf417, DecodeType.QR))
{
    read.QualitySettings.AllowIncorrectBarcodes = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//read barcode image with AllowIncorrectBarcodes set to True
Console.WriteLine("AllowIncorrectBarcodes: true");
using (BarCodeReader read = new BarCodeReader($"{path}pdf417_qr_corrupted.png", DecodeType.Pdf417, DecodeType.QR))
{
    read.QualitySettings.AllowIncorrectBarcodes = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

## **Reading Severely Distorted QR Codes and Micro QR Codes**
***Aspose.BarCode for Android via Java*** allows reading severely corrupted *QR Code* and *Micro QR Code* labels. This can be enabled by setting the *setAllowQRMicroQrRestoration* parameter. 
<!--The following code sample illustrates how to read a severely damaged *QR Code* barcode that is demonstrated further.-->

<p align="center"><img src="microqr_3d_distorted.png"></p>

<!--{{< highlight java>}}
Console.WriteLine("QRMicroQrRestoration:");

//recognize image with AllowQRMicroQrRestoration false
Console.WriteLine("AllowQRMicroQrRestoration: false");
using (BarCodeReader read = new BarCodeReader($"{path}microqr_3d_distorted.png", DecodeType.MicroQR))
{
    read.QualitySettings.AllowQRMicroQrRestoration = false;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//recognize image with AllowQRMicroQrRestoration true
Console.WriteLine("AllowQRMicroQrRestoration: true");
using (BarCodeReader read = new BarCodeReader($"{path}microqr_3d_distorted.png", DecodeType.MicroQR))
{
    read.QualitySettings.AllowQRMicroQrRestoration = true;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

## **Reading Industrial Data Matrix Barcodes**
Industrial *Data Matrix* barcodes often have dotted patterns or other decoration elements and are placed onto metallic surfaces, in this way, creating embossed indelible barcode labels. To facilitate the recognition of such barcodes, it is possible to enable a special parameter called *setAllowDatamatrixIndustrialBarcodes* that allows reading dashed labels in a slow mode. 
<!--The following code snippet explains how to read sample industrial *Data Matrix* barcodes that are shown in the image below.-->

<p align="center"><img src="datamatrix_industrial.png" width="30%" height="30%"></p>

<!--{{< highlight java>}}
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



