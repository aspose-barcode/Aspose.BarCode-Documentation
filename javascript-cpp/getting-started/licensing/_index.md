---
title: Licensing
type: docs
feedback: BARCODECOM
weight: 70
description: "Setting the License for Aspose.BarCode for JavaScript via C++"
keywords: "Generate Barcodes, Read Barcodes, How to Generate Barcodes in JavaScript, Aspose.BarCode License, Aspose.BarCode Licensing, Get License for Aspose.Barcode"
url: /javascript-cpp/licensing/
---

## **Overview**
***Aspose.BarCode for JavaScript via C++*** can be used to generate barcode labels in its unlicensed state, but with certain limitations. When using the library without a license, a watermark stating “Aspose” will be placed on all generated barcode images. Additionally, while the library supports reading all barcode types, only the *Code39* symbology is available without restrictions; for other barcode types, 30% of the decoded text will be masked with "*". To fully utilize the library’s capabilities, including barcode generation and recognition without watermarks or text masking, a valid license must be applied.

## **How to Obtain a License**
To explore the full range of features in ***Aspose.BarCode for JavaScript via C++***, you can request a 30-day temporary license. Detailed information and instructions for obtaining a temporary license can be found at [How to get a Temporary License?](https://purchase.aspose.com/temporary-license). For ongoing use without limitations, a commercial license is necessary. Pricing and licensing details are available [here](https://purchase.aspose.com/pricing/barcode/javascriptcpp/).

## **How to Install the License**
To ensure your license is protected from unauthorized use, it must be encrypted before use. Follow these steps to encrypt and install your license:

1. **Encrypt Your License**:
   - Use the `encrypt_lic.html` utility provided with the library.
   - Open `encrypt_lic.html` in a web browser.
   - Click the button to select your license file.
   - After encryption, you will receive a message confirming “Encrypt OK: aspose.enc”. Click the provided link to download the encrypted license file named `aspose.enc`.

2. **Set the License**:
   - To apply the encrypted license, call the `SetLicense` method of the class [*Aspose.BarCode.License*](https://reference.aspose.com/barcode/javascript-cpp/aspose.barcode/license).
   - Ensure that the `SetLicense` method is invoked before performing any operations with the library.

By setting the license as described, you will unlock all features of ***Aspose.BarCode for JavaScript via C++***, allowing you to generate and recognize barcodes without any restrictions or watermarks.
