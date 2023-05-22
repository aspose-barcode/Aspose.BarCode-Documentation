---
title: Aspose.BarCode for Reporting Services 23.5 Release Notes
type: docs
weight: 20
url: /reportingservices/aspose-barcode-for-reporting-services-23-5-release-notes/
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.BarCode for Reporting Services 23.5](https://downloads.aspose.com/barcode/reportingservices/new-releases/aspose.barcode-for-reporting-services-23.5/).

{{% /alert %}} 
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-38462|Add support of Han Xin Code to Aspose.Barcode|Enhancement|

## **Public API and Backward Incompatible Changes**

- Added property Aspose.BarCode.ReportingServices.BarcodeRSUI.HanXin
- Added class Aspose.BarCode.ReportingServices.HanXinRSUI
- Added property Aspose.BarCode.ReportingServices.HanXinRSUI.HanXinECIEncoding
- Added property Aspose.BarCode.ReportingServices.HanXinRSUI.HanXinEncodeMode
- Added property Aspose.BarCode.ReportingServices.HanXinRSUI.HanXinErrorLevel
- Added property Aspose.BarCode.ReportingServices.HanXinRSUI.HanXinVersion		

```cs
// ECI mode
var codetext = "ΑΒΓΔΕ";
using (var generator = new BarcodeGenerator(EncodeTypes.HanXin, codetext))
{
    generator.Parameters.Barcode.HanXin.HanXinEncodeMode = HanXinEncodeMode.ECI;
    generator.Parameters.Barcode.HanXin.HanXinECIEncoding = ECIEncodings.ISO_8859_7;
    generator.Save("test.bmp");
}

// Unicode mode
var codetext = "abcd АБВ ıntəˈnæʃənəl テスト 안녕하세요 테스트 테스트";
using (var generator = new BarcodeGenerator(EncodeTypes.HanXin, codetext))
{
    generator.Parameters.Barcode.HanXin.HanXinEncodeMode = HanXinEncodeMode.Unicode;
    generator.Save("test.bmp");
}

// URI mode
var codetext = "https://www.test.com/%BC%DE%%%ab/search=test";
using (var generator = new BarcodeGenerator(EncodeTypes.HanXin, codetext))
{
    generator.Parameters.Barcode.HanXin.HanXinEncodeMode = HanXinEncodeMode.URI;
    generator.Save("test.bmp");
}
```