---
title: Barcode Reading Settings
type: docs
description: "This article describes how to adjust various barcode recognition settings in Aspose.BarCode for PHP via Java according to business needs"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Read Many Barcodes in One Image, Aspose.BarCode, Read Barcode PHP"
ai_search_scope: "barcode_phpjava_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 20
url: /phpjava/barcode-reading-settings/
---

{{% alert color="primary" %}}[Read Barcodes Online](https://products.aspose.app/barcode/recognize): You can test the quality of ***Aspose.BarCode*** recognition functionality and view results online.{{% /alert %}}
  
## **Overview**
In the reading process implemented in ***Aspose.BarCode for PHP via Java***, data decoding is initiated according to the special protocol after scanning the raw data from a graphical representation. Some linear and postal barcode types have passed standardization after their wide implementation, and therefore, it has led to the presence of incompatible decoding formats. To resolve possible conflicts, class [*BarCodeReader*](https://reference.aspose.com/barcode/php/classBarCodeReader) provides a special class called [*BarcodeSettings*](https://reference.aspose.com/barcode/php/classBarcodeSettings) used to manage barcode decoding settings.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/phpjava/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}


## **Checksum Controls**
Various 1D and postal types include checksum control mechanisms for data integrity verification. To adjust checksum settings for data validation purposes, class [*BarcodeSettings*](https://reference.aspose.com/barcode/php/classBarcodeSettings) contains the [*ChecksumValidation*](https://reference.aspose.com/barcode/php/classChecksumValidation) class. Generally, barcode types can be classified according to the following types: with obligatory checksum controls and with optional ones. The [*ChecksumValidation*](https://reference.aspose.com/barcode/php/classChecksumValidation) class suggests different options for these two groups. The barcode reading procedure varies in line with checksum settings.  

``` php
$generator = new BarcodeGenerator(EncodeTypes::EAN_13, "1234567890128");
$generator->save("c:/test.png", BarcodeImageFormat::PNG);
$reader = new BarCodeReader("c:/test.png", DecodeType::EAN_13);
//checksum disabled
$reader->getBarcodeSettings()->setChecksumValidation(ChecksumValidation::OFF);
foreach($reader->readBarCodes() as $result)
{
     echo ("BarCode CodeText: ".$result->getCodeText());
     echo ("BarCode Value: " + result.getExtended().getOneD().getValue());
     echo ("BarCode Checksum: " + result.getExtended().getOneD().getCheckSum());
}
$reader = new BarCodeReader(@"c:\test.png", DecodeType::EAN_13);
//checksum enabled
$reader->getBarcodeSettings()->setChecksumValidation(ChecksumValidation::ON);
foreach($reader->readBarCodes() as $result)
{
     echo ("BarCode CodeText: " + result.CodeText);
     echo ("BarCode Value: " + result.getExtended().getOneD().getValue());
     echo ("BarCode Checksum: " + result.getExtended().getOneD().getCheckSum());
}
```

### **Checksum Validation for Barcodes with Obligatory Checksum**
Barcoded types with obligatory checksum controls require performing compulsive checksum validation when [*ChecksumValidation*](https://reference.aspose.com/barcode/php/classChecksumValidation) is initialized using *DEFAULT* or *ON* values. Alternatively, setting the *OFF* value turns off checksum verification and in this way, allows decoding information from invalid barcodes. This option increases the probability of incorrect recognition.  
  
<p align="center"><img src="code11.png"></p> 

### **Checksum Validation for Barcodes with Optional Checksum**
[*ChecksumValidation*](https://reference.aspose.com/barcode/php/classChecksumValidation) allows enabling and disabling checksum controls for barcode standards with optional checksum verification. To request checksum validation, the following setting should be enabled: *ON*. When other options, *DEFAULT* and *OFF*, are used, checksum controls are disabled.  
  
<p align="center"><img src="code39.png"></p>

## **Managing Barcodes with Unicode Encodings**
***Aspose.BarCode for PHP via Java*** provides class [*BarcodeSettings*](https://reference.aspose.com/barcode/php/classBarcodeSettings). It includes the *setDetectEncoding* function that enables the automatic reading of UTF8 and UTF16 Unicode encodings for 2D types and allows re-encoding barcode information in a string with Unicode characters. If this reading mode is turned off, barcode information can be scanned and decoded manually based on the desired encoding.  
  
<p align="center"><img src="qrdetectencoding.png"></p>

``` php
$generator = new BarcodeGenerator(EncodeTypes::QR, "Слово"))
$im = $generator->generateBarcodeImage(BarcodeImageFormat::PNG);
 
//encoding detection for Unicode encodings is enabled
$reader = new BarCodeReader($im, DecodeType::QR);
$reader->getBarcodeSettings()->setDetectEncoding(true);
foreach($reader->readBarCodes() as $result)
    echo ("BarCode CodeText: ".$result->getCodeText());
 
//encoding detection is disabled
$reader = new BarCodeReader($im, DecodeType::QR);
$reader->getBarcodeSettings()->setDetectEncoding(false);
foreach($reader->readBarCodes() as $result)
    echo ("BarCode CodeText: ".$result->getCodeText());
```

## **FNC Symbols**
The GS1 association suggests using FNC character to perform decoding of some barcodes, including *Code 128* and *Code 128*. Four types of FNC symbols (FNC1-4) are supported. FNC1 is the most widely used one that is intended for GS1 Application Identifier (AI) marking. When a barcode does not relate to any of GS1 types (for example, *Code 128* or *GS1 Code 128*), the decoder processes FNC symbols as “<FNC#>”. These symbols can be removed from decoding results passing the *False* value to the *setStripFNC* function.    
  
<p align="center"><img src="code128fnc.png"></p>

``` php
$generator = new BarcodeGenerator(EncodeTypes::GS_1_CODE_128, "(02)04006664241007(37)1(400)7019590754");
$generator->save("c:/test.png", BarcodeImageFormat::PNG);
$reader = new BarCodeReader("c:/test.png", DecodeType::CODE_128);
 
//StripFNC disabled
$reader->getBarcodeSettings()->setStripFNC(false);
foreach($reader->readBarCodes() as $result)
{
    echo ("BarCode CodeText: ".$result->getCodeText());
}
 
$reader = new BarCodeReader("c:/test.png", DecodeType::CODE_128);
 
//StripFNC enabled
$reader->getBarcodeSettings()->setStripFNC(true);
foreach($reader->readBarCodes() as $result)
{
    echo ("BarCode CodeText: ".$result->getCodeText());
}
```

## **Read Australia Post Barcodes**
*Australia Post* is a 4-state postal barcode type implemented by the Australian Post. This type requires including special two-digit format control code (FCC) fields and eight-digit sorting code (SC) fields into barcode information. FCC fields are intended to set one of three supported types with various fixed numbers of bars: 37, 52, or 67 bars. For some FCC, barcodes may comprise a customer information (CI) field that indicates one of the encoding types supporting numerical or alphanumeric characters. Customer information can take 31 bars in 67-length barcodes or 16 bars in 52-length ones. The *Australia Post* symbology has checksum controls and supports Reed-Solomon error correction.  
  
Because of the possible presence of customer information in barcode information for *Australia Post*, the reading process has some peculiarities. Class [*AustraliaPostSettings*](https://reference.aspose.com/barcode/php/classAustraliaPostSettings) is provided to manage recognition parameters according to specific industrial needs. 

### **Decoding Customer Information in Standard Formats**
The *Australia Post* standard enables encoding additional customer data in three formats; automatic detection of the used format is not supported. The desired decoding format can be enabled through the *setCustomerInformationInterpretingType* function of class [*AustraliaPostSettings*](https://reference.aspose.com/barcode/php/classAustraliaPostSettings) using the properties of class [*CustomerInformationInterpretingType*](https://reference.aspose.com/barcode/php/classCustomerInformationInterpretingType) shown in the table below.
  
|Australia Post Encoding Table|Supported Symbols|
|---|---|
|CTable|Numerical digits, English letters, space symbol, and #|
|NTable|Numerical digits|
|Other|0, 1, 2, and 3 that correspond to H, A, D, and T states|
  
**CTable**   
  
<p align="center"><img src="australiapostctable.png"></p>

``` php
$generator = new BarcodeGenerator(EncodeTypes::AUSTRALIA_POST, "5912345678ABCde");
$generator->getParameters()->getBarcode()->getAustralianPost()->setAustralianPostEncodingTable(CustomerInformationInterpretingType::C_TABLE);
$image = $generator->generateBarcodeImage(BarcodeImageFormat::PNG);
$reader = new BarCodeReader($image, DecodeType::AUSTRALIA_POST);
$reader->setCustomerInformationInterpretingType(CustomerInformationInterpretingType::C_TABLE);
foreach($reader->readBarCodes() as $result)
{
    print("BarCode Type: ".$result->getCodeType());
    print("BarCode CodeText: ".$result->getCodeText());
}
```

**NTable**  

``` php
$generator = new BarcodeGenerator(EncodeTypes::AUSTRALIA_POST, "59123456781234567");
$generator->getParameters()->getBarcode()->getAustralianPost()->setAustralianPostEncodingTable(CustomerInformationInterpretingType::N_TABLE);
$image = $generator->generateBarcodeImage(BarcodeImageFormat::PNG);
$reader = new BarCodeReader($image, DecodeType::AUSTRALIA_POST);
$reader->setCustomerInformationInterpretingType(CustomerInformationInterpretingType::N_TABLE);
foreach($reader->readBarCodes() as $result)
{
   print("BarCode Type: ".$result->getCodeType());
   print("BarCode CodeText: ".$result->getCodeText());
}
``` 
  
<p align="center"><img src="australiapostntable.png"></p>

**Other**  
    
``` php
$generator = new BarcodeGenerator(EncodeTypes::AUSTRALIA_POST, "59123456780123012301230123");
$generator->getParameters()->getBarcode()->getAustralianPost()->setAustralianPostEncodingTable(CustomerInformationInterpretingType::OTHER);
$image = $generator->generateBarcodeImage(BarcodeImageFormat::PNG);
$reader = new BarCodeReader($image, DecodeType::AUSTRALIA_POST);
$reader->setCustomerInformationInterpretingType(CustomerInformationInterpretingType::OTHER));
foreach($reader->readBarCodes() as $result)
{
   print("BarCode Type: ".$result->getCodeType());
   print("BarCode CodeText: ".$result->getCodeText());
}
```

<p align="center"><img src="australiapostother.png"></p>

### **Removal of Filling Patterns**
The *Australia Post* type requires setting a fixed size for each subtype. When the *CTable* format is enabled, the empty space included in the input message is decoded as “z”. To disable this property, the *setIgnoreEndingFillingPatternsForCTable* function needs to be called.  
    
<p align="center"><img src="australiapostctableignoreending.png"></p>

``` php
$generator = new BarcodeGenerator(EncodeTypes::AUSTRALIA_POST, "5912345678AB");
$generator->getParameters()->getBarcode()->getAustralianPost()->setAustralianPostEncodingTable(CustomerInformationInterpretingType::C_TABLE);
$image = generator->generateBarCodeImage(BarcodeImageFormat::PNG);
$reader = new BarCodeReader($image, null, DecodeType::AUSTRALIA_POST);
$reader->getBarcodeSettings()->getAustraliaPost()->setCustomerInformationInterpretingType(CustomerInformationInterpretingType::C_TABLE);
$reader->getBarcodeSettings()->getAustraliaPost()->setIgnoreEndingFillingPatternsForCTable(true);
foreach($reader->readBarCodes() as $result)
    echo("BarCode Type: ".$result->getCodeType());
    echo("BarCode CodeText: ".$result->getCodeText());
}
```