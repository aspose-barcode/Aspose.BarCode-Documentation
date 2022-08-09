---
title: Barcode Recognition using Barcode Java API
linktitle: Barcode Reading API
description: "Description of Barcode Java API for barcode recognition"
type: docs
weight: 90
url: /java/read-barcodes-with-aspose-barcode-apis/

---

## **Scan Barcode from Image**
The following example demonstrates how to scan a barcode image using Aspose.BarCode.

|![todo:image_alt_text](http://i.imgur.com/S5k75Xf.jpg)|
| :- |
|**Sample barcode image**|
  

|![todo:image_alt_text](http://i.imgur.com/97XU28P.jpg)|
| :- |
|**Recognition result**|
  
{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-barcode_recognition-basic_features-Barcode_Recognition-Barcode_Recognition.java" >}}

{{< gist "aspose-barcode" "e49c13ebe68efe7c059e32871b13a3ab" "Examples-src-main-java-com-aspose-barcode-examples-barcode_recognition-basic_features-SupportedImageFormats-.java" >}}

## **Recognize Specific Barcode Type**
This article shows the basic settings of the BarCodeReader class.

### **Barcode Type**
The example below specifies the barcode type in the constructor of the BarCodeReader class and use the *Read()* method to recognize barcodes in an image.

When we already know the barcode type passed to the reader, this is the most efficient way to write the program. Recognition speeds up considerably when the barcode type is known.

|![todo:image_alt_text](http://i.imgur.com/h5sWyXL.jpg)|
| :- |
  
{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-barcode_recognition-basic_features-SpecificBarcodeSymbology-SpecificBarcodeSymbology.java" >}}

|![todo:image_alt_text](http://i.imgur.com/SBzZiCy.jpg)|
| :- |
|**Recognition result**|
  
For unknown barcode types, either call the *Read()* method with no arguments or programmatically loop through every symbology. This slows down recognition.

#### **BarCodeReadType**
The BarCodeReader class' getReadType() method returns the symbology type of the recognized barcode. Continuing the sample above, the first recognized barcode's SymbologyType is:

**Java**

{{< highlight csharp >}}

 BarCodeReadType symbologyType = reader.getReadType();

{{< /highlight >}}

For barcode symbologies with variations, it's original SymbologyType or superset SymbologyType is returned. For example, both Code39Standard and Code39Extended barcodes are recognized as Code39Extended barcodes.
#### **Code Text**
The *getCodeText()* method of class BarCodeReader returns a string representing the barcode's decoded data.

**Java**

{{< highlight csharp >}}

 String strCodeText = reader.getCodeText();

{{< /highlight >}}

## **Recognizing Multiple Symbologies in Single Image**
There might be situations when there is more than one barcode in an image. Aspose.BarCode can easily recognize all the barcodes of supported symbology types. This can be done by specifying the symbology type or setting Symbology.AllSupportedTypes.

The image below contains two barcodes of the Code39Standard and Pdf417 types.

**Two barcodes, one image**

|![todo:image_alt_text](http://i.imgur.com/5prpHFS.png)|
| :- |
  
As the BarCodeReader.read() method returns a Boolean value, it is possible to call it in a while loop to recognize all the barcodes in an image. For the above image, the read() method returns true for the first barcode, and then again for the second barcode. It returns false in the third iteration.

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-barcode_recognition-basic_features-RecognizingMultipleSymbologiesInSingleImage-RecognizingMultipleSymbologiesInSingleImage.java" >}}

The above code snippet assumes that we already know the symbology types of the barcodes in the image and specified the symbologies. If the symbologies are not known in advance, use BarCodeReadType.AllSupportedTypes to check for any symbology type.
