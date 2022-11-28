---
title: Aspose.BarCode for PHP via Java 20.10
type: docs
weight: 5
url: /java/aspose-barcode-for-php-via-java-20-10/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for PHP via Java 20.10](https://downloads.aspose.com/barcode/php/new-releases/aspose.barcode-for-php-via-java-20.10/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-37595 |Implement BarWidthReduction parameter for barcode generation|Enhancement|
|BARCODENET-37640 |Improve BarWidthReduction parameter usability for 2D barcodes|Enhancement|
|BARCODENET-37637 |Issue with DataMatrix encoding|Bug|


## **Public API and Backward Incompatible Changes**
- Added function Generator.BarcodeParameters.setBarWidthReduction(Unit):void
- Added function Generator.BarcodeParameters.getBarWidthReduction():Unit

## **Usage examples**
{{< highlight java>}}
    $gen = new BarcodeGenerator(EncodeTypes::UPCA,"112345678);
    $gen->getParameters()->getBarcode()->getBarWidthReduction()->setPixels(2);
    $barcodeImage = $gen->generateBarcodeImage("PNG");
{{< /highlight >}}