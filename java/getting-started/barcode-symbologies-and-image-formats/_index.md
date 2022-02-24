---
title: Barcode Symbologies and Image Formats
type: docs
weight: 20
url: /java/supported-file-formats/
---
***Aspose.BarCode for .NET*** supports over 60 different [barcode types](https://en.wikipedia.org/wiki/Barcode#Types_of_barcodes) used in a variety of industries, namely, 1D (linear), 2D (including QR codes), and postal symbologies. The detailed information about generating barcodes using various barcode standards can be found in section [Generation Specifics for Symbologies](/barcode/net/generate-barcode-with-different-symbology/)
    
**Linear barcode types**, or *1D barcodes*, correspond to the first generation of one-dimensional barcodes (1D) that are used to represent information by varying the widths and spacings of parallel lines. Some 1D symbologies allow encoding only numbers, while others permit encoding also letters.  

**Matrix codes**, also known as *2D barcodes*, have been introduced as a two-dimensional way to encode information. Two-dimensional (2D) barcodes are generated using various symbols and shapes. This barcode type is considered to be more efficient, as such barcodes contain more data per unit area, and most of them are self-correctable.  
  
**Postal barcode types** are specific barcode symbologies used by postal services in different countries.
  
<table> 
<tr> <th></th><th></th> 
<th>Supported Symbologies</th> 
</tr> 
<tr> <th rowspan="2">1D (Linear)</th> 
<th>Numeric Only</th> 
<td>Code 11, Code 32, Codabar, DataBar Omnidirectional, DataBar Stacked Omnidirectional, DataBar Limited, DataBar Truncated, DataBar Stacked, EAN 13, EAN 14, EAN 8,
IATA 2-of-5, Italian Post 25, Interleaved 2-of-5, ISBN, ISMN, ISSN, ITF 6, ITF 14, Matrix 2-of-5, MSI, OPC, PatchCode, Pharmacode, PZN, SSCC 14, SSCC 18, 
Standard 2-of-5, EAN 5, EAN 2, UPC-A, UPC-E, UpcaGs1DatabarCoupon
</td> 
</tr> 
<tr> <th>Alpha-Numeric</th> 
<td>Code 128, Code 39, Code 93, Code 16K, Codablock-F, DataBar Expanded, DataBar Expanded Stacked, GS1 Codablock-F, GS1 Code 128, VIN</td> 
 </tr> 
<tr> <th colspan ="2" >2D</th> 
<td>QR, Micro QR Code, PDF417, Compact PDF417, Macro PDF417, Micro PDF417, Aztec, DataMatrix, DotCode, GS1 DataMatrix, GS1 QR Code, MaxiCode</td> 
 </tr> 
 <tr> <th colspan ="2">Postal</th> 
<td>Australia Post, AustralianPostParcel, Deutsche Post Identcode, Deutsche Post Leticode, Planet, Postnet, RM4SCC, SingaporePost, SwissPostParcel, USPS OneCode</td> 
 </tr> 
</tr> 
</table>

## **Image Formats**
***Aspose.BarCode for .NET*** allows rendering barcode labels in the five most widespread image formats. Two additional vector formats can be used for barcode generation, but they are not supported for rendering by the SQL Server Reporting Services engine. The image formats available for input and output are listed below.


|**Format**|**Description**|**Load**|**Save**|
| :- | :- | :- | :- |
|[JPEG](https://docs.fileformat.com/Image/JPEG/)|The image file format was standardized by the Joint Photographic Experts Group.|{{< emoticons/tick >}}|{{< emoticons/tick >}}|
|[TIFF](https://docs.fileformat.com/Image/TIFF/)|Tagged Image File Format|{{< emoticons/tick >}}|{{< emoticons/tick >}} |
|[PNG](https://docs.fileformat.com/Image/PNG/)|Portable Network Graphics Image|{{< emoticons/tick >}}|{{< emoticons/tick >}}|
|[BMP](https://docs.fileformat.com/Image/BMP/)|Bitmap Image Files|{{< emoticons/tick >}}|{{< emoticons/tick >}}|
|[GIF](https://docs.fileformat.com/Image/GIF/)|Graphical Interchange Format Image|{{< emoticons/tick >}}|{{< emoticons/tick >}}|
|[EXIF](https://docs.fileformat.com/image/exif/)|Exchangeable Image File Format|{{< emoticons/tick >}}|{{< emoticons/tick >}}|
|[EMF](https://docs.fileformat.com/Image/EMF/)|Enhanced Metafile Format| |{{< emoticons/tick >}}|
|[SVG](https://docs.fileformat.com/page-description-language/SVG/)|Scalable Vector Graphics Files| |{{< emoticons/tick >}} |





### **Numeric Only Symbologies**
- EAN13
- EAN8
- UPCA
- UPCE
- BooklandEAN
- Interleaved2of5
- Standard2of5
- MSI
- Code11
- Codabar
- Postnet
- Planet
- EAN14(SCC14)
- SSCC18
- ITF14
- Leticode
- OPC
### **Alpha-Numeric Symbologies**
- Code128
- EAN128
- Code39 Extended
- Code39 Standard
- Code93 Extended
- Code93 Standard
- Australia Post
- Matrix 2 of 5
- PZN
- Deutsche Post Identcode
- VIN
### **2D Symbologies**
- PDF417
- DataMatrix
- Aztec
- QR
- Swiss QR (QR Bill)