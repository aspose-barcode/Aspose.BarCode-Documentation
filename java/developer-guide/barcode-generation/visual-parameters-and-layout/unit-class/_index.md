---
title: Unit class
type: docs
weight: 10
url: /java/developer-guide/barcode-generation2/visual-parameters-and-layout/unit-class/
---

# Unit class

## Overview

In Aspose.BarCode for Java, many size-related parameters are represented by a `Unit` object. For example, X-Dimension, bar height, padding, and border width use `Unit`.

A `Unit` lets you set a value in different measurement systems. This is useful when you need physical sizes for printing and pixels for on-screen output.

## Supported units

A `Unit` can be set using the following methods:

- `setPixels(int pixels)`
- `setMillimeters(float millimeters)`
- `setInches(float inches)`
- `setPoints(float points)`

## Example: X-Dimension in pixels (screen output)

```java
import com.aspose.barcode.generation.*;

public class UnitExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ABC123");

        // Use pixels for screen output.
        generator.getParameters().getBarcode().getXDimension().setPixels(3);

        generator.save("barcode_xdim.png", BarCodeImageFormat.PNG);
    }
}
```

## Notes about Resolution

If you work in millimeters or inches, the final raster image still depends on the output resolution (DPI). For print-oriented layouts, set the target DPI using `generator.getParameters().setResolution(...)` and use physical units for geometry.

## Example: physical units for printing

```java
import com.aspose.barcode.generation.*;

public class UnitMillimetersExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ABC123");

        generator.getParameters().setResolution(300.0f);
        generator.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
        generator.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);

        generator.save("barcode_print.png", BarCodeImageFormat.PNG);
    }
}
```
