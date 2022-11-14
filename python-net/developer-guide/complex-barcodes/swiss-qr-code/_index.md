---
title: Swiss QR Code
type: docs
description: "This article explains how to Generate and Read Swiss QR Codes using Aspose.BarCode for Python via .NET"
keywords: "Generate Swiss QR Codes, How to Create Swiss Barcodes, Swiss QR Code, Aspose.BarCode, Generate Barcode in Python"
weight: 10
url: /python-net/swiss-qr-code/
---

## **Overview**
*Swiss QR Code* has been created to automate payment digital operations in Switzerland. Currently, payment bills and receipts issued there need to be marked with a *Swiss QR Code* that stores the details about transactions. Unlike usual *QR Codes*, *Swiss QR Codes* have the Swiss cross sign in the center.  
  
The *Swiss QR Code* standard has been introduced to work with QR bills in electronic payments. A *Swiss QR Code* contains all necessary payment information required to execute payments or process a QR invoice. ***Aspose.BarCode for Python via .NET*** includes [*SwissQRBill*](https://reference.aspose.com/barcode/python-net/) and [*SwissQRCodetext*](https://reference.aspose.com/barcode/python-net/aspose.barcode.complexbarcode/swissqrcodetext) classes to work with *Swiss QR* codes.  
  
General rules for creating *Swiss QR Codes* and payment documents are described in the ["Swiss Implementation Guidelines for the QR-bill"](https://www.paymentstandards.ch/dam/downloads/ig-qr-bill-en.pdf) standard that relies on the ISO 20022 standard.

## **Generate Swiss QR Codes**
To generate a *Swiss QR Code*, it is necessary to create an instance of [*ComplexBarcodeGenerator*](https://reference.aspose.com/barcode/python-net/aspose.barcode.complexbarcode/complexbarcodegenerator/) and enter input data into [*SwissQRCodetext*](https://reference.aspose.com/barcode/python-net/aspose.barcode.complexbarcode/swissqrcodetext).  

<p align="center"><img src="swissqrbill.png"></p> 

Following code samples demonstrate how to generate *Swiss QR Code* images.

```python
    def minimalValidSwissQR(self):
        swissQRCodetext = complexbarcode.SwissQRCodetext()
        swissQRCodetext.bill.account = "CH450023023099999999A"
        swissQRCodetext.bill.creditor.name = "Name"
        swissQRCodetext.bill.creditor.country_code = "NL"
        
        return swissQRCodetext
```

```python
    def test_SwissQR_FullyInitialized_Test(self):
        swissQRCodetext = complexbarcode.SwissQRCodetext()
        swissQRCodetext.bill.account = "CH450023023099999999A"
        swissQRCodetext.bill.bill_information= "BillInformation"
        swissQRCodetext.bill.amount = 1024
        swissQRCodetext.bill.creditor.name = "Creditor.Name"
        swissQRCodetext.bill.creditor.address_line1 = "Creditor.AddressLine1"
        swissQRCodetext.bill.creditor.address_line2 = "Creditor.AddressLine2"
        swissQRCodetext.bill.creditor.country_code = "NL"
        swissQRCodetext.bill.unstructured_message = "UnstructuredMessage"
        swissQRCodetext.bill.reference = "Reference"
        swissQRCodetext.bill.alternative_schemes = [complexbarcode.AlternativeScheme("AlternativeSchemeInstruction1"), complexbarcode.AlternativeScheme("AlternativeSchemeInstruction2")]
        swissQRCodetext.bill.debtor = complexbarcode.Address()
        swissQRCodetext.bill.debtor.name = "Debtor.Name"
        swissQRCodetext.bill.debtor.address_line1 = "Debtor.AddressLine1"
        swissQRCodetext.bill.debtor.address_line2 = "Debtor.AddressLine2"
        swissQRCodetext.bill.debtor.country_code = "LU"
        
        cg = complexbarcode.ComplexBarcodeGenerator(swissQRCodetext)
        res = cg.generateBarCodeImage(generation.BarCodeImageFormat.PNG)
        
        cr = barcoderecognition.BarCodeReader(res, barcoderecognition.DecodeType.QR)
        self.assertEqual(cr.read_bar_codes().length, 1)
        test = complexbarcode.ComplexCodetextReader.tryDecodeSwissQR(cr.found_bar_codes[0].code_text)
        
        self.assertTrue(swissQRCodetext.bill.equals(test.bill))
```

## **Read Swiss QR Codes**
Class [*ComplexCodetextReader*](https://reference.aspose.com/barcode/python-net/aspose.barcode.complexbarcode/complexcodetextreader) is used to extract input data from different complex barcode types, in this case, *Swiss QR Code*. To decode *Swiss QR Codes*, first, it is necessary to create an instance of class [*BarCodeReader*](https://reference.aspose.com/barcode/python-net/aspose.barcode.barcoderecognition/barcodereader) and set it to the value *DecodeType.QR*. then, the decoded data needs to be parsed using class [*ComplexCodetextReader*](https://reference.aspose.com/barcode/python-net/aspose.barcode.complexbarcode/complexcodetextreader) by calling the *try_decode_swiss_qr(encoded_codetext)* method that returns an instance of [*SwissQRCodetext*](https://reference.aspose.com/barcode/python-net/aspose.barcode.complexbarcode/swissqrcodetext) with the decoded information.