---
title: Licensing
type: docs
weight: 40
url: /phpjava/licensing/
---

## **Overview**

The evaluation version of **Aspose.BarCode for PHP via Java** allows full barcode generation functionality but adds a
watermark (“Aspose”) to each generated image. It also supports barcode recognition for all types; however, only 
*Code 39* can be fully decoded. For all other symbologies, 30% of the recognized text will be replaced with asterisks ("*").

Any additional functionality—such as saving clean images, full barcode decoding, and advanced settings—requires applying
a valid license.

Once a license is applied, all limitations are removed, including watermarking and masked output, unlocking full access
to barcode generation and recognition capabilities.

---

## **How to Obtain a License**

To evaluate the full version without restrictions, you can request a **30-day temporary license**.  
More information is available here: <a href="https://purchase.aspose.com/temporary-license" target="_blank">How to get a
Temporary License?</a>

For production use, a commercial license is required. License pricing and details are available at:  
<a href="https://purchase.aspose.com/admin/pricing/barcode/php-java" target="_blank">Pricing for Aspose.BarCode for PHP
via Java</a>

Every license includes:

- **1-year subscription**: Access to all updates and bug fixes during the subscription period.
- **Free technical support**: Available to both licensed and evaluation users without limitations.

---

## **License File**

The license is an XML file that contains key information about the purchased license, including:

- `License Type`
- `Order ID`
- `Product Names` to which the license applies
- `Customer` information
- `Edition Type` of the license
- `Serial Number` of the issued license

A **trial license** includes an additional field, `LicenseExpiry`, 
which defines the date until which the license remains valid. 
After this date, the trial license becomes inactive.

Both **trial** and **commercial** licenses include a `SubscriptionExpiry` field. 
This defines the end of the update subscription period. 
Until this date, the customer is entitled to receive all product updates.
> ⚠️ **Note:** Typically, the `LicenseExpiry` date is earlier than the `SubscriptionExpiry`.  
> Therefore, for trial licenses, the `SubscriptionExpiry` value has no practical effect.


Aspose.BarCode typically delivers monthly updates that may include:

- Bug fixes
- Performance improvements
- New feature additions

> ⚠️ **Do not modify the license file.**  
> The license file is digitally signed. 
> Any changes — including extra spaces or line breaks — 
> will result in the file being corrupted and failing validation.

## **Applying a License**
Customer can apply license file in several ways.
1. #### Applying for whole session:
The license must be set before any barcode generation or recognition operations.
Once set, the license remains in effect and does not need to be reapplied for each request.

Example for **BarcodeGenerator** and **BarCodeReader**

```php
    $license = new License();
    Assert::assertFalse($license->isLicensed());
    $license->setLicense(LICENSE_PATH);
    Assert::assertTrue($license->isLicensed());
    $codeText = "12345678";
    $encodeType = EncodeTypes::CODE_11;
    $generator = new BarcodeGenerator($encodeType, $codeText);
    $base64Image = $generator->generateBarCodeImage(BarCodeImageFormat::PNG, false);
    // last parameter`$passLicense` has default valuse `false` and can be ommitted
    Assert::assertTrue($license->isLicensed());
    $reader = new BarCodeReader($base64Image, null, null);
    $resultsArray = $reader->readBarCodes(false);
     // parameter `$passLicense` has default valuse `false` and can be ommitted
    $barCodeResult = $resultsArray[0];
    $codeTextAct = $barCodeResult->getCodeText();
    $codeTypeAct = $barCodeResult->getCodeTypeName();
    Assert::assertTrue($license->isLicensed());
```

Example for **ComplexBarcodeGenerator** and **BarCodeReader**

