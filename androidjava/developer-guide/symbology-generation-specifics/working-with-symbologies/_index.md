---
title: Working with Barcode Types
type: docs
description: "Description of Various Barcode Types Supported in Aspose.BarCode for Android"
keywords: "Generate Barcodes, Barcode Types, Barcode Symbology, How to Generate Barcodes in Android, Barcode types in Aspose.BarCode for Android, 2D Barcodes, Linear Barcodes, 1D Barcode, Postal Barcodes, Generate QR, QR Code, Generate Code 39, Generate PDF417, Generate Micro QR Code, Generate Data Matrix"
ai_search_scope: "barcode_androidjava_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 10
url: /androidjava/working-with-barcode-types/

---
This article introduces general information about barcode types and describes their key properties along with providing sample barcode labels and code snippets to generate barcodes of different types. 

## **Overview**
A barcode is a graphical code composed of parallel lines and spaces of different widths or various figures combined in a visual pattern to encode data. After being generated and printed out, barcode labels get placed on scannable surfaces. Barcodes have been introduced as machine-readable tags to enable fast automatical information fetching from graphic data. A single barcode may correspond to approximately 25 characters for 1D types or 2,000 for 2D ones. The greater the number of characters to be encoded in a single barcode, the larger the generated barcode.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}
  
### **Supported Barcode Types**
All types supported in ***Aspose.BarCode for Android via Java*** are outlined below.
  
<table> 
<tr> <th></th><th></th> 
<th><p align="center"><b>Supported Barcode Types</b></p></th> 
</tr> 
<tr> <th rowspan="2">1D</th> 
<th>Numerical Only</th> 
<td>Code 11, Code 32, Codabar, DataBar Omnidirectional, DataBar Stacked Omnidirectional, DataBar Limited, DataBar Truncated, DataBar Stacked, EAN 13, EAN 14, EAN 8,
IATA 2-of-5, Italian Post 25, Interleaved 2-of-5, ISBN, ISMN, ISSN, ITF 6, ITF 14, Matrix 2-of-5, MSI, OPC, Patch Code, Pharmacode, PZN, SSCC 14, SSCC 18, 
Standard 2-of-5, EAN 5, EAN 2, UPC-A, UPC-E, UpcaGs1DatabarCoupon
</td> 
</tr> 
<tr> <th>Alpha-Numeric</th> 
<td>Code 128, Code 39, Code 93, Code 16K, CodablockF, DataBar Expanded, DataBar Expanded Stacked, GS1 CodablockF, GS1 Code 128, VIN</td> 
 </tr> 
<tr> <th colspan ="2" >2D</th> 
<td>QR Code, Micro QR Code, PDF417, Compact PDF417, Macro PDF417, Micro PDF417, Aztec Code, Data Matrix, DotCode, GS1 Data Matrix, GS1 QR Code, MaxiCode</td> 
 </tr> 
 <tr> <th colspan ="2">Postal</th> 
<td>Australia Post, AustralianPostParcel, Deutsche Post Identcode, Deutsche Post Leticode, Planet, Postnet, RM4SCC, SingaporePost, Swiss Post Parcel, USPS OneCode</td> 
 </tr> 
</tr> 
</table>
    

## **Setting Barcode Type**
***Aspose.BarCode for Android via Java*** supports nearly all widely used barcode types. In general, to generate a barcode image, it is necessary to create an instance of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/BarcodeGenerator) with two main parameters to be initialized: data contents to be encoded using the *setCodeText* method and the barcode type in the *setBarcodeType* method. The *setBarcodeType* method is used to define the type of generated barcodes. Developers can assign any options to the *setBarcodeType* property from the list of predefined barcode types supported by class [*BarcodeGenerator*](https://reference.aspose.com/barcode/androidjava/com.aspose.barcode.generation/BarcodeGenerator). However, not all types enable barcode generation with input text in a required format due to the limitations of a barcode type itself.  
  
Below, two barcode types, *Code 39* and *QR Code*, are considered as examples to demonstrate how to generate barcodes in ***Aspose.BarCode for Android via Java***. 
  
**Code 39**    
*Code 39* is a barcode type with variable length. Its specification is limited to 43 characters, including uppercase letters (A-Z), numerical digits, and some special characters (-, ., $, /, +, %, and space). Each character is decoded by nine elements: five bars and four spaces. This type has low data density and does not allow ensuring recognition accuracy as it does not require setting an obligatory checksum by default. 

<p align="center"><image src="code39extended.png"></p>
  
<!--The code snippet provided below illustrates how to generate and read *Code 39* barcodes.
  
{{< highlight java>}}

public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "Code39.png";//"path/to/image.png";
        //generate
        BarcodeGenerator bg = new BarcodeGenerator(EncodeTypes.CODE_39_EXTENDED, "123");
        {
            bg.getParameters().getBarcode().getXDimension().setPixels(4);
            try
            {
                bg.save(filePath, BarCodeImageFormat.PNG);
            }
            catch (IOException e)
            {
                e.printStackTrace();
            }
        }

        //recognize
        BarCodeReader br = new BarCodeReader(filePath, DecodeType.CODE_39_STANDARD, DecodeType.CODE_39_EXTENDED);
        BarCodeResult[] barCodeResults = br.readBarCodes();
        for (BarCodeResult result : barCodeResults)
        {
            System.out.println("CodeType: " + result.getCodeTypeName());
            System.out.println("CodeText: " + result.getCodeText());
        }
    }

