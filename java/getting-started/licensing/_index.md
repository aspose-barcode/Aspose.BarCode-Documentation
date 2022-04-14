---
title: Licensing
type: docs
weight: 50
url: /java/licensing/
---

## **Overview**
without license, ***Aspose.BarCode for Java*** allows generating barcode images without restrictions. However, a watermark will be displayed on the resulting barcode image (words “Aspose”). The unlicensed version can be used to read barcodes of all supported symbologies. Please note that only the *Code39* symbology can be read without limitations; as a result of reading barcodes correponding to other symbologies, 30% of decoded text will be masked with " * ". All other actions with barcodes using ***Aspose.BarCode for Java*** need setting a license. Purchsing a license will provide access to the whole functionality of the library and you will be able to perform barcode generation and reading without limitations and watermark placement.  

## **How to Obtain License**
If you want to try the full version of ***Aspose.BarCode for Java***, you can try a temporary license that is valid for 30 days. Please read [How to get a Temporary License?](https://purchase.aspose.com/temporary-license) for more information. To use the library without limitations, purchasing a commercial license is necessary. You can get all information about pricing and conditions [here](https://purchase.aspose.com/admin/pricing/barcode/java). 

Each Aspose license enables a one-year subscription with free upgrades to any new releases or fixes that are published during this period. Technical support is provided for free unlimitedly both to licensed and evaluation users.

## **License Setting**
The license is a plain-text XML file that includes details such as the product name, the number of developers it is licensed for, subscription expiry date, and others. The license file is signed digitally, so it must not be modified in any way. Adding even an extra line break into the license file will result in invalidating the license. You need to activate the license to enable the unlimited use of library functions. You only have to enable the license once per application (or process). 

The license can be loaded from a stream or file using the following locations:

1. Explicit path
1. Folder that comprises Aspose.BarCode.jar

You need to call the *setLicense* method of class [*License*](https://apireference.aspose.com/barcode//java/com.aspose.barcode/license) to apply the license to the component. The easiest way to activate the license is to place the license file into the same folder as Aspose.BarCode.jar and specify the license file name without a path, as shown in the following example.

### **Apply License From File**
In this example, Aspose.BarCode will attempt to find the license file in the folder that contains JARs of your application.

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-ApplyALicense-ApplyALicense.java" >}}

### **Apply License From Stream**
In this example, the license is initialized from a stream.

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-ApplyLicenseFromStream-ApplyLicenseFromStream.java" >}}

### **Applying Metered Key**
Aspose.BarCode for Java allows developers to apply metered keys. It is a new licensing mechanism that can be applied along with the existing licensing method. Those customers who want to be billed based on the usage of API features can apply metered licensing. For more details, please refer to [Metered Licensing FAQ](https://purchase.aspose.com/faqs/licensing/metered).

Class [*Metered*](https://apireference.aspose.com/barcode/java/com.aspose.barcode.metered/package-frame) has been introduced to apply the metered key. The sample code snippet demonstrating how to set metered public and private keys is provided below.

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-ApplyMeteredKey-ApplyMeteredKey.java" >}}