```php
      //Prepare Mailmark Codetext
      $mailmarkCAndLCodetext = new MailmarkCodetext(null);
      $mailmarkCAndLCodetext->setFormat(4);
      $mailmarkCAndLCodetext->setVersionID(1);
      $mailmarkCAndLCodetext->setClass_("0");
      $mailmarkCAndLCodetext->setSupplychainID(384224);
      $mailmarkCAndLCodetext->setItemID(16563762);
      $mailmarkCAndLCodetext->setDestinationPostCodePlusDPS("EF61AH8T ");
      //Install License
      $license = new License();
      Assert::assertFalse($license->isLicensed());
      $license->setLicense(PHP_LICENSE_PATH);
      Assert::assertTrue($license->isLicensed());
      $generator = new ComplexBarcodeGenerator($mailmarkCAndLCodetext);
      $base64Image = $generator->generateBarCodeImage(BarCodeImageFormat::PNG);
      Assert::assertTrue($license->isLicensed());
      $barCodeReader = new BarCodeReader($base64Image, null, DecodeType::MAILMARK);
      $resultsArray = $barCodeReader->readBarCodes(false);
      Assert::assertEquals(sizeof($resultsArray), 1);
      $resultCodeText = $barCodeReader->getFoundBarCodes()[0]->getCodeText();
      Assert::assertEquals("4100016563762EF61AH8T", trim($resultCodeText));
      $mailmarkCodetext = ComplexCodetextReader::tryDecodeMailmark($resultCodeText);
      Assert::assertTrue($license->isLicensed());
```

2. ####  Passing license with each individual request to the Java backend:
 In this mode, the license is not applied globally.
 The PHP code explicitly passes the license with each individual request to the Java backend.
 After Java processes the request and returns the result to PHP, the license state is cleared on the Java side
 and the application reverts to a non-licensed state until new request with passing license file.
  Only 3 methods has parameter `bool $passLicense`:
```php  
       Generation -> BarcodeGenerator -> generateBarCodeImage(int $format, bool $passLicense = false): string
       Recognition -> BarCodeReader -> readBarCodes(bool $passLicense = false): array
       ComplexBarcode -> ComplexBarcodeGenerator -> generateBarcodeImage(int $format, bool $passLicense = false): string
 ``` 

Example for **BarcodeGenerator** and **BarCodeReader**

```php
       $license = new License();
       License::prepareLicenseContent(TestsAssist::PHP_LICENSE_PATH);
       Assert::assertFalse($license->isLicensed());
       $codeText = "12345678";
       $encodeType = EncodeTypes::CODE_11;
       $generator = new BarcodeGenerator($encodeType, $codeText);
       $base64Image = $generator->generateBarCodeImage(BarCodeImageFormat::PNG, true);
       Assert::assertFalse($license->isLicensed());
       $reader = new BarCodeReader($base64Image, null, null);
       $resultsArray = $reader->readBarCodes(true);
       $barCodeResult = $resultsArray[0];
       $codeTextAct = $barCodeResult->getCodeText();
       $codeTypeAct = $barCodeResult->getCodeTypeName();
       Assert::assertFalse($license->isLicensed());
```

Example for **ComplexBarcodeGenerator** and **BarCodeReader**

```php
       //Prepare Mailmark Codetext
       $mailmarkCAndLCodetext = new MailmarkCodetext(null);
       $mailmarkCAndLCodetext->setFormat(4);
       $mailmarkCAndLCodetext->setVersionID(1);
       $mailmarkCAndLCodetext->setClass_("0");
       $mailmarkCAndLCodetext->setSupplychainID(384224);
       $mailmarkCAndLCodetext->setItemID(16563762);
       $mailmarkCAndLCodetext->setDestinationPostCodePlusDPS("EF61AH8T ");
       //Prepare license and pass it with each request to Java side
       $license = new License();
       License::prepareLicenseContent(ta::PHP_LICENSE_PATH);
       Assert::assertFalse($license->isLicensed());
       $generator = new ComplexBarcodeGenerator($mailmarkCAndLCodetext);
       $base64Image = $generator->generateBarCodeImage(BarCodeImageFormat::PNG, true);
       Assert::assertFalse($license->isLicensed()); //false
       $barCodeReader = new BarCodeReader($base64Image, null, DecodeType::MAILMARK);
       $resultsArray = $barCodeReader->readBarCodes(true);
       Assert::assertEquals(sizeof($resultsArray), 1);
       $resultCodeText = $barCodeReader->getFoundBarCodes()[0]->getCodeText();
       $mailmarkCodetext = ComplexCodetextReader::tryDecodeMailmark($resultCodeText);
       Assert::assertEquals("4100016563762EF61AH8T", trim($mailmarkCodetext->getConstructedCodetext()));
       Assert::assertFalse($license->isLicensed());
```

