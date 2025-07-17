---
title: Licensing
type: docs
ai_search_scope: "barcode_androidjava_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 40
feedback: BARCODECOM
url: /androidjava/licensing/
---

## **Overview**

The evaluation mode of ***Aspose.BarCode for Android via Java*** allows generating barcode images without restrictions. However, a
watermark will be displayed on the resulting barcode image (words “Aspose”). The unlicensed version can be used to read
barcodes of all supported types. Please note that only *Code 39* can be decoded without limitations; as a result of
reading barcodes corresponding to other types, 30% of decoded text will be masked with " * ". All other actions with
barcodes using ***Aspose.BarCode for Android via Java*** need setting a license. After purchasing a license, you will get access to
the whole functionality of the library and the ability to perform barcode generation and reading without limitations and
watermark placement.

## **How to Obtain License**

If you want to try the full version of ***Aspose.BarCode for Android via Java***, you can request a temporary license  
valid for 30 days. Please read <a href="https://purchase.aspose.com/temporary-license" target="_blank">How to get a Temporary License?</a>  
for more information.

To use the library without limitations, purchasing a commercial license is necessary.  
You can find all pricing and licensing details
<a href="https://purchase.aspose.com/pricing/barcode/android-java/" target="_blank">here</a>.

Each Aspose license enables a one-year subscription with free upgrades to any new releases or fixes that are published
during this period. Technical support is provided for free unlimitedly both to licensed and evaluation users.

## **How to Install License**

The license is a plain-text XML file that includes details such as the product name, the number of developers it is
licensed for, subscription expiry date, and others. The license file is signed digitally, so it must not be modified in
any way. Adding even an extra line break into the license file will result in invalidating the license. You need to
activate the license to enable the unlimited use of library functions. You only have to enable the license once per
application (or process).

The license can be loaded from a stream or file.
You need to call the *setLicense* method of class [
*License*](https://reference.aspose.com/barcode//java/com.aspose.barcode/license) to apply the license to the component.

### **Using Singleton for License Initialization**

The most effective way to implement the license is through lazy initialization using the Singleton pattern in your code.
Below, we demonstrate how to achieve this with just a few additional lines of code in your project.
{{< highlight java >}}
public class LicenseSingleton
{
    private static LicenseSingleton instance;
    private LicenseSingleton(String pathToLicenseFile)
    {
      try
      {
      // Initialize the license
       com.aspose.barcode.License license = new com.aspose.barcode.License();
       license.setLicense(pathToLicenseFile);
      }
      catch (Exception e)
      {
        e.printStackTrace();
      }
    } 
}

public static synchronized void setLicense()
{
    if (instance == null)
    {
      instance = new LicenseSingleton(pathToLicenseFile);
    }
}
{{< /highlight >}}

You can now initialize the license in your code by simply calling LicenseSingleton.setLicense():
{{< highlight java >}}
LicenseSingleton.setLicense();
BarCodeReader reader = new BarCodeReader(path, DecodeType.CODE_39_FULL_ASCII);
for (BarCodeResult result : reader.readBarCodes())
{
  System.out.printf("CodeText: %s%n", result.getCodeText());;
  System.out.printf("CodeType: %s%n", result.getCodeType());;
}
{{< /highlight >}}

### **Install License From File**

{{< highlight java >}}
com.aspose.barcode.License license = new com.aspose.barcode.License();
license.setLicense(pathToLicenseFile);
{{< /highlight >}}
or
{{< highlight java >}}
com.aspose.barcode.License license = new License();
license.setLicense(new File(pathToLicenseFile));
{{< /highlight >}}

### **Install License From Stream**

{{< highlight java >}}
License license = new License();
Path filePath = Paths.get(pathToLicenseFile);
try (InputStream inputStream = Files.newInputStream(filePath))
{
  license.setLicense(inputStream);
}
catch (IOException e)
{
  e.printStackTrace();
}
{{< /highlight >}}

<!--
### **Configure Metered Key**
Aspose.BarCode for Android via Java allows developers to apply metered keys. It is a new licensing mechanism that can be applied along with the existing licensing method. Those customers who want to be billed based on the usage of API features can apply metered licensing. For more details, please refer to [Metered Licensing FAQ](https://purchase.aspose.com/faqs/licensing/metered).

Class [*Metered*](https://reference.aspose.com/barcode/java/com.aspose.barcode.metered/package-frame) has been introduced to apply the metered key. The sample code snippet demonstrating how to set metered public and private keys is provided below.

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-ApplyMeteredKey-ApplyMeteredKey.java" >}}
-->
