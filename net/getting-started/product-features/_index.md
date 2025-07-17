---
title: Product Features
type: docs
ai_search_scope: "barcode_dotnet_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 30
feedback: BARCODECOM
description: "Product Features of Aspose.BarCode for .NET: Barcode Generation, Recognition, Customization of Barcode Appearance-Related Parameters"
keywords: "Generate Barcodes, Read Barcodes, How to Generate Barcodes in C# .NET, Use Advanced Settings to Style and Customize Barcodes, Aspose.BarCode, C#"
url: /net/product-features/
---

## **General Features**
- Barcode generation
- Barcode recognition
- Symbology specification (80+ symbologies: 1D, 2D, DataBar, Postal, HIBC, GS1 types)
- Managing barcode appearance-related parameters
- Image rotation
- Encoding and decoding non-English characters in 2D types
- Customizing recognition engine variables
- Saving to or loading from a stream or a file
- Label printing
- Working with complex barcodes (e.g. Swiss QR Code) 

## **Barcode Recognition Features**
- Class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader): reading 1D and 2D barcodes at any angle from an image
- Supporting popular image formats: JPEG, TIFF, PNG, BMP, and GIF
- Reading images with resolution from 75 to 600 dpi
- Reading highly blurred or noised images
- Specifying image areas to scan barcodes
- Predefining target barcode types
- Managing recognition engine variables to reach the best trade-off between reading speed and quality (both manually and through embedded presets). For example, the following cases can be allowed for recognition: color barcodes on color background, dashed industrial Datamatrix barcodes, decreased images, damaged barcodes with incorrect text, damaged QR Codes, and others
- Detecting and then reading all barcodes presented in the scanned region
- Reading barcodes of different 1D types from a single scanned region
- Defining the angle and region information for all barcodes recognized in an image (using points, quadrangle, or rectangle to specify a bounding barcode region)
- Performing checksum validation for 1D and postal barcodes
- Increasing the barcode detection speed through multi-threading
- Scanning from multi-page TIFF through System.Drawing
- Scanning from PDF format via [*Aspose.PDF*](https://products.aspose.com/pdf/)

## **Barcode Generation Features**
- Class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator): generating barcode labels according to required settings
- Providing a wide range of options to customize barcode image appearance (size, resolution, height, background color, bar color, rotation angle, X-dimension, image quality, captions, wide-to-narrow-ratio, and others)
- Saving barcode labels in various image formats: JPEG, TIFF, PNG, BMP, GIF, EMF, and SVG 
- Customizing the barcode encoding type and parameters
- Supporting checksum addition (for 1D barcodes) and supplement data
- Supporting X- and Y-dimensions for 2D barcodes
- Customizing a wide-to-narrow ratio for the supported symbologies to improve recognition precision
- Setting an encoding type for 2D barcodes: Error Checking and Correcting (ECC) or Extended Channel Interpretation (ECI)
- Providing visual components for barcode generation in WinForms and WPF (e.g. supporting WYSIWYG editing through GUI-based controls)
- Encoding DataMatrix barcodes through X12, EDIFACT, and Base 256
- Embedding barcodes to Word and PDF formats via [*Aspose.Words*](https://products.aspose.com/words/) and [*Aspose.PDF*](https://products.aspose.com/pdf/)

## **Barcode Imaging Features**
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
