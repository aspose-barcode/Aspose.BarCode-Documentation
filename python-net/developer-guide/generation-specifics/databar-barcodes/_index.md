---
title: Generate DataBar Barcodes
linktitle: DataBar
type: docs
weight: 100
url: /python-net/generate-databar/

---
{{% alert color="primary" %}}[Generate DataBar Barcodes Online](https://products.aspose.app/barcode/generate/databar): You can check the quality of ***Aspose.BarCode*** generation for DataBar barcodes and view results online.{{% /alert %}}

## **Overview**
The *DataBar* standard was developed in the 2000s in compliance with the GS1 standard. It was intended to address problems with barcode types introduced in the 70s. However, it was also important to preserve one of the key features of 1D barcodes, i.e, the laser scanning ability. The following subtypes are represented within the *DataBar* type: 
- *DataBar Omnidirectional* / *DataBar Stacked Omnidirectional*
- *DataBar Expanded* / *DataBar Expanded Stacked*
- *DataBar Truncated* / *DataBar Stacked*
- *DataBar Limited*
  
Except for *DataBar Limited*, all aforementioned subtypes have two-row and multiple-row (at most 10 rows) versions. This property enables fitting the barcode layout to the limited horizontal space. *DataBar* standards have been introduced to work with GS1 identification codes (Application Identifiers) used to mark trade items. All *DataBar* subtypes excluding *DataBar Expanded* / *DataBar Expanded Stacked* are applicable only to the trade identifiers determined using Global Trade Item Number (GTIN) in *GTIN12* or *GTIN13* digital formats with the 14-digit data structure. In contrast, *DataBar Expanded* barcodes are compatible with any type of application identifiers and may contain additional data in any format as it allows encoding uppercase and lowercase English alphabet symbols, numerical digits, and 21 punctuation signs.  

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Barcode Height Settings**
*DataBar* standards can be classified into two types: continuous and stacked. ***Aspose.BarCode for Python via .NET*** provides a special mode to customize the height of barcodes for each of these types, as explained further in the article.

### **Continuous Barcode Types**
*DataBar Omnidirectional*, *DataBar Truncated*, *DataBar Limited*, and *DataBar Expanded* correspond to continuous barcode types. For such symbologies, barcode height can be adjusted using the *bar_height* property of class [*BarcodeParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/barcodeparameters/).  
  
The following *DataBar Omnidirectional* barcode images have been created setting various barcode heights.
   
|Barcode Height|Is Set to 30 Pixels|Is Set to 60 Pixels|
| :-: | :-: | :-: |
| |<img src="databarbarheight30pixels.png">|<img src="databarbarheight60pixels.png">|
    
### **Stacked Barcode Types**
*DataBar Stacked Omnidirectional*, *DataBar Stacked*, and *DataBar Expanded Stacked* can be classified as stacked barcode types. For such symbologies, the height of barcodes can be customized using the *aspect_ratio* property of class [*DataBarParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/databarparameters/). *AspectRatio* is specified as a relative coefficient to the value of *XDimension*.  
  
The following *DataBar Stacked Omnidirectional* barcodes have been generated setting different values of the aspect ratio.
  
|Aspect Ratio|Is Set to 15|Is Set to 30|
| :-: | :-: | :-: |
| |<img src="databaraspectratio15.png">|<img src="databaraspectratio30.png">|
  
 
## **DataBar Expanded Stacked Layout Settings**
The *DataBar Expanded Stacked* subtype supports a flexible layout that may be adjusted by changing barcode row and column numbers. ***Aspose.BarCode*** allows adding up to 22 segments to compose at most 10 strings. The layout of *DataBar Expanded Stacked* barcodes can be customized using *rows* and *columns* properties of class [*DataBarParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/databarparameters/). It should be noted that first, the number of segments in a row has to be determined using the *columns* property.  
  
Following *DataBar Expanded Stacked* barcodes have varying barcode layouts.
  
|Layout Settings|4 Columns|3 Rows|6 Columns and 10 Rows|
| :-: | :-: | :-: | :-: |
| |<img src="databarcols4.png">|<img src="databarrows3.png">|<img src="databarcols6rows10.png">|
    
## **Compatibility with GS1 Components**
Considering that *DataBar Expanded* / *DataBar Expanded Stacked* subtypes enable data encoding in any format, it may be important to ensure compatibility of the encoded information with GS1 standards. This can be implemented through the *is_allow_only_gs1_encoding* property of class [*DataBarParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/databarparameters/). This property requests checking for compatibility of the encoded data with GS Application Identifiers. An exception is thrown if an inconsistency is identified. It can also serve to verify the correctness of GTIN values in other *DataBar* subtypes.     
  
Following *DataBar Expanded* barcodes have been generated using the GS1-compatible and non-compatible data formats.
  
|GS1 Compatibility|GS1 Compatible Encoding|Alternate Encoding|
| :-: | :-: | :-: |
| |<img src="databargs1rightencoding.png">|<img src="databargs1variableencoding.png">|
    
## **Enabling 2D Component**
*DataBar* standards allow adding a 2D component linkage flag to enable creating a related 2D barcode that can be printed together with the corresponding *DataBar* barcode. Such a flag is often used in GS1-compatible composite barcode types. ***Aspose.BarCode for Python via .NET*** provides the *is_2d_composite_component* property of class [*DataBarParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/databarparameters/) that allows setting this flag manually for specific industrial standards without changing the data encoded in the main barcode.  
  
The following *DataBar Expanded* barcodes have different settings for the 2D component flag.
  
|2D Component Flag|Is Disabled|Is Enabled|
| :-: | :-: | :-: |
| |<img src="databar2dcomponentdisabled.png">|<img src="databar2dcomponentenabled.png">|
  
