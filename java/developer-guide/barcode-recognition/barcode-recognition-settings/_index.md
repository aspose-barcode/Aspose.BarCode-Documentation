---
title: Recognition Settings
type: docs
description: "This article describes how to adjust various barcode recognition settings in Aspose.BarCode for Java according to business needs"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcode Java"
weight: 20
url: /java/barcode-recognition-settings/
---

{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can test the quality of ***Aspose.BarCode*** recognition functionality and view the results online.{{% /alert %}}
  
## **Overview**
In ***Aspose.BarCode for Java***, after reading the raw data from a barcode graphical representation, the library initiates data decoding that is performed according to the specific protocol. Often, in the case of using particular 1D and postal barcode types, conflicting data decoding formats may appear because some barcode symbologies have undergone standardization later than the start of their wide usage. To resolve such conflicts, class [*BarCodeReader*]() contains a group of properties called [*BarcodeSettings*]() that are responsible for data decoding settings.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Checksum Verification**
In many 1D and postal symbologies, data integrity verification and decoding are based on checksum control mechanisms. Class [*BarcodeSettings*]() provides the [*ChecksumValidation*]() property that is used to manage checksum settings for data validation and decoding. In general, barcode standards can be divided into two groups: those with obligatory checksum and those with optional one. Depending on this, the [*ChecksumValidation*]() field can take different values; hence, the barcode recognition process will change according to particular checksum settings.  

### **Checksum Validation for Barcodes with Obligatory Checksum**
Symbologies with obligatory checksum always require performing checksum control when the [*ChecksumValidation*]() property is set to *ChecksumValidation.Default* or *ChecksumValidation.On*. Otherwise, this parameter can take the value *ChecksumValidation.Off* that disables checksum controls for barcode type with obligatory checksum and thus allows reading data from incorrectly generated barcodes. However, in this case, the probability of inaccurate recognition increases considerably.  
  
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

### **Checksum Validation for Barcodes with Optional Checksum**
For symbologies with optional checksum control, [*ChecksumValidation*]() can be set in such a way to enable checksum checking, namely, it needs to take the value *ChecksumValidation.On*. Otherwise, when the values *ChecksumValidation.Default* and *ChecksumValidation.Off* are used, checksum validation is omitted.  
  
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

## **Recognition and Processing of Unicode Encodings**
In ***Aspose.BarCode for Java***, there is a special parameter called [*DetectEncoding*]() that allows enabling the automatic recognition of UTF8 and UTF16 Unicode encodings for 2D barcode recognition, as well as re-encoding the data into a Unicode string. When this mode is disabled, the barcode data can be read and decoded manually using the required encoding.  
  
The following code snippet shows how to automatically decode barcodes with UTF8 and UTF16 Unicode encodings (a sample *QR Code* barcode image shown below has been considered). 

{{< highlight csharp>}}
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "بالقمة Aspose"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.QR.CodeTextEncoding = Encoding.UTF8;
    gen.Save($"{path}QRDetectEncoding.png", BarCodeImageFormat.Png);
}

Console.WriteLine("ReadDetectEncoding:");
//read barcode image with DetectEncoding set to true
Console.WriteLine("DetectEncoding: true");
using (BarCodeReader read = new BarCodeReader($"{path}QRDetectEncoding.png", DecodeType.QR))
{
    read.BarcodeSettings.DetectEncoding = true;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}

//read barcode image with DetectEncoding set to False
Console.WriteLine("DetectEncoding: false");
using (BarCodeReader read = new BarCodeReader($"{path}QRDetectEncoding.png", DecodeType.QR))
{
    read.BarcodeSettings.DetectEncoding = false;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="qrdetectencoding.png"></p>

## **Using FNC Symbols**
The GS1 association utilizes FNC symbols to manage decoding for *Code 128* and some other barcode types. There are four types of FNC symbols (FNC1-4) among which FNC1 is the most widespread one and is used for GS1 Application Identifier (AI) marking. When the library detects that a barcode does not correspond to any of GS1 types (e.g. *Code 128* or *GS1 Code 128*), the decoder outputs FNC symbols as “<FNC#>”. Such messages can be deleted from the recognition results by setting the [*StripFNC*]() property to false.  
  
The following code sample shows how to work with FCN symbols while reading a *Code 128* barcode demonstrated below.

{{< highlight csharp>}}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code128, "Aspose" + FNC1 + FNC2 + FNC3))
{
    gen.Parameters.Barcode.XDimension.Pixels = 2;
    gen.Save($"{path}Code128FNC.png", BarCodeImageFormat.Png);
}