{{< /highlight >}}  
-->
  
**QR Code**  
*QR Code* is a 2D type that is used to encode long strings of alphanumeric data, typically text or URL. A *QR Code* label is composed of an array of black and white squares that can be recognized by smartphones and other readers. The *QR Code* type provides high data encoding density. Moreover, it supports the **Reed-Solomon** error correction that allows not only to restore corrupted data but also to ensure correct information decoding.  

<p align="center"><image src="qrcode.png"></p>
  
<!--The code sample below can be used to create and decode *QR Codes*.  

{{< highlight java>}}

public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "qr.png";//"path/to/image.png";
        //generate
        BarcodeGenerator bg = new BarcodeGenerator(EncodeTypes.QR, "Aspose常に先を行く");
        {
            bg.getParameters().getBarcode().getXDimension().setPixels(4);
            bg.getParameters().getBarcode().getQR().setQrEncodeType(QREncodeType.FORCE_QR);
            bg.getParameters().getBarcode().getQR().setQrEncodeMode(QREncodeMode.ECI_ENCODING);
            bg.getParameters().getBarcode().getQR().setQrErrorLevel(QRErrorLevel.LEVEL_L);
            bg.getParameters().getBarcode().getQR().setQrECIEncoding(ECIEncodings.UTF8);
            bg.getParameters().getBarcode().getQR().setQrVersion(QRVersion.VERSION_05);
            try
            {
                bg.save(filePath, BarCodeImageFormat.PNG);
            }
            catch (IOException e)
            {
                e.printStackTrace();
            }
        }

        //recognize
        BarCodeReader br = new BarCodeReader(filePath, DecodeType.QR);
        BarCodeResult[] barCodeResults = br.readBarCodes();
        for(BarCodeResult result : barCodeResults)
        {
            System.out.println("CodeType: " + result.getCodeTypeName());
            System.out.println("CodeText: " + result.getCodeText());
        }
    }

{{< /highlight >}} 
-->

## **Data Encoding Formats**
<a name="dataencoding"></a>

Different types have different underlying data encoding approaches and capabilities. Accordingly, barcode label size and the amount of data to be encoded are predefined for each type. Some barcode types allow encoding only digits or a limited set of characters and digits, while others can accept any byte sequence without limitations.  
Further in the article, several barcode types (*EAN 13*, *Code 11*, *GS1 Code 128*, and *PDF417*) with different data densities are presented as examples.   

**EAN 13**  
*EAN 13* barcodes can encode only numerical digits. Specifically, the *EAN 13* data encoding format requires encoding precisely 12 digits with the 13th one used as a control sum calculated according to the specified algorithm. 
  
<p align="center"><image src="ean13.png"></p>

<!--The following code snippet explains how to generate *EAN13* barcodes.
  
