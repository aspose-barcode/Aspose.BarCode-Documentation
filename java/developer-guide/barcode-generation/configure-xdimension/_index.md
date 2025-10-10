---
title: "Set Barcode X-Dimension in Aspose.BarCode for Java"
description: "Learn how to configure X-Dimension for 1D and 2D barcodes in Aspose.BarCode for Java. Adjust barcode density, image size, and printing quality using precise X-Dimension values."
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/configure-xdimension/
---

# **Configuring X-Dimension in Aspose.BarCode for Java**

In *Aspose.BarCode for Java*, the **X-Dimension** defines the smallest unit of a barcode image:
- For **1D barcodes**, it is the width of the narrowest bar or space.
- For **2D barcodes**, it represents the size of a single module (square cell).

This parameter directly affects **barcode density**, **overall image size**, and **scanner readability**.

---

## **Overview**

The `X-Dimension` value is controlled through the [`getXDimension()`](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeParameters#getXDimension--) method of the `BarcodeParameters` class.

This method returns a [`Unit`](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/Unit) object, allowing you to specify the measurement in various units:

- `setPixels(int pixels)`
- `setMillimeters(float mm)`
- `setInches(float inches)`
- `setPoints(float points)`

---

## **How X-Dimension Influences Barcode Size**

The smaller the X-Dimension, the denser the barcode becomes and the more information it can store per linear inch.  
However, **reducing X-Dimension too much** may cause printing or scanning issues because very thin bars can blur or merge when printed.

Conversely, a **larger X-Dimension** produces a wider barcode but improves scan reliability.

---

## **Default Behavior**

By default, the barcode engine sets an optimal X-Dimension automatically depending on the symbology and selected `AutoSizeMode`.

- If `AutoSizeMode.NONE` is used — X-Dimension directly determines barcode size.  
- If `AutoSizeMode.Interpolation` or `AutoSizeMode.Nearest` is used — barcode width and height are prioritized, and X-Dimension may be adjusted internally.

---

## **Example 1: Setting X-Dimension in Millimeters (1D Barcode)**

```java
import com.aspose.barcode.generation.*;

public class ExampleXDimensionLinear {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ASPOSE-12345");

        // Set X-Dimension to 0.3 mm
        generator.getParameters().getBarcode().getXDimension().setMillimeters(0.3f);
        generator.getParameters().getBarcode().getBarHeight().setMillimeters(12.0f);

        // Save the generated barcode image
        generator.save("code128_xdim_0_3mm.png", BarCodeImageFormat.PNG);
    }
}
```

This code sets the width of the narrowest bar to **0.3 mm**, which is a typical value for high-resolution thermal or laser printers.

---

## **Example 2: Setting X-Dimension in Pixels (2D Barcode)**

```java
import com.aspose.barcode.generation.*;

public class ExampleXDimension2D {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.DATA_MATRIX, "ASPOSE");

        // Set the size of each module to 8 pixels
        generator.getParameters().getBarcode().getXDimension().setPixels(8);

        generator.save("datamatrix_xdim_8px.png", BarCodeImageFormat.PNG);
    }
}
```

Here, each square module of the DataMatrix barcode will have a side length of 8 pixels.

---

## **Recommended X-Dimension Values**

| Application | Typical X-Dimension | Unit | Notes |
|--------------|--------------------|-------|--------|
| Office laser printing | 0.25–0.35 | mm | High resolution (≥300 dpi) |
| Thermal label printer | 0.30–0.40 | mm | Optimal for logistics and retail |
| Inkjet / Offset printing | 0.35–0.45 | mm | Use together with BarWidthReduction |
| High-density 2D codes | 0.40–0.60 | mm | QR / DataMatrix — small modules may blur |

---

## **Combining X-Dimension with BarWidthReduction**

In offset or inkjet printing, ink spread may cause bars to become slightly thicker.  
To compensate, use **BarWidthReduction** together with **X-Dimension**:

```java
import com.aspose.barcode.generation.*;

public class ExampleBarWidthReduction {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "ASPOSE");

        // Set X-Dimension and BarWidthReduction
        gen.getParameters().getBarcode().getXDimension().setMillimeters(0.3f);
        gen.getParameters().getBarcode().getBarWidthReduction().setPixels(2);

        gen.save("code128_bwr.png", BarCodeImageFormat.PNG);
    }
}
```

This will narrow each bar by 2 pixels to offset possible ink expansion during printing.

---

## **Summary**

| Property | Description |
|-----------|--------------|
| **X-Dimension** | Defines the minimum width of bars (1D) or modules (2D). |
| **Unit** | Allows setting the value in pixels, millimeters, inches, or points. |
| **Effect** | Controls barcode density, image size, and readability. |
| **Recommended Range** | 0.25–0.45 mm for most printing scenarios. |

By carefully tuning the X-Dimension, developers can achieve optimal balance between compact barcode size and reliable scanning performance across various printing environments.

---
