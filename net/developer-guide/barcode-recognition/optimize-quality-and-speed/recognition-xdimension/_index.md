---
title: Recognition XDimension Mode
type: docs
description: "This article explains how barcode recognition can be optimized for different bercode sizes and scan resolutions"
keywords: "Improve Barcode Recognition, Optimize Barcode Reading, Optimized Scan for Barcode Recognition, Barcode Resolution, Speed Up Barcode Reading, Image Processing for Barcode, Read Many Barcodes from One Image, Aspose.BarCode, Read Barcode C#"
weight: 20
feedback: BARCODECOM
url: /net/recognition-xdimension/
aliases:
- /net/detect-barcode-regions/

---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can check the quality of Aspose.BarCode recognition and view the results online.{{% /alert %}}
## **Overview**
***Aspose.BarCode for .NET*** provides special mode which uses knowledge about barcode minimal element: matrix cell or bar. This mode can be set with [*XDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension) and [*UseMinimalXDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/xdimensionmode/) properties from [*QualitySettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings) and allows to cut off noise, text and non-barcode elements to increase performance. With using [*UseMinimalXDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/xdimensionmode/) other property [*MinimalXDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/minimalxdimension) is used to set minimal barcode element.
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **XDimension Mode**
This section provides detailed information about [*XDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension) and [*UseMinimalXDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/xdimensionmode/) properties to enable required modes and listed in the table below.

|XDimension Mode|Description|
|---|---|
|*Auto*| At this time the same mode as *Normal*. In the future AI based detection |
|*Small*| Detects barcodes with small [*XDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension) in 1 pixel or more of minimal barcode element |
|*Normal*| Detects barcodes with base [*XDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension) 2-5 pixels or more of minimal barcode element. The value is depends from barcode type |
|*Large*| Detects barcodes with large [*XDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension) captured with high-resolution cameras |
|*UseMinimalXDimension*| Detects barcodes with [*XDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension) set in [*UseMinimalXDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/xdimensionmode/) property |

## **Using XDimension with 1D Barcode Types**
The following table shows difference in recognition quality, depends on [*XDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/xdimension) settings.

<p align="center"><img src="many_code128.png" height="45%" width="45%"></p>

| XDimension Normal | XDimension Small | XDimension UseMinimalXDimension | 
|---|---|---|
| Recognized barcodes: **2** | Recognized barcodes: **5** | Recognized barcodes: **5** |

``` csharp
Console.WriteLine("ReadXDimension1DDocument:");
//recognize image with XDimension Normal
Console.WriteLine("XDimensionMode: Normal");
using (BarCodeReader read = new BarCodeReader($"{path}many_code128.png", DecodeType.Code128))
{
    read.QualitySettings.XDimension = XDimensionMode.Normal;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}


//recognize image with XDimension 
Console.WriteLine("XDimensionMode: Small");
using (BarCodeReader read = new BarCodeReader($"{path}many_code128.png", DecodeType.Code128))
{
    read.QualitySettings.XDimension = XDimensionMode.Small;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//recognize image with XDimension 
Console.WriteLine("XDimensionMode: UseMinimalXDimension");
using (BarCodeReader read = new BarCodeReader($"{path}many_code128.png", DecodeType.Code128))
{
    read.QualitySettings.XDimension = XDimensionMode.UseMinimalXDimension;
    read.QualitySettings.MinimalXDimension = 1;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
```

<details>  
<summary>View the results of code execution</summary>

```text  
ReadXDimension1DDocument:
XDimensionMode: Normal
Barcodes read: 2
Code128:Aspose Code 03
Code128:Aspose Code 04
XDimensionMode: Small
Barcodes read: 5
Code128:Aspose Diag 01
Code128:Aspose Code 02
Code128:Aspose Code 03
Code128:Aspose Code 01
Code128:Aspose Code 04
XDimensionMode: UseMinimalXDimension
Barcodes read: 5
Code128:Aspose Diag 01
Code128:Aspose Code 02
Code128:Aspose Code 03
Code128:Aspose Code 01
Code128:Aspose Code 04
```

</details>


<p align="center"><img src="code128_big_and_small.png" width="25%" height="25%"></p>

| XDimension Normal | XDimension Small |
|---|---|---|
| Recognized barcodes: **2** | Recognized barcodes: **3** |

``` csharp
Console.WriteLine("ReadXDimension1DThreeCode128:");
//recognize image with XDimension Normal
Console.WriteLine("XDimensionMode: Normal");
using (BarCodeReader read = new BarCodeReader($"{path}code128_big_and_small.png ", DecodeType.Code128))
{
    read.QualitySettings.XDimension = XDimensionMode.Normal;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}


//recognize image with XDimension Small
Console.WriteLine("XDimensionMode: Small");
using (BarCodeReader read = new BarCodeReader($"{path}code128_big_and_small.png ", DecodeType.Code128))
{
    read.QualitySettings.XDimension = XDimensionMode.Small;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
```

<details>  
<summary>View the results of code execution</summary>

```text  
ReadXDimension1DThreeCode128:
XDimensionMode: Normal
Barcodes read: 2
Code128:Aspose BIG1
Code128:Aspose BIG2
XDimensionMode: Small
Barcodes read: 3
Code128:Aspose BIG1
Code128:Aspose SML1
Code128:Aspose BIG2
```

</details>
