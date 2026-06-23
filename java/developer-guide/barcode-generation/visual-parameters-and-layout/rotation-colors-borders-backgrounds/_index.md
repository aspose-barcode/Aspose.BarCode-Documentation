---
title: "Rotation, Colors, Borders, and Backgrounds"
description: "Customize barcode rotation, foreground colors, backgrounds, transparency, padding, and borders."
type: docs
weight: 24
url: /java/developer-guide/barcode-generation/visual-parameters-and-layout/rotation-colors-borders-backgrounds/
---

# Rotation, Colors, Borders, and Backgrounds

The appearance of a barcode image can be customized without changing the encoded data.

## Rotate the barcode

```java
generator.getParameters().setRotationAngle(90.0f);
```

The rotation is applied to the complete generated image. Arbitrary angles are supported, but right-angle rotations generally preserve crisp module geometry more reliably.

## Set module and background colors

```java
generator.getParameters().setBackColor(new Color(245, 248, 252));
generator.getParameters().getBarcode().setBarColor(new Color(20, 45, 90));
```

Maintain strong contrast between bars or modules and the background. Low-contrast combinations can reduce recognition reliability.

## Add a border

```java
generator.getParameters().getBorder().setVisible(true);
generator.getParameters().getBorder().setColor(Color.GRAY);
generator.getParameters().getBorder().getWidth().setPixels(2);
generator.getParameters().getBorder().setDashStyle(BorderDashStyle.SOLID);
```

A border must not intrude into the required blank margins around the barcode.

## Use transparency

PNG supports an alpha channel, so an ARGB color can be used as a transparent or semi-transparent background.

```java
generator.getParameters().setBackColor(new Color(255, 255, 255, 0));
```

Some output formats do not preserve transparency. Test the final image format and rendering pipeline.

## Complete example


<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/RotationExample.java" target="_blank">View RotationExample.java</a>

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/ColorsExample.java" target="_blank">View ColorsExample.java</a>

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/BordersExample.java" target="_blank">View BordersExample.java</a>

You can also browse the <a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation" target="_blank">Generation examples directory</a>.