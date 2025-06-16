---
title: Supported Barcode Types
type: docs
weight: 50
feedback: BARCODECOM
description: "1D, 2D, and Postal Barcode Symbologies Supported in Aspose.BarCode for Java"
keywords: "Generate Barcodes, Read Barcodes, How to Generate Barcodes in Java, Barcode Type, Matrix Barcodes, 1D Barcode, 2D Barcode, QR Code, MicroQR Code, Code 128, Aspose.BarCode, Java"
url: /phpjava/barcode-types/
---

***Aspose.BarCode for Java*** supports over 80
different <a href="https://en.wikipedia.org/wiki/Barcode#Types_of_barcodes" target="_blank">barcode types</a> used in a
variety of industries, namely, 1D (linear), 2D (including QR codes), and postal symbologies. The detailed information
about generating barcodes using various barcode standards can be found in
section <a href="/barcode/java/generate-barcode-types/" target="_blank">Generation Specifics for Symbologies</a>.

**Linear barcode types**, or *1D barcodes*, correspond to the first generation of one-dimensional barcodes (1D) that are
used to represent information by varying the widths and spacings of parallel lines. Some 1D symbologies allow encoding
only numbers, while others permit encoding also letters.

**DataBar barcodes** (former RSS-14) are 1D and 1D stacked barcodes, which were developed to efficiently encode 
<a href="https://ref.gs1.org/ai/?lang=en" target="_blank">*GS1 Application Identifier*</a> data.


**Matrix barcodes**, also known as *2D barcodes*, have been introduced as a two-dimensional way to encode information.
Two-dimensional (2D) barcodes are generated using various symbols and shapes. This barcode type is considered to be more
efficient, as such barcodes contain more data per unit area, and most of them are self-correctable.

**Postal barcodes** are specific symbologies used by postal services in different countries.

**HIBC barcodes** encode data in <a href="https://www.hibcc.org/udi-labeling-standards/barcode-standards/" target="_blank">special format</a> 
which is used in Health Industry. As transport, the barcodes use other 1D and 2D barcodes and encode data as Alpha-Numeric.


**GS1 barcodes** use other 1D and 2D barcodes to encode 
<a href="https://ref.gs1.org/ai/?lang=en" target="_blank">*GS1 Application Identifier*</a> data.

| Barcode Family            | Barcode Types                                                                                                                                                                                                                   |
|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1D Numeric (Linear)       | Codabar, Code11, Code128, DataLogic2of5, EAN13, EAN14, EAN8, IATA2of5, ISBN, ISMN, ISSN, ITF14, ITF6, Interleaved2of5, ItalianPost25, MSI, Matrix2of5, OPC, PZN, PatchCode, Pharmacode, SCC14, SSCC18, Standard2of5, UPCA, UPCE |
| 1D Alpha-Numeric (Linear) | CodablockF, Code128, Code16K, Code32, Code39Extended, Code39Standard, Code93Extended, Code93Standard, VIN                                                                                                                       |
| DataBar (RSS-14)          | DatabarExpanded, DatabarExpandedStacked, DatabarLimited, DatabarOmniDirectional, DatabarStacked, DatabarStackedOmniDirectional, DatabarTruncated                                                                                |
| 2D                        | Aztec, CompactPdf417, DataMatrix, DotCode, HanXin, MacroPdf417, MaxiCode, MicroPdf417, MicroQR, Pdf417, QR, RectMicroQR(rMQR), Swiss QR Code                                                                                    |
| Postal                    | AustraliaPost, AustralianPosteParcel, DeutschePostIdentcode, DeutschePostLeitcode, DutchKIX, Mailmark, Mailmark 2D, OneCode, Planet, Postnet, RM4SCC, SingaporePost, SwissPostParcel                                            |
| HIBC                      | HIBCAztecLIC, HIBCAztecPAS, HIBCCode128LIC, HIBCCode128PAS, HIBCCode39LIC, HIBCCode39PAS, HIBCDataMatrixLIC, HIBCDataMatrixPAS, HIBCQRLIC, HIBCQRPAS                                                                            |
| GS1                       | GS1Aztec, GS1CodablockF, GS1Code128, GS1CompositeBar (GS1 Composite barcode), GS1DataMatrix, GS1DotCode, GS1HanXin, GS1MicroPdf417, GS1QR, UpcaGs1Code128Coupon, UpcaGs1DatabarCoupon                                           |
| Other                     | MicrE13B(recognition only)                                                                                                                                                                                                      |
