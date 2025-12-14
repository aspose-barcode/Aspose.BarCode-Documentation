---
title: Generate and Read HIBC LIC Barcodes in C#
linktitle: HIBC LIC
type: docs
feedback: BARCODECOM
ai_search_scope: "barcode_dotnet_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 50
url: /net/hibc-lic-barcodes/
aliases:
- /net/hibc-lic/
---

## **Overview**
HIBCC Licensed Identification Code (LIC) is a standardized identifier that is used to track products, packages, and containers. This special barcode standard is mainly used to mark goods produced for the healthcare sphere. It has been introduced by Healthcare Industry Bar Code Council (HIBCC), a non-profit organization aimed to develop and promote the use of standardized barcode types in the healthcare industry. The data elements encoded in the HIBC LIC may include the product identifier, the lot number, the expiration date, and other information about the product. Each field is encoded in a specific format, and the HIBCC provides guidelines on how to encode data in the HIBC LIC.  
***Aspose.BarCode for .NET*** provides tools to generate and read barcodes using the HIBC LIC standard. Main barcode data can be encoded using of the following types: Code 39, Code 128, Aztec Code, Data Matrix, or QR Code. A barcode type has to be set in the [*BarcodeType*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/barcodetype/) property. To select the required HIBC LIC format for generated barcode, developers need to use class [*ComplexBarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexbarcodegenerator/) together with special classes for HIBC LIC, including [*HIBCLICComplexCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/hibcliccomplexcodetext/), [*HIBCLICCombinedCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/hibcliccombinedcodetext/), [*HIBCLICPrimaryDataCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/hibcliccombinedcodetext/primarydata/), and [*HIBCLICSecondaryAndAdditionalDataCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/hibcliccombinedcodetext/secondaryandadditionaldata/). 

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}


## **Generate HIBC LIC Barcodes**
As specified by the HIBCC (Health Industry Business Communications Council), HIBC barcodes can store both primary and secondary information. Below, it is explained how to create HIBC LIC barcodes encoding primary data, secondary data, or both using the barcode library.

### **Primary Data**
All medical products must be appropriately marked with symbols, which store information about the identification code of the labeler, product number or its catalog identifier, and the unit measure. These data elements are used to identify and track products, packages, and containers throughout the supply chain. Class [*HIBCLICPrimaryDataCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/hibcliccombinedcodetext/primarydata/) needs to be used for HIBC LIC barcode generation to encode the primary data in the required format.  
The code sample below demonstrates how to generate HIBC LIC barcodes and encode the primary data. 

<p align="center"><img src="hibclicprimary.png"></p>

``` csharp
//create a HIBC LIC barcode
HIBCLICPrimaryDataCodetext complexCodetext = new HIBCLICPrimaryDataCodetext();
complexCodetext.BarcodeType = EncodeTypes.HIBCQRLIC;
//specify primary data
complexCodetext.Data = new PrimaryData();
complexCodetext.Data.ProductOrCatalogNumber = "12345";
complexCodetext.Data.LabelerIdentificationCode = "A999";
complexCodetext.Data.UnitOfMeasureID = 1;

//encode HIBC LIC data
using (ComplexBarcodeGenerator gen = new ComplexBarcodeGenerator(complexCodetext))
{
    gen.Parameters.Barcode.XDimension.Pixels = 10;
    gen.Save($"{path}HIBCLICPrimary.png");
}
```

### **Secondary Data**
Additional data fields can also be encoded in the HIBC LIC if they are needed for a specific application, namely, expiration date, product quantity, lot number, serial number, and date of manufacture. This auxiliary information can be encoded in HIBC LIC barcodes as secondary data, as explained in the code sample below. Class [*HIBCLICSecondaryAndAdditionalDataCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/hibcliccombinedcodetext/secondaryandadditionaldata/) can be used to encode secondary data in the required format.

<p align="center"><img src="hibclicsecondary.png"></p>

``` csharp
//create HIBC LIC Code
HIBCLICSecondaryAndAdditionalDataCodetext complexCodetext = new HIBCLICSecondaryAndAdditionalDataCodetext();
complexCodetext.BarcodeType = EncodeTypes.HIBCQRLIC;
//create secondary data
complexCodetext.Data = new SecondaryAndAdditionalData();
complexCodetext.Data.ExpiryDate = DateTime.Now;
complexCodetext.Data.ExpiryDateFormat = HIBCLICDateFormat.MMDDYY;
complexCodetext.Data.Quantity = 30;
complexCodetext.Data.LotNumber = "LOT123";
complexCodetext.Data.SerialNumber = "SERIAL123";
complexCodetext.Data.DateOfManufacture = DateTime.Now;
complexCodetext.LinkCharacter = 'S';

//encode HIBC LIC Code
using (ComplexBarcodeGenerator gen = new ComplexBarcodeGenerator(complexCodetext))
{
    gen.Parameters.Barcode.XDimension.Pixels = 10;
    gen.Save($"{path}HIBCLICSecondary.png");
}
```

