---
title: Recognition Color Schemes Modes
type: docs
description: "This article explains how barcode recognition can be optimized for different color schemes"
keywords: "Improve Barcode Recognition, Read Inverted Barcodes, Read Colored Barcode, Aspose.BarCode, Read Barcode"
weight: 40
feedback: BARCODECOM
url: /javascript-cpp/recognition-color-scheme/

---
{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can check the quality of Aspose.BarCode recognition and view the results online.{{% /alert %}}
## **Overview**
***Aspose.BarCode for JavaScript via C++*** allows reading barcodes with non-typical color schemes, like barcodes with inverted colors (luminance) and color barcodes on color images. To do this, two properties [*InverseImage*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings/properties/inverseimage) and [*ComplexBackground*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings/properties/complexbackground) are added to [*QualitySettings*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings). Additional recognition modes for non-typical color schemes can reduce recognition performance and increase recognition time.
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/javascript-cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Inverse Image Mode**

Aspose.BarCode for JavaScript via C++ provides a special feature called [*InverseImage*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings/properties/inverseimage) to facilitate the recognition of barcodes with inverted colors (luminance). This feature can be used when barcodes are printed or displayed with dark backgrounds and light bar elements or when they are captured in inverted color schemes.

The table below describes the different options for *InverseImage* mode:

| **Inverse Image Mode** | **Description** |
|------------------------|-----------------|
| *Auto*                  | Currently functions the same as *Disabled*. This option turns off additional recognition for barcodes with inverted colors. Future updates may include barcode types like *QR* using this mode. |
| *Disabled*              | Disables the additional recognition process for barcodes with inverted colors. |
| *Enabled*               | Activates additional recognition for barcodes with inverted colors, improving recognition accuracy for images where the barcodes have reversed color schemes. |

### **Recognition Results Example:**

The following table shows the difference in barcode recognition quality based on whether *InverseImage* mode is enabled or disabled:

<p align="center"><img src="aztec_regular_inverse.png" width="20%" height="20%"></p>

| **Inverse Image Disabled** | **Inverse Image Enabled** |
|----------------------------|---------------------------|
| Recognized barcodes: **1**  | Recognized barcodes: **2** |

### **Explanation:**
- **Disabled mode**: Only the regular color scheme is analyzed, potentially missing barcodes that have been inverted.
- **Enabled mode**: The recognition engine applies additional processing to detect barcodes with inverted color schemes, leading to a higher recognition count and improved performance in cases where the barcodes are displayed or printed with reversed colors.

This mode is particularly useful when dealing with non-standard barcode presentations or scanned documents with varying contrast and luminance.


```javascript

// recognize image with Inverse image mode Disabled
console.log("InverseImageMode: Disabled");
var reader = new BarCodeInstance.BarCodeReader(`${path}aztec_regular_inverse.png`, "Aztec");
reader.QualitySettings.InverseImage = BarCodeInstance.InverseImageMode.Disabled;
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}
reader.delete();

// recognize image with Inverse image mode Enabled
console.log("InverseImageMode: Enabled");
var reader = new BarCodeInstance.BarCodeReader(`${path}aztec_regular_inverse.png`, "Aztec");
reader.QualitySettings.InverseImage = BarCodeInstance.InverseImageMode.Enabled;
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}

reader.delete();

```

## **Complex Background Mode**

Aspose.BarCode for JavaScript via C++ includes a special option called [*ComplexBackground*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode.barcoderecognition/qualitysettings/properties/complexbackground) that allows the barcode recognition engine to better handle barcodes printed or displayed on complex colored backgrounds. This feature uses techniques like color quantization to differentiate between the barcode and the background, enhancing recognition accuracy.

The following table outlines the available modes for *ComplexBackground*:

| **Complex Background Mode** | **Description** |
|-----------------------------|-----------------|
| *Auto*                       | Currently functions the same as *Disabled*. Does not enable additional recognition for barcodes with colored backgrounds. |
| *Disabled*                   | Disables the feature that allows recognition of barcodes on colored backgrounds. |
| *Enabled*                    | Activates the mode for recognizing barcodes on colored backgrounds by attempting to subtract the background from the image. |

### **Recognition Results Example:**

The table below illustrates the effect of enabling or disabling the *ComplexBackground* mode on recognition quality:

<p align="center"><img src="qr_color.png" width="15%" height="15%"></p>

| **Complex Background Disabled** | **Complex Background Enabled** |
|---------------------------------|--------------------------------|
| Recognized barcodes: **0**      | Recognized barcodes: **1**     |

### **Explanation:**
- **Disabled mode**: The barcode recognition engine treats the entire image as a whole, potentially failing to detect barcodes if the background color interferes with the barcode's visibility.
- **Enabled mode**: The recognition engine processes the image to isolate the barcode from the background, increasing the chances of successful recognition for barcodes printed on colored or patterned backgrounds.

This mode is particularly valuable when dealing with images that contain barcodes on complex or multicolored backgrounds, where standard recognition might not suffice.


```javascript
// recognize image with Complex background mode Disabled
console.log("ComplexBackgroundMode: Disabled");
var reader = new BarCodeInstance.BarCodeReader(`${path}qr_color.png`, "QR");
reader.QualitySettings.ComplexBackground = BarCodeInstance.ComplexBackgroundMode.Disabled;
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}

// recognize image with Complex background mode Enabled
console.log("ComplexBackgroundMode: Enabled");
var reader = new BarCodeInstance.BarCodeReader(`${path}qr_color.png`, "QR");
reader.QualitySettings.ComplexBackground = BarCodeInstance.ComplexBackgroundMode.Enabled;
reader.ReadBarCodes();
for (var i = 0; i < reader.FoundCount; i++) {
    const result = reader.FoundBarCodes(i);
    console.log(`${result.CodeType}: ${result.CodeText}`);
}

reader.delete();

```


