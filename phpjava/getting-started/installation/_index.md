---
title: Installation
type: docs
weight: 30
url: /phpjava/installation/
aliases:
- /java/aspose-barcode-for-php-via-java-installation/
---
### **Platform and Compatibility**

**Aspose.BarCode for PHP via Java** is a platform-independent product that can be used on any operating system — including **Windows**, **Linux**, and **Solaris** — where both PHP and Java are installed.

### **System Requirements**

- **PHP**: Version 7.4 or higher
- **Java**: JDK 1.8 or higher

It requires Java SE 1.8 or later and works with various JDK distributions, including but not limited to:

- **Oracle JDK**
- **BellSoft Liberica JDK**
- **Amazon Corretto**
- **OpenJDK**
- **Other compatible distributions**

This flexibility ensures that **Aspose.BarCode for PHP via Java** can integrate seamlessly into most environments, whether for development, testing, or production.

### **Installation Options**

You have several options to install the product:

#### **1. Clone from GitHub**

Clone the Aspose.BarCode repository from GitHub:  
<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-PHP-via-Java/tree/master" target="_blank">Aspose.BarCode for PHP via Java Repository</a>

```bash
git clone git@github.com:aspose-barcode/Aspose.BarCode-for-PHP-via-Java.git
```

#### **2. Install via Composer**

Example `composer.json`:

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

```bash
composer install
```

> **GD Extension Required**  
> This library requires the <a href="https://www.php.net/manual/en/book.image.php" target="_blank">GD extension</a> to be installed and enabled in your PHP environment.  
> Composer **does not install PHP extensions** — it only verifies their presence during installation.

If `ext-gd` is missing, you may encounter the following error:

```
- aspose/barcode 25.5.5 requires ext-gd * -> it is missing from your system.
```

Need help installing GD?  
See the <a href="https://www.php.net/manual/en/image.installation.php" target="_blank">official PHP GD installation guide</a>,  
or refer to your operating system’s package manager.

#### **3. Download from Aspose Website**

Download the ZIP archive from the <a href="https://releases.aspose.com/barcode/php/" target="_blank">Aspose website</a>.  
This archive contains:

- `doc/` — includes `aspose-barcode-php-25.5-javadoc.zip`, the compressed API docs
- `license/` — contains the End User License Agreement and third-party licenses
- `lib/` — includes PHP source files and the product JAR file
- `bin/` — includes scripts for launching the Java server
- `README.md` — general instructions

You can copy the contents of the `lib/` folder into a suitable directory in your application (e.g., `barcode-lib`) 
and the `bin/` folder as well.  
Then, update the command lines in the scripts to reflect your folder structure, for example:

**Windows:**
```cmd
set JAR_PATH=%SCRIPT_DIR%..\barcode-lib\aspose-barcode-php-25.5.jar
```

**Linux/macOS:**
```bash
JAR_PATH="$SCRIPT_DIR/../barcode-lib/aspose-barcode-php-25.5.jar"
```

### **Running and Testing**

Start the Java Apache Thrift server using `start_server.cmd` or `start_server.sh`.

Example console output:
```log
Starting Thrift server...
Thrift server started! Logs are in server.log.
Initializing Thrift server on port 9090...
? Thrift server started successfully on port 9090
```

Run a basic PHP test:

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
