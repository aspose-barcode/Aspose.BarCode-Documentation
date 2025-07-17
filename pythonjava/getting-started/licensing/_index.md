---
title: Licensing
type: docs
ai_search_scope: "barcode_python-java_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 40
url: /python-java/licensing/
---

## **Overview**

The evaluation version of **Aspose.BarCode for Python via Java** allows full barcode generation functionality but adds a
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
<a href="https://purchase.aspose.com/pricing/barcode/python-java/" target="_blank">Pricing for Aspose.BarCode for Python
via Java</a>

Every license includes:

- **1-year subscription**: Access to all updates and bug fixes during the subscription period.
- **Free technical support**: Available to both licensed and evaluation users without limitations.

---

## **License File**

The license is an XML file that contains essential information about your license, including:

- `License Type`
- `Order ID`
- `Product Names` the license applies to
- `Customer` details
- `Edition Type`
- `Serial Number`

A **trial license** includes an additional field, `LicenseExpiry`,
which specifies the expiration date.
After this date, the trial license becomes inactive.

Both **trial** and **commercial** licenses include a `SubscriptionExpiry` field,
which defines the period during which you are entitled to receive product updates,
such as:

- Bug fixes
- Performance enhancements
- New feature additions

> ⚠️ **Note:** Typically, the `LicenseExpiry` date is earlier than the `SubscriptionExpiry`.  
> Therefore, for trial licenses, the `SubscriptionExpiry` has no practical effect.

> ⚠️ **Do not modify the license file.**  
> The license is digitally signed.
> Any changes — including additional spaces or line breaks —
> will corrupt the file and cause validation to fail.

---

## **Applying a License**

```python
    from asposebarcode import Recognition, Assist
    license = Assist.License()
    license.setLicense(path_to_license_file)
    reader = Recognition.BarCodeReader("image.png",None, Recognition.DecodeType.DATABAR_EXPANDED_STACKED)
```
