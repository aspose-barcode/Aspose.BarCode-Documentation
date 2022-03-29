---
title: Loading Barcode Images using Java API
linktitle: Loading Barcode Images
type: docs
weight: 50
url: /java/loading-barcode-images/
description: Barcode Java API contains two powerful classes to handle barcode generation and recognition. You can load an image from file or stream to read barcode.
---

## **Loading from a File**
Aspose.BarCode for Java contains two powerful classes, BarCodeGenerator and BarCodeReader that handle barcode generation and recognition respectively.

To load an image from a file, pass a file name as a string to the BarCodeReader constructor which accepts a string to load an existing bar code image.

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-barcode_recognition-loading_barcode_images-LoadingFromAFile-LoadingFromAFile.java" >}}
## **Loading from a Stream**
To load an image from a stream, simply pass a stream object that contains a barcode image to the BarCodeReader class constructor accepting an InputStream.

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-barcode_recognition-loading_barcode_images-LoadingFromAStream-LoadingFromAStream.java" >}}
