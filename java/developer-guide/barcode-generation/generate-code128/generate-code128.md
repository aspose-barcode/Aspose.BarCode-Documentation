---
title: Generate Code128
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/generate-code128/
---

# Generate Code 128 — Quick Guide

## Overview

**Code 128** is a high‑density linear symbology widely used in logistics, inventory, and retail.  
It supports the full ASCII set and provides excellent data density and reliability. Aspose.BarCode for Java
automatically optimizes **subset selection (A/B/C)** for your input to keep symbols compact.

---

## Quick Start

```java
import com.aspose.barcode.generation.*;

public class Code128QuickStart {
    public static void main(String[] args) {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ASPOSE123");
        // Reasonable defaults are applied automatically
        generator.save("code128_quick.png", BarCodeImageFormat.PNG);
    }
}
```

---

## Common Scenarios

### 1) Control Size (X‑Dimension & Height)

```java
import com.aspose.barcode.generation.*;

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "ABC123");

// X‑Dimension (narrow bar width)
gen.getParameters().getBarcode().getXDimension().setPixels(2);
// Or in millimeters
gen.getParameters().getBarcode().getXDimension().setMillimeters(0.3f);

// Bar (symbol) height
gen.getParameters().getBarcode().getBarHeight().setPixels(60);
// Or in millimeters
gen.getParameters().getBarcode().getBarHeight().setMillimeters(15.0f);

gen.save("code128_sized.png", BarCodeImageFormat.PNG);
```

### 2) Human‑Readable Text (Code Text)

```java
import com.aspose.barcode.generation.*;

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "PRODUCT-789");

// Show codetext BELOW the bars (if CodeTextParameters are present in your build)
gen.getParameters().getBarcode().getCodeTextParameters().setLocation(CodeLocation.BELOW);
// Font and spacing
gen.getParameters().getBarcode().getCodeTextParameters().setFont(new FontUnit("Arial", 12));
gen.getParameters().getBarcode().getCodeTextParameters().getSpace().setPoint(2);

gen.save("code128_with_text.png", BarCodeImageFormat.PNG);
```

### 3) Print Quality (Resolution)

```java
import com.aspose.barcode.generation.*;

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "PRINT-READY");

// 300 DPI is a typical target for labels
gen.getParameters().setResolution(300.0f);

gen.save("code128_300dpi.png", BarCodeImageFormat.PNG);
```

### 4) Colors, Quiet Zone (Padding) & Border

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "STYLE-01");

// Colors
gen.getParameters().setBackColor(Color.WHITE);
gen.getParameters().getBarcode().setBarColor(Color.BLACK);

// Quiet zone (padding) for reliable scanning
gen.getParameters().getBarcode().getPadding().getLeft().setPixels(12);
gen.getParameters().getBarcode().getPadding().getRight().setPixels(12);
gen.getParameters().getBarcode().getPadding().getTop().setPixels(6);
gen.getParameters().getBarcode().getPadding().getBottom().setPixels(6);

// Optional border for visualization
gen.getParameters().getBorder().setVisible(true);
gen.getParameters().getBorder().getWidth().setPixels(2);

gen.save("code128_style.png", BarCodeImageFormat.PNG);
```

### 5) Rotation

```java
import com.aspose.barcode.generation.*;

BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "ROTATE");
gen.getParameters().setRotationAngle(90.0f);
gen.save("code128_rotate_90.png", BarCodeImageFormat.PNG);
```

---

## GS1‑128 (EAN‑128)

GS1‑128 is a structured variant of Code 128 that uses **Application Identifiers (AIs)**:

```java
import com.aspose.barcode.generation.*;

BarcodeGenerator gen = new BarcodeGenerator(
    EncodeTypes.GS_1_CODE_128,
    "(01)09501101530008(17)251231(10)BATCH-42"
);
// FNC1 is handled automatically for GS1
gen.save("gs1_128.png", BarCodeImageFormat.PNG);
```

**Common AIs:** `(01)` GTIN, `(10)` Batch/Lot, `(17)` Expiration Date, `(21)` Serial Number.

---

## Subsets (A/B/C) — How It Works

- **A**: Uppercase + control chars; **B**: Upper+Lower + symbols; **C**: double‑digit numeric pairs (max density).  
- The engine **auto‑switches** subsets to minimize symbol length. You can just pass your string.

```java
// Numeric → Subset C for compactness
new BarcodeGenerator(EncodeTypes.CODE_128, "123456789012");

// Mixed content → optimal automatic switching
new BarcodeGenerator(EncodeTypes.CODE_128, "ABC123def456");
```

---

## Best Practices

1. **X‑Dimension**: 0.30–0.40 mm for label printers; 2–3 px for on‑screen.  
2. **Quiet Zone**: ≥ 10× X‑Dimension on left/right; a few modules on top/bottom.  
3. **Height**: ≥ 15% of barcode width or ≥ 0.25 in for printed labels.  
4. **Resolution**: ≥ 300 DPI for print.  
5. **Test Scanning** with your target devices and media.  
6. **Keep Data Reasonable**: shorter strings scan faster and produce smaller symbols.

---

## Full Example

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

public class CompleteCode128Example {
    public static void main(String[] args) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "INVENTORY-2025-001");

            // Geometry
            gen.getParameters().getBarcode().getXDimension().setMillimeters(0.33f);
            gen.getParameters().getBarcode().getBarHeight().setMillimeters(16.0f);

            // Print quality
            gen.getParameters().setResolution(300.0f);

            // Code text (if available in your build)
            gen.getParameters().getBarcode().getCodeTextParameters().setLocation(CodeLocation.BELOW);
            gen.getParameters().getBarcode().getCodeTextParameters().setFont(new FontUnit("Arial", 10));
            gen.getParameters().getBarcode().getCodeTextParameters().getSpace().setPoint(2);

            // Styling
            gen.getParameters().setBackColor(Color.WHITE);
            gen.getParameters().getBarcode().setBarColor(Color.BLACK);
            gen.getParameters().getBorder().setVisible(true);
            gen.getParameters().getBorder().getWidth().setPixels(2);
            gen.getParameters().getBarcode().getPadding().getLeft().setPixels(12);
            gen.getParameters().getBarcode().getPadding().getRight().setPixels(12);
            gen.getParameters().getBarcode().getPadding().getTop().setPixels(6);
            gen.getParameters().getBarcode().getPadding().getBottom().setPixels(6);

            gen.save("code128_complete.png", BarCodeImageFormat.PNG);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

---

## Error Handling

```java
try {
    BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.CODE_128, "YOUR-DATA");
    gen.save("output.png", BarCodeImageFormat.PNG);
} catch (Exception e) {
    System.err.println("Error generating barcode: " + e.getMessage());
}
```

---

## See Also

- [Configure X‑Dimension](../configure-xdimension/)
- [Customize Appearance](../customize-appearance/)
- [GS1‑128 Overview](/java/developer-guide/barcode-generation/gs1-128/)
