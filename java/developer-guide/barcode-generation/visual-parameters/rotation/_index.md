---
title: "Rotate Barcode Images"
description: "Learn how to rotate generated barcode images in Aspose.BarCode for Java using right-angle and arbitrary rotation values."
type: docs
weight: 70
url: /java/developer-guide/barcode-generation/visual-parameters/rotation/
---

# Rotate Barcode Images

Aspose.BarCode for Java allows you to rotate the complete generated barcode image without changing the encoded data.

Rotation is applied to:

- barcode bars or modules;
- human-readable code text;
- captions;
- padding;
- borders.

The complete source code for the examples in this article is available on GitHub:

<a href="https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/visual_parameters/RotationExample.java" target="_blank">View RotationExample.java</a>

set

## Rotate a barcode by 90 degrees

Use `setRotationAngle` to rotate a generated image clockwise.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "ROTATE-90"
);

generator.getParameters().setRotationAngle(90.0f);

generator.save(
        "code128_rotate_90.png",
        BarCodeImageFormat.PNG
);
```

Right-angle rotations such as 90, 180, and 270 degrees usually preserve crisp barcode geometry and are broadly compatible with scanners.

## Rotate a barcode by 180 degrees

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "ROTATE-180"
);

generator.getParameters().setRotationAngle(180.0f);

generator.save(
        "code128_rotate_180.png",
        BarCodeImageFormat.PNG
);
```

## Use a negative rotation angle

Negative values rotate the image counterclockwise.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "ROTATE-NEGATIVE"
);

generator.getParameters().setRotationAngle(-90.0f);

generator.save(
        "code128_rotate_negative_90.png",
        BarCodeImageFormat.PNG
);
```

## Rotate by an arbitrary angle

The API accepts arbitrary angle values.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.QR,
        "ARBITRARY-ANGLE"
);

generator.getParameters().setRotationAngle(25.0f);

generator.save(
        "qr_rotate_25.png",
        BarCodeImageFormat.PNG
);
```

Angles that are not multiples of 90 degrees can require a larger output canvas and may introduce interpolation around barcode edges. This can reduce recognition reliability for small or low-resolution images.

## Recommendations

- Prefer 90, 180, and 270 degree rotations when possible.
- Use a sufficiently large module or bar width.
- Keep enough padding so that the rotated symbol is not clipped.
- Test arbitrary-angle images with the intended scanner.
- Verify the final image after printing or format conversion.
