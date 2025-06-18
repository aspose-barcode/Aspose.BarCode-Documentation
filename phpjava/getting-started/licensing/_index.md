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

## **Applying a License**

The license is a XML file that contains key information about baied license including
`License Type`, `Order ID`, `Products Names` for which it allowed to be applied,
information about `Customer`, `Edition Type` of License, `Serial Number` of given License.
The trial license contains field `LicenseExpiry` and can be used only until this date is reached.
Both trial and commercial licenses contain field  `SubscriptionExpiry`. 
Until this date is reached the customer can obtain updates of his product.
Product gives updates ussually every month in new release.
These updates incudes bug fixing, improvements and adding new features.


> ⚠️ **Do not modify the license file.** Even minor changes (e.g., extra spaces or line breaks) will invalidate the
> file.

To enable the full functionality of the library, you must apply the license using the provided API methods.

```php
$license = new Java("com.aspose.barcode.License");
$license->setLicense("path/to/Aspose.BarCode.Java.lic");
