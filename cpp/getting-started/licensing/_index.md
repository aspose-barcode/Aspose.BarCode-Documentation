---
title: Licensing
type: docs
weight: 50
url: /cpp/licensing/
---

## **Evaluation Version Limitations**
An evaluation version of Aspose.Barcode for C++ can be downloaded from the downloads section of Aspose's web site at <https://releases.aspose.com/barcode/cpp>.
Or you can use [NuGet package](https://www.nuget.org/packages/Aspose.barcode.Cpp/) in your application.
Only Code39 barcodes could be created or recognized in this mode without limitations.
For other types of barcodes evaluation watermark will be added on generated barcodes and part of the recognized text will be returned.

## **Licensing**
You could request a [Temporary License](https://purchase.aspose.com/temporary-license) to test full Aspose.BarCode for C++ functionality.
Check the pricing information and purchase a full license at <https://purchase.aspose.com/pricing/barcode/cpp>.

## **Apply License using File or Stream Object**
The license can be loaded from a file or stream object. Aspose.Barcode for C++ will try to find the license in the following locations:

- Explicit path
- Current working directory

The easiest way to set a license is to put the license file in the folder you start your application from and specify the file name, without a path, as shown in the example below.
### **Loading a License from File**

{{% alert color="primary" %}}

When you call the SetLicense method, the license name that you pass should be that of the license file. For example, if you change the license file name to "Aspose.Barcode.lic.xml", pass that file name to the License::SetLicense(…) method.

{{% /alert %}}

{{< highlight cpp >}}

auto license = System::MakeObject<License>();

license->SetLicense(u"Aspose.BarCode.CPP.lic");

{{< /highlight >}}
### **Loading a License from a Stream Object**
The following example shows how to load a license from a stream.

{{< highlight cpp >}}

auto license = System::MakeObject<License>();

auto licenseStream = System::MakeObject<System::IO::FileStream>(u"Aspose.BarCode.CPP.lic", System::IO::FileMode::Open);    
    
license->SetLicense(licenseStream);

{{< /highlight >}}


