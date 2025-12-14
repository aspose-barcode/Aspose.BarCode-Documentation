---
title: Quick Start
type: docs
ai_search_scope: "barcode_nodejsjava_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 80
feedback: BARCODECOM
url: /nodejsjava/quick-start
---

This section provides quick code samples to help you get started with barcode 
generation and recognition using Aspose.BarCode for Node.js via Java.

## **How to Read Barcodes from an Image**
This example demonstrates how to recognize a Code 128 barcode from an image file.

{{<highlight javascript>}}
const license = new License();
license.setLicense('Aspose.BarCode.NodeJsviaJava.lic');
const fileName = 'testdata/QuickStart/code_128.gif';
const reader = new BarCodeReader(fileName, null,DecodeType.CODE_128);
const barCodeResults = reader.readBarCodes();
for (const barCodeResult of barCodeResults) {
    console.log('Code Type:', barCodeResult.getCodeTypeName());
    console.log('Code Text:', barCodeResult.getCodeText());
}
{{</highlight>}}

## **How to Generate and read Barcode**
These example shows how to generate and read QR code.

{{<highlight javascript>}}
const license = new License();
license.setLicense('Aspose.BarCode.NodeJsviaJava.lic');
let codetext = "QRおねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。vvおねがいします。おねがいします。おねがいします。おねがいします。genrateおねがいします。おねがいします。おねがいします。おねがいします。qr code with given。おねがいします。@Y&#^##()おねがいします。textします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。heightします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。width。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがいします。おねがい";
let gen = new BarcodeGenerator(EncodeTypes.QR, codetext);
let reader = new BarCodeReader(gen.generateBarCodeImage(BarCodeImageFormat.PNG), null, DecodeType.QR);
let res = reader.readBarCodes();
const barCodeResults = reader.readBarCodes();
for (const barCodeResult of barCodeResults) {
    console.log('Code Type:', barCodeResult.getCodeTypeName());
    console.log('Code Text:', barCodeResult.getCodeText());
}
{{</highlight>}}

## **How to Generate a Barcode and Save to a File**
These example shows how to generate a QR code and save it as a PNG file.

{{<highlight javascript>}}
const license = new License();
license.setLicense('Aspose.BarCode.NodeJsviaJava.lic');
const codeText = '01234567';
const generator = new BarcodeGenerator(EncodeTypes.QR, codeText);
const filePath = 'testdata/QuickStart/qr.png';
generator.save(filePath, BarCodeImageFormat.PNG);
const reader = new BarCodeReader(filePath, null, DecodeType.QR);
const barCodeResults = reader.readBarCodes();
for (const barCodeResult of barCodeResults) {
    console.log('Code Type:', barCodeResult.getCodeTypeName());
    console.log('Code Text:', barCodeResult.getCodeText());
}
{{</highlight>}}



