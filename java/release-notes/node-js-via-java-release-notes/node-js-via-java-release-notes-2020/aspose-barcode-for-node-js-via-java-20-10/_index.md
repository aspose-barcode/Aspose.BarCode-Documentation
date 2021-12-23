---
title: Aspose.BarCode for Node.js via Java 20.10
type: docs
weight: 50
url: /java/aspose-barcode-for-node-js-via-java-20-10/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Node.js via Java 20.10](https://downloads.aspose.com/barcode/nodejs/new-releases/aspose.barcode-for-node.js-via-java-20.10/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37595 |Implement BarWidthReduction parameter for barcode generation|Enhancement|
|BARCODENET-37640 |Improve BarWidthReduction parameter usability for 2D barcodes|Enhancement|
|BARCODENET-37637 |Issue with DataMatrix encoding|Bug|


## **Public API and Backward Incompatible Changes**
- Added function Generator.BarcodeParameters.setBarWidthReduction(Unit)
- Added function Generator.BarcodeParameters.getBarWidthReduction():Unit

## **Usage Examples**
{{< highlight java>}}
    let gen = new BarcodeGenerator(EncodeTypes.UPCA, "112345678);
    gen.getParameters().getBarcode().getBarWidthReduction().setPixels(2);
    let barcodeImageBase64 = gen.generateBarcodeImage("PNG");
{{< /highlight >}}