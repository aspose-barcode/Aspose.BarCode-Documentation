---
title: Basic Barcode Generation and Reading Workflow Example
type: docs
description: >-
  Demonstrates how to generate a Code128 barcode, save it as a PNG image, and
  then read the barcode using Aspose.BarCode for .NET with all supported decode
  types.
keywords:
  - Aspose.BarCode
  - C#
  - .NET
  - barcode generation
  - barcode reading
  - Code128
  - BarCodeReader
  - BarcodeGenerator
  - PNG
  - workflow example
ai_search_scope: barcode_dotnet_doc
ai_search_endpoint: 'https://docsearch.api.aspose.cloud/ask'
weight: 10
feedback: BARCODECOM
notoc: true
url: /net/barcode-reading/basic-barcode-generation-and-reading-workflow-example/
gist_url: 'https://gist.github.com/fahadadeel/477a1c5f9b3f37e80d0f6970086fa3ce'
gist_id: 477a1c5f9b3f37e80d0f6970086fa3ce
---
The example first sets the Aspose.BarCode license, then builds absolute paths for the data and output folders. It generates a Code128 barcode containing the text "Workflow Test 123" with a 2‑pixel X‑dimension and 300 dpi resolution, saving the image as PNG. Afterwards, a BarCodeReader is instantiated for the generated image using DecodeType.AllSupportedTypes, and each detected barcode is printed to the console with its text and symbology name.

## Key Features

- License initialization
- Dynamic output directory creation
- Barcode generation with custom X‑dimension and resolution
- Saving barcode to PNG format
- Reading barcodes using BarCodeReader with DecodeType.AllSupportedTypes
- Iterating over detection results and retrieving code text and type

1. **License Setup** – `LicenseHelper.SetLicense();` loads the Aspose.BarCode license to enable full functionality.
2. **Path Preparation** – Calculates the base directory, creates an `outputs` folder, and builds the full file name for the test barcode image.
3. **Barcode Generation** – Creates a `BarcodeGenerator` for `EncodeTypes.Code128` with the message "Workflow Test 123". Customizes the barcode:
   - `XDimension.Pixels = 2` sets the module width.
   - `Resolution = 300` defines the image DPI.
   - `Save(..., BarCodeImageFormat.Png)` writes the barcode to a PNG file.
4. **Reading the Barcode** – Instantiates `BarCodeReader` with the generated PNG and `DecodeType.AllSupportedTypes` to enable detection of any supported symbology.
5. **Processing Results** – Loops through `reader.ReadBarCodes()`; for each `result`, outputs the decoded text (`result.CodeText`) and the symbology name (`result.CodeTypeName`).
6. **Completion Message** – Writes a final console line indicating successful workflow execution.

## Source Code

The following code sample demonstrates the implementation:

{{< gist "fahadadeel" "477a1c5f9b3f37e80d0f6970086fa3ce" "BasicReadingExampleWorkFlow.cs" >}}

## How to Use This Example

1. **Copy the Code**: Use the copy button in the code block above to copy the complete example
2. **View Full Gist**: Visit the [complete example on GitHub Gist](https://gist.github.com/fahadadeel/477a1c5f9b3f37e80d0f6970086fa3ce) for additional files and documentation
3. **Download**: Clone the gist directly to your machine:
   ```bash
   git clone https://gist.github.com/477a1c5f9b3f37e80d0f6970086fa3ce.git
   ```
4. **Integration**: Add the code to your Aspose.BarCode for .NET project and ensure proper license setup
