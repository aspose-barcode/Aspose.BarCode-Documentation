---
title: Quick Start
type: docs
ai_search_scope: "barcode_python-java_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 80
feedback: BARCODECOM
url: /python-java/quick-start
---

This section provides quick code samples to help you get started with barcode 
generation and recognition using Aspose.BarCode for Python via Java.

## **How to Read Barcodes from an Image**
This example demonstrates how to recognize a Code 128 barcode from an image file.

{{<highlight python>}}
    license = Assist.License()
    license.setLicense(pythonLicensePath)
    barcodeReader = BarCodeReader(image_path,None, DecodeType.CODE_128)
    barcodeReader.setQualitySettings(QualitySettings.getMaxQuality())
    results = barcodeReader.readBarCodes()
    for result in results:
        print("Code Type:", result.getCodeTypeName())
        print("Code Text:", result.getCodeText())
{{</highlight>}}

## **How to Generate a Barcode and Save to a File**
This example shows how to generate a QR code and save it as a PNG file.

{{<highlight python>}}
    license = Assist.License()
    license.setLicense(pythonLicensePath)
    generator = BarcodeGenerator(EncodeTypes.CODE_128, "123456")
    image = generator.generateBarCodeImage()
    generator.save(image_path, Generation.BarCodeImageFormat.PNG)
    barcodeReader = BarCodeReader(image_path, None, DecodeType.CODE_128)
    barcodeReader.setQualitySettings(QualitySettings.getMaxQuality())
    results = barcodeReader.readBarCodes()
    for result in results:
        print("Code Type:", result.getCodeTypeName())
        print("Code Text:", result.getCodeText())
{{</highlight>}}

## **How to Generate and Read a Complex Barcode**
This example demonstrates how to generate and read a complex Mailmark 2D barcode.
{{<highlight python>}}
    license = Assist.License()
    license.setLicense(pythonLicensePath)
    swissQRCodetext = ComplexBarcode.SwissQRCodetext(None)
    swissQRCodetext.getBill().setAccount("CH450023023099999999A")
    swissQRCodetext.getBill().getCreditor().setName("Name")
    swissQRCodetext.getBill().getCreditor().setCountryCode("NL")
    swissQRCodetext.getBill().setBillInformation("BillInformation")
    complexBarcodeGenerator = ComplexBarcodeGenerator(swissQRCodetext)
    file_path = os.path.join(folder, "swiss_qr_codetext.png")
    complexBarcodeGenerator.save(file_path, BarCodeImageFormat.PNG)
    barCodeReader = BarCodeReader(file_path, None, Recognition.DecodeType.QR)
    barCodeResults = barCodeReader.readBarCodes()
    for result in barCodeResults:
        print("BarCode Type: " + result.getCodeTypeName())
        print("BarCode CodeText: " + result.getCodeText())
{{</highlight>}}