{{< highlight java>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.EAN13, "1234567890128");
gen.Parameters.Barcode.XDimension.Pixels = 2;
gen.Save($"{path}Ean13.png", BarCodeImageFormat.Png);
{{< /highlight >}}--> 
  
**Code 11**  
*Code 11* allows encoding a string of any length (theoretically, unlimited), including numerical digits and the dash sign (-).
  
<p align="center"><image src="code11.png"></p>
  
<!--The following code sample demonstrates how to create a *Code 11* barcode.
  
{{< highlight java>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code11, "1234-5678");
gen.Save($"{path}Code11.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
  
**GS1 Code 128**  
*GS1 Code 128* can encode any of ASCII alphanumeric characters similarly to the basic *Code 128* type. However, in *GS1 Code 128*, the data encoding format is defined strictly according to the GS1 standards.  
  
<p align="center"><image src="gs1code128.png"></p>
  
<!--The code example provided below can be used to generate a *GS1 Code128* barcode.
  
{{< highlight java>}}
public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "Code128.png";//"path/to/image.png";
        //generate
        BarcodeGenerator bg = new BarcodeGenerator(EncodeTypes.CODE_128, "Aspose");
        {
            bg.getParameters().getBarcode().getXDimension().setPixels(2);
            try
            {
                bg.save(filePath, BarCodeImageFormat.PNG);
            }
            catch (IOException e)
            {
                e.printStackTrace();
            }
        }

        //recognize
        BarCodeReader br = new BarCodeReader(filePath, DecodeType.CODE_128);
        BarCodeResult[] barCodeResults = br.readBarCodes();
        for (BarCodeResult result : barCodeResults)
        {
            System.out.println("CodeType: " + result.getCodeTypeName());
            System.out.println("CodeText: " + result.getCodeText());
        }
    }
{{< /highlight >}}
-->

**PDF417**  
The *PDF417* barcode is a 2D high-density type that is capable of encoding any sequence of bytes, including text, numbers, files, and actual data bytes. It supports the Reed-Solomon error correction and thus provides high recognition accuracy.
  
<p align="center"><image src="pdf417.png"></p>
  
<!--The following code snippet illustrates how to generate and read *PDF417* barcodes.
  
{{< highlight java>}}

public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "BasicPDF417.png";//"path/to/image.png";
        //generate
        BarcodeGenerator bg = new BarcodeGenerator(EncodeTypes.PDF_417, "Aspose");
        {
            bg.getParameters().getBarcode().getXDimension().setPixels(2);
            bg.getParameters().getBarcode().getPdf417().setColumns(3);
            //set error level 2
            bg.getParameters().getBarcode().getPdf417().setPdf417ErrorLevel(Pdf417ErrorLevel.LEVEL_2);
            try
            {
                bg.save(filePath, BarCodeImageFormat.PNG);
            }
            catch (IOException e)
            {
                e.printStackTrace();
            }
        }

        //recognize
        BarCodeReader br = new BarCodeReader(filePath, DecodeType.PDF_417,DecodeType.COMPACT_PDF_417,DecodeType.MACRO_PDF_417);
        BarCodeResult[] barCodeResults = br.readBarCodes();
        for (BarCodeResult result : barCodeResults)
        {
            System.out.println("CodeType: " + result.getCodeTypeName());
            System.out.println("CodeText: " + result.getCodeText());
        }
    }

{{< /highlight >}} 
-->

## **Data Density**
<a name="datadensity"></a>
Data density is one of the most important properties of barcode types. It defines how much information can be encoded in a single barcode. It is low for 1D barcodes and considerably high for 2D matrix barcode types. The difference in data density for 2D and 1D types can exceed 10 times.
The barcode types discussed below, *Code93* and *Data Matrix*, are provided as examples of barcode types with different density values.  

**Code 93**  
*Code 93* is a more secure and compact version of *Code 39* that can encode both alphabet characters and numerical digits. *Code 93* has quite low data density; therefore, with respect to other types, it requires generating larger barcodes to encode the same amounts of information.  
  
<p align="center"><image src="code93extended.png"></p>
  
<!--The following code sample shows how to generate a *Code93* barcode.
  
{{< highlight java>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Code93Extended, "$&This Code#*");
gen.Save($"{path}Code93Extended.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->

**Data Matrix**  
*Data Matrix* is a 2D code that allows encoding large amounts of data in a compact space. A single *Data Matrix* can contain up to 2,335 alphanumeric or 3,116 numerical characters. This is 10 times greater than the standard data density of 1D barcodes.
  
<p align="center"><image src="datamatrix.png"></p>

<!--The code example below can be used to create and recognize *Data Matrix* barcodes.  

{{< highlight java>}}
public void generateAndReadDataMatrix()
    {
        String filePath = Global.getTestDataFolder("cards") + "DataMatrix.png";//"path/to/image.png";
        //generate
        BarcodeGenerator bg = new BarcodeGenerator(EncodeTypes.DATA_MATRIX, "Åspóse.Barcóde©");
        {
            bg.getParameters().getBarcode().getXDimension().setPixels(4);
            bg.getParameters().getBarcode().getDataMatrix().setDataMatrixEcc(DataMatrixEccType.ECC_200);
            bg.getParameters().getBarcode().getDataMatrix().setDataMatrixVersion(DataMatrixVersion.ECC200_22x22);
            try
            {
                bg.save(filePath, BarCodeImageFormat.PNG);
            }
            catch (IOException e)
            {
                e.printStackTrace();
            }
        }

        //recognize
        BarCodeReader br = new BarCodeReader(filePath, DecodeType.DATA_MATRIX);
        BarCodeResult[] barCodeResults = br.readBarCodes();
        for (BarCodeResult result : barCodeResults)
        {
            System.out.println("CodeType: " + result.getCodeTypeName());
            System.out.println("CodeText: " + result.getCodeText());
        }
    }
{{< /highlight >}}
-->

## **Barcode Shapes**
<a name="shape"></a>
In general, the surfaces to place printed barcodes can have various shapes. At the same time, barcodes can be of rectangular or square forms only. Accordingly, if there is a large space to put a rectangular barcode, the generation of a square-shaped barcode is unacceptable from the viewpoint of space usage.  
Further, two barcode types, *Micro QR Code* and *Compact PDF417*, are considered as examples of barcodes with different shapes. 

**Micro QR Code**  
*Micro QR Code* provides large data density; however, it has a square shape and thus needs square space to be placed. A major feature of *MicroQR* is that it has only one position detection pattern instead of three ones for regular *QR Code* and requires a more compact placement area.
  
<p align="center"><image src="microqr.png"></p>
  
<!--The following code snippet illustrates how to generate and read *Micro QR Codes*.
  
{{< highlight java>}}


public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "MicroQRCode.png";//"path/to/image.png";
        //generate
        BarcodeGenerator bg = new BarcodeGenerator(EncodeTypes.QR, "Aspose");
        {
            bg.getParameters().getBarcode().getXDimension().setPixels(4);
            bg.getParameters().getBarcode().getQR().setQrEncodeType(QREncodeType.FORCE_MICRO_QR);
            bg.getParameters().getBarcode().getQR().setQrErrorLevel(QRErrorLevel.LEVEL_L);
            bg.getParameters().getBarcode().getQR().setQrECIEncoding(ECIEncodings.UTF8);
            bg.getParameters().getBarcode().getQR().setQrVersion(QRVersion.VERSION_M4);
            try
            {
                bg.save(filePath, BarCodeImageFormat.PNG);
            }
            catch (IOException e)
            {
                e.printStackTrace();
            }
        }

        //recognize
        BarCodeReader br = new BarCodeReader(filePath, DecodeType.MICRO_QR);
        BarCodeResult[] barCodeResults = br.readBarCodes();
        for(BarCodeResult result : barCodeResults)
        {
            System.out.println("CodeType: " + result.getCodeTypeName());
            System.out.println("CodeText: " + result.getCodeText());
        }
    }

{{< /highlight >}}
-->
  
**Compact PDF417**    
*Compact PDF417* can be used when space limitations are the main concern and barcode damage is unlikely. It has less data density compared with other 2D barcodes; however, owing to its property to have a length 64 times larger than height, it is more suitable for narrow rectangular areas with size limitations.
  
<p align="center"><image src="compactpdf417.png"></p>
  
<!--The code sample below can be used to create and recognize *Compact PDF417* barcodes.
  
{{< highlight java>}}

public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "CompactPDF417.png";//"path/to/image.png";
        //generate
        BarcodeGenerator bg = new BarcodeGenerator(EncodeTypes.PDF_417, "Aspose");
        {
            bg.getParameters().getBarcode().getXDimension().setPixels(2);
            //set Pdf417 truncated or Compact Pdf417
            bg.getParameters().getBarcode().getPdf417().setPdf417Truncate(true);
            //set 3 columns
            bg.getParameters().getBarcode().getPdf417().setColumns(3);
            //set error level 2
            bg.getParameters().getBarcode().getPdf417().setPdf417ErrorLevel(Pdf417ErrorLevel.LEVEL_2);
            try
            {
                bg.save(filePath, BarCodeImageFormat.PNG);
            }
            catch (IOException e)
            {
                e.printStackTrace();
            }
        }

        //recognize
        BarCodeReader br = new BarCodeReader(filePath, DecodeType.PDF_417,DecodeType.COMPACT_PDF_417,DecodeType.MACRO_PDF_417);
        BarCodeResult[] barCodeResults = br.readBarCodes();
        for (BarCodeResult result : barCodeResults)
        {
            System.out.println("CodeType: " + result.getCodeTypeName());
            System.out.println("CodeText: " + result.getCodeText());
        }
    }

{{< /highlight >}} 
-->

## **Barcode Recognition Precision**
<a name="precision"></a>
In some cases, the data fetched after barcode recognition may be incorrect. Generally, 1D barcodes do not include a checksum or contain only simple controls; accordingly, this may result in reading erroneous data from barcodes. In turn, the majority of 2D barcodes rely on the Reed-Solomon error correction, which allows ensuring correct barcode recognition and partially recovering the data from damaged barcodes.  
The types outlined below, *Interleaved 2-of-5* and *Aztec Code*, are considered as examples of barcode types with different recognition accuracy.
  
**Interleaved 2-of-5**  
*Interleaved 2-of-5* can encode sequences of digits of any length as long as such a sequence contains an even number of digits. By default, it does not require setting a checksum and thus can be read with errors.
  
<p align="center"><image src="interleaved2of5.png"></p>
  
<!--The following code example describes how to generate *Interleaved 2-of-5* barcodes.
  
{{< highlight java>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Interleaved2of5, "1234567890");
gen.Save($"{path}Interleaved2of5.png", BarCodeImageFormat.Png);
{{< /highlight >}}-->
  
**Aztec Code**  
*Aztec Code* is a highly efficient 2D type that uses square modules with a unique finder pattern in the middle of a barcode, which allows barcode scanners to identify cell locations required for barcode reading. This barcode type not only enables encoding any sequence of bytes but also ensures correct data recognition.
  
<p align="center"><image src="aztecfull.png"></p>
  
<!--The code snippet given below shows how to generate and recognize *Aztec Code* barcodes.
  
{{< highlight java>}}

public void generateAndRead()
    {
        String filePath = Global.getTestDataFolder("cards") + "AztecFullRange.png";//"path/to/image.png";
        //generate
        BarcodeGenerator bg = new BarcodeGenerator(EncodeTypes.AZTEC, "Åspóse.Barcóde©");
        {
            bg.getParameters().getBarcode().getXDimension().setPixels(4);
            //set symbol mode FullRange
            bg.getParameters().getBarcode().getAztec().setAztecSymbolMode(AztecSymbolMode.FULL_RANGE);
            //set error correction capacity to 10% (can be from 5% to 95%)
            bg.getParameters().getBarcode().getAztec().setAztecErrorLevel(10);
            try
            {
                bg.save(filePath, BarCodeImageFormat.PNG);
            }
            catch (IOException e)
            {
                e.printStackTrace();
            }
        }

        //recognize
        BarCodeReader br = new BarCodeReader(filePath, DecodeType.AZTEC);
        BarCodeResult[] barCodeResults = br.readBarCodes();
        for (BarCodeResult result : barCodeResults)
        {
            System.out.println("CodeType: " + result.getCodeTypeName());
            System.out.println("CodeText: " + result.getCodeText());
        }
    }
    
{{< /highlight >}}
-->
  
## **Postal Barcodes** 
Postal symbologies correspond to the specific industrial barcode types that are used only for the needs of postal services. They have much lower data density compared with 2D barcodes and are capable of encoding limited sets of characters, mainly, only numerical ones. Unlike traditional barcodes, postal types usually vary the height of bars to encode information. At present, postal services tend to replace specified postal types with widely used 2D barcodes. However, this transition process cannot be completed immediately; therefore, ***Aspose.Barcode for Android via Java*** supports the most widely used postal types in addition to 1D and 2D ones.

**Postnet**  
*Postnet* allows encoding only digits corresponding to ZIP or ZIP+4 codes in half- and full-height bars; its parameters are similar to those of 1D barcodes. In this barcode type, each digit is encoded by a set of five bars, two of which are of full height.
Two type considered below, *Postnet* and *RM4SCC*, are provided as examples of postal barcodes supported in ***Aspose.Barcode for Android via Java***. 
<p align="center"><image src="postnet.png"></p>
  
<!--The following code example illustrates how to generate a *Postnet* barcode.
  
{{< highlight java>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Postnet, "1159628792");
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}Postnet.png", BarCodeImageFormat.Png);
{{< /highlight >}}--> 

**RM4SCC**  
*RM4SCC* is capable of encoding only digits and English alphabet capital characters. Its parameters are similar to those of 1D barcodes. In this barcode type, each character corresponds to four bars so that two of them are extended upwards and the other two - downwards. The combination of such bars with variable height provides combinations to encode 36 possible characters: 10 numerical and 26 alphabetical ones.
  
<p align="center"><image src="rm4scc.png"></p>

<!--The code snippet given below shows how to generate a *Postnet* barcode.
   
{{< highlight java>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.RM4SCC, "N101HU9Z");
gen.Parameters.Barcode.XDimension.Pixels = 3;
gen.Save($"{path}RM4SCC.png", BarCodeImageFormat.Png);
{{< /highlight >}}--> 


