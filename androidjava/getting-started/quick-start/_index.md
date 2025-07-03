---
title: Quick Start
type: docs
weight: 80
feedback: BARCODECOM
url: /androidjava/quick-start
---

This section provides quick code samples to help you get started with barcode 
generation and recognition using Aspose.BarCode for Android via Java.

## **How to Read Barcodes from an Image**
This example demonstrates how to recognize a Code 128 barcode from an image file.

{{<highlight java>}}
    String fileName = folder + "code_128.gif";
    String licensePath = "Aspose.BarCode.Android.Java.lic");
    License license = new License();
    license.setLicense(licensePath);
    BarCodeReader reader = new BarCodeReader(fileName, DecodeType.CODE_128);
    BarCodeResult[] barCodeResults = reader.readBarCodes();
    for (BarCodeResult barCodeResult : barCodeResults)
    {
    Log.d("Quick Start","Code Type : " + barCodeResult.getCodeTypeName());
    Log.d("Quick Start","Code Text : " + barCodeResult.getCodeText());
    }
{{</highlight>}}
## **How to Read Barcodes from a Stream**
This example demonstrates how to recognize a Code 128 barcode from a stream.

{{< highlight java >}}
    String licensePath =  "Aspose.BarCode.Java.lic";
    License license = new License();
    license.setLicense(licensePath);
    String filePath = folderPath + "image.png";
    try (FileInputStream fileStream = new FileInputStream(filePath))
    {
        BarCodeReader reader = new BarCodeReader(fileStream);
        for (BarCodeResult result : reader.readBarCodes())
        {
        System.out.printf("Symbology Type: %s%n", result.getCodeType());
        System.out.printf("CodeText: %s%n", result.getCodeText());
        }
    }
    catch (IOException e)
    {
        e.printStackTrace();
    }
{{< /highlight >}}

## **How to Generate a Barcode and Save to a File**
This example shows how to generate a QR code and save it as a PNG file.

{{<highlight java>}}
    String licensePath = "Aspose.BarCode.Android.Java.lic";
    License license = new License();
    license.setLicense(licensePath);
    String codeText = "01234567";
    SymbologyEncodeType encodeType = EncodeTypes.QR;
    BarcodeGenerator generator = new BarcodeGenerator(encodeType, codeText);
    Context context = InstrumentationRegistry.getInstrumentation().getTargetContext();
    File imageFile = new File(context.getFilesDir(), "qr.png");
    String pathToFile = imageFile.getPath();
    generator.save(pathToFile);
    Log.d("QuickStart", "Barcode saved to " + pathToFile);
    BarCodeReader reader = new BarCodeReader(pathToFile, DecodeType.QR);
    BarCodeResult[] barCodeResults = reader.readBarCodes();
    for (BarCodeResult barCodeResult : barCodeResults)
    {
        Log.d("Quick Start","Code Type : " + barCodeResult.getCodeTypeName());
        Log.d("Quick Start","Code Text : " + barCodeResult.getCodeText());
    }
{{</highlight>}}

## **How to Generate and Read a Complex Barcode**
This example demonstrates how to generate and read a complex Mailmark 2D barcode.
{{<highlight java>}}
    String licensePath = "Aspose.BarCode.Android.Java.lic";
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
    Bitmap bitmap = cg.generateBarCodeImage();
    BarCodeReader barCodeReader = new BarCodeReader(bitmap, DecodeType.DATA_MATRIX);
    Log.d("Quick Start", "Found barcodes: " + barCodeReader.readBarCodes().length);
    Mailmark2DCodetext mailmark2DCodetextActual = ComplexCodetextReader.tryDecodeMailmark2D(barCodeReader.getFoundBarCodes()[0].getCodeText());
    Log.d("Quick Start","Codetext: " + mailmark2DCodetextActual.getConstructedCodetext());
{{</highlight>}}

## **How to Work with Non-ASCII Symbols**
This example demonstrates how to generate and read a PDF417 barcode containing non-ASCII text.
{{<highlight java>}}
    String licensePath =  "Aspose.BarCode.Java.lic";
    License license = new License();
    license.setLicense(licensePath);
    ByteArrayOutputStream outputStream = new ByteArrayOutputStream();
    BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.PDF_417);
    gen.setCodeText("sýkora je malý pták", StandardCharsets.UTF_8);
    gen.save(outputStream, BarCodeImageFormat.PNG);
    BarCodeReader reader = new BarCodeReader(new ByteArrayInputStream(outputStream.toByteArray()), DecodeType.PDF_417);
    BarCodeResult[] results = reader.readBarCodes();
    for (BarCodeResult result : results)
    {
        Log.d("Quick Start","Code Type : " + result.getCodeTypeName());
        Log.d("Quick Start","Code Text : " + result.getCodeText(StandardCharsets.UTF_8));
    }
{{</highlight>}}



