---
title: Specific Parameters of 2D Barcode Types in Aspose.BarCode via .NET
linktitle: 2D Barcode Types
type: docs
weight: 20
notoc: true
url: /net/2d-barcode-types/
aliases:
- /net/managing-2d-barcodes/
---
**Two-dimensional (2D)** barcodes have been introduced to address the limitations of linear symbologies. 2D barcodes are more complex and can include not only text data but also other types of information: price, quantity, web address, etc. They can be composed of rectangles, dots, hexagons, or other geometric patterns called matrix codes. By storing data both horizontally and vertically to form a square or rectangle, significantly more information can be encoded. Accordingly, 2D barcodes encode much larger amounts of information compared with typical 1D symbologies. 2D symbologies benefit from high readability and can mitigate poor printing quality as they contain additional data so that even if one or more cells are damaged, the barcode is still readable.  

**QR Code**  
*QR Code* is a 2D symbology that is used to encode long strings of alphanumeric data, typically text or URL. A *QR Code* label is composed of an array of black and white squares that can be recognized by smartphones and other readers. The *QR Code* symbology provides high data encoding density. Moreover, it supports the **Reed-Solomon** error correction that allows not only to restore corrupted data but also to ensure correct information decoding.  

<p align="center"><image src="qrcode.png"></p>
  
The code sample below can be used to generate a *QR Code* barcode.  

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Aspose常に先を行く");
gen.Parameters.Barcode.QR.QrEncodeMode = QREncodeMode.ECIEncoding;
gen.Parameters.Barcode.QR.QrECIEncoding = ECIEncodings.UTF8;
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}QrCode.png", BarCodeImageFormat.Png);
{{< /highlight >}} 


**PDF417**  
The *PDF417* barcode is a 2D high-density symbology that is capable of encoding any sequence of bytes, including text, numbers, files, and actual data bytes. It supports the Reed-Solomon error correction and thus provides high recognition accuracy.
  
<p align="center"><image src="pdf417.png"></p>
  
The following code snippet illustrates how to generate a *PDF417* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Save($"{path}Pdf417.png", BarCodeImageFormat.Png);
{{< /highlight >}} 

**Data Matrix**  
*Data Matrix* is a 2D type that allows encoding large amounts of data in a compact space. A single *Data Matrix* can contain up to 2,335 alphanumeric or 3,116 numerical characters. This is 10 times greater than the standard data density of 1D barcodes.
  
<p align="center"><image src="datamatrix.png"></p>

The code example below can be used to create a *Data Matrix* barcode.  

{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DataMatrix, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}DataMatrix.png", BarCodeImageFormat.Png);
{{< /highlight >}}

**Aztec Code**  
*Aztec Code* is a highly efficient 2D symbology that uses square modules with a unique finder pattern in the middle of a barcode, which allows barcode scanners to identify cell locations required for barcode reading. This barcode type not only enables encoding any sequence of bytes but also ensures correct data recognition.
  
<p align="center"><image src="aztecfull.png"></p>
  
The code snippet given below shows how to generate an *Aztec* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Aztec, "Åspóse.Barcóde©");
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}AztecFull.png", BarCodeImageFormat.Png);
{{< /highlight >}} 


**Micro QR Code**  
The *Micro QR Code* symbology provides large data density; however, it has a square shape and thus needs square space to be placed. A major feature of *Micro QR Code* is that it has only one position detection pattern instead of three ones for regular *QR Code* and requires a more compact placement area.
  
<p align="center"><image src="microqr.png"></p>
  
The following code snippet illustrates how to generate a *Micro QR Code*.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.QR, "Åspóse.Barcóde©");
gen.Parameters.Barcode.QR.QrEncodeType = QREncodeType.ForceMicroQR;
gen.Parameters.Barcode.XDimension.Pixels = 8;
gen.Save($"{path}MicroQR.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
**Compact PDF417**    
*Compact PDF417* can be used when space limitations are the main concern and symbol damage is unlikely. It has less data density compared with other 2D barcodes; however, owing to its property to have a length 64 times larger than height, it is more suitable for narrow rectangular areas with size limitations.
  
<p align="center"><image src="compactpdf417.png"></p>
  
The code sample below can be used to create a *Compact PDF417* barcode.
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.Pdf417, "Åspóse.Barcóde©");
//Compact version of Pdf417
gen.Parameters.Barcode.Pdf417.Pdf417Truncate = true;
gen.Parameters.Barcode.Pdf417.Rows = 6;
gen.Save($"{path}CompactPdf417.png", BarCodeImageFormat.Png);
{{< /highlight >}} 
