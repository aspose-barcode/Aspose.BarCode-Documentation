---
title: Installation
type: docs
weight: 60
url: /phpjava/installation/
aliases:
- /java/aspose-barcode-for-php-via-java-installation/
---

## 📦 Installation Options
You have several options to install product.
**1 Clone from GitHub**
- Clone the Aspose.BarCode from GitHub repository
  <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-PHP-via-Java/tree/master" target="_blank">
  Aspose.BarCode for PHP via Java Repository </a> 

```
git clone git@github.com:aspose-barcode/Aspose.BarCode-for-PHP-via-Java.git
```

**2 Install by composer**
- Example of composer.json

```json
{
  "require": {
    "aspose/barcode": "25.5.5",
    "ext-gd": "*"
  },
  "autoload": {
    "psr-4": {
      "MyApp\\": "src/"
    }
  }
}
```
Then run:
``` bash
composer install
```
⚠️ GD Extension Required
Note: This library requires the <a href="https://www.php.net/manual/en/book.image.php" target="_blank">GD extension</a> 
to be installed and enabled in your PHP environment.
Composer does not install PHP extensions — it only verifies their presence during installation.

If ext-gd is missing, you may encounter the following error:
```
- aspose/barcode 25.5.5 requires ext-gd * -> it is missing from your system.
```
Need help installing GD? 
See instructions <a href="https://www.php.net/manual/en/image.installation.php" target="_blank">here</a>, 
or refer to your operating system’s package manager.


**2 Download from Company WebSite**

Download zip archive from <a href="https://releases.aspose.com/barcode/php/" target="_blank">Aspose Company website</a>.
This archive contains 
- folder `doc` with `aspose-barcode-php-25.5-javadoc.zip` which is the compressed API Docs
- folder `licence` that contains `End User License Agreement` and `Third Party Licenses` describing files
- folder `lib` that contains PHP files and JAR file of product
- folder `bin` that contains scripts for launch Java server
- README.md

You may copy content of lib folder to suitable folder in your application like `barcode-lib`
and copy `bin` folder to your application. Correct the command line in the scripts depending on
where you situated the lib files. For example like:
```cmd
set JAR_PATH=%SCRIPT_DIR%..\barcode-lib\aspose-barcode-php-25.5.jar
```
or
```bash
JAR_PATH="$SCRIPT_DIR/../barcode-lib/aspose-barcode-php-25.5.jar"
```

### Running and testing
Launch Java Apache Thrift server by `start_server.cmd` or `start_server.sh`.
You will see console with messages like
```log
Starting Thrift server...
Thrift server started! Logs are in server.log.
Initializing Thrift server on port 9090...
? Thrift server started successfully on port 9090
```
Run PHP test
```php
  $license = new License();
  $license->setLicense(PHP_LICENSE_PATH);
  $codeText = "12345678";
  $encodeType = EncodeTypes::CODE_11;
  $generator = new BarcodeGenerator($encodeType, $codeText);
  $base64Image = $generator->generateBarCodeImage(BarCodeImageFormat::PNG);
  $reader = new BarCodeReader($base64Image, null, null);
  $resultsArray = $reader->readBarCodes();
  $barCodeResult = $resultsArray[0];
  $codeText = $barCodeResult->getCodeText();
  $codeType = $barCodeResult->getCodeTypeName();
  print("codeText " . $codeText);
  print("codeType " . $codeType);
```


