---
title: Set Target Barcode Types for Recognition
linktitle: Set Target Barcode Types
type: docs
description: "This Article Describes How to Set Target Barcode Types for Recognition"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcode Python"
weight: 20
url: /python-net/set-target-barcode-types/
---

## **Overview**
***Aspose.BarCode for Python via .NET*** supports barcode recognition for 60+ various barcode types. To improve the efficiency of the recognition process and optimize its timing, it is recommended to set target symbologies in advance. Otheriwise, the *ALL_SUPPORTED_TYPES* setting of the [*DecodeType*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/decodetype/) enum will be used by default meaning that the library will look over all supported barcode types to check for their presence in the source image. Using this setting will increase the time needed to complete barcode recognition. 

### **List Target Barcode Types in DecodeType**
Target barcode types can be specified by grouping them in a list and passing it to the *BarCodeReader()* constructor or the *set_bar_code_read_type* method.  

### **Use *MultyDecodeType* Mode**
The other way to specify target barcode types is to determine them using a constructor of class [*MultyDecodeType*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/multydecodetype/) and then pass it to class [*BarCodeReader*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodereader/) or the *set_bar_code_read_type* method.  

### **Use Predefined Barcode Type Sets**
Class [*DecodeType*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/decodetype/) provides the following symbology sets for barcode reading:
-	*ALL_SUPPORTED_TYPES* - all available barcode types
-	*TYPES_1D* - all supported 1D types
-	*TYPES_2D* - all supported 2D types
-	*POSTAL_TYPES* - all available postal types
-	*MOST_COMMON_TYPES* - a set of most widespread barcode types defined according to Aspose recommendations

The required set can be specified in the *BarCodeReader* constructor or passed to the *bar_code_read_type* property.

