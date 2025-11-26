---
title: "Region of Interest (ROI)"
description: "Learn how to limit barcode recognition to specific regions in an image using BarCodeReader in Aspose.BarCode for Java."
type: docs
weight: 20
url: /java/developer-guide/barcode-recognition/region-of-interest
---

# Barcode Recognition in a Region of Interest (ROI)

`BarCodeReader` in Aspose.BarCode for Java allows you to restrict recognition to specific rectangular areas of an image,  
known as *regions of interest* (ROIs). This can significantly speed up recognition and improve accuracy when barcodes  
are located in known zones on complex layouts.

This article explains how to:

1. Recognize a single barcode from a specific region of a composite image.
2. Use ROIs with 2D and 1D barcode type groups.
3. Define multiple ROIs and read several barcodes in one pass.
4. Compare full-image scanning with ROI-based scanning.
5. Use an ROI on a single image where the barcode is not located at the origin.

All code snippets below are taken **directly** from the sample test class:

`com.aspose.barcode.guide.recognition.roi.RegionOfInterestExamples`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/roi/RegionOfInterestExamples.java" target="_blank" rel="noopener noreferrer">RegionOfInterestExamples.java</a>

---

## Test Data and Setup

Before looking at the ROI scenarios, the test class prepares a folder for the generated fixtures and initializes the license.  
All image files used in the examples are created inside a dedicated `IMAGES_FOLDER`.

```java
public class RegionOfInterestExamples {

    private static final String IMAGES_FOLDER =
            ExampleAssist.getOrCreateResourceFolderPath("quick_start", "recognition", "roi");

    @BeforeClass
    public void setUp() throws Exception {
        LicenseAssist.setupLicense();
        Files.createDirectories(Paths.get(IMAGES_FOLDER));
    }

    // ...
}
```

The helper method `getFullPath` is used to build full file paths under this folder:

```java
private static String getFullPath(String fileName) {
    return Paths.get(IMAGES_FOLDER, fileName).toString();
}
```

Two image fixtures are generated on demand:

- `roi_canvas.png` – a composite canvas containing multiple barcodes (Code 128, QR, Data Matrix, EAN-13) at different positions.
- `code128_offset.png` – a single Code 128 symbol placed away from the origin of the image.

These fixtures are created by the helper methods shown in the **Helper Methods and Fixtures** section.

---

## 1. Single ROI for a Code 128 Area on a Composite Canvas

In many layouts the barcode occupies only a specific area, while the rest of the image contains unrelated content.  
This example demonstrates how to define a `Rectangle` for the Code 128 area on a composite canvas and limit recognition to that region only.

```java
@Test
public void roiCode128OnlyArea() throws Exception {
    ensureRoiCanvasPng();
    Rectangle roi = new Rectangle(20, 20, 440, 140);
    BarCodeReader reader = new BarCodeReader(getFullPath("roi_canvas.png"), roi, DecodeType.CODE_128);
    assertRecognized(reader, "roiCode128OnlyArea", 1, DecodeType.CODE_128);
}
```

**Key points**

- `ensureRoiCanvasPng()` prepares the composite image `roi_canvas.png` if it does not exist.
- `Rectangle roi = new Rectangle(20, 20, 440, 140);` defines the region where the Code 128 symbol is located.
- `BarCodeReader` is constructed with an image path, a single ROI rectangle, and a specific decode type (`CODE_128`).
- Only the defined ROI is scanned, which reduces the search area and can improve performance.

---

## 2. Single ROI for a QR Code Using `TYPES_2D`

Sometimes the exact symbology may vary, but you know that the barcode in a particular area is definitely 2D.  
This example shows how to define a QR-specific ROI but use the broader `TYPES_2D` group as the decode type set.

