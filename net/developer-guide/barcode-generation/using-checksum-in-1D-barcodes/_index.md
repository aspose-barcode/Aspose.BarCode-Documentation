---
title: Using Checksum in 1D barcodes
type: docs
weight: 80
url: /net/using-checksum-in-1D-barcodes/
---

## Overview

## Definition of Checksum in 1D Barcodes
  
**Code39 Checksum**
  
{{< highlight csharp>}}
foreach (var value in encodedCodetext)
    checkSum = (checkSum + value) % 43;
{{< /highlight >}} 
  
**Code128 Checksum**
  
{{< highlight csharp>}}
for (var pos = 0; pos < encodedCodetext.Length; ++pos)
    checkSum = (checkSum + encodedCodetext[pos] * (pos + 1)) % 103;
{{< /highlight >}} 
  
## Setting Checksum in Barcodes

  
|Checksum Setting|1D Symbologies|
|---|---|
|**Optional**|Codabar, Italian Post 25, Interleaved 2 of 5, Matrix 2 of 5, MSI, PatchCode, Pharmacode, PZN, Standard 2 of 5, Code39|
|**Obligatory**|Code11, Code32, Databar OmniDirectional, Databar Stacked OmniDirectional, DatabarLimited, DatabarTruncated, Databar Stacked, EAN13, EAN14, EAN8, IATA 2 of 5, ISBN, ISMN, ISSN, ITF6, ITF14, OPC, SSCC14, SSCC18, EAN5, EAN2, UPC A, UPC E, UpcaGs1DatabarCoupon, Code128, Code93, Code16K, CodablockF, Databar Expanded, Databar Expanded Stacked, GS1 CodablockF, GS1 Code 128, VIN|

### Optional Checksum Settings

### Obligatory Checksum Settings

## Displaying Checksum for Code128