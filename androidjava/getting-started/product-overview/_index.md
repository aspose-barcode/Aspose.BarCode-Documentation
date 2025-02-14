---
title: Product Overview
type: docs
weight: 10
url: /androidjava/product-overview/
---

## **General Features**
- Generate and identify barcodes efficiently
- Support for **80+ barcode symbologies**, including **1D, 2D, DataBar, Postal, HIBC, and GS1 types**
- Customize barcode appearance settings
- Rotate barcode images as needed
- Encode and decode **non-English characters** in 2D barcodes
- Fine-tune recognition engine parameters for better accuracy
- Save and load barcodes from **streams or files**
- Print barcode labels efficiently
- Work with **complex barcodes**, such as **Swiss QR Code**

## **Barcode Recognition Features**
**Class <a href="https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.barcoderecognition/barcodereader/" target="_blank">BarCodeReader</a>**
is intended for detecting and reading barcodes from images.
- **BarCodeReader class**: Read **1D and 2D barcodes** at any angle from an image
- Support for multiple **image formats**
- Reading images with resolutions ranging from 75 to 600 dpi
- **Recognize barcodes in challenging conditions**, such as **blurry, noisy, or damaged images**
- **Specify targeted scan areas** within an image for faster and more precise recognition
- **Predefine barcode symbologies** to optimize the recognition process
- **Fine-tune the recognition engine** for the best balance between speed and accuracy (manually or using built-in presets).  
  Examples of supported scenarios:
    - Color barcodes on color backgrounds
    - Dashed industrial **DataMatrix** barcodes
    - Scaled-down images
    - Damaged barcodes with incorrect text
    - Corrupted **QR Codes** and more

- **Detect and read all barcodes** within the specified scan region
- **Read multiple barcode** from a single scanned area
- **Retrieve angle and region information** for each recognized barcode (bounding region can be defined using points, quadrangles, or rectangles)
- **Perform checksum validation** for **1D and postal barcodes**
- **Enhance detection speed** using **multi-threading**
- **Extract barcodes from PDFs** using **Aspose.PDF**

## **Barcode Generation Features**
- **Class <a href="https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/barcodegenerator/" target="_blank">BarcodeGenerator</a>**
generate barcode with customizable settings
- **Extensive barcode customization options**, including size, resolution, height, background color, bar color, rotation angle, X-dimension, image quality, captions, wide-to-narrow ratio, and more
- Save barcodes in multiple image formats
- **Configure barcode encoding types and parameters** for enhanced flexibility
- **Support checksum addition** for **1D barcodes** and **supplementary data**
- **Adjust X- and Y-dimensions** for **2D barcodes**
- **Fine-tune wide-to-narrow ratios** for supported symbologies to improve recognition accuracy
- **Set encoding types for 2D barcodes**, including **Error Checking and Correcting (ECC)** and **Extended Channel Interpretation (ECI)**
- **Encode DataMatrix barcodes** using **X12, EDIFACT, and Base 256**

## **Input Image Formats**
- JPEG
- PNG
- GIF
- BMP
- WEBP
- HEIF/HEIC
## **Output Image Formats**
- JPEG
- PNG
- GIF
- BMP
- WEBP
- EMF
- PDF
## **Supported Platforms**
- Supported starting from Android 8.0 (Oreo) - SDK 26.
## **Supported Barcode Symbologies**
***Aspose.BarCode for Android via Java*** supports over 80
different <a href="https://en.wikipedia.org/wiki/Barcode#Types_of_barcodes" target="_blank">barcode types</a> used in a
variety of industries, namely, 1D (linear), 2D (including QR codes), and postal symbologies. The detailed information
about generating barcodes using various barcode standards can be found in
section <a href="/barcode/java/generate-barcode-types/" target="_blank">Generation Specifics for Symbologies</a>.

**Linear barcode types**, or *1D barcodes*, correspond to the first generation of one-dimensional barcodes (1D) that are
used to represent information by varying the widths and spacings of parallel lines. Some 1D symbologies allow encoding
only numbers, while others permit encoding also letters.

**DataBar barcodes** (former RSS-14) are 1D and 1D staked barcodes, which were developed to efficiently encode [*GS1
Application Identifier*](https://ref.gs1.org/ai/?lang=en) data.

**Matrix barcodes**, also known as *2D barcodes*, have been introduced as a two-dimensional way to encode information.
Two-dimensional (2D) barcodes are generated using various symbols and shapes. This barcode type is considered to be more
efficient, as such barcodes contain more data per unit area, and most of them are self-correctable.

**Postal barcodes** are specific symbologies used by postal services in different countries.

**HIBC barcodes** encode data in [special format](https://www.hibcc.org/udi-labeling-standards/barcode-standards/) which
is used in Health Industry. As transport, the barcodes use other 1D and 2D barcodes and encode data as Alpha-Numeric.

**GS1 barcodes** use other 1D and 2D barcodes to encode [*GS1 Application Identifier*](https://ref.gs1.org/ai/?lang=en)
data.