```java
@Test
public void roiQrAreaTypes2D() throws Exception {
    ensureRoiCanvasPng();
    Rectangle roi = new Rectangle(470, 10, 250, 250);
    BarCodeReader reader = new BarCodeReader(getFullPath("roi_canvas.png"), roi, DecodeType.TYPES_2D);
    assertRecognized(reader, "roiQrAreaTypes2D", 1, DecodeType.QR);
}
```

**Key points**

- The ROI `(470, 10, 250, 250)` targets the area where the QR code is drawn on the composite canvas.
- `DecodeType.TYPES_2D` tells `BarCodeReader` to search for any supported 2D symbology within that region.
- The test verifies that a single QR code is correctly recognized from the specified ROI.

---

## 3. Multiple ROIs in One Pass for 1D Barcodes

You may have several distinct regions on the same image that each contain a different 1D barcode.  
This example uses an array of `Rectangle` objects to define multiple ROIs and reads both a Code 128 and an EAN-13 symbol in a single pass.

```java
@Test
public void roiTwoAreas1DPass() throws Exception {
    ensureRoiCanvasPng();
    Rectangle[] areas = new Rectangle[] {
            new Rectangle(20, 20, 440, 140),    // Code 128
            new Rectangle(470, 240, 450, 160)   // EAN-13
    };
    BarCodeReader reader = new BarCodeReader(getFullPath("roi_canvas.png"), areas, DecodeType.TYPES_1D);
    BarCodeResult[] results = reader.readBarCodes();
    boolean hasCode128 = false, hasEan13 = false;
    for (BarCodeResult r : results) {
        System.out.println("[roiTwoAreas1DPass] " + r.getCodeTypeName() + " | " + r.getCodeText());
        if (r.getCodeType() == DecodeType.CODE_128) hasCode128 = true;
        if (r.getCodeType() == DecodeType.EAN_13) hasEan13 = true;
    }
    Assert.assertTrue(hasCode128, "Expected CODE_128 in ROI results");
    Assert.assertTrue(hasEan13, "Expected EAN_13 in ROI results");
}
```

**Key points**

- Two ROIs are defined:
    - Top-left region for the Code 128 symbol.
    - Bottom-right region for the EAN-13 symbol.
- `BarCodeReader` is constructed with an array of `Rectangle` objects and `DecodeType.TYPES_1D` to search for any supported 1D barcode types.
- The loop over `results` checks that both `CODE_128` and `EAN_13` have been detected at least once.
- This pattern is useful for structured layouts (labels, forms) where multiple barcodes are placed in predictable zones.

---

## 4. Comparing Full-Image Scanning with ROI-Based Scanning

In some cases you may want to compare the behavior of full-image recognition with ROI-based recognition.  
This example first scans the entire composite canvas to verify that multiple barcodes are present, and then scans only a Data Matrix region using a dedicated ROI.

```java
@Test
public void roiVsFullImage() throws Exception {
    ensureRoiCanvasPng();

    BarCodeReader full = new BarCodeReader(getFullPath("roi_canvas.png"), DecodeType.ALL_SUPPORTED_TYPES);
    BarCodeResult[] fullResults = full.readBarCodes();
    Assert.assertTrue(fullResults.length >= 3, "Expected several symbols on the full canvas");

    Rectangle dmArea = new Rectangle(10, 190, 230, 230);
    BarCodeReader roiOnly = new BarCodeReader(getFullPath("roi_canvas.png"), dmArea, DecodeType.DATA_MATRIX);
    assertRecognized(roiOnly, "roi_canvas.png@roiDataMatrix", 1, DecodeType.DATA_MATRIX);
}
```

**Key points**

- `DecodeType.ALL_SUPPORTED_TYPES` is used for the full-image scan to detect multiple barcodes of different symbologies.
- The assertion `fullResults.length >= 3` ensures that the canvas contains several readable barcodes.
- `dmArea` defines the area where the Data Matrix symbol is located.
- The second reader is constrained to the Data Matrix ROI and uses `DecodeType.DATA_MATRIX` to focus on that symbology only.

