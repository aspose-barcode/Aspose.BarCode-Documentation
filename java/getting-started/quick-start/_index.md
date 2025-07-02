---
title: Quick Start - Code Examples
type: docs
weight: 80
feedback: BARCODECOM
url: /java/quick-start
---


## **How to read barcodes on image**
{{<highlight java>}}
    public void recognitionExample() throws Exception
    {
        String fileName = "code128.gif";
        String licensePath =  "Aspose.BarCode.Java.lic";
        License license = new License();
        license.setLicense(licensePath);
        BarCodeReader reader = new BarCodeReader(fileName, DecodeType.CODE_128);
        BarCodeResult[] barCodeResults = reader.readBarCodes();
        for (BarCodeResult barCodeResult : barCodeResults)
        {
            System.out.println("Code Type : " + barCodeResult.getCodeTypeName());
            System.out.println("Code Text : " + barCodeResult.getCodeText());
    }
}
{{</highlight>}}

## **How to generate barcode and save to the file**
{{<highlight java>}}
    public void generationExample() throws Exception
    {
        String licensePath =  "Aspose.BarCode.Java.lic";
        License license = new License();
        license.setLicense(licensePath);
        String codeText = "01234567";
        SymbologyEncodeType encodeType = EncodeTypes.QR;
        BarcodeGenerator generator = new BarcodeGenerator(encodeType, codeText);
        String pathToFile = folder + "qr.png";
        generator.save(pathToFile);
        BarCodeReader reader = new BarCodeReader(pathToFile, DecodeType.QR);
        BarCodeResult[] barCodeResults = reader.readBarCodes();
        for (BarCodeResult barCodeResult : barCodeResults)
        {
            System.out.println("Code Type : " + barCodeResult.getCodeTypeName());
            System.out.println("Code Text : " + barCodeResult.getCodeText());
        }
    }
{{</highlight>}}

## **How to generate barcode and read complex barcode**
{{<highlight java>}}
public void generationAndReadComplexBarcodeExample() throws Exception
{
    String licensePath = Global.getTestDataFolder("License/sha256/Aspose/Java/Aspose.BarCode.Java.256.lic");
    License license = new License();
    license.setLicense(licensePath);
    Mailmark2DCodetext mailmark2DCodetext = new Mailmark2DCodetext();
    mailmark2DCodetext.setUPUCountryID("JGB ");
    mailmark2DCodetext.setInformationTypeID("0");
    mailmark2DCodetext.setVersionID("1");
    mailmark2DCodetext.setclass("1");
    mailmark2DCodetext.setSupplyChainID(123);
    mailmark2DCodetext.setItemID(1234);
    mailmark2DCodetext.setDestinationPostCodeAndDPS("QWE1");
    mailmark2DCodetext.setRTSFlag("0");
    mailmark2DCodetext.setReturnToSenderPostCode("QWE2");
    mailmark2DCodetext.setDataMatrixType(Mailmark2DType.TYPE_29);
    mailmark2DCodetext.setCustomerContent("CUSTOM_DATA");
    ComplexBarcodeGenerator cg = new ComplexBarcodeGenerator(mailmark2DCodetext);
    BufferedImage res = cg.generateBarCodeImage();
    BarCodeReader barCodeReader = new BarCodeReader(res, DecodeType.DATA_MATRIX);
    {
        System.out.println("Found barcodes: " + barCodeReader.readBarCodes().length);
        Mailmark2DCodetext mailmark2DCodetextActual = ComplexCodetextReader.tryDecodeMailmark2D(barCodeReader.getFoundBarCodes()[0].getCodeText());
        System.out.println("Codetext: " + mailmark2DCodetextActual.getConstructedCodetext());
    }
}
{{</highlight>}}

## **How to Work with Non-ASCII Symbols**
This example demonstrates how to generate and read a PDF417 barcode containing non-ASCII text.
{{<highlight java>}}
    ByteArrayOutputStream outputStream = new ByteArrayOutputStream();
    BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.PDF_417);
    gen.setCodeText("sýkora je malý pták", StandardCharsets.UTF_8);
    gen.save(outputStream, BarCodeImageFormat.PNG);
    BarCodeReader reader = new BarCodeReader(new ByteArrayInputStream(outputStream.toByteArray()), DecodeType.PDF_417);
    BarCodeResult[] results = reader.readBarCodes();
    System.out.printf("Code Type: %s%n", results[0].getCodeTypeName());
    System.out.printf("Code Text: %s%n", results[0].getCodeText(StandardCharsets.UTF_8));

{{</highlight>}}
