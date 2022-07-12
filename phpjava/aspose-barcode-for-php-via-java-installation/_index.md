---
title: Aspose.BarCode for PHP via Java Installation
type: docs
weight: 10
url: /java/aspose-barcode-for-php-via-java-installation/
---

Aspose.BarCode for PHP via Java is a platform-independent API and can be used on any platform (Windows, Linux, etc.) where PHP and Java Bridge are installed.

## **System Requirements**
- Tomcat Server 8.0 or above installed.
- PHP/JavaBridge is configured.
- FastCGI is installed.
- Downloaded Aspose.Barcode component.

## **Supported Platforms**
- PHP 5.x or 7.x
- Java 1.8 or above

## **Installation**
### **Method 1**
- Clone the Repository
{{< highlight php >}}
git clone git@github.com:asposemarketplace/Aspose-Barcode-Java-for-PHP.git
{{< /highlight >}}

- Setup the project using composer
{{< highlight php >}}
composer install
{{< /highlight >}}

### **Method 2**
- In the composer.json file of your PHP project, add the following lines
{{< highlight php >}}
{    
    "require": {        
        "asposebarcode/aspose_barcode_java_for_php": "dev-master"    
    }
}
{{< /highlight >}}

- Run the install command
{{< highlight php >}}
composer install
{{< /highlight >}}

{{% alert color="primary" %}} 

Read more about composer on http://www.getcomposer.com

{{% /alert %}} 