---

## 5. ROI on a Single Image Where the Barcode Is Not at the Origin

Barcodes are often not placed at the top-left corner of an image; they can be centered or shifted according to the design.  
This example uses a single barcode image where the Code 128 symbol is intentionally offset inside a larger canvas and demonstrates how to define an ROI around it.

```java
@Test
public void roiSingleImageSubRegion() throws Exception {
    ensureCode128OffsetPng();
    Rectangle roi = new Rectangle(150, 80, 480, 160);
    BarCodeReader reader = new BarCodeReader(getFullPath("code128_offset.png"), roi, DecodeType.CODE_128);
    assertRecognized(reader, "", 1, DecodeType.CODE_128);
}
```

**Key points**

- `ensureCode128OffsetPng()` creates an image where the barcode is drawn with an offset from the top-left corner.
- `Rectangle roi = new Rectangle(150, 80, 480, 160);` defines the sub-region that encloses the Code 128 symbol.
- `BarCodeReader` scans only that sub-region, which is important when the rest of the image contains non-barcode graphics or margins.

---

## Helper Methods and Fixtures

The ROI examples rely on two helper methods that generate test fixtures: one composite canvas with multiple barcodes and one single-image canvas with an offset barcode.  
These methods use `BarcodeGenerator` to create individual symbols and then compose them into larger images.

### Composite ROI Canvas: `roi_canvas.png`

```java
private void ensureRoiCanvasPng() throws Exception {
    ensureImage("roi_canvas.png", (fullPath) -> {
        String tmpCode128 = getFullPath("tmp_roi_code128.png");
        String tmpQR     = getFullPath("tmp_roi_qr.png");
        String tmpDM     = getFullPath("tmp_roi_dm.png");
        String tmpEAN    = getFullPath("tmp_roi_ean13.png");

        BarcodeGenerator c128 = new BarcodeGenerator(EncodeTypes.CODE_128, "ROI-CODE128-12345");
        c128.getParameters().getBarcode().getXDimension().setPixels(2);
        c128.getParameters().getBarcode().getBarHeight().setPixels(60);
        c128.save(tmpCode128, BarCodeImageFormat.PNG);

        BarcodeGenerator qr = new BarcodeGenerator(EncodeTypes.QR, "ROI-QR-DEMO");
        qr.getParameters().getBarcode().getXDimension().setPixels(4);
        qr.save(tmpQR, BarCodeImageFormat.PNG);

        BarcodeGenerator dm = new BarcodeGenerator(EncodeTypes.DATA_MATRIX, "ROI-DM-0001");
        dm.getParameters().getBarcode().getXDimension().setPixels(4);
        dm.save(tmpDM, BarCodeImageFormat.PNG);

        BarcodeGenerator ean = new BarcodeGenerator(EncodeTypes.EAN_13, "5901234123457");
        ean.getParameters().getBarcode().getXDimension().setPixels(2);
        ean.save(tmpEAN, BarCodeImageFormat.PNG);

        try {
            BufferedImage code128Img = ImageIO.read(Paths.get(tmpCode128).toFile());
            BufferedImage qrImg      = ImageIO.read(Paths.get(tmpQR).toFile());
            BufferedImage dmImg      = ImageIO.read(Paths.get(tmpDM).toFile());
            BufferedImage eanImg     = ImageIO.read(Paths.get(tmpEAN).toFile());

            int canvasW = 920;
            int canvasH = 420;
            BufferedImage canvas = new BufferedImage(canvasW, canvasH, BufferedImage.TYPE_INT_ARGB);
            Graphics2D g = canvas.createGraphics();

            g.drawImage(code128Img, 20, 20, null);
            g.drawImage(qrImg,      480, 20, null);
            g.drawImage(dmImg,       20, 200, null);
            g.drawImage(eanImg,     480, 260, null);

            g.dispose();
            ImageIO.write(canvas, "PNG", Paths.get(fullPath).toFile());
        } catch (IOException e) {
            throw new RuntimeException(e);
        } finally {
            safeDelete(tmpCode128);
            safeDelete(tmpQR);
            safeDelete(tmpDM);
            safeDelete(tmpEAN);
        }
    });
}
```

