---
title: Read Damaged or Distorted Barcodes
linktitle: Read Damaged Barcodes
type: docs
description: "This article explains how barcode recognition can be optimized in terms of accuracy and speed in case of various distortions"
keywords: "Improve Barcode Recognition, Read Barcodes with Gaussian Noise, Read Inverted Barcodes, Read Colored Barcode, Read Distorted QR Code, Read Corrupted Barcodes, Read Industrual DataMatrix, Aspose.BarCode, Read Barcode C#"
weight: 30
feedback: BARCODECOM
url: /net/read-damaged-barcodes/
aliases:
- /net/recognition-specifics/
---
 
## **Read Barcode Images with Gaussian Noise**
Gaussian noise is one of the most frequent distortions that may affect the quality of barcode images. The most crucial problems arise in cases when barcode images are monochrome or when the distortion grain is much larger than the minimal barcode element. To mitigate such negative effects, it may be useful to apply median filtering methods that are suitable for both 1D and 2D barcodes. Although median filtering methods also introduce distortions by eliminating barcode elements together with noise, they still may be succeed in improving readability of key barcode modules.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

### **Median Filtering for 2D Barcodes**
In ***Aspose.BarCode for .NET***, median filtering can be implemented using a special property called [*AllowMedianSmoothing*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowmediansmoothing) and setting the median filtering window in the [*MedianSmoothingWindowSize*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/mediansmoothingwindowsize) parameter. Unlike 1D barcodes, automated selection of a suitable median filtering window is not supported for 2D symbologies.  
  
The following code snippet illustrates how to perform median filtering for the sample barcode image given below.
  
<p align="center"><img src="datamatrix_noised.png" width="15%" height="15%"></p>

{{< highlight csharp>}}
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
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
  
MedianSmoothing:  
- AllowMedianSmoothing: false  
Barcodes read: 0  
- AllowMedianSmoothing: true  
Barcodes read: 1  
DataMatrix:87918-1023  
  
</details>

### **Median Filtering for 1D Barcodes**
One-dimensional filtering for linear barcodes can be set using a parameter called [*AllowSaltAndPaperFiltering*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowsaltandpaperfiltering). In this case, the filtering window size is selected automatically.  
  
 The following code sample explains how to apply median filtering to 1D barcodes, such as, for example, the barcode image shown further. 

<p align="center"><img src="saltandpaper.png" width="30%" height="30%"></p>

{{< highlight csharp>}}
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
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
  
SaltAndPaperFiltering:  
- AllowSaltAndPaperFiltering: false  
Barcodes read: 0  
- AllowSaltAndPaperFiltering: true  
Barcodes read: 1  
Code39Standard:0058  
  
</details>

### **Median Filtering for Postal Barcodes**
One-dimensional median filtering for postal symbologies can be performed using the [*AllowMicroWhiteSpotsRemoving*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowmicrowhitespotsremoving) property. The size of the filtering window is set automatically.  
  
The following code snippet demonstrates how to perform median filtering in the case of postal barcodes (as the sample *Planet* barcode given below).

<p align="center"><img src="planet_noised.png" width="40%" height="40%"></p>

{{< highlight csharp>}}
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
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
  
MicroWhiteSpotsRemoving:  
- AllowMicroWhiteSpotsRemoving: false  
Barcodes read: 0  
- AllowMicroWhiteSpotsRemoving: true  
Barcodes read: 1  
Planet:990000837284  
  
</details>

### **Filter Out White Spots**
The presence of white spots in barcode images is a frequent problem that appears while sending documents with barcodes through fax transmission.  To mitigate this issue in ***Aspose.BarCode for .NET***, it is possible to use a special setting called [*AllowWhiteSpotsRemoving*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowwhitespotsremoving) that allows filtering out not all Gaussian noise but only white spots.  
  
The following code sample illustrates how to filter out white spot artifacts from the source barcode image demonstrated below.

<p align="center"><img src="code128_whitespots.png" width="30%" height="30%"></p>

{{< highlight csharp>}}
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
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
  
MicroWhiteSpotsRemoving:  
- AllowMicroWhiteSpotsRemoving: false  
Barcodes read: 0  
- AllowMicroWhiteSpotsRemoving: true  
Barcodes read: 1  
Planet:990000837284  
  
