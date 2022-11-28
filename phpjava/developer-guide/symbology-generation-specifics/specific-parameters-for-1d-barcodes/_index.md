---
title: Setting Parameters of 1D Barcode Types
type: docs
description: "Set Specific Display Parameters for 1D Barcodes in Aspose.BarCode for PHP via Java"
keywords: "Generate Barcodes, Customize 1D Barcode Image, Adjust Bar Height in Aspose.BarCode for PHP, Work with Barcode Image in Aspose.BarCode for PHP, Generate Barcodes in Aspose.BarCode, Customized Linear Barcodes, Change Bar Height, Set Empty Bar Filling for 1D Barcodes, Barcode Wide-to-Narrow Ratio, Set Wide-to-Narrow Ratio in Aspose.BarCode"
weight: 20
url: /phpjava/1d-barcode-parameters/
---

## **Overview**
***Aspose.BarCode for PHP via Java*** enables customizing various parameters that are specific for 1D barcode generation. Particularly for 1D barcode standards, developers can adjust the following display properties: the height of bars, the mode of bar filling, the wide-to-narrow ratio, and the automatic correction of invalid barcode text.  
This article describes how to manage these properties using specified classes and properties of the library.  

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/phpjava/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Setting Bar Height**
Bar height of 1D single-row barcodes can be adjusted by setting [*AutoSizeMode*](https://reference.aspose.com/barcode/php/classAutoSizeMode) to *NONE*. In this case, regardless of the value specified through the *setXDimension* function, the bar height can be regulated using the *setBarHeight* function of class [*BarcodeParameters*](https://reference.aspose.com/barcode/php/classBarcodeParameters). This function does not apply to multiple-row barcodes and 2D barcodes.
  
|Bar Height|Is Set to 40 Pixels|Is Set to 80 Pixels|
| :-: | :-: | :-: |
| |<img src="barheight40code128.png">|<img src="barheight80code128.png">|
  
```php
$generator = new BarcodeGenerator(EncodeTypes::DATA_MATRIX);
$generator->setAutoSizeMode(AutoSizeMode.NEAREST);
$generator->getBarCodeWidth()->setMillimeters(50);
$generator->getBarCodeHeight()->setInches(1.3f);
$generator->save("test.png");
```

``` php
$generator = new BarcodeGenerator(EncodeTypes::DATA_MATRIX);
$generator->getParameters()->getBarcode()->setAutoSizeMode(AutoSizeMode::INTERPOLATION);
$generator->getParameters()->getBarcode()->getBarCodeWidth()->setMillimeters(50);
$generator->getParameters()->getBarcode()->getBarCodeHeight()->setInches(1.3);
$generator->save("test.png", "PNG);
``` 

## **Bar Filling Modes**
For 1D barcodes, ***Aspose.BarCode for PHP via PHP via Java*** provides a specific mode to generate barcodes with empty bars instead of filled ones. Such a modification can be done using the *setFilledBars* function of class [*BarcodeParameters*](https://reference.aspose.com/barcode/php/classBarcodeParameters). This property is set to *True* by default and is valid only for 1D barcodes. 
  
|Bar Filling|Filled|Empty|
| :-: | :-: | :-: |
| |<img src="barsfilledcode128.png">|<img src="barsemptycode128.png">|
  

## **Setting Wide-to-Narrow Ratio**
Two-width 1D barcodes are based on the binary code principle, meaning that information is encoded using bars and spaces with two options of width: wide and narrow. Two-width barcode symbologies include the following: *Codabar*, *Code 11*, *Code 32*, *Code 39*, *DataLogic 2-of-5*, *IATA 2-of-5*, *Interleaved 2-of-5*, *ITF 6*, *ITF 14*, *Matrix 2-of-5*, *MSI*, *OPC*, *PZN*, *Standard 2-of-5*, and *VIN*.  
  
In ***Aspose.BarCode for PHP via Java***, the **wide-to-narrow ratio** defines the relation between the width of wide and narrow elements. It can be set using the *setWideNarrowRatio* function of class [*BarcodeParameters*](https://reference.aspose.com/barcode/php/classBarcodeParameters). The larger if the value of the wide-to-narrow ratio, the larger is the width of the generated barcode. However, the readability also improves with an increase in this parameter. By default, *WideNarrowRatio* is set to 3.  
  
|Wide-to-Narrow Ratio|Is Set to 2|Is Set to 5|
| :-: | :-: | :-: |
| |<img src="widenarrow2code39.png">|<img src="widenarrow5code39.png">|
  
  
## **Handling Exception on Incorrect Barcode Text**
In case when a barcode has not been created correctly due to invalid barcode text, by default, the barcode library can generate additional dummy data to bring the barcode into line with the standard or delete conflicting characters. Thereafter barcode generation is considered successful.  
  
Developers can change this behaviour by using the *setThrowExceptionWhenCodeTextIncorrect* function of [*BarcodeParameters*](https://reference.aspose.com/barcode/php/classBarcodeParameters). When this property is enabled, an exception is thrown if the barcode text has been found incorrect or incomplete.
  
|Barcode Text Correctness|Correct with Valid Barcode Text|Adjusted with Invalid Barcode Text|
| :-: | :-: | :-: |
| |<img src="itf6correct.png">|<img src="itf6filled.png">|
  
