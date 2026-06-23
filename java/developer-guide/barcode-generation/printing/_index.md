---
title: "Printing"
description: "Configure output resolution, DPI-based physical dimensions, wide-to-narrow ratio, and anti-aliasing."
type: docs
weight: 50
url: /java/developer-guide/barcode-generation/printing/
---

# Printing

Printer-oriented barcode generation requires control over physical dimensions, raster resolution, and rendering behavior.

## Set resolution and physical dimensions

```java
generator.getParameters().setResolution(300.0f);
generator.getParameters().getBarcode().getXDimension()
        .setMillimeters(0.33f);
generator.getParameters().getBarcode().getBarHeight()
        .setMillimeters(18.0f);
```

Resolution determines how physical units are converted to pixels. At a higher DPI, the same physical X-dimension is represented by more pixels. Setting DPI does not add detail when every dimension is already fixed in pixels.

The dimensions in an example are not universal print defaults. Verify them against the applicable barcode application specification, printer resolution, substrate, ink spread, and scanner distance.

## Configure wide-to-narrow ratio

Some linear symbologies use narrow and wide elements.

```java
generator.getParameters().getBarcode().setWideNarrowRatio(2.5f);
```

Use a ratio supported by the selected symbology and printing process. See the <a href="https://docs.aspose.com/barcode/info-cards/code-39/" target="_blank">Code 39 standard overview</a>.

## Configure anti-aliasing

```java
generator.getParameters().setUseAntiAlias(false);
```

Disabling anti-aliasing keeps raster module edges crisp. Enabling it can produce smoother visual edges but may introduce intermediate colors around very small bars or modules. Test both the printed result and the target scanner.

For thermal printers, calculate physical dimensions for the actual device resolution, such as 203 or 300 DPI, rather than resizing a previously rendered bitmap.

## Complete example


<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/print_options/PrintOptionsExample.java" target="_blank">View PrintOptionsExample.java</a>

You can also browse the <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation" target="_blank">Generation examples directory</a>.