### **Combined Data**
The barcode library provides an option to encode both primary and secondary data in a single HIBC LIC barcode. This can be done by using class [*HIBCLICCombinedCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/hibcliccombinedcodetext/), as demonstrated in the code sample below. 

<p align="center"><img src="hibcliccombined.png"></p>

``` csharp
//create HIBC LIC Combined Code
HIBCLICCombinedCodetext complexCodetext = new HIBCLICCombinedCodetext();
complexCodetext.BarcodeType = EncodeTypes.HIBCQRLIC;
//create primary data
complexCodetext.PrimaryData = new PrimaryData();
complexCodetext.PrimaryData.ProductOrCatalogNumber = "12345";
complexCodetext.PrimaryData.LabelerIdentificationCode = "A999";
complexCodetext.PrimaryData.UnitOfMeasureID = 1;
//create secondary data
complexCodetext.SecondaryAndAdditionalData = new SecondaryAndAdditionalData();
complexCodetext.SecondaryAndAdditionalData.ExpiryDate = DateTime.Now;
complexCodetext.SecondaryAndAdditionalData.ExpiryDateFormat = HIBCLICDateFormat.MMDDYY;
complexCodetext.SecondaryAndAdditionalData.Quantity = 30;
complexCodetext.SecondaryAndAdditionalData.LotNumber = "LOT123";
complexCodetext.SecondaryAndAdditionalData.SerialNumber = "SERIAL123";
complexCodetext.SecondaryAndAdditionalData.DateOfManufacture = DateTime.Now;

//encode HIBC LIC Combined Code
using (ComplexBarcodeGenerator gen = new ComplexBarcodeGenerator(complexCodetext))
{
    gen.Parameters.Barcode.XDimension.Pixels = 10;
    gen.Save($"{path}HIBCLICCombined.png");
}
```



## Read and Decode HIBC LIC Barcodes
To decode HIBC LIC barcodes, it is first necessary to create an instance of class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader/) and set the appropriate value of the [*DecodeType*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/decodetype/) property. Then, the obtained barcode type can be processed by calling the [*TryDecodeHIBCLIC*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexcodetextreader/trydecodehibclic/) of class [*ComplexCodetextReader*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/complexcodetextreader/). This method returns an object of class [*HIBCLICComplexCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/hibcliccomplexcodetext/). Such objects can be further transformed into objects of classes [*HIBCLICPrimaryDataCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/hibclicprimarydatacodetext/), [*HIBCLICSecondaryAndAdditionalDataCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/hibclicsecondaryandadditionaldatacodetext/), or [*HIBCLICCombinedCodetext*](https://reference.aspose.com/barcode/net/aspose.barcode.complexbarcode/hibcliccombinedcodetext/) depending on the format of the encoded data. The following code sample shows how to read HIBC LIC barcodes.

``` csharp
//recognize a HIBC LIC Combined barcode
using (BarCodeReader reader = new BarCodeReader($"{path}HIBCLICCombined.png", DecodeType.HIBCQRLIC))
{
    foreach (BarCodeResult result in reader.ReadBarCodes())
    {
        HIBCLICComplexCodetext codetext = ComplexCodetextReader.TryDecodeHIBCLIC(result.CodeText);
        HIBCLICCombinedCodetext combinedCodetext = codetext as HIBCLICCombinedCodetext;
        if (combinedCodetext == null)
            continue;

        Console.WriteLine($"Product or catalog number: {combinedCodetext.PrimaryData.ProductOrCatalogNumber}");
        Console.WriteLine($"Labeler identification code: {combinedCodetext.PrimaryData.LabelerIdentificationCode}");
        Console.WriteLine($"Unit of measure ID: {combinedCodetext.PrimaryData.UnitOfMeasureID}");
        Console.WriteLine($"Expiry date: {combinedCodetext.SecondaryAndAdditionalData.ExpiryDate}");
        Console.WriteLine($"Quantity: {combinedCodetext.SecondaryAndAdditionalData.Quantity}");
        Console.WriteLine($"Lot number: {combinedCodetext.SecondaryAndAdditionalData.LotNumber}");
        Console.WriteLine($"Serial number: {combinedCodetext.SecondaryAndAdditionalData.SerialNumber}");
        Console.WriteLine($"Date of manufacture: {combinedCodetext.SecondaryAndAdditionalData.DateOfManufacture}");
    }
}
```