---
title: Generate DataBar Barcodes in Java
linktitle: DataBar
type: docs
weight: 50
url: /java/databar-barcodes/
aliases:
- /java/generate-segments-per-row-barcode/
---
{{% alert color="primary" %}}[Generate DataBar Barcodes Online](https://products.aspose.app/barcode/generate/databar): You can check the quality of ***Aspose.BarCode*** generation for DataBar barcodes and view results online.{{% /alert %}}

## **Overview**
The *DataBar* standard was developed in the 2000s in compliance with the GS1 standard. It was intended to address problems with barcode types introduced in the 70s. However, it was also important to preserve one of the key features of 1D barcodes, i.e, the laser scanning ability. The following subtypes are represented within the *DataBar* type: 
- *DataBar Omnidirectional* / *DataBar Stacked Omnidirectional*
- *DataBar Expanded* / *DataBar Expanded Stacked*
- *DataBar Truncated* / *DataBar Stacked*
- *DataBar Limited*
  
Except for *DataBar Limited*, all aforementioned subtypes have two-row and multiple-row (at most 10 rows) versions. This property enables fitting the barcode layout to the limited horizontal space. *DataBar* standards have been introduced to work with GS1 identification codes (Application Identifiers) used to mark trade items. All *DataBar* subtypes excluding *DataBar Expanded* / *DataBar Expanded Stacked* are applicable only to the trade identifiers determined using Global Trade Item Number (GTIN) in *GTIN12* or *GTIN13* digital formats with the 14-digit data structure. In contrast, *DataBar Expanded* barcodes are compatible with any type of application identifiers and may contain additional data in any format as it allows encoding uppercase and lowercase English alphabet symbols, numerical digits, and 21 punctuation signs.  

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Barcode Height Settings**
*DataBar* standards can be classified into two types: continuous and stacked. ***Aspose.BarCode for Java*** provides a special mode to customize the height of barcodes for each of these types, as explained further in the article.

### **Continuous Barcode Types**
*DataBar Omnidirectional*, *DataBar Truncated*, *DataBar Limited*, and *DataBar Expanded* correspond to continuous barcode types. For such symbologies, barcode height can be adjusted using the *setBarHeight* method of class [*BarcodeParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeParameters).  
  
The following *DataBar Omnidirectional* barcode images have been created setting various barcode heights.
   
|Barcode Height|Is Set to 30 Pixels|Is Set to 60 Pixels|
| :-: | :-: | :-: |
| |<img src="databarbarheight30pixels.png">|<img src="databarbarheight60pixels.png">|
  
<!--The following code snippet explains how to modify the barcode height while generating continuous barcodes.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarOmniDirectional, "(01)12345678901231");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//set barheight 30 pixels
gen.Parameters.Barcode.BarHeight.Pixels = 30;
gen.Save($"{path}DatabarBarHeight30Pixels.png", BarCodeImageFormat.Png);
//set barheight 60 pixels
gen.Parameters.Barcode.BarHeight.Pixels = 60;
gen.Save($"{path}DatabarBarHeight60Pixels.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
  
### **Stacked Barcode Types**
*DataBar Stacked Omnidirectional*, *DataBar Stacked*, and *DataBar Expanded Stacked* can be classified as stacked barcode types. For such symbologies, the height of barcodes can be customized by calling the *setAspectRatio* method of class [*DataBarParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/DataBarParameters). *AspectRatio* is specified as a relative coefficient to the value of *XDimension*.  
  
The following *DataBar Stacked Omnidirectional* barcodes have been generated setting different values of the aspect ratio.
  
|Aspect Ratio|Is Set to 15|Is Set to 30|
| :-: | :-: | :-: |
| |<img src="databaraspectratio15.png">|<img src="databaraspectratio30.png">|
  
<!--The following code snippet shows how to manage barcode height in stacked barcodes adjusting the value of the aspect ratio.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarStackedOmniDirectional, "(01)12345678901231");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//set DataBar AspectRatio 15
gen.Parameters.Barcode.DataBar.AspectRatio = 15;
gen.Save($"{path}DatabarAspectRatio15.png", BarCodeImageFormat.Png);
//set DataBar AspectRatio 30
gen.Parameters.Barcode.DataBar.AspectRatio = 30;
gen.Save($"{path}DatabarAspectRatio30.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
  
## **DataBar Expanded Stacked Layout Settings**
The *DataBar Expanded Stacked* subtype supports a flexible layout that may be adjusted by changing barcode row and column numbers. ***Aspose.BarCode*** allows adding up to 22 segments to compose at most 10 strings. The layout of *DataBar Expanded Stacked* barcodes can be customized through *setRows* and *setColumns* methods of class [*DataBarParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/DataBarParameters). It should be noted that first, the number of segments in a row has to be determined using the *setColumns* method.  
  
Following *DataBar Expanded Stacked* barcodes have varying barcode layouts.
  
|Layout Settings|4 Columns|3 Rows|6 Columns and 10 Rows|
| :-: | :-: | :-: | :-: |
| |<img src="databarcols4.png">|<img src="databarrows3.png">|<img src="databarcols6rows10.png">|
  
<!--The following code sample explains how to manage layout settings in *DataBar Expanded Stacked* barcodes.
   
{{< highlight csharp>}}
//set 4 columns
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarExpandedStacked, "Databar Expanded Stacked long");
gen.Parameters.Barcode.DataBar.Columns = 4;
gen.Save($"{path}DatabarCols4.png", BarCodeImageFormat.Png);
//set 3 rows
gen = new BarcodeGenerator(EncodeTypes.DatabarExpandedStacked, "Databar Expanded Stacked long");
gen.Parameters.Barcode.DataBar.Rows = 3;
gen.Save($"{path}DatabarRows3.png", BarCodeImageFormat.Png);
//set 6 columns 10 rows
gen = new BarcodeGenerator(EncodeTypes.DatabarExpandedStacked, "Databar Expanded Stacked long");
gen.Parameters.Barcode.DataBar.Columns = 6;
gen.Parameters.Barcode.DataBar.Rows = 10;
gen.Save($"{path}DatabarCols6Rows10.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
  
## **Compatibility with GS1 Components**
Considering that *DataBar Expanded* / *DataBar Expanded Stacked* subtypes enable data encoding in any format, it may be important to ensure compatibility of the encoded information with GS1 standards. This can be implemented through the *setAllowOnlyGS1Encoding* method of class [*DataBarParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/DataBarParameters). This method requests checking for compatibility of the encoded data with GS Application Identifiers. An exception is thrown if an inconsistency is identified. This method can also serve to verify the correctness of GTIN values in other *DataBar* subtypes.     
  
Following *DataBar Expanded* barcodes have been generated using the GS1-compatible and non-compatible data formats.
  
|GS1 Compatibility|GS1 Compatible Encoding|Alternate Encoding|
| :-: | :-: | :-: |
| |<img src="databargs1rightencoding.png">|<img src="databargs1variableencoding.png">|
  
<!--The following code sample demonstrates how to verify compatibility with GS1 standards for *DataBar Expanded* barcodes.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarExpanded, "");
//right codetext with GS1Encoding check
gen.CodeText = "(01)12345678901231";
gen.Parameters.Barcode.DataBar.IsAllowOnlyGS1Encoding = true;
gen.Save($"{path}DatabarGS1RightEncoding.png", BarCodeImageFormat.Png);
//variable codetext without GS1Encoding check
gen.CodeText = "ASPOSE";
gen.Parameters.Barcode.DataBar.IsAllowOnlyGS1Encoding = false;
gen.Save($"{path}DatabarGS1VariableEncoding.png", BarCodeImageFormat.Png);
//variable codetext with GS1Encoding check
try
{
    gen.CodeText = "ASPOSE";
    gen.Parameters.Barcode.DataBar.IsAllowOnlyGS1Encoding = true;
    gen.GenerateBarCodeImage();
}
catch (Exception e)
{
    Console.WriteLine(e.Message);
}
{{< /highlight >}}-->
  
## **Enable 2D Component**
*DataBar* standards allow adding a 2D component linkage flag to enable creating a related 2D barcode that can be printed together with the corresponding *DataBar* barcode. Such a flag is often used in GS1-compatible composite barcode types. ***Aspose.BarCode for Java*** provides the *set2DCompositeComponent* method of class [*DataBarParameters*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/DataBarParameters) that allows setting this flag manually for specific industrial standards without changing the data encoded in the main barcode.  
  
The following *DataBar Expanded* barcodes have different settings for the 2D component flag.
  
|2D Component Flag|Is Disabled|Is Enabled|
| :-: | :-: | :-: |
| |<img src="databar2dcomponentdisabled.png">|<img src="databar2dcomponentenabled.png">|
  
<!--The following code snippet shows how to manage the linkage to a 2D component in *DataBar Expanded* barcodes.
    
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarExpanded, "(01)12345678901231");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//disable 2D component flag
gen.Parameters.Barcode.DataBar.Is2DCompositeComponent = false;
gen.Save($"{path}Databar2DComponentDisabled.png", BarCodeImageFormat.Png);
//enable 2D component flag
gen.Parameters.Barcode.DataBar.Is2DCompositeComponent = true;
gen.Save($"{path}Databar2DComponentEnabled.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->