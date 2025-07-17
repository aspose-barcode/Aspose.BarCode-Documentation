---
title: Set Target Regions for Recognition
linktitle: Set Target Regions
type: docs
description: "This Article Describes How to Set Target Regions in Source Image for Recognition"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Barcode in WPF Project, Aspose.BarCode, Read Barcode Python"
ai_search_scope: "barcode_python-net_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 30
url: /python-net/set-target-regions/
---

## **Overview**
Developers can specify explicitly not only the desired types but also a target region or regions in the source image. This allows optimizing the scanning process by avoiding areas without barcodes. Target regions can be determined using a class called [*Quadrangle*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/quadrangle/). Setting target regions allows improving recognition efficiency and avoiding the regions without any barcodes. Target areas have to be determined accurately as the Aspose library applies heuristic approaches to identify target barcode detection areas. Focusing on too many image regions can lead to recognition efficiency deterioration.

## **Set Unique Target Region**
To set one target area for barcode recognition, it is necessary to create an object of the [*Quadrangle*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/quadrangle/) type and then pass it to the *BarCodeReader* constructor or the *setBarCodeImage* method.  
  

## **Set Several Target Regions**
It is also possible to set several target areas for barcode detection within one source image. This can be done in the same way as described above for one target region, i.e., using the *BarCodeReader* constructor or the *setBarCodeImage* method.  
  