**What this does**

- Generates four separate barcode images:
    - Code 128 (`ROI-CODE128-12345`)
    - QR (`ROI-QR-DEMO`)
    - Data Matrix (`ROI-DM-0001`)
    - EAN-13 (`5901234123457`)
- Creates a `920 x 420` ARGB canvas and draws each barcode at a specific position.
- Saves the resulting composite image as `roi_canvas.png`.
- Cleans up all temporary files after the canvas has been created.

These coordinates correspond to the ROIs used in the previous examples.

---

### Offset Code 128 Image: `code128_offset.png`

```java
private void ensureCode128OffsetPng() throws Exception {
    ensureImage("code128_offset.png", (fullPath) -> {
        String tmp = getFullPath("tmp_offset_code128.png");

        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "OFFSET-C128");
        gen.getParameters().getBarcode().getXDimension().setPixels(2);
        gen.getParameters().getBarcode().getBarHeight().setPixels(60);
        gen.save(tmp, BarCodeImageFormat.PNG);

        try {
            BufferedImage symbol = ImageIO.read(Paths.get(tmp).toFile());
            int canvasW = symbol.getWidth() + 200;
            int canvasH = symbol.getHeight() + 200;

            BufferedImage canvas = new BufferedImage(canvasW, canvasH, BufferedImage.TYPE_INT_ARGB);
            Graphics2D g = canvas.createGraphics();
            g.drawImage(symbol, 150, 80, null);
            g.dispose();

            ImageIO.write(canvas, "PNG", Paths.get(fullPath).toFile());
        } catch (IOException e) {
            throw new RuntimeException(e);
        } finally {
            safeDelete(tmp);
        }
    });
}
```

**What this does**

- Generates a temporary Code 128 symbol (`OFFSET-C128`) with specific size parameters.
- Creates a larger ARGB canvas around it.
- Draws the symbol at coordinates `(150, 80)`, leaving margins around the barcode.
- Saves the result as `code128_offset.png`, which is then used by the `roiSingleImageSubRegion` test.

---

### Shared Helper: `ensureImage` and `safeDelete`

```java
private void ensureImage(String fileName, ImageSupplier generator) throws Exception {
    Path p = Paths.get(IMAGES_FOLDER, fileName);
    Files.createDirectories(p.getParent());
    if (!Files.exists(p)) {
        generator.supply(p.toString());
        Assert.assertTrue(Files.exists(p), "Failed to create fixture: " + p);
        Assert.assertTrue(Files.size(p) > 0, "Fixture is empty: " + p);
    }
}
```

**What this does**

- `ensureImage` creates the parent directory, calls the generator only if the file does not exist, and asserts that the resulting file exists and is non-empty.
- `safeDelete` removes temporary files without failing the test if deletion is not possible.

---

## Summary

This guide showed how to use regions of interest (ROIs) with `BarCodeReader` in Aspose.BarCode for Java:

- Define a single ROI to limit recognition to one barcode area.
- Use 2D and 1D type groups (`TYPES_2D`, `TYPES_1D`) in combination with ROIs.
- Specify multiple ROIs in a single `BarCodeReader` instance to scan several zones at once.
- Compare full-image scanning with targeted ROI-based scanning to focus on a specific symbology.
- Work with images where the barcode is offset from the origin and select only the relevant sub-region.

All examples are taken directly from:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/roi/RegionOfInterestExamples.java" target="_blank" rel="noopener noreferrer">RegionOfInterestExamples.java</a>

Use this class as a reference when implementing ROI-based recognition in your own applications.
