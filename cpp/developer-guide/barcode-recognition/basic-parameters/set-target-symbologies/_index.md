---
title: Set Target Barcode Types for Recognition
linktitle: Set Target Barcode Types
type: docs
description: "This Article Describes How to Set Target Barcode Types for Recognition"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Barcode in WPF Project, Aspose.BarCode, Read Barcode C++"
ai_search_scope: "barcode_cpp_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 20
feedback: BARCODECOM
url: /cpp/set-target-barcode-types/
---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
***Aspose.BarCode for C++*** supports more than 60 barcode types for recognition. To minimize the time required to complete recognition and avoid attempts to recognize outdated barcodes that are still used as a legacy of some industrial systems, it is recommended to select target barcode symbologies that will be considered for recognition. However, in the case when there is no information about precise symbologies that can be presented in a source image, it is possible to use the default setting *DecodeType.AllSupportedTypes* for the *DecodeType* property so that the source image will be checked for the presence of all supported barcode types. This setting results in the increased time required to complete barcode recognition. 

## **List Barcode Types Defined in DecodeType**
Target symbologies for barcode recognition can be specified as a list and passed to the [*BarCodeReader*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.bar_code_recognition.bar_code_reader/) constructor or the *SetBarCodeReadType* method.  
  

## ***MultyDecodeType* Mode**
The other way to set target symbologies for recognition is to list the required barcode types in a constructor of class *MultyDecodeType* and then to pass an instance of this class to the [*BarCodeReader*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.bar_code_recognition.bar_code_reader/) constructor or the *SetBarCodeReadType* method.  
  

## **Predefined Sets of Types**
Class *DecodeTypes* contains various predefined sets of symbologies for recognition, including the following ones:
-	*AllSupportedTypes* - all supported barcode types
-	*Types1D* - all supported 1D symbologies
-	*Types2D* - all supported 2D symbologies
-	*PostalTypes* - all supported postal symbologies that are mainly used by postal services
-	*MostCommonTypes* - a set of most widely used barcode standards defined according to the Aspose recommendations

The required symbology set can be defined in the [*BarCodeReader*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.bar_code_recognition.bar_code_reader/) constructor or the *SetBarCodeReadType* method.
  