</details>

## **Reduce Barcode Image Size to Eliminate Visual Artifacts**
In some cases, distortions caused by excessive scaling of a barcode image can be mitigated by reducing the scale space. In ***Aspose.BarCode for .NET***, it can be done using a special setting called [*AllowDecreasedImage*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowdecreasedimage). Its purpose is to reduce the size of an image and in this way, to facilitate barcode reading by eliminating visual artifacts.   
  
The following code snippet explains how to the size of the source barcode image shown below can be reduced to improve recognition quality.

<p align="center"><img src="datamatrix_waved.png" width="20%" height="20%"></p>

{{< highlight csharp>}}
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
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
  
DecreasedImage:  
- AllowDecreasedImage: false  
Barcodes read: 0  
- AllowDecreasedImage: true  
Barcodes read: 1  
DataMatrix:D19-WQ9-F91046-0811  
  
</details>


## **Read Barcodes with Erased or Displaced Bars**
While scanning or sending barcode images using fax transmission, the problem of displaced or erased bars in 1D barcode labels often appears, especially, in those printed out using ink-jet printers. To resolve this issue, ***Aspose.BarCode for .NET*** provides two settings called [*AllowOneDWipedBarsRestoration*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowonedwipedbarsrestoration) and [*CheckMore1DVariants*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/checkmore1dvariants) that allow selecting the most suitable recognition option according to the checksum value and other barcode elements. However, it should be noted that enabling these settings may result in incorrect recognition of 1D barcodes.  
  
The following code snippet shows how to work with a barcode image having displaced bars as in the example provided below.  

<p align="center"><img src="code128_wipedbars.png" width="40%" height="40%"></p>

{{< highlight csharp>}}
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
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
  
OneDWipedBarsRestoration:  
- AllowQRMicroQrRestoration and CheckMore1DVariants: false  
Barcodes read: 0  
- AllowQRMicroQrRestoration and CheckMore1DVariants: true  
Barcodes read: 1  
Code128:JJBEA129955634111200235  
  
</details>

## **Read Evidently Incorrect Barcodes**
In cases when it is necessary just to detect the presence of barcodes regardless of their validity and corresponding recognition correctness, it is possible to enable two special settings called [*AllowIncorrectBarcodes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowincorrectbarcodes) and [*ReadTinyBarcodes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/readtinybarcodes). The first one is used to attempt performing partial barcode recognition even if the reading process has provided incorrect results; in this case, the barcode data is decoded with the [*Confidence*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcoderesult/properties/confidence) level being *None*, which means that the correctness of recognition is not guaranteed.  
  
The [*ReadTinyBarcodes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/readtinybarcodes) option facilitates reading small barcode labels in large images. It is ignored if [*AllowIncorrectBarcodes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowincorrectbarcodes) is set to *True*. However, enabling this parameter may result in recognizing false barcodes in place of actual text or tables.  
  
The following code snippet explains how to force the recognition of the barcode known as unreadable (given below).

<p align="center"><img src="pdf417_qr_corrupted.png" width="30%" height="30%"></p>

{{< highlight csharp>}}
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
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
  
IncorrectBarcodes:  
- AllowIncorrectBarcodes: false  
Barcodes read: 0  
- AllowIncorrectBarcodes: true  
Barcodes read: 2  
Pdf417:Aspose Pdf417  
QR:Aspose QR  
  
</details>

## **Read Severely Distorted QR Codes and Micro QR Codes**
***Aspose.BarCode for .NET*** allows reading severely corrupted *QR Code* and *Micro QR Code* labels. This can be enabled by setting the [*AllowQRMicroQrRestoration*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/allowqrmicroqrrestoration) parameter. The following code sample illustrates how to read a severely damaged *QR Code* barcode that is demonstrated further.

<p align="center"><img src="microqr_3d_distorted.png"></p>

{{< highlight csharp>}}
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
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
  
QRMicroQrRestoration:  
- AllowQRMicroQrRestoration: false  
Barcodes read: 0  
- AllowQRMicroQrRestoration: true  
Barcodes read: 1  
MicroQR:FV50CE  
  
</details>

