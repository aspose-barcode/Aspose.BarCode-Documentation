---
title: Get Product Name and DLL Version
type: docs
description: "How to Obtain the Information about Product Name and DLL Version"
keywords: "Aspose Barcode, aspose barcode library, aspose version, aspose dll version, aspose c# version"
weight: 20
feedback: BARCODECOM
notoc: true
url: /net/get-product-name-and-dll/
aliases: [/net/get-the-product-name-and-dll-version-information/]
---

The system information about the ***Aspose.BarCode*** library can be obtained using structure [*BuildVersionInfo*](https://reference.aspose.com/barcode/net/aspose.barcode/buildversioninfo/) that provides the following data:
- Assembly version
- File version
- Product title
- Major product version
- Minor product version
- Product release date
  
The following code sample illustrates how to implement this feature.
  
{{< highlight csharp>}}
//the code shows the system information about Aspose.BarCode dll
Console.WriteLine("Assembly version: " + BuildVersionInfo.AssemblyVersion);
Console.WriteLine("File Version: " + BuildVersionInfo.FileVersion);
Console.WriteLine("Product: " + BuildVersionInfo.Product);
Console.WriteLine("Product Major: " + BuildVersionInfo.ProductMajor);
Console.WriteLine("Product Minor: " + BuildVersionInfo.ProductMinor);
Console.WriteLine("Release Date: " + BuildVersionInfo.ReleaseDate);
{{< /highlight >}}

