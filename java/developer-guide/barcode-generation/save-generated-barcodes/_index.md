---
title: Save Generated Barcodes
type: docs
weight: 40
url: /java/developer-guide/barcode-generation2/save-generated-barcodes/
---

# Save Generated Barcodes

This article describes how to save generated barcode images to a file or stream, and how to choose between raster and vector output formats.

## Choose an output format

When you generate barcodes, choose the output format based on how the barcode will be used.

### Raster formats

Raster formats store a fixed grid of pixels. Use them when you need a bitmap image.

- **PNG**: default choice for most workflows (lossless).
- **TIFF**: common in printing workflows.
- **BMP**: uncompressed bitmap (large files).
- **GIF**: limited colors.
- **JPEG**: lossy compression; can introduce artifacts that reduce scan reliability.

{{% alert color="warning" %}}
**Avoid JPEG for Barcodes!**  
JPEG compression is designed for photographs, not sharp edges. It introduces compression artifacts (noise) around the bars, which can make the barcode unreadable by scanners.  
**Always prefer PNG or TIFF** for raster images.
{{% /alert %}}

### Vector formats

Vector formats store drawing operations. Use them when you need to scale the barcode without rasterization artifacts.

- **SVG**: common for web and design workflows.
- **EMF**: common in Windows printing workflows.

## Save to file

Use `save(path, format)` to write the generated barcode to a file.

```java
import com.aspose.barcode.generation.*;

public class SaveToFileExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "12345678");
        generator.save("barcode.png", BarCodeImageFormat.PNG);
    }
}
```

## Save to stream

Use `save(OutputStream, format)` when you need the result as bytes.

```java
import com.aspose.barcode.generation.*;
import java.io.ByteArrayOutputStream;

public class SaveToStreamExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "STREAM-TEST");

        ByteArrayOutputStream stream = new ByteArrayOutputStream();
        generator.save(stream, BarCodeImageFormat.PNG);

        byte[] imageBytes = stream.toByteArray();
    }
}
```

## Example: save in multiple formats

The following example saves the same barcode in several formats.

```java
import com.aspose.barcode.generation.*;

public class MultipleFormatsExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "FORMAT-TEST");

        gen.save("code128.png", BarCodeImageFormat.PNG);
        gen.save("code128.tiff", BarCodeImageFormat.TIFF);
        gen.save("code128.svg", BarCodeImageFormat.SVG);
    }
}
```
