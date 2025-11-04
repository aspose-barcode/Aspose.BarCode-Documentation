---
title: Basic Reading Workflow with Barcode Generation and Recognition
type: docs
description: >-
  This example shows how to generate a Code‑128 barcode, save it as a PNG image,
  and then read the barcode back using Aspose.BarCode for .NET. It demonstrates
  a complete end‑to‑end workflow that can be used in automated tests or QA
  pipelines.
keywords:
  - Aspose.BarCode for .NET
  - barcode generation
  - barcode reading
  - Code128 barcode
  - BarCodeReader
  - DecodeType.AllSupportedTypes
  - XDimension
  - .NET example
  - automated QA workflow
  - barcode image PNG
  - Aspose barcode tutorial
ai_search_scope: barcode_dotnet_doc
ai_search_endpoint: 'https://docsearch.api.aspose.cloud/ask'
weight: 10
feedback: BARCODECOM
notoc: true
url: >-
  /net/barcode-reading/basic-reading-workflow-with-barcode-generation-and-recognition/
gist_url: 'https://gist.github.com/fahadadeel/97825b94284004194c32c3fe8abe4f40'
gist_id: 97825b94284004194c32c3fe8abe4f40
---
The program first sets the Aspose license, then builds absolute paths for the project’s data folder and an output sub‑folder. It creates a Code‑128 barcode with the text *Workflow Test 123*, configures the X‑dimension to 2 pixels and the image resolution to 300 dpi, and saves the image as PNG. Afterwards a BarCodeReader is instantiated for the generated file with `DecodeType.AllSupportedTypes`, which enables detection of any supported barcode type. The reader scans the image, returns a collection of `BarCodeResult` objects, and the code prints each barcode’s text and type to the console.

## Key Features

- License initialization with LicenseHelper
- Dynamic creation of output directories
- Barcode generation using BarcodeGenerator
- Custom X‑Dimension and image resolution settings
- Saving barcode image in PNG format
- Barcode recognition with BarCodeReader
- DecodeType.AllSupportedTypes to auto‑detect any barcode format
- Iterating over multiple detection results
- Retrieving CodeText and CodeTypeName from detection results

[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object]

## Source Code

The following code sample demonstrates the implementation:

{{< gist "fahadadeel" "97825b94284004194c32c3fe8abe4f40" "BasicReadingExampleWorkFlow.cs" >}}

## How to Use This Example

1. **Copy the Code**: Use the copy button in the code block above to copy the complete example
2. **View Full Gist**: Visit the [complete example on GitHub Gist](https://gist.github.com/fahadadeel/97825b94284004194c32c3fe8abe4f40) for additional files and documentation
3. **Download**: Clone the gist directly to your machine:
   ```bash
   git clone https://gist.github.com/97825b94284004194c32c3fe8abe4f40.git
   ```
4. **Integration**: Add the code to your Aspose.BarCode for .NET project and ensure proper license setup
