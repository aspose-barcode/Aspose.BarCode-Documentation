---
title: Recognition Color Schemes Modes
type: docs
description: "This article explains how barcode recognition can be optimized for different color schemes"
keywords: "Improve Barcode Recognition, Read Inverted Barcodes, Read Colored Barcode, Aspose.BarCode, Read Barcode C#"
weight: 40
feedback: BARCODECOM
url: /net/recognition-color-scheme/
aliases:
- /net/read-non-typical-barcodes/

---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can check the quality of Aspose.BarCode recognition and view the results online.{{% /alert %}}
## **Overview**
***Aspose.BarCode for .NET*** allows reading barcodes with non-typical color schemes, like barcodes with inverted colors (luminance) and color barcodes on color images. To do this, two properties [*InverseImage*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/inverseimage) and [*ComplexBackground*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/complexbackground) are added to [*QualitySettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings). Additional recognition modes for non-typical color schemes can reduce recognition performance and increase recognition time.
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Inverse Image Mode**
***Aspose.BarCode for .NET*** enables reading barcode images with inverted colors. To do this, it is required to use a special property called [*InverseImage*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/inverseimage), as listed in the table below.

|Inverse Image Mode|Description|
|---|---|
|*Auto*| At this time the same as Disabled. Disables additional recognition for barcodes with inverted colors (luminance). In the future, barcode types like *QR* can use this mode |
|*Disabled*| Disables additional recognition for barcodes with inverted colors (luminance) |
|*Enabled*| Enables additional recognition for barcodes with inverted colors (luminance) |

The following table shows difference in recognition quality, depends on option value.

<p align="center"><img src="aztec_regular_inverse.png" width="20%" height="20%"></p>

| Inverse Image Disabled | Inverse Image Enabled |
|---|---|
| Recognized barcodes: **1** | Recognized barcodes: **2** |

``` csharp
Console.WriteLine("ReadInverseImage:");
//recognize image with Inverse image mode Disabled
Console.WriteLine("InverseImageMode: Disabled");
using (BarCodeReader read = new BarCodeReader($"{path}aztec_regular_inverse.png", DecodeType.Aztec))
{
    read.QualitySettings.InverseImage = InverseImageMode.Disabled;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//recognize image with Inverse image mode Enabled
Console.WriteLine("InverseImageMode: Enabled");
using (BarCodeReader read = new BarCodeReader($"{path}aztec_regular_inverse.png", DecodeType.Aztec))
{
    read.QualitySettings.InverseImage = InverseImageMode.Enabled;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
```

<details>  
<summary>View the results of code execution</summary>

```text  
ReadInverseImage:
InverseImageMode: Disabled
Barcodes read: 1
Aztec:Aspose Regular
InverseImageMode: Enabled
Barcodes read: 2
Aztec:Aspose Regular
Aztec:Aspose Inverse
```

</details>

## **Complex Background Mode**
***Aspose.BarCode for .NET*** enables reading colored barcodes on a colored background. With property [*ComplexBackground*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/qualitysettings/properties/complexbackground) the barcode recognition engine attempts to distinguish the colored background from barcode labels through color quantization and then subtract it. Mode list is shown in the table below.

|Complex Background Mode|Description|
|---|---|
|*Auto*| At this time the same as Disabled. Disables additional recognition of color barcodes on color images |
|*Disabled*| Disables additional recognition of color barcodes on color images |
|*Enabled*| Enables additional recognition of color barcodes on color images |

The following table shows difference in recognition quality, depends on option value.

<p align="center"><img src="qr_color.png" width="15%" height="15%"></p>

| Complex Background Disabled | Complex Background Enabled |
|---|---|
| Recognized barcodes: **0** | Recognized barcodes: **1** |

``` csharp
Console.WriteLine("ReadComplexBackground:");
//recognize image with Complex background mode Disabled
Console.WriteLine("ComplexBackgroundMode: Disabled");
using (BarCodeReader read = new BarCodeReader($"{path}qr_color.png", DecodeType.QR))
{
    read.QualitySettings.ComplexBackground = ComplexBackgroundMode.Disabled;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}

//recognize image with Complex background mode Enabled
Console.WriteLine("ComplexBackgroundMode: Enabled");
using (BarCodeReader read = new BarCodeReader($"{path}qr_color.png", DecodeType.QR))
{
    read.QualitySettings.ComplexBackground = ComplexBackgroundMode.Enabled;
    Console.WriteLine($"Barcodes read: {read.ReadBarCodes().Length}");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
```

<details>  
<summary>View the results of code execution</summary>

```text  
ReadComplexBackground:
ComplexBackgroundMode: Disabled
Barcodes read: 0
ComplexBackgroundMode: Enabled
Barcodes read: 1
QR:Aspose常に先を行く
```

</details>
