---
title: Set Barcode Checksum Verification
linktitle: Set Checksum Verification
type: docs
description: "This article describes how to set checksum verification in Aspose.BarCode for .NET"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcode C#"
feedback: BARCODECOM
ai_search_scope: "barcode_dotnet_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 40
url: /net/set-checksum-verification/
---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
In many 1D and postal symbologies, data integrity verification and decoding are based on checksum control mechanisms. Class [*BarcodeSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesettings
) provides the [*ChecksumValidation*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesettings/properties/checksumvalidation) property that is used to manage checksum settings for data validation and decoding. In general, barcode standards can be divided into two groups: those with obligatory checksum and those with optional one. Depending on this, the [*ChecksumValidation*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesettings/properties/checksumvalidation) field can take different values; hence, the barcode recognition process will change according to particular checksum settings.  

## **Checksum Validation for Barcodes with Obligatory Checksum**
Symbologies with obligatory checksum always require performing checksum control when the [*ChecksumValidation*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesettings/properties/checksumvalidation) property is set to *ChecksumValidation.Default* or *ChecksumValidation.On*. Otherwise, this parameter can take the value *ChecksumValidation.Off* that disables checksum controls for barcode type with obligatory checksum and thus allows reading data from incorrectly generated barcodes. However, in this case, the probability of inaccurate recognition increases considerably.  
  
The following code snippet explains how to manage checksum validation settings for the symbology with obligatory checksum (in this case, a sample *Code 11* barcode image provided below has been considered). 
 
{{< highlight csharp>}}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code11, "123456"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Save($"{path}Code11.png", BarCodeImageFormat.Png);
}

//read barcode image with ChecksumValidation.Default being set
Console.WriteLine("ReadChecksumCode11:");
Console.WriteLine("ChecksumValidation: Default");
using (BarCodeReader read = new BarCodeReader($"{path}Code11.png", DecodeType.Code11))
{
    read.BarcodeSettings.ChecksumValidation = ChecksumValidation.Default;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine($"1D Value:{result.Extended.OneD.Value}");
        Console.WriteLine($"1D CheckSum:{result.Extended.OneD.CheckSum}");
    }
}

//read barcode image with ChecksumValidation.Off being set
Console.WriteLine("ChecksumValidation: Off");
using (BarCodeReader read = new BarCodeReader($"{path}Code11.png", DecodeType.Code11))
{
    read.BarcodeSettings.ChecksumValidation = ChecksumValidation.Off;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine($"1D Value:{result.Extended.OneD.Value}");
        Console.WriteLine($"1D CheckSum:{result.Extended.OneD.CheckSum}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="code11.png"></p> 

## **Checksum Validation for Barcodes with Optional Checksum**
For symbologies with optional checksum control, [*ChecksumValidation*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodesettings/properties/checksumvalidation) can be set in such a way to enable checksum checking, namely, it needs to take the value *ChecksumValidation.On*. Otherwise, when the values *ChecksumValidation.Default* and *ChecksumValidation.Off* are used, checksum validation is omitted.  
  
The following code sample illustrates the options of reading barcodes with optional checksum (a *Code 39* barcode image shown below has been used). 
  
{{< highlight csharp>}}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code39Extended, "123456"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Parameters.Barcode.IsChecksumEnabled = EnableChecksum.Yes;
    gen.Save($"{path}Code39.png", BarCodeImageFormat.Png);
}

//read barcode image with ChecksumValidation.Default being set
Console.WriteLine("ReadChecksumCode39:");
Console.WriteLine("ChecksumValidation: Default");
using (BarCodeReader read = new BarCodeReader($"{path}Code39.png", DecodeType.Code39Extended))
{
    read.BarcodeSettings.ChecksumValidation = ChecksumValidation.Default;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine($"1D Value:{result.Extended.OneD.Value}");
        Console.WriteLine($"1D CheckSum:{result.Extended.OneD.CheckSum}");
    }
}

//read barcode image with ChecksumValidation.On being set
Console.WriteLine("ChecksumValidation: On");
using (BarCodeReader read = new BarCodeReader($"{path}Code39.png", DecodeType.Code39Extended))
{
    read.BarcodeSettings.ChecksumValidation = ChecksumValidation.On;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
        Console.WriteLine($"1D Value:{result.Extended.OneD.Value}");
        Console.WriteLine($"1D CheckSum:{result.Extended.OneD.CheckSum}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="code39.png"></p>

