---
title: DotCode Barcodes
type: docs
weight: 190
url: /net/dotcode/
---

## **Overview**
DotCode is a 2D barcode type used to ensure accurate barcode reading and decoding for barcodes created with high-speed inkjet or laser printing.  
Main features of DotCode include the following:
-	Can encode both textual data and streams of bytes
-	Supports Reed-Solomon error correction
-	Maximal encoding capacity is not limited meaning that the size of input data is variable
-	Supports ECI
-	Supports the structured append mechanism to combine data stored in different barcodes
-	Supports the division of the data encoded in a single barcode into several messages


{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Set DotCode Layout**
To generate DotCode barcodes with the predefined layout, it is necessary to initialize [*Rows*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeparameters/rows/) and [*Columns*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeparameters/columns/) properties of class [*DotCodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeparameters/).
The DotCode standard sets the following restrictions on the number of rows and columns:
-	the minimal number of rows or columns is 5. To improve recognition quality, it is recommended to set at least 7 rows and columns,
-	Sum of the numbers of rows and columns in a DotCode barcode must be an odd number.
It is also possible to define the odd number of rows or columns only. In this case, the second layout parameter will be set automatically. If the manually specified number of rows and columns is not enough to generate a DotCode barcode, an exception will be thrown.  
  
| |12 Rows|18 Columns|26 Rows and 29 Columns|
|--|--|--|--|
| |<p align="center"><img src="dotcoderows12.png" width="40%" height="40%"></p>|<p align="center"><img src="dotcodecolumns18.png" width="40%" height="40%"></p>|<p align="center"><img src="dotcoderows26columns29.png" width="40%" height="40%"></p>|
  
The following code sample explains how to set the layout for a generated DotCode barcode.

``` csharp
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DotCode, "Aspose"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 10;
    //set columns 18
    gen.Parameters.Barcode.DotCode.Columns = 18;
    gen.Save($"{path}DotCodeColumns18.png", BarCodeImageFormat.Png);
    //set rows 12
    gen.Parameters.Barcode.DotCode.Columns = -1;
    gen.Parameters.Barcode.DotCode.Rows = 12;
    gen.Save($"{path}DotCodeRows12.png", BarCodeImageFormat.Png);
    //set rows 20 columns 29
    gen.Parameters.Barcode.DotCode.Columns = 29;
    gen.Parameters.Barcode.DotCode.Rows = 26;
    gen.Save($"{path}DotCodeRows26Columns29.png", BarCodeImageFormat.Png);
}

```

## **Set Encoding Mode**
The barcode library supports three different encoding modes to generate DotCode barcodes. These modes are briefly described below:
- *Auto*. The data is processed using the encoding specified in the [*ECIEncoding*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeparameters/eciencoding/) property. By default, ISO-8859-1 is used.
- *Bytes*. This mode is intended to encode streams of bytes. If the input text contains a Unicode symbol, it will be encoded with two bytes.
- *ExtendedCodetext*. Besides the main input data, information passed to the [*Codetext*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/codetext/) property includes special control words. These words provide extended controls over the data encoding process and allow inserting textual parts with different encodings into a single barcode. 
To set the required encoding mode, it is necessary to initialize the [*DotCodeEncodeMode*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeparameters/dotcodeencodemode/) of class [*DotCodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeparameters/).

### ***Auto* Encoding Mode**
In the *Auto* encoding mode, the barcode data is encoded using the value passed to the [*ECIEncoding*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeparameters/eciencoding/) property. The ISO-8859-1 encoding is applied by default. The following code sample shows how to generate DotCode barcode in the *Auto* mode.    
  
<p align="center"><img src="dotcodeencodemodeauto.png" width="20%" height="20%"></p>
  
``` csharp
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DotCode, "犬Right狗"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 10;

    //set DotCode ECI encoding to UTF8
    gen.Parameters.Barcode.DotCode.ECIEncoding = ECIEncodings.UTF8;
    gen.Save($"{path}DotCodeEncodeModeAuto.png", BarCodeImageFormat.Png);
}
```

### ***Bytes* Encoding Mode**
The *Bytes* mode is used to encode byte streams. If the input data includes a Unicode symbol, the barcode library encodes it with two bytes. The code sample below explains how to work with the *Bytes* encoding mode.   

<p align="center"><img src="dotcodeencodemodebytes.png" width="20%" height="20%"></p>  
  
``` csharp
byte[] encodedArr = { 0xFF, 0xFE, 0xFD, 0xFC, 0xFB, 0xFA, 0xF9 };

//encode an array to a string
StringBuilder strBld = new StringBuilder();
foreach (byte bval in encodedArr)
    strBld.Append((char)bval);
var codetext = strBld.ToString();

using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DotCode, codetext))
{
    gen.Parameters.Barcode.XDimension.Pixels = 10;
    //set DotCode encode mode to Bytes
    gen.Parameters.Barcode.DotCode.DotCodeEncodeMode = DotCodeEncodeMode.Bytes;
    gen.Save($"{path}DotCodeEncodeModeBytes.png", BarCodeImageFormat.Png);

}
```

### ***Extended Codetext* Mode**
In the *Extended Codetext* mode, the input data passed to the [*Codetext*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/codetext/) property contains special control words in addition to main information. Such words activate extended controls over data encoding and enable storing textual parts with different encodings in a single barcode. To generate DotCode barcodes in this format, it is recommended to use class [*DotCodeExtCodetextBuilder*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeextcodetextbuilder/). To generate DotCode barcodes in this format, it is recommended to use class [*DotCodeExtCodetextBuilder*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeextcodetextbuilder/).   
The following code sample demonstrate how to use the *Extended Codetext* mode.  

<p align="center"><img src="dotcodeextendedcodetext.png" width="20%" height="20%"></p>


```csharp
//create codetext
DotCodeExtCodetextBuilder textBuilder = new DotCodeExtCodetextBuilder();
textBuilder.AddFNC1FormatIdentifier();
textBuilder.AddECICodetext(ECIEncodings.UTF8, "犬Right狗");
textBuilder.AddPlainCodetext("Plain text");
textBuilder.AddFNC3SymbolSeparator();
textBuilder.AddFNC3ReaderInitialization();
textBuilder.AddPlainCodetext("Reader initialization info");

//generate barcode text
string codetext = textBuilder.GetExtendedCodetext();

//generate a DotCode barcode
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DotCode, codetext))
{
    gen.Parameters.Barcode.XDimension.Pixels = 10;

    gen.Parameters.Barcode.DotCode.DotCodeEncodeMode = DotCodeEncodeMode.ExtendedCodetext;
    gen.Save($"{path}DotCodeExtendedCodetext.png", BarCodeImageFormat.Png);
}
```

### **Structured Append Mode**
The barcode library supports a special generation mode to create DotCode barcodes with a structured append. This mode allows combining up to 35 DotCode barcodes. To enable this generation mode, it is necessary to initialize the following properties:
-	[*DotCodeStructuredAppendModeBarcodesCount*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeparameters/dotcodestructuredappendmodebarcodescount/2) – the number of barcodes to be combined (value from 1 to 35)
-	[*DotCodeStructuredAppendModeBarcodeId*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeparameters/dotcodestructuredappendmodebarcodeid/) – the position of a barcode in the set (value from 1 to DotCodeStructuredAppendModeBarcodesCount)  
  
The following code sample shows how to enable the *Structured Append* mode.    
  
<p align="center"><img src="dotcodestructuredappendmode.png" width="20%" height="20%"></p>

``` csharp
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DotCode, "Aspose"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 10;
    //set DotCode strucutured append mode
    gen.Parameters.Barcode.DotCode.DotCodeStructuredAppendModeBarcodeId = 3;
    gen.Parameters.Barcode.DotCode.DotCodeStructuredAppendModeBarcodesCount = 5;
    gen.Save($"{path}DotCodeStructuredAppendMode.png", BarCodeImageFormat.Png);
}
```

## **Aspect Ratio**
By default, the ratio between X and Y coordinates in a DotCode barcode equals to 1. To manually adjust this ratio with custom values, developers can initialize the [*AspectRatio*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeparameters/aspectratio/) property of class [*DotCodeParameters*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeparameters/), which is relative to the value of [*XDimension*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodeparameters/xdimension/). The code sample below explains how to modify the aspect ratio in a generated DotCode barcode.   

<p align="center"><img src="dotcodeaspectratio0.5.png"></p>
  
``` csharp
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DotCode, "Aspose"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 10;
    //set aspect ratio 0.5
    gen.Parameters.Barcode.DotCode.AspectRatio = 0.5f;
    gen.Save($"{path}DotCodeAspectRatio0.5.png", BarCodeImageFormat.Png);
}
```

## **Hardware Reader Initialization**
To encode a special flag indicating that the data encoded in a DotCode barcode is intended to initialize a hardware reader, it is possible to set the [*IsReaderInitialization*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/dotcodeparameters/isreaderinitialization/) property. The following code sample shows how to enable this property.  
  
``` csharp
using (BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DotCode, "Aspose"))
{
    gen.Parameters.Barcode.XDimension.Pixels = 10;
    //set flag that indicates that data is encoded for reader initialization
    gen.Parameters.Barcode.DotCode.IsReaderInitialization = true;
    gen.Save($"{path}DotCodeReaderInitialization.png", BarCodeImageFormat.Png);
}
```