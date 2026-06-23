---
title: "Save Generated Barcodes"
description: "Save generated barcodes to raster and vector formats or write them to a stream."
type: docs
weight: 30
url: /java/developer-guide/barcode-generation/save-generated-barcodes/
---

# Save Generated Barcodes

Call `BarcodeGenerator.save` to write the generated barcode to a file or output stream.

## Save raster images

```java
generator.save("barcode.png", BarCodeImageFormat.PNG);
generator.save("barcode.jpg", BarCodeImageFormat.JPEG);
generator.save("barcode.bmp", BarCodeImageFormat.BMP);
generator.save("barcode.tif", BarCodeImageFormat.TIFF);
```

Raster formats store pixels. PNG is suitable for lossless output and transparency. JPEG applies lossy compression and should be validated carefully for small barcode modules. BMP and TIFF can be useful in desktop, archival, or print workflows.

## Save vector images

```java
generator.save("qrcode.svg", BarCodeImageFormat.SVG);
```

SVG stores vector geometry and scales without normal raster resampling. Vector output is useful for documents and print layouts, but the final rendering process still needs to preserve valid module dimensions.

## Save to a stream

```java
ByteArrayOutputStream outputStream = new ByteArrayOutputStream();
generator.save(outputStream, BarCodeImageFormat.PNG);
byte[] imageBytes = outputStream.toByteArray();
```

Stream output is useful for web responses, database storage, message payloads, and in-memory processing.

## Complete example

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/save_options/SaveGeneratedBarcodes.java" target="_blank">View SaveGeneratedBarcodes.java</a>

You can also browse the <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation" target="_blank">Generation examples directory</a>.
