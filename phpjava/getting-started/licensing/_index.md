---
title: Licensing
type: docs
weight: 50
url: /phpjava/licensing/

---

## **Overview**
The evaluation mode of ***Aspose.BarCode for PHP via Java*** allows generating barcode images without restrictions. However, a watermark will be displayed on the resulting barcode image (words “Aspose”). The unlicensed version can be used to read barcodes of all supported types. Please note that only *Code 39* can be decoded without limitations; as a result of reading barcodes corresponding to other types, 30% of decoded text will be masked with " * ". All other actions with barcodes using this barcode library need setting a license. After purchasing a license, you will get access to the whole functionality of the library and the ability to perform barcode generation and reading without limitations and watermark placement.  

## **How to Obtain License**
If you want to try the full version of ***Aspose.BarCode for PHP via Java***, you can try a temporary license that is valid for 30 days. Please read [How to get a Temporary License?](https://purchase.aspose.com/temporary-license) for more information. To use the library without limitations, purchasing a commercial license is necessary. You can get all information about pricing and conditions [here](https://purchase.aspose.com/admin/pricing/barcode/php-java). 

Each Aspose license enables a one-year subscription with free upgrades to any new releases or fixes that are published during this period. Technical support is provided for free unlimitedly both to licensed and evaluation users.

## **License Setting**
The license is a plain-text XML file that includes details such as the product name, the number of developers it is licensed for, subscription expiry date, and others. The license file is signed digitally, so it must not be modified in any way. Adding even an extra line break into the license file will result in invalidating the license. You need to activate the license to enable the unlimited use of library functions. You only have to enable the license once per application (or process). 

The license can be loaded from a stream or file using the following locations:

1. Explicit path
1. Folder that comprises Aspose.BarCode.jar

You need to call the *setLicense* method of class [*License*](https://reference.aspose.com/barcode/php/classLicense/) to apply the license to the component. The easiest way to activate the license is to place the license file into the same folder as Aspose.BarCode.jar and specify the license file name without a path.


