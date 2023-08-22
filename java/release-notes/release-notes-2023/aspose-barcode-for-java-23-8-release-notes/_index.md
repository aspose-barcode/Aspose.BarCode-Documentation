---
title: Aspose.BarCode for Java 23.8 Release Notes
type: docs
weight: 930
url: /java/aspose-barcode-for-java-23-8-release-notes/
---

{{% alert color="primary" %}}

This page contains release notes information for [Aspose.BarCode for Java 23.8](https://downloads.aspose.com/barcode/java/new-releases/aspose.barcode-for-java-23.8/).

{{% /alert %}}
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-38666|Fix decreased performance of DataMatrix recognition|Bug|
|BARCODENET-38536|Code throws System.IndexOutOfRangeException with empty string|Bug|
|BARCODENET-37518|Improve Micro PDF417 reader|Enhancement|
|BARCODENET-37840|Replace color binarization algorithm|Enhancement|
|BARCODENET-38584|Improve Han Xin Code support|Enhancement|
|BARCODENET-38591|Improve DataMatrix Industrial recognition engine|Enhancement|

## Public API changes and backwards compatibility

Added:

- method com.aspose.barcode.barcoderecognition.QualitySettings.getAllowAdditionalRestorations():boolean
- method com.aspose.barcode.barcoderecognition.QualitySettings.setAllowAdditionalRestorations(boolean)
- method com.aspose.barcode.barcoderecognition.Pdf417ExtendedParameters.isReaderInitialization():boolean
- class  Aspose.BarCode.Generation.HanXinExtCodetextBuilder
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.#ctor
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.addECI(String,int)
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.addAuto(String)
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.addBinary(String)
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.addURI(String)
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.addText(String)
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.addNumeric(String)
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.addUnicode(String)
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.addCommonChineseRegionOne(String)
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.addCommonChineseRegionTwo(String)
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.addGB18030TwoByte(String)
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.addGB18030FourByte(String)
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.addGS1(String)
- method Aspose.BarCode.Generation.HanXinExtCodetextBuilder.getExtendedCodetext

```Java
// Extended Mode with HanXinExtCodetextBuilder
 HanXinExtCodetextBuilder codeTextBuilder = new HanXinExtCodetextBuilder();
 codeTextBuilder.addGB18030TwoByte("漄");
 codeTextBuilder.addGB18030FourByte("㐁");
 codeTextBuilder.addCommonChineseRegionOne("全");
 codeTextBuilder.addCommonChineseRegionTwo("螅");
 codeTextBuilder.addNumeric("123");
 codeTextBuilder.addText("qwe");
 codeTextBuilder.addUnicode("ıntəˈnæʃənəl");
 codeTextBuilder.addECI("ΑΒΓΔΕ", 9);
 codeTextBuilder.addAuto("abc");
 codeTextBuilder.addBinary("abc");
 codeTextBuilder.addURI("backslashes_should_be_doubled\000555:test");
 codeTextBuilder.addGS1("(01)03453120000011(17)191125(10)ABCD1234(21)10");
 String str = codeTextBuilder.getExtendedCodetext();
 String expectedStr = "漄㐁全螅123qweıntəˈnæʃənəlΑΒΓΔΕabcabcbackslashes_should_be_doubled\000555:test(01)03453120000011(17)191125(10)ABCD1234(21)10";

 //generate
 BarcodeGenerator bg = new BarcodeGenerator(EncodeTypes.HAN_XIN, str);
 bg.getParameters().getBarcode().getHanXin().setHanXinEncodeMode(HanXinEncodeMode.EXTENDED);
 BufferedImage img = bg.generateBarCodeImage();
 BarCodeReader r = new BarCodeReader(img, DecodeType.HAN_XIN))
 BarcodeResult[] found = r.readBarCodes();
 Assert.assertEquals(1, found.length);
 Assert.assertEquals(expectedStr, found[0].getCodeText());
```
