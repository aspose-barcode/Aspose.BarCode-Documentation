---
title: Barcode Type Definition
type: docs
weight: 10
url: /jasperreports/what-is-a-barcode-symbology/
aliases:
- /jasperreports/specify-symbologies-for-barcodes/
---

A barcode type (or symbology) is a system of encoding data so that a scanner and/or a decoding system may together read and decode the data. Apart from the actual technique of encoding bars and spaces, a number of technical specifications or characteristics define and separate different symbologies. Different barcode symbologies may have different features and characteristics.

Sometimes, barcode types are also referred to as a *language* in the sense that it allows humans to interact with computers just like other programming languages do. The bars and spaces in a barcode are the elements of the language that can be understood by a computer. In the industry, people use barcode readers or scanners to read information from a barcode, and different actions are performed on the basis of that information. Not all barcode readers support all barcode types, with the exception of Code128 which is supported by most readers.

***Aspose.BarCode for Jasper Reports*** supports generation and recognition of most popular one-dimensional (1D) and two-dimensional (2D) barcode symbologies.

**Code Sample**  
  
**JRXML**

``` csharp

 <image hAlign="Center">

    <reportElement x="0" y="100" width="500" height="250" />

    <imageExpression class="net.sf.jasperreports.engine.JRRenderable"><![CDATA[new com.aspose.barcode.jr.BarCodeRenderer(com.aspose.barcode.jr.BarCodeAttributesFactory.Create("codetext","DataMatrix",java.awt.Color.BLACK))]]></imageExpression>

</image>

```