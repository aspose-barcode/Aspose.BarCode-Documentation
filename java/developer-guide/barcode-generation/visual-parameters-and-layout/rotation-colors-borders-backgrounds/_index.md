---
title: Rotation, Colors, Borders, Backgrounds
type: docs
weight: 40
url: /java/developer-guide/barcode-generation2/visual-parameters-and-layout/rotation-colors-borders-backgrounds/
---

# Rotation, Colors, Borders, Backgrounds

## Overview

This page shows how to control presentation parameters such as colors, borders, and rotation.

## Notes for scan reliability

- Use a high-contrast foreground and background.
- Avoid gradients and low-contrast color pairs.
- Keep padding (quiet zone) clear of any decorative elements.

## Background and bar colors

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

public class BasicColors {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "COLOR");

        generator.getParameters().setBackColor(Color.WHITE);
        generator.getParameters().getBarcode().setBarColor(Color.BLACK);

        generator.save("barcode_colors.png", BarCodeImageFormat.PNG);
    }
}
```

## Transparent Background

To create a barcode with a transparent background (for example, to overlay on another image or a colored page), set the alpha component of the background color to 0. This typically requires saving in a format that supports transparency, such as PNG.

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

public class TransparentBackgroundExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "TRANSPARENT");

        // Set background color with Alpha = 0 (fully transparent)
        // new Color(red, green, blue, alpha)
        generator.getParameters().setBackColor(new Color(255, 255, 255, 0));
        
        // Bars remain opaque black
        generator.getParameters().getBarcode().setBarColor(Color.BLACK);

        // Save as PNG (supports transparency)
        generator.save("barcode_transparent.png", BarCodeImageFormat.PNG);
    }
}
```

## Custom RGB colors

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

public class CustomRgbColors {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.QR, "COLOR");

        generator.getParameters().setBackColor(new Color(240, 248, 255));
        generator.getParameters().getBarcode().setBarColor(new Color(25, 25, 112));

        generator.save("barcode_custom_rgb.png", BarCodeImageFormat.PNG);
    }
}
```

## Border

```java
import com.aspose.barcode.generation.*;
import java.awt.Color;

public class BorderExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "BORDER");

        generator.getParameters().getBorder().setVisible(true);
        generator.getParameters().getBorder().getWidth().setPixels(2);
        generator.getParameters().getBorder().setColor(Color.RED);

        generator.save("barcode_border.png", BarCodeImageFormat.PNG);
    }
}
```

## Rotation

You can rotate barcode images by setting the rotation angle in degrees.

```java
import com.aspose.barcode.generation.*;

public class RotationExample {
    public static void main(String[] args) throws Exception {
        BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.CODE_128, "ROTATE");

        generator.getParameters().setRotationAngle(90.0f);
        generator.save("barcode_rotate_90.png", BarCodeImageFormat.PNG);

        generator.getParameters().setRotationAngle(-90.0f);
        generator.save("barcode_rotate_-90.png", BarCodeImageFormat.PNG);

        generator.getParameters().setRotationAngle(180.0f);
        generator.save("barcode_rotate_180.png", BarCodeImageFormat.PNG);
    }
}
```
