---
title: "Region of Interest (ROI)"
description: "Learn how to limit barcode recognition to specific regions in an image using BarCodeReader in Aspose.BarCode for Java."
type: docs
weight: 40
url: /java/developer-guide/barcode-recognition/region-of-interest
---

# Barcode Recognition in a Region of Interest (ROI)

`BarCodeReader` in Aspose.BarCode for Java allows you to restrict recognition to specific rectangular areas of an image,  
known as *regions of interest* (ROIs). This can significantly reduce processing time and improve recognition accuracy  
when barcodes are located in known zones on complex layouts.

Typical scenarios for using ROI:

- A barcode occupies a fixed area of a label or form.
- Several different barcodes are placed in distinct regions of a single image.
- You want to focus recognition on 1D or 2D barcodes in a specific part of the image.
- You want to compare full-image recognition with targeted recognition inside a sub-region.
- A barcode is offset inside a larger canvas (for example, centered with margins).

All examples in this article are based on the sample class:

`com.aspose.barcode.guide.recognition.roi.RegionOfInterestExamples`

You can find the full source code on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/roi/RegionOfInterestExamples.java" target="_blank" rel="noopener noreferrer">RegionOfInterestExamples.java</a>

In the snippets below, `getFullPath("...")` represents a helper that returns the file system path to the sample image.  
In your code you can pass a plain file path string instead.

---

## 1. Limiting Recognition to a Single Region

The simplest use case is to scan only one rectangular area of the image that contains a specific barcode.  
This helps to ignore all other content (background graphics, text, additional symbols) outside the region.

```java
Rectangle roi = new Rectangle(20, 20, 440, 140);
BarCodeReader reader = new BarCodeReader(getFullPath("roi_canvas.png"), roi, DecodeType.CODE_128);
```

In this example:

- `roi` defines a rectangular region where a Code 128 barcode is located.
- The `BarCodeReader` constructor receives:
    - the image path,
    - the ROI rectangle,
    - the expected barcode type (`DecodeType.CODE_128`).

Only the specified region is scanned instead of the full image.

---

## 2. Using ROI with 2D Barcode Type Groups

If you know that a given region contains a 2D barcode, but do not want to hard-code a specific symbology,  
you can pass the `TYPES_2D` group as the decode type. The ROI will still limit recognition to the selected area.

```java
Rectangle roi = new Rectangle(470, 10, 250, 250);
BarCodeReader reader = new BarCodeReader(getFullPath("roi_canvas.png"), roi, DecodeType.TYPES_2D);
```

Here:

- The rectangle bounds the area of a QR code on the sample canvas.
- `DecodeType.TYPES_2D` instructs `BarCodeReader` to search for any supported 2D barcode type inside that region.
- This approach is useful when the image layout is fixed, but the exact 2D symbology may vary.

---

## 3. Multiple ROIs in a Single Pass

A common pattern is to read several barcodes from fixed positions on the same image (for example, top-left and bottom-right corners).  
`BarCodeReader` can accept an array of rectangles to scan multiple ROIs in one pass.

```java
Rectangle[] areas = new Rectangle[] {
    new Rectangle(20, 20, 440, 140),
    new Rectangle(470, 240, 450, 160)
};

BarCodeReader reader = new BarCodeReader(getFullPath("roi_canvas.png"), areas, DecodeType.TYPES_1D);
BarCodeResult[] results = reader.readBarCodes();
```

In this example:

- The first rectangle covers a Code 128 area.
- The second rectangle covers an EAN-13 area.
- `DecodeType.TYPES_1D` limits recognition to all supported 1D barcode types.
- `readBarCodes()` returns all barcodes found in the specified ROIs.

This pattern is well suited for structured documents and labels with multiple fixed barcode fields.

---

## 4. Full-Image Scan vs ROI-Based Scan

Sometimes it is useful to first scan the entire image to confirm that multiple barcodes are present,  
and then perform ROI-based recognition to focus on a particular symbology in a known area.

```java
BarCodeReader fullReader =
        new BarCodeReader(getFullPath("roi_canvas.png"), DecodeType.ALL_SUPPORTED_TYPES);
BarCodeResult[] fullResults = fullReader.readBarCodes();

Rectangle dataMatrixArea = new Rectangle(10, 190, 230, 230);
BarCodeReader roiReader =
        new BarCodeReader(getFullPath("roi_canvas.png"), dataMatrixArea, DecodeType.DATA_MATRIX);
BarCodeResult[] roiResults = roiReader.readBarCodes();
```

Here:

- The full-image reader uses `DecodeType.ALL_SUPPORTED_TYPES` to detect all possible barcodes on the canvas.
- The ROI reader is restricted to a rectangle that contains a Data Matrix symbol and uses `DecodeType.DATA_MATRIX`.
- This combination lets you:
    - verify the overall content of the image,
    - and then focus on a specific region and symbology for more precise processing.

---

## 5. ROI on an Image with an Offset Barcode

Barcodes are not always aligned with the image origin. They may be placed with margins or centered on a larger canvas.  
In such cases, you can select a sub-region that encloses the symbol and ignore the rest of the image.

```java
Rectangle roi = new Rectangle(150, 80, 480, 160);
BarCodeReader reader = new BarCodeReader(getFullPath("code128_offset.png"), roi, DecodeType.CODE_128);
BarCodeResult[] results = reader.readBarCodes();
```

In this scenario:

- The file `code128_offset.png` contains a single Code 128 symbol drawn away from the top-left corner.
- The ROI rectangle covers only the barcode area.
- `BarCodeReader` processes only this sub-region, which is helpful when the margins or background graphics are not relevant.

---

## Summary

Regions of interest (ROIs) allow you to control exactly where `BarCodeReader` looks for barcodes inside an image.  
By providing one or more `Rectangle` instances to the constructor, you can:

- Speed up recognition on large or complex images.
- Reduce the influence of background noise and unrelated content.
- Combine ROIs with type groups like `TYPES_1D` and `TYPES_2D`.
- Compare full-image scanning with focused recognition in specific zones.
- Work effectively with layouts where barcodes are placed away from the image origin.

All ROI examples shown here are based on:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/recognition/roi/RegionOfInterestExamples.java" target="_blank" rel="noopener noreferrer">RegionOfInterestExamples.java</a>

Use the demonstrated patterns as a reference when adding ROI-based recognition to your own Java applications.
