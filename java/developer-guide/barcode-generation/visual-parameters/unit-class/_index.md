---
title: "Unit Class"
description: "Use the Unit class to define barcode measurements in pixels, millimeters, inches, and points."
type: docs
weight: 80
url: /java/developer-guide/barcode-generation/visual-parameters-and-layout/unit-class/
---

# Unit Class

Most size-related generation properties are represented by the `Unit` class. A `Unit` stores one physical value and exposes conversions to other units.

## Set values in pixels

```java
generator.getParameters().getBarcode().getXDimension().setPixels(3.0f);
generator.getParameters().getBarcode().getBarHeight().setPixels(100);
```

Pixel values are direct raster measurements and do not scale when the output resolution changes.

## Set values in physical units

```java
generator.getParameters().setResolution(300.0f);
generator.getParameters().getBarcode().getXDimension()
        .setMillimeters(0.33f);
generator.getParameters().getBarcode().getBarHeight()
        .setMillimeters(15.0f);
```

Physical values are converted to pixels according to the current resolution. Use `updateResolution` when working with a standalone `Unit` object or when inspecting a conversion explicitly.

```java
Unit unit = new Unit();
unit.updateResolution(300.0f);
unit.setInches(0.25f);
float pixels = unit.getPixels();
```

## Supported measurements

Common setters include:

- `setPixels`
- `setMillimeters`
- `setInches`
- `setPoint`
- `setDocument`

Use physical units for printer-oriented layouts and pixels for fixed raster assets. Do not mix a fixed physical X-dimension with an auto-size mode that recalculates module size.

## Complete example


<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/UseUnitExample.java" target="_blank">View UseUnitExample.java</a>

set