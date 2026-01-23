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
- Pure managed .NET library.
- Supports modern .NET platforms including **.NET Framework**, **.NET**, and **.NET Core**.
- Works across a wide range of platforms supported by **.NET and .NET MAUI**, including **Windows, Linux, macOS, Android, and iOS**.
- Compatible with other Aspose products for extended document workflows.
- Optimized for high-throughput barcode generation and recognition.
- Supports multi-core processing where applicable.
- Designed for batch processing and server-side scenarios.
- Supports common raster image formats for input and output: **BMP**, **JPEG**, **GIF**, **TIFF**, and **PNG**.
- Supports vector image formats for output: **SVG**, **EMF**, and **PDF**.
- Supports a wide range of international barcode standards and symbologies.
- Supports **GS1** standards and industry-specific barcode formats.
- Simple licensing model suitable for development and production environments.
- License can be embedded and protected within the application.

## **Barcode Generation Features**
- The **[*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator)** class provides flexible and reliable barcode generation capabilities.
- Generate a wide range of **1D and 2D barcode symbologies**, including linear, matrix, stacked, postal, GS1, and industry-specific formats.
- Manage barcode size and layout, including X-dimension (module width), bar height, margins and quiet zones, auto-sizing, and scaling.
- Customize barcode appearance, including foreground and background colors, rotation to any angle, borders and frames, and captions with configurable font, alignment, and positioning.
- Generate barcodes with **high-resolution output** suitable for printing and screen display.
- Configure symbology-specific parameters, such as error correction levels (for 2D barcodes), columns, rows, and encoding modes where applicable, as well as checksums and supplemental data for supported 1D barcodes.
- Export generated barcodes to raster image formats (**BMP, JPEG, GIF, TIFF, PNG**) and vector formats (**SVG, EMF, PDF**).
- Generate barcode images fully in memory or save them directly to files or streams.
- Embed barcodes into Word and PDF documents via **[*Aspose.Words*](https://products.aspose.com/words/)** and **[*Aspose.PDF*](https://products.aspose.com/pdf/)**.
- Use visual components for barcode generation in **WinForms** and **WPF** applications.

## **Barcode Recognition Features**
- The **[*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/)** class enables detection and recognition of barcodes from images, image streams, and files.
- Recognize a wide range of **1D and 2D barcode symbologies**, including linear, matrix, stacked, postal, GS1, and industry-specific formats.
- Detect and read barcodes **at any orientation**, including rotated and skewed images.
- Read multiple barcodes from a single image.
- Restrict recognition to **specific image regions** to improve performance and accuracy.
- Validate checksums for supported 1D and postal barcode types.
- Retrieve detailed recognition results, including barcode type, decoded text, and barcode location.
- Process images in common raster formats (**BMP, JPEG, GIF, TIFF, PNG**).
- Support batch processing and high-throughput recognition scenarios.
- Scan barcodes from **multi-page TIFF** images via **System.Drawing** or **Aspose.Drawing.Common**.
- Scan barcodes from **PDF documents** via **[*Aspose.PDF*](https://products.aspose.com/pdf/)**.
- Select predefined recognition modes optimized for different scenarios, such as fast detection, high accuracy, or degraded image conditions.
- Adjust recognition parameters to handle low-quality or noisy images, complex backgrounds, small or dense barcodes, and inverted or low-contrast barcodes.
- Improve recognition performance by limiting expected barcode types and applying appropriate quality presets.

## **Complex Barcode Features**
- The **[*ComplexBarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexbarcodegenerator/)** and **[*ComplexCodetextReader*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexcodetextreader/)** classes enable generation and recognition of complex barcodes based on **structured domain models**, rather than manual composition of barcode text.
- Support complex standards that require strict payload structure, field validation, and formatting rules (for example, **Driving License ID Code** or **Swiss QR Code**).
- Parse and interpret complex barcode payloads into **strongly typed structured data representations**.
- Validate encoded data against format and checksum rules defined by the corresponding complex barcode specification.
- Eliminate manual handling of low-level encoding details such as field separators, control codes, and field ordering.
- Support **round-trip workflows**, converting **structured data into barcode images** and **recognized barcode data back into structured objects**.
