---
title: Barcode Types and Image Formats
type: docs
weight: 20
url: /java/supported-file-formats/
---
***Aspose.BarCode for Java*** supports more than 60 [barcode types](https://en.wikipedia.org/wiki/Barcode#Types_of_barcodes) used in various industries, i.e., linear (1D), matrix (2D), and postal barcodes. The detailed description about barcode generation for different types can be found in section [Generation Specifics for Barcode Types](/barcode/java/symbology/)
    
**Linear barcode types**, or *1D barcodes*, relate to the first generation of one-dimensional (1D) barcode types that decode data by changing the widths of black and white parallel lines. Particular 1D standards support encoding only numbers, while others allow encoding also letters and special symbols.  

**Matrix barcode types**, also referred as *2D barcode types*, have been developed as an advanced way to encode data. Two-dimensional (2D) types imply creating barcodes composed of various figures and shapes. These barcode standards are deemed to have better efficiency compared with 1D barcodes owing to their improved data density and data recovery mechanisms.  
  
**Postal types** are special barcode standards introduced by postal services in various countries.
  
<table> 
<tr> <th></th><th></th> 
<th>Supported Barcode Types</th> 
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
<td>QR Code, Micro QR Code, PDF417, Compact PDF417, Macro PDF417, Micro PDF417, Aztec Code, Data Matrix, DotCode, GS1 DataMatrix, GS1 QR Code, MaxiCode</td> 
 </tr> 
 <tr> <th colspan ="2">Postal</th> 
<td>Australia Post, Australian Post Parcel, Deutsche Post Identcode, Deutsche Post Leticode, Planet, Postnet, RM4SCC, SingaporePost, Swiss Post Parcel, USPS OneCode</td> 
 </tr> 
</tr> 
</table>
  
## **Image Formats**
***Aspose.BarCode for Java*** enables outputting barcode images using five most common raster image file formats and two vector image formats. The latter ones are available for rendering only by the SQL Server Reporting Services engine. Image formats supported for input and output are listed below.
  
|**Format**|**Description**|**Recognition**|**Generation**|
| :- | :- | :- | :- |
|[JPEG](https://docs.fileformat.com/Image/JPEG/)|File format standardized by the Joint Photographic Experts Group|{{< emoticons/tick >}}|{{< emoticons/tick >}}|
|[TIFF](https://docs.fileformat.com/Image/TIFF/)|Tagged Image File Format|{{< emoticons/tick >}}|{{< emoticons/tick >}} |
|[PNG](https://docs.fileformat.com/Image/PNG/)|Portable Network Graphics Image|{{< emoticons/tick >}}|{{< emoticons/tick >}}|
|[BMP](https://docs.fileformat.com/Image/BMP/)|Bitmap Image File|{{< emoticons/tick >}}|{{< emoticons/tick >}}|
|[GIF](https://docs.fileformat.com/Image/GIF/)|Graphical Interchange Format Image|{{< emoticons/tick >}}|{{< emoticons/tick >}}|
|[EXIF](https://docs.fileformat.com/image/exif/)|Exchangeable Image File Format|{{< emoticons/tick >}}|{{< emoticons/tick >}}|
|[EMF](https://docs.fileformat.com/Image/EMF/)|Enhanced Metafile Format| |{{< emoticons/tick >}}|
|[SVG](https://docs.fileformat.com/page-description-language/SVG/)|Scalable Vector Graphics Format| |{{< emoticons/tick >}} |
  