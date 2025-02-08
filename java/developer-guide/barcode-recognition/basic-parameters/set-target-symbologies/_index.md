---
title: Set Target Barcode Types for Recognition
linktitle: Set Target Barcode Types
type: docs
description: "This Article Describes How to Set Target Barcode Types for Recognition"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Aspose.BarCode, Read Barcode Java"
weight: 20
feedback: BARCODECOM
url: /java/set-target-barcode-types/
---

## **Overview**
***Aspose.BarCode for Java*** supports barcode recognition for 60+ various barcode types. To improve the efficiency of the recognition process and optimize its timing, it is recommended to set target symbologies in advance. Otheriwise, the *DecodeType.ALL_SUPPORTED_TYPES* setting of the [*DecodeType*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/DecodeType) enum will be used by default meaning that the library will look over all supported barcode types to check for their presence in the source image. Using this setting will increase the time needed to complete barcode recognition. 

## **List Target Barcode Types in DecodeType**
Target barcode types can be specified by grouping them in a list and passing it to the *BarCodeReader()* constructor or the *setBarCodeReadType* method.  
  
<!--The following code snippet shows how to determine target barcode types (i.e. *Code 128*,*Code 39*, and *RM4SCC*) using [*DecodeType*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/DecodeType).
  
{{< highlight java>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png"))
{
    reader.SetBarCodeReadType(DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC);
    Console.WriteLine("ReadDecodeTypeList:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

## Use ***MultyDecodeType* Mode**
The other way to specify target barcode types is to determine them using a constructor of class [*MultyDecodeType*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/MultyDecodeType) and then pass it to class [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) or the *setBarCodeReadType* method.  
  
<!--The following code sample demonstrates how to set target symbologies (i.e. *Code 39*, *Code 128*, and *RM4SCC*) using [*MultyDecodeType*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/MultyDecodeType).
  
{{< highlight java>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png"))
{
    reader.SetBarCodeReadType(new MultyDecodeType(DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC));
    Console.WriteLine("ReadMultyDecodeType:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

## **Use Predefined Symbology Sets**
Class [*DecodeType*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/DecodeType) provides the following symbology sets for barcode reading:
-	*ALL_SUPPORTED_TYPES* - all available barcode types
-	*TYPES_1D* - all supported 1D types
-	*TYPES_2D* - all supported 2D types
-	*POSTAL_TYPES* - all available postal types
-	*MOST_COMMON_TYPES* - a set of most widespread barcode types defined according to Aspose recommendations

The required set can be specified in the *BarCodeReader* constructor or passed to the *setBarCodeReadType* method.
  
<!--The following code snippet shows how to work with the *TYPES_2D* set.
  
{{< highlight java>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Types2D))
{
    Console.WriteLine("ReadTypes2D:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->