//read barcode image with StripFNC set to False
Console.WriteLine("ReadWithStripFNC:");
Console.WriteLine("StripFNC: false");
using (BarCodeReader read = new BarCodeReader($"{path}Code128FNC.png", DecodeType.Code128))
{
    read.BarcodeSettings.StripFNC = false;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}

//read barcode image with StripFNC set to True
Console.WriteLine("StripFNC: true");
using (BarCodeReader read = new BarCodeReader($"{path}Code128FNC.png", DecodeType.Code128))
{
    read.BarcodeSettings.StripFNC = true;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="code128fnc.png"></p>

## **Reading Australia Post Barcodes**
*Australia Post* is a 4-state postal symbology used in the Australian Post. In this barcode standard, input messages include specific 2-digit format control code (FCC) fields and 8-digit sorting code (SC) fields. FCC fields are used to indicate one of three available barcode types with different fixed lengths: 37, 52, or 67 bars. Depending on FCC, barcodes may contain a customer information (CI) field that identifies one of the encoding types that support numerical or alphanumeric symbols. Customer information can occupy 16 bars in 52-length barcodes or 31 bars in 67-length ones. The Australia Post standard contains a checksum and information used for Reed-Solomon data recovery.  
*See more details about this symbology [here](/barcode/java/postal-barcodes/#australia-post-symbology)*.  
  
Due to the possibility to add customer information in barcode input data, barcode recognition for *Australia Post* barcodes has some specifics. In ***Aspose.BarCode for Java***, developers can use class [*AustraliaPostSettings*]() to customize recognition parameters for this barcode standard according to particular requirements. Further, the main properties of class [*AustraliaPostSettings*]() are explained in detail.

### **Decoding Customer Information in Standard Formats**
The *Australia Post* symbology allows encoding additional customer information in three different formats; automatic recognition of the format used for encoding is not possible. In ***Aspose.BarCode for Java***, the required decoding format can be set in the [*CustomerInformationInterpretingType*]() field that can take the following values as explained in the table below.
  
|Australia Post Encoding Table|Supported Symbols|
|---|---|
|CTable|Numerical digits, English letters, space symbol, and #|
|NTable|Numerical digits|
|Other|0, 1, 2, and 3 that correspond to H, A, D, and T states, respectively|
  
**CTable**  
  
The following code snippet explains how to set the decoding format using the *CTable* option for the barcode image shown below. 
  
{{< highlight csharp>}}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.AustraliaPost, "6201234567ASPOSE"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.BarHeight.Pixels = 50;
    gen.Parameters.Barcode.AustralianPost.AustralianPostEncodingTable = CustomerInformationInterpretingType.CTable;
    gen.Save($"{path}AustraliaPostCTable.png", BarCodeImageFormat.Png);
}

//read barcode image
Console.WriteLine("ReadAustraliaPostCTable:");
using (BarCodeReader read = new BarCodeReader($"{path}AustraliaPostCTable.png", DecodeType.AustraliaPost))
{
    read.BarcodeSettings.AustraliaPost.CustomerInformationInterpretingType = CustomerInformationInterpretingType.CTable;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="australiapostctable.png"></p>

**NTable**  
  
The following code sample shows how to apply the decoding format with the *NTable* option while reading the barcode image provided below. 
  
{{< highlight csharp>}}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.AustraliaPost, "620123456701234"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.BarHeight.Pixels = 50;
    gen.Parameters.Barcode.AustralianPost.AustralianPostEncodingTable = CustomerInformationInterpretingType.NTable;
    gen.Save($"{path}AustraliaPostNTable.png", BarCodeImageFormat.Png);
}

//read barcode image
Console.WriteLine("ReadAustraliaPostNTable:");
using (BarCodeReader read = new BarCodeReader($"{path}AustraliaPostNTable.png", DecodeType.AustraliaPost))
{
    read.BarcodeSettings.AustraliaPost.CustomerInformationInterpretingType = CustomerInformationInterpretingType.NTable;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="australiapostntable.png"></p>

**Other**  
  
The following code snippet demonstrates how to set the *Other* decoding format for the barcode image given below. 
  
{{< highlight csharp>}}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.AustraliaPost, "6201234567321032103210"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.BarHeight.Pixels = 50;
    gen.Parameters.Barcode.AustralianPost.AustralianPostEncodingTable = CustomerInformationInterpretingType.Other;
    gen.Save($"{path}AustraliaPostOther.png", BarCodeImageFormat.Png);
}

//read barcode image
Console.WriteLine("ReadAustraliaPostOther:");
using (BarCodeReader read = new BarCodeReader($"{path}AustraliaPostOther.png", DecodeType.AustraliaPost))
{
    read.BarcodeSettings.AustraliaPost.CustomerInformationInterpretingType = CustomerInformationInterpretingType.Other;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="australiapostother.png"></p>

### **Removal of Fill Patterns**
The *Australia Post* standard imposes using fixed size for each subtype. When barcode decoding is performed in the *CTable* format, the data filling empty space in the input message is decoded as symbol “z”. To avoid such a result, it is necessary to set the [*IgnoreEndingFillingPatternsForCTable*]() property to *True*.  
  
The following code sample illustrates how to eliminate filling patters while using the *CTable* decoding mode for the barcode image demonstrated below. 

{{< highlight csharp>}}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.AustraliaPost, "6201234567END"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.BarHeight.Pixels = 50;
    gen.Parameters.Barcode.AustralianPost.AustralianPostEncodingTable = CustomerInformationInterpretingType.CTable;
    gen.Save($"{path}AustraliaPostCTableIgnoreEnding.png", BarCodeImageFormat.Png);
}

Console.WriteLine("ReadAustraliaPostCTableIgnoreEnding:");
//read barcode image with IgnoreEndingFillingPatternsForCTable set to true
Console.WriteLine("IgnoreEndingFillingPatternsForCTable: true");
using (BarCodeReader read = new BarCodeReader($"{path}AustraliaPostCTableIgnoreEnding.png", DecodeType.AustraliaPost))
{
    read.BarcodeSettings.AustraliaPost.CustomerInformationInterpretingType = CustomerInformationInterpretingType.CTable;
    read.BarcodeSettings.AustraliaPost.IgnoreEndingFillingPatternsForCTable = true;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}

//read barcode image with IgnoreEndingFillingPatternsForCTable set to false
Console.WriteLine("IgnoreEndingFillingPatternsForCTable: false");
using (BarCodeReader read = new BarCodeReader($"{path}AustraliaPostCTableIgnoreEnding.png", DecodeType.AustraliaPost))
{
    read.BarcodeSettings.AustraliaPost.CustomerInformationInterpretingType = CustomerInformationInterpretingType.CTable;
    read.BarcodeSettings.AustraliaPost.IgnoreEndingFillingPatternsForCTable = false;
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="australiapostctableignoreending.png"></p>

### **Decoding Customer Information in Custom Format**
***Aspose.BarCode for Java*** allows developers to decode customer information in their own format. For this purpose, the library provides a special interface called [*CustomerInformationDecoder*](). In such a way, decoding of barcode data is performed using this interface; the properties [*CustomerInformationInterpretingType*]() and [*IgnoreEndingFillingPatternsForCTable*]() are ignored.  
  
The following code snippet explains how to decode customer information inputted in the *NTable* format while reading the sample *Australia Post* barcode shown below. 

{{< highlight csharp>}}
class NTableDecoder : AustraliaPostCustomerInformationDecoder
{
    string[] N_Table = { "00", "01", "02", "10", "11", "12", "20", "21", "22", "30" };
    public string Decode(string customerInformationField)
    {
        StringBuilder bd = new StringBuilder();
        for (int i = 0; i < customerInformationField.Length; i += 2)
        {
            if (i + 2 <= customerInformationField.Length)
            {
                string tmp = customerInformationField.Substring(i, 2);
                for (int j = 0; j < N_Table.Length; j++)
                {
                    if (N_Table[j].Equals(tmp))
                    {
                        bd.Append(j);
                        break;
                    }
                }
            }
        }
        return bd.ToString();
    }
}
//create barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.AustraliaPost, "620123456701234"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 4;
    gen.Parameters.Barcode.BarHeight.Pixels = 50;
    gen.Parameters.Barcode.AustralianPost.AustralianPostEncodingTable = CustomerInformationInterpretingType.NTable;
    gen.Save($"{path}AustraliaPostCustomerInformationDecoder.png", BarCodeImageFormat.Png);
}

//read barcode image
Console.WriteLine("ReadAustraliaPostCustomerInformationDecoder:");
using (BarCodeReader read = new BarCodeReader($"{path}AustraliaPostCustomerInformationDecoder.png", DecodeType.AustraliaPost))
{
    read.BarcodeSettings.AustraliaPost.CustomerInformationDecoder = new NTableDecoder();
    foreach (BarCodeResult result in read.ReadBarCodes())
    {
        Console.WriteLine($"CodeType:{result.CodeTypeName}");
        Console.WriteLine($"CodeText:{result.CodeText}");
    }
}
{{< /highlight >}}
  
<p align="center"><img src="australiapostcustomerinformationdecoder.png"></p>
