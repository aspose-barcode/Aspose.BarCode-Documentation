---
title: Set Target Barcode Types for Recognition
linktitle: Set Target Barcode Types
type: docs
feedback: BARCODECOM
description: "This Article Describes How to Set Target Barcode Types for Recognition"
keywords: "Read barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Barcode in WPF Project, Aspose.BarCode, Read Barcode C#"
ai_search_scope: "barcode_dotnet_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 20
url: /net/set-target-barcode-types/
---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
***Aspose.BarCode for .NET*** supports more than 60 barcode types for recognition. To minimize the time required to complete recognition and avoid attempts to recognize outdated barcodes that are still used as a legacy of some industrial systems, it is recommended to select target barcode symbologies that will be considered for recognition. However, in the case when there is no information about precise symbologies that can be presented in a source image, it is possible to use the default setting *DecodeType.AllSupportedTypes* for the [*DecodeType*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/decodetype) property so that the source image will be checked for the presence of all supported barcode types. This setting results in the increased time required to complete barcode recognition. 

## **List Barcode Types Defined in DecodeType**
Target symbologies for barcode recognition can be specified as a list and passed to the [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) constructor or the [*SetBarCodeReadType*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/setbarcodereadtype/methods/1) method.  
  
The following code snippet demonstrates how to set target symbologies (*Code 39*, *Code 128*, and *RM4SCC*) using [*DecodeType*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/decodetype).
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png"))
{
    reader.SetBarCodeReadType(DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC);
    Console.WriteLine("ReadDecodeTypeList:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

## ***MultyDecodeType* Mode**
The other way to set target symbologies for recognition is to list the required barcode types in a constructor of class [*MultyDecodeType*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/multydecodetype) and then to pass an instance of this class to the [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) constructor or the [*SetBarCodeReadType*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/setbarcodereadtype/methods/1) method.  
  
The following code sample explains how to define target symbologies for barcode reading (in this case, *Code 39*, *Code 128*, and *RM4SCC*) through [*MultyDecodeType*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/multydecodetype).
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png"))
{
    reader.SetBarCodeReadType(new MultyDecodeType(DecodeType.Code39Extended, DecodeType.Code128, DecodeType.RM4SCC));
    Console.WriteLine("ReadMultyDecodeType:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

## **Predefined Sets of Types**
Class [*DecodeTypes*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/decodetype) contains various predefined sets of symbologies for recognition, including the following ones:
-	*AllSupportedTypes* - all supported barcode types
-	*Types1D* - all supported 1D symbologies
-	*Types2D* - all supported 2D symbologies
-	*PostalTypes* - all supported postal symbologies that are mainly used by postal services
-	*MostCommonTypes* - a set of most widely used barcode standards defined according to the Aspose recommendations

 The required symbology set can be defined in the [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) constructor or the [*SetBarCodeReadType*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition.barcodereader/setbarcodereadtype/methods/1) method.
  
The following code snippet illustrates how to specify target barcode types using the predefined set called *Types2D*.
  
{{< highlight csharp>}}
using (BarCodeReader reader = new BarCodeReader($"{path}multiple_codes.png", DecodeType.Types2D))
{
    Console.WriteLine("ReadTypes2D:");
    foreach (BarCodeResult result in reader.ReadBarCodes())
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

