---
title: Mailmark 2D Barcodes
type: docs
description: "This article explains how to Generate and Read Royal Mail Mailmark 2D Barcodes using Aspose.BarCode for Java"
keywords: "Generate Mailmark Barcode, Royal Mail Mailmark Barcodes, Royal Mail Barcode, Aspose.BarCode, Generate Barcodes in Java"
weight: 20
url: /java/mailmark-2D-barcode/
---

## **Overview**
Royal Mail has developed a special postal barcode standard called *Mailmark* to store postal and shipping data using the the *DataMatrix* symbology format. *Mailmark 2D* supports three subtypes, namely, 7, 9, and 29, that provides various capacities to encode customer information. When required, customer data can be added to main barcode text using specific fields. The available customer data capacity varies depending on the used *Mailmark* subtype and the barcode text encoding. additional customer data fields may be used to store information about printing and scanning procedures, item identifiers, or data required to perform barcode scanning through mobile devices.  

To encode barcode data, the *Mailmark 2D* symbology applies the common C40 set of characters, including numerical digits, uppercase English letters, and space. All barcode data fields except customer information must have the format suitable for the specified encoding mode. In contrast, customer data does not need to support encoding compatibility. It should be noted that applying non-conventional encodings may require extra data capacity.  
  
To process *Mailmark 2D* barcode images, ***Aspose.BarCode for Java*** provides class [*Mailmark2DCodetext*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/Mailmark2DCodetext).
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Generation of Mailmark 2D Barcodes**
Developers can create *Mailmark 2D* barcodes in the following manner. First, it is necessary to generate an instance of class [*Mailmark2DCodetext*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/Mailmark2DCodetext) entering information to be encoded. Then, the method *generateBarCodeImage()* of class [*ComplexBarcodeGenerator*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/ComplexBarcodeGenerator) needs to be called to complete barcode generation. The [*Mailmark2DType*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/Mailmark2DType) enumeration is intended to determine the desired *Mailmark 2D* subtype ofor the generated barcode.  
  
Following *Mailmark 2D* barcode images have been generated using various *Mailmark 2D* subtypes.
  
|<p align="center">**Mailmark 2D**</p>|<p align="center">**Type 7**</p>|<p align="center">**Type 9**</p>|<p align="center">**Type 29**</p>|
| :-: | :-: | :-: | :-: |
| |<img src="mailmark2dtype7.png">|<img src="mailmark2dtype9.png">|<img src="mailmark2dtype29.png">|
  
The following code sample explains how to create *Mailmark 2D* barcodes of different subtypes.
  
{{< highlight csharp>}}
ComplexBarcodeGenerator generator = null;

//create Mailmark 2D barcode
Mailmark2DCodetext mailmark2D = new Mailmark2DCodetext();
mailmark2D.UPUCountryID = "JGB ";
mailmark2D.InformationTypeID = "0";
mailmark2D.VersionID = "1";
mailmark2D.Class = "1";
mailmark2D.SupplyChainID = 123;
mailmark2D.ItemID = 1234;
mailmark2D.DestinationPostCodeAndDPS = "QWE1";
mailmark2D.RTSFlag = "0";
mailmark2D.ReturnToSenderPostCode = "QWE2";

//encode Mailmark 2D Type 7 barcode
mailmark2D.DataMatrixType = Mailmark2DType.Type_7;
mailmark2D.CustomerContent = "CUSTOM";
generator = new ComplexBarcodeGenerator(mailmark2D);
generator.Parameters.Barcode.XDimension.Pixels = 4;
generator.Save($"{path}Mailmark2DType7.png");

//encode Mailmark 2D Type 9 barcode
mailmark2D.DataMatrixType = Mailmark2DType.Type_9;
mailmark2D.CustomerContent = "CUSTOM DATA";
generator = new ComplexBarcodeGenerator(mailmark2D);
generator.Parameters.Barcode.XDimension.Pixels = 4;
generator.Save($"{path}Mailmark2DType9.png");

//encode Mailmark 2D Type 29 barcode
mailmark2D.DataMatrixType = Mailmark2DType.Type_29;
mailmark2D.CustomerContent = "CUSTOM DATA";
generator = new ComplexBarcodeGenerator(mailmark2D);
generator.Parameters.Barcode.XDimension.Pixels = 4;
generator.Save($"{path}Mailmark2DType29.png");
{{< /highlight >}}
  
## **Mailmark 2D Barcode Recognition**
Using the ***Aspose.BarCode for Java*** functionality, developers can read *Mailmark 2D* barcodes of all types. First, it is necessary to generate an instance of class [*BarCodeReader*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) setting it to *DecodeType.DataMatrix*. Thereafter, barcode data can be parsed using the *tryDecodeMailmark2D(java.lang.String encodedCodetext)* method of class [*ComplexCodetextReader*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/ComplexCodetextReader) that generates an instance of [*Mailmark2DCodetext*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.complexbarcode/Mailmark2DCodetext) containing decoded information.  
  
The following code snippet shows how to read *Mailmark 2D* barcodes.

{{< highlight csharp>}}
Console.OutputEncoding = Encoding.Unicode;
//recognize Mailmark 2D barcode
BarCodeReader reader = new BarCodeReader($"{path}Mailmark2DType9.png", DecodeType.DataMatrix);
foreach (BarCodeResult result in reader.ReadBarCodes())
{
    Mailmark2DCodetext mailmarkResult = ComplexCodetextReader.TryDecodeMailmark2D(result.CodeText);
    if (null == mailmarkResult) continue;
    Console.WriteLine($"UPUCountryID:{mailmarkResult.UPUCountryID}");
    Console.WriteLine($"InformationTypeID:{mailmarkResult.InformationTypeID}");
    Console.WriteLine($"VersionID:{mailmarkResult.VersionID}");
    Console.WriteLine($"Class:{mailmarkResult.Class}");
    Console.WriteLine($"SupplyChainID:{mailmarkResult.SupplyChainID}");
    Console.WriteLine($"ItemID:{mailmarkResult.ItemID}");
    Console.WriteLine($"DestinationPostCodeAndDPS:{mailmarkResult.DestinationPostCodeAndDPS}");
    Console.WriteLine($"RTSFlag:{mailmarkResult.RTSFlag}");
    Console.WriteLine($"ReturnToSenderPostCode:{mailmarkResult.ReturnToSenderPostCode}");
    Console.WriteLine($"CustomerContent:{mailmarkResult.CustomerContent}");
}
{{< /highlight >}} 