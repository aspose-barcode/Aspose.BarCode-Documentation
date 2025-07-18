---
title: Generate Patch Code Barcodes
linktitle: Patch Code
type: docs
description: "Aspose.BarCode for Python via .NET enables Patch Code barcode generation"
keywords: Generate Patch Code Barcodes, Create Patch Code, How to Generate Patch Code Barcodes, Aspose.BarCode for Python
ai_search_scope: "barcode_python-net_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 140
url: /python-net/generate-patch-code/

---
{{% alert color="primary" %}}[Generate Patch Code Barcodes Online](https://products.aspose.app/barcode/generate/patchcode): You can check the quality of ***Aspose.BarCode*** generation for Patch Code barcodes and view the results online.{{% /alert %}}

## **Overview**
Kodak introduced the *Patch Code* barcode standard to improve the efficiency of automated multi-page document scanning. *Patch Code* barcodes are not intended to encode information. Here, barcode patterns denote various tasks to be executed. ***Aspose.BarCode for Python via .NET*** allows generating six *Patch Code* patterns and provides two generation modes: creating barcode images for manual placement on a page or generating entire A4 or US Letter pages. *Patch Code* barcodes are printed out on four sides of a document page. By design, scanning only one of the sides is sufficient to perform barcode reading. This enables barcode recognition for rotated pages.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Patch Code Patterns**
***Aspose.BarCode for Python via .NET*** supports *Patch Code* barcode generation using six main patterns. The extended set of patterns suggested by Kodak that has not been standardized is not available. The main six patterns are: *Patch I*, *Patch II*, *Patch III*, *Patch IV*, *Patch T*, and *Patch VI*.  
  
Following *Patch Code* barcodes correspond to six basic *Patch Code* patterns.
  
|Patch Code Patterns|Patch I|Patch II|Patch III|Patch IV|Patch T|Patch VI|  
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| |<img src="patchcodei.png">|<img src="patchcodeii.png">|<img src="patchcodeiii.png">|<img src="patchcodeiv.png">|<img src="patchcodet.png">|<img src="patchcodevi.png">|
  
## **Patch Code Generation Modes**
Two generation modes are available for *Patch Code*: generating barcode images or creating A4 or US Letter pages with landscape or portrait orientation. Moreover, it is possible to add an optional *QR Code* barcode as a supplement barcode add-on that may be useful to complete barcode scanning. Using other symbologies as add-on barcodes is not available.  
  
**Patch Code Generation Formats** 
  
To manage the generation format for *Patch Code* barcodes, developers can use the *patch_format* property of class [*PatchCodeParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/patchcodeparameters/). This property refers to the [*PatchFormat*](/barcode/python-net/api-reference/aspose.barcode.generation/patchformat/) enum that includes the following values: 
- *PATCH_ONLY* - the default mode that is used to generate basic *Patch Code* barcodes are generated 
- *A4* - this mode is intended to create portrait-oriented A4 pages with *Patch Code* barcodes on borders and a *QR Code* barcode inside the page (optionally)
- *A4_LANDSCAPE* - this mode is used to generate landscape-oriented A4 pages with *Patch Code* barcodes on borders and a *QR Code* barcode inside the page (optionally) 
- *US_LETTER* - this mode is used to create portrait-oriented US Letter pages with *Patch Code* barcodes on borders and a *QR Code* barcode inside the page (optionally)
- *US_LETTER_LANDSCAPE* - this mode is applied to generate landscape-oriented US pages with *Patch Code* barcodes on borders and a *QR Code* inside the page (optionally)

**Complementary QR Code Settings**  
As mentioned above, it is possible to place a complementary *QR Code* add-on inside a page (A4 or US Letter) with *Patch Code* barcodes. It can be done by passing some textual data to the *extra_barcode_text* property of class [*PatchCodeParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/patchcodeparameters/) and then initializing the *location* property of class [*CodeTextParameters*](/barcode/python-net/api-reference/aspose.barcode.generation/codetextparameters/) with the *NONE* value (the [*CodeLocation*](/barcode/python-net/api-reference/aspose.barcode.generation/codelocation/) enum).  
  
Following *Patch Code* barcodes have been created with and without complementary *QR Code* add-ons.
  
|Complementary QR Code Add-On|Is Disabled|Is Enabled|
| :-: | :-: | :-: |
| |<img src="patchcodea4withoutqr.png" width="40%" height="40%" alttext="Patch Code Barcode Without QR">|<img src="patchcodea4withqr.png" width="40%" height="40%" alttext="Patch Code Barcode With QR">|
  
