---
title: Set Barcode Source
type: docs
description: "This Article Describes How to Set Barcode Source for Recognition"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Barcode in WPF Project, Aspose.BarCode, Read Barcode Python"
weight: 10
url: /python-net/set-barcode-source/

---

## **Overview**
There are three ways to set the barcode recognition source: from an image file, a bitmap, or a stream. The following five raster image formats are supported: PNG, JPEG, BMP, TIFF, or GIF. Three options to set the barcode reading source are explained further. 

## **Read Barcodes from Files**
First of all, barcodes can be scanned and recognized from image files. The full or relative path to the source needs to be specified in the *BarCodeReader* constructor. Alternatively, the *set_bar_code_image* method can be used to pass the path to the existing object of class [*BarCodeReader*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/).  


## **Read Barcodes from Bitmap Objects**
It is possible to use a graphical object or a bitmap as a source for barcode reading. Bitmap objects allow working with images consisting of pixel data. To read barcodes from a bitmap, the created bitmap object needs to be passed to the *BarCodeReader()* constructor or the *set_bar_code_image* method. 

## **Read Barcodes from Streams**
In ***Aspose.BarCode for Python via .NET***, a stream (in a binary format) can be also used as a source for barcode recognition. This option can be useful in some situations owing to its versatility and accessibility without file systems. A stream to read barcodes from needs to be passed to the *BarCodeReader()* constructor or the *set_bar_code_image* method.
