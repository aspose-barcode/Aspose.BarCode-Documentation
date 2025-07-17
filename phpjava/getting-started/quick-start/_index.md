---
title: Quick Start
type: docs
ai_search_scope: "barcode_phpjava_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 80
feedback: BARCODECOM
url: /phpjava/quick-start
---

This section provides quick code samples to help you get started with barcode 
generation and recognition using Aspose.BarCode for PHP via Java.

## **How to Read Barcodes from an Image**
This example demonstrates how to recognize a Code 128 barcode from an image file.

{{<highlight php>}}
    $license = new License();
    $license->setLicense("Aspose.BarCode.PHP.Java.lic");
    $filePath = "code_128.gif";
    $reader = new BarCodeReader($filePath, null, DecodeType::CODE_128);
    $resultsArray = $reader->readBarCodes();
    foreach ($resultsArray as $barCodeResult) {
        $codeText = $barCodeResult->getCodeText();
        $codeType = $barCodeResult->getCodeTypeName();
        echo "CodeText: $codeText\n";
        echo "CodeType: $codeType\n";
    }
{{</highlight>}}

## **How to Generate a Barcode and Save to a File**
This example shows how to generate a QR code and save it as a PNG file.

{{<highlight php>}}
    $license = new License();
    $license->setLicense("Aspose.BarCode.PHP.Java.lic");
    $filePath = "qr.png";
    $generator = new \Aspose\Barcode\BarcodeGenerator(\Aspose\Barcode\EncodeTypes::QR, "123456");
    $generator->save($filePath, \Aspose\Barcode\BarCodeImageFormat::PNG);
    $reader = new BarCodeReader($filePath, null, DecodeType::QR);
    $resultsArray = $reader->readBarCodes();
    foreach ($resultsArray as $barCodeResult) {
        $codeText = $barCodeResult->getCodeText();
        $codeType = $barCodeResult->getCodeTypeName();
        echo "CodeText: $codeText\n";
        echo "CodeType: $codeType\n";
    }
{{</highlight>}}

## **How to Generate and Read a Complex Barcode**
This example demonstrates how to generate and read a complex Mailmark 2D barcode.
{{<highlight php>}}
    $license = new License();
    $license->setLicense("Aspose.BarCode.PHP.Java.lic");
    $swissQRCodetext = new SwissQRCodetext(null);
    $bill = $swissQRCodetext->getBill();
    $bill->setAccount("CH450023023099999999A");
    $bill->getCreditor()->setName("Name");
    $bill->getCreditor()->setCountryCode("NL");
    $bill->setBillInformation("BillInformation");
    $complexBarcodeGenerator = new ComplexBarcodeGenerator($swissQRCodetext);
    $image_path = "swiss-qr-codetext.png";
    $complexBarcodeGenerator->save($image_path, \Aspose\Barcode\BarCodeImageFormat::PNG);
    $reader = new \Aspose\Barcode\BarCodeReader($image_path, null, \Aspose\Barcode\DecodeType::ALL_SUPPORTED_TYPES);
    $resultsArray = $reader->readBarCodes();
    foreach ($resultsArray as $barCodeResult) {
        $codeText = $barCodeResult->getCodeText();
        $codeType = $barCodeResult->getCodeTypeName();
        echo "CodeText: $codeText\n";
        echo "CodeType: $codeType\n";
    }
{{</highlight>}}



