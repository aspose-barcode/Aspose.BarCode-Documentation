---
title: Aspose.BarCode for Java 23.9 Release Notes
type: docs
weight: 920
url: /java/aspose-barcode-for-java-23-9-release-notes/
---

{{% alert color="primary" %}}

This page contains release notes information for [Aspose.BarCode for Java 23.9](https://downloads.aspose.com/barcode/java/new-releases/aspose.barcode-for-java-23.9/).

{{% /alert %}}
## **All Changes**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|BARCODENET-38631|Loading BMP image fails|Bug|
|BARCODENET-38678|Can’t read data matrix from the JPG image|Bug|
|BARCODENET-37507|Improve Aztec decoder|Enhancement|
|BARCODEJAVA-1701|Improve the performance of the product|Enhancement|
|BARCODEJAVA-1682|Replace the calls of java.util.Date which is discommended by java.time.LocalDateTime in all the public members|Enhancement|

## Public API changes and backwards compatibility

GS1Aztec barcode type was added to DecodeType and EncodeTypes.

New public property Aztec has been added to the BarCodeExtendedParameters of BarCodeResult with the following properties:
- StructuredAppendBarcodeId
- StructuredAppendBarcodesCount
- StructuredAppendFileId
- IsReaderInitialization

New public methods have been added to the com.aspose.barcode.generation.AztecParameters
getAztecEncodeMode():AztecEncodeMode
setAztecEncodeMode(AztecEncodeMode):void


New public methods have been added to the com.aspose.barcode.generation.AztecParameters of BarcodeParameters
getECIEncoding():int
setECIEncoding(int):void

Sample generation and recognition code:
```java
String codetext = "犬Right狗";
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.AZTEC, codetext);
generator.getParameters().getBarcode().getAztec().setECIEncoding(ECIEncodings.UTF8);
generator.save(filePath, BarCodeImageFormat.PNG);
BufferedImage image = generator.generateBarCodeImage();
BarCodeReader reader = new BarCodeReader(image, DecodeType.AZTEC);
BarCodeResult[] barCodeResults = reader.readBarCodes();
System.out.println("Codetext: " + barCodeResults[0].getCodeText());
```
New public enum AztecEncodeMode has been added with AUTO (default), BYTES and EXTENDED_CODETEXT values.
```java
//Bytes mode
byte[] encodedArr = {(byte)0xFF, (byte)0xFE, (byte)0xFD, (byte)0xFC, (byte)0xFB, (byte)0xFA, (byte)0xF9};
//encode array to string
StringBuilder strBld = new StringBuilder();
for (byte bval : encodedArr)
{
   strBld.append((char) bval);
}
String codetext = strBld.toString();
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.AZTEC, codetext);
generator.getParameters().getBarcode().getAztec().setAztecEncodeMode(AztecEncodeMode.BYTES);
generator.save(filePath + "APITests2.png", BarCodeImageFormat.PNG);

```

New public class com.aspose.barcode.generation.AztecExtCodetextBuilder has been added.
This class can be used for generating codetext for ExtendedCodetext Mode of AztecEncodeMode.

Sample generation and recognition code:
```java
//create codetext
AztecExtCodetextBuilder textBuilder = new AztecExtCodetextBuilder();
textBuilder.addECICodetext(ECIEncodings.UTF8, "犬Right狗");
textBuilder.addPlainCodetext("Plain text");

//generate codetext
String codetext = textBuilder.getExtendedCodetext();

//generate Aztec
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.AZTEC, codetext);
generator.getParameters().getBarcode().getCodeTextParameters().setTwoDDisplayText("Extended Codetext");

//set encode mode to ExtendedCodetext
generator.getParameters().getBarcode().getAztec().setAztecEncodeMode(AztecEncodeMode.EXTENDED_CODETEXT);

//try to recognize
BarCodeReader reader = new BarCodeReader(generator.generateBarCodeImage(), DecodeType.AZTEC);
for (BarCodeResult result : reader.readBarCodes())
{
  System.out.println("AztecExtendedCodetext:" + result.getCodeText());
}
```

New public methods have been added to the com.aspose.barcode.generation.AztecParameters
getStructuredAppendBarcodeId():int
setStructuredAppendBarcodeId(int):void
getStructuredAppendBarcodesCount:int
setStructuredAppendBarcodesCount(int):void
getStructuredAppendFileId():String
setStructuredAppendFileId(String):void

Sample generation and recognition code:
```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.AZTEC, "Aspose");
//set Aztec strucutured append mode
generator.getParameters().getBarcode().getAztec().setStructuredAppendBarcodeId(3);
generator.getParameters().getBarcode().getAztec().setStructuredAppendBarcodesCount(5);
generator.getParameters().getBarcode().getAztec().setStructuredAppendFileId("ABCD");
BufferedImage image = generator.generateBarCodeImage();
BarCodeReader reader = new BarCodeReader(image, DecodeType.AZTEC);
reader.readBarCodes();
System.out.println("Barcode ID: " + reader.getFoundBarCodes()[0].getExtended().getAztec().getStructuredAppendBarcodeId());
System.out.println("Barcodes count: " + reader.getFoundBarCodes()[0].getExtended().getAztec().getStructuredAppendBarcodesCount());
System.out.println("File ID: " + reader.getFoundBarCodes()[0].getExtended().getAztec().getStructuredAppendFileId());
```

New public methods have been added to the com.aspose.barcode.generation.AztecParameters
isReaderInitialization():doolean
setReaderInitialization(boolean):void

Sample generation and recognition code:
```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.AZTEC, "Aspose");
//set flag that indicates that data is encoded for reader programming
generator.getParameters().getBarcode().getAztec().setReaderInitialization(true);
BufferedImage image = generator.generateBarCodeImage();
BarCodeReader reader = new BarCodeReader(image, DecodeType.AZTEC);
reader.readBarCodes();
System.out.println("Is reader programming: " + reader.getFoundBarCodes()[0].getExtended().getAztec().isReaderInitialization());
```

New public methods have been added to the com.aspose.barcode.generation.AztecParameters
getLayersCount():int
setLayersCount(int):void
Sample generation and recognition code:
```java
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.AZTEC, "Aspose");
generator.getParameters().getBarcode().getAztec().setLayersCount(8);
BufferedImage image = generator.generateBarCodeImage();
BarCodeReader reader = new BarCodeReader(image, DecodeType.AZTEC);
reader.readBarCodes();
        System.out.println("Codetext:" + reader.getFoundBarCodes()[0].getCodeText());
```

