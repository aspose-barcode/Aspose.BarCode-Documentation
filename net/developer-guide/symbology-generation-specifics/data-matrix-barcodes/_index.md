---
title: Data Matrix Barcodes
type: docs
description: "The Data Matrix barcode is a high-density, two-dimensional (2D) symbology that encodes text, numbers, and actual data bytes, it is used to encode product and serial number information on electrical rating plates."
keywords: "Generate DataMatrix barcode, How to generate Data Matrix barcode, DataMatrix encoding, Aspose.BarCode for .NET, C# "
weight: 130
url: /net/datamatrix-barcode/
---

## **Create a Data Matrix Barcode**
*Data Matrix* is used to encode the information about product and serial number on electrical rating plates; to mark surgical instruments in Japan; to identify lenses, circuit boards, and other items during manufacturing. *Data Matrix* barcodes can store up to 2,000 characters. ***Aspose.BarCode for .NET*** provides a simple and convenient way to generate *Data Matrix* barcodes.

### **How to Generate a Data Matrix Barcode**
To generate *Data Matrix* barcodes it is required to create an instance of class *BarcodeGenerator* and set the *EncodeType* property to "DataMatrix". Then, the input data to be encoded need to be inserted in the *CodeText* property.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-UseEncodeModeDatamatrixbarcode-UseEncodeModeDatamatrixbarcode.cs" >}}

### **Encode Mode**
***Aspose.BarCode for .NET*** supports several types of data encoding for Data Matrix barcodes. By default, the *Auto* mode is set, indicating the encoder to choose the most appropriate encode mode that will likely produce the smallest picture under the same settings. The encoder attempts to encode two characters into a single byte. The following code snippet shows how to set the encoding mode.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-CreateEnCodeDatamatrixBarCode-CreateEnCodeDatamatrixBarCode.cs" >}}

### **Custom Encoding Mode**
***Aspose.BarCode for .NET*** supports the [Custom encode mode](https://apireference.aspose.com/barcode/net/aspose.barcode.windows.forms/barcodecontrol/properties/datamatrixencodemode) property for *Data Matrix* to enable various encoding standards, for example, such as **UTF8**. The following code snippet illustrates how to use custom encoding mode.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-CustomEncodingModeInDataMatrix-CustomEncodingModeInDataMatrix.cs" >}}

## **Create C40 Encoded Data Matrix Barcode**
***Aspose.BarCode for .NET*** supports creating Data Matrix barcodes using the *C40* encoding scheme. The following code snippet demonstrates how to create a barcode in this way.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-CreateC40DatamatrixBarCode-CreateC40DatamatrixBarCode.cs" >}}

## **Create Text Encoded Data Matrix Barcode**
***Aspose.BarCode for .NET*** enables generating *Data Matrix* barcodes using the *Text* encoding scheme. The following code snippet explains how to generate barcodes in this way.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-CreateTextDatamatrixBarCode-CreateTextDatamatrixBarCode.cs" >}}

## **Create X12 Encoded Data Matrix Barcode**
***Aspose.BarCode for .NET*** allows creating *Data Matrix* barcodes with the *X12* encoding scheme. The following code sample demonstrates how to create barcodes using this scheme.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-CreateX12DatamatrixBarCode-createX12datamatrixbarcode.cs" >}}

## **Create EDIFACT Encoded Data Matrix Barcode**
***Aspose.BarCode for .NET*** support barcode generation for the *Data Matrix* symbology using the *EDIFACT* encoding scheme that allows encoding six bits per character with four characters packed into three bytes. The following code snippet shows how to generated *EDIFACT*-encoded barcode.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-CreateAndManageTwoDBarcodes-CreateEDIFACTDatamatrixBarCode-createEDIFACTdatamatrixbarcode.cs" >}}




