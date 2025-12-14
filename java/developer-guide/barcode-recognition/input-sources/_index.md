---
title: "Input Sources: Files, Streams, and Bitmaps"
description: "How to create BarCodeReader from file paths, streams, BufferedImage, and in-memory data."
type: docs
weight: 10
url: /java/developer-guide/barcode-recognition/input-sources
---

# Input Sources: Files, Streams, and Bitmaps

`BarCodeReader` can read barcode images from file paths, streams, and in-memory objects (like `BufferedImage` or `byte[]`).
Use the simplest option that matches how you already store or receive image data.

## Read from a file path

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

String imagePath = "path/to/barcode.png";

BarCodeReader reader = new BarCodeReader(imagePath, DecodeType.CODE_128);
BarCodeResult[] results = reader.readBarCodes();
```

## Read from an `InputStream`

Use this when images come from uploads, network responses, archives, or any pipeline that already uses streams.
Always ensure streams are properly closed.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import java.io.FileInputStream;

String imagePath = "path/to/barcode.png";

try (FileInputStream stream = new FileInputStream(imagePath)) {
    BarCodeReader reader = new BarCodeReader(stream);
    BarCodeResult[] results = reader.readBarCodes();
}
```

## Read from a `BufferedImage`

Use this when your code already preprocesses images using Java 2D or a third-party imaging library.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import java.awt.image.BufferedImage;
import javax.imageio.ImageIO;
import java.io.File;

String imagePath = "path/to/barcode.png";

BufferedImage image = ImageIO.read(new File(imagePath));
BarCodeReader reader = new BarCodeReader(image);
BarCodeResult[] results = reader.readBarCodes();
```

## Read from a byte array

Use this when images are stored in a database, cache, or message payload.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.io.ByteArrayInputStream;

String imagePath = "path/to/barcode.png";
byte[] bytes = Files.readAllBytes(Paths.get(imagePath));

try (ByteArrayInputStream stream = new ByteArrayInputStream(bytes)) {
    BarCodeReader reader = new BarCodeReader(stream);
    BarCodeResult[] results = reader.readBarCodes();
}
```

## Read from Base64

This is common in REST APIs where images are embedded into JSON.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import java.io.ByteArrayInputStream;
import java.util.Base64;

String base64 = getBase64FromClient(); // e.g. JSON field "image"

String cleanBase64 = base64.contains(",")
        ? base64.substring(base64.indexOf(",") + 1)
        : base64;

byte[] decodedBytes = Base64.getDecoder().decode(cleanBase64);

try (ByteArrayInputStream stream = new ByteArrayInputStream(decodedBytes)) {
    BarCodeReader reader = new BarCodeReader(stream);
    BarCodeResult[] results = reader.readBarCodes();
}
```

## Handling invalid input

If the input is missing or not a real image, reader creation or `readBarCodes()` can throw an exception.
Wrap the call in `try/catch` and handle errors at your application boundary.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;

try {
    BarCodeReader reader = new BarCodeReader("non_existent.png");
    BarCodeResult[] results = reader.readBarCodes();
} catch (Exception e) {
    handleError(e);
}
```
