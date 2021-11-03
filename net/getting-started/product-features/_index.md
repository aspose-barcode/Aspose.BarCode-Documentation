---
title: Product Features
type: docs
weight: 30
url: /net/product-features/
---

## **General Features**
- Barcode generation
- Barcode recognition
- Symbology specification (60+ symbologies)
- Image rotation
- Encoding and decoding non-English characters in 2D types
- Saving to or loading from stream or file
- Label printing

## **Barcode Recognition**

- ***Class BarcodeReaderReading***: reading 1D and 2D barcodes at any angle from an image
- Supporting popular image formats: JPEG, TIFF, PNG, BMP, GIF and EXIF
- Reading images with resolution from 75 to 600 dpi
- Reading highly blurred or noised images
- Specifying an image area to scan a barcode
- Specifying target barcode types
- Customize internal engine variables to reach the best trade-off between recognition speed and quality
- Defining region information for all barcodes recognized in an image
- Scanning from multi-page TIFF

## **Barcode Generation**
- ***Class BarcodeGenerator***
- Setting appearance properties for a barcode and its caption
- Outputting different image formats: JPEG, TIFF, PNG, BMP, GIF, EXIF 
- Customizing the barcode encoding mode and parameters
- Supporting checksum addition (for 1D barcodes) and supplement data
- Supporting X- and Y-dimensions for 2D barcodes
- Achieving a wide-to-narrow ratio for supported symbologies
- Setting an encoding type for 2D barcodes: Error Checking and Correcting (ECC) or Extended Channel Interpretation (ECI)
- Supporting WYSIWYG editing through GUI-based controls
- Encoding DataMatrix barcodes through X12, EDIFACT, and Base 256 

### **Barcode Imaging**
- Customizing barcode image borders, border color, style, margins, and width
- Customizing barcode image color, back color, and bar color
- Customizing bar height
- Customizing barcode caption and its font, background / foreground colors, alignment, and location
- Rotating barcode images to any degree
- Setting the required quality and resolution of barcode images to be generated
- Anti-aliasing for barcode images
- Selecting size units (inches or millimeters)
- Auto-sizing of barcode images
- Generating barcode images in the required image format (BMP, JPEG, GIF, PNG, TIFF, WMF, or metafile)
- Rendering barcode images on any device

### **Complex Generation Features**
- ***Class ComplexBarcode***: generating 
- 