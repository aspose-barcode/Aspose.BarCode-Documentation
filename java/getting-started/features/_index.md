---
title: Features
type: docs
weight: 30
url: /java/features/
---

## **General Features**
- Creating barcode labels
- Reading barcode images
- Supporting multiple symbology specifications (60+ symbologies: 1D, 2D, and postal barcodes)
- Managing barcode appearance-related parameters
- Image rotation
- Encoding and decoding non-English characters in 2D types
- Customizing recognition engine variables
- Saving to or loading from a stream or a file
- Label printing
- Working with complex barcodes (e.g. Swiss QR Code) 

## **Barcode Recognition**
- Reading 1D and 2D barcodes at any angle from an image
- Supporting popular image formats: JPEG, TIFF, PNG, BMP, and GIF
- Reading images with resolution from 75 to 600 dpi
- Reading highly blurred or noised images
- Specifying image areas to scan barcodes
- Predefining target barcode types
- Managing recognition engine variables to reach the best trade-off between reading speed and quality (both manually and through embedded presets). For example, the following cases can be allowed for recognition: color barcodes on color background, dashed industrial Datamatrix barcodes, decreased images, damaged barcodes with incorrect text, damaged QR/MicroQR barcodes, and others
- Detecting and then reading all barcodes presented in the scanned region
- Reading barcodes of different 1D symbologies from a single scanned region
- Defining the angle and region information for all barcodes recognized in an image (using points, quadrangle, or rectangle to specify a bounding barcode region)
- Performing checksum validation for 1D and postal barcodes
- Increasing the barcode detection speed through multi-threading
- Scanning from multi-page TIFF through System.Drawing

## **Barcode Generation**
- Generating barcode labels according to required settings
- Providing a wide range of options to customize barcode image appearance (size, resolution, height, background color, bar color, rotation angle, X-dimension, image quality, captions, wide-to-narrow-ratio, and others)
- Saving barcode labels in various image formats: JPEG, TIFF, PNG, BMP, GIF, EMF, and SVG 
- Customizing the barcode encoding type and parameters
- Supporting checksum addition (for 1D barcodes) and supplement data
- Supporting X- and Y-dimensions for 2D barcodes
- Customizing a wide-to-narrow ratio for the supported symbologies to improve recognition precision
- Setting an encoding type for 2D barcodes: Error Checking and Correcting (ECC) or Extended Channel Interpretation (ECI)
- Providing visual components for barcode generation in WinForms and WPF (e.g. supporting WYSIWYG editing through GUI-based controls)
- Encoding DataMatrix barcodes through X12, EDIFACT, and Base 256

## **Barcode Imaging**
- Customizing barcode image borders, border color, style, margins, and width
- Customizing barcode image color, background color, and bar color
- Customizing bar height
- Customizing barcode caption and its font, background/foreground colors, alignment, and location
- Rotating barcode images to any degree
- Setting the required quality and resolution setting for barcode images to be generated
- Anti-aliasing for barcode images
- Selecting size units (inches or millimeters)
- Auto-sizing of barcode images
- Rendering barcode images on any device


The tables below summarize the availability of features of Aspose.BarCode for Java and links to supported Barcode generation and recognition symbologies.
**Features Summary**

|**General**|
| :- |
|JSP, Servlet support|
|**Image Formats**|
|JPEG|
|Metafile|
|TIFF|
|**Barcode Features**|
|Font Handling|
|X-Dimension|
|Y-Dimension|
|Bar Height Customization|
|Checksum|
|Supplement Data|
|wide narrow ratio|
|Background Color|
|Fore Color|
|Barcode Alignment & Location|
|WYSIWYG Editing|
|**Image Formatting Features**|
|Background Color|
|Fore Color|
|Border Style|
|Image Margin|
|The rotation at any angle|
|Customized Resolution|
|Caption Above|
|Caption Below|
|Auto Sizing|
|High Image Quality|
|Image Scaling|
|**Other Features**|
|Enumerate local available printers and resolutions|
|HTTP Handler Support|

### **Barcode Recognition Features**
- Aspose.BarCode.BarCodeReader reads the most common 1D, 2D barcodes anywhere at any angle from an image.

### **Barcode Imaging Features**
- Manipulate barcode image borders, border color, style, margins & width etc.
- Barcode image color, back color and bar color can be modified.
- Rotate barcode images to any degree.
- High-Quality barcode images.
- Anti-Aliasing for barcode images.
- Barcode Image MarginsF can be managed.
- Customized Resolution.
- Size in inches and millimeters.
- Auto Sizing of barcode images.
- Create barcode images to image formats like JPEG, TIFF, PNG, TIFF, WMF, metafile etc.
- Render barcode images on any device and create device resolution dependent images.
