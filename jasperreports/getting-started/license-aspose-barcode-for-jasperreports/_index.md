---
title: Licensing
type: docs
weight: 80
url: /jasperreports/license-aspose-barcode-for-jasperreports/
aliases:
- /jasperreports/introduction/
- /jasperreports/evaluation-version-limitations/
- /jasperreports/applying-a-license/
- /jasperreports/evaluate-aspose-barcode/
---

## **Overview**
The evaluation mode of ***Aspose.BarCode for JasperReports*** allows generating barcode images without restrictions. However, a watermark will be displayed on the resulting barcode image (words “Aspose”). The unlicensed version can be used to read barcodes of all supported types. Please note that only *Code 39* can be decoded without limitations; as a result of reading barcodes corresponding to other types, 30% of decoded text will be masked with " * ". All other actions with barcodes using ***Aspose.BarCode for JasperReports*** need setting a license. After purchasing a license, you will get access to the whole functionality of the library and the ability to perform barcode generation and reading without limitations and watermark placement.  

## **How to Obtain License**
If you want to try the full version of ***Aspose.BarCode for JasperReports***, you can try a temporary license that is valid for 30 days. Please read [How to get a Temporary License?](https://purchase.aspose.com/temporary-license) for more information. To use the library without limitations, purchasing a commercial license is necessary. You can get all information about pricing and conditions [here](https://purchase.aspose.com/admin/pricing/barcode/java). 

Each Aspose license enables a one-year subscription with free upgrades to any new releases or fixes that are published during this period. Technical support is provided for free unlimitedly both to licensed and evaluation users.

## **License Setting**
To apply a license:

1. Save the license file to a folder on your disk. For example C:\Lic\Aspose.BarCode.JasperReport.lic.
1. Call the License.setLicense(filename) method and pass the file name as an argument.
   When this statement is called, the licensed is set and the **Aspose.Demo** label no longer appears on top of the barcode image.

The following code snippet sets the license for ***Aspose.BarCode for JasperReports***. 

**Java**

``` java

 // Set license

License lic = new License();

lic.setLicense("C:\\ Lic\\Aspose.BarCode.JasperReports.lic");

```

You need to call the setLicense() method only once per process or application.
