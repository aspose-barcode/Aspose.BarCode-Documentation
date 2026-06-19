---

title: "Generate Code 128 Barcodes"
description: "Learn how to generate Code 128 barcodes in Aspose.BarCode for Java, configure human-readable text, print resolution, colors, padding, borders, rotation, and compact layouts."
type: docs
weight: 10
url: /java/developer-guide/barcode-generation/generate-code128/
---------------------------------------------------------------

# Generate Code 128 Barcodes

Code 128 is a high-density linear symbology that can encode numeric data, uppercase and lowercase letters, punctuation, and control characters. By default, Aspose.BarCode for Java uses automatic encoding mode to select and switch between Code 128 code sets A, B, and C.

The complete source code for the examples in this article is available on GitHub:

[View GenerateCode128.java](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/blob/master/src/test/java/com/aspose/barcode/guide/generation/GenerateCode128.java)

You can also browse all barcode generation examples in the [Generation examples directory](https://github.com/aspose-barcode/Aspose.BarCode-for-Java/tree/master/src/test/java/com/aspose/barcode/guide/generation).

## Generate a basic Code 128 barcode

Create a `BarcodeGenerator` with `EncodeTypes.CODE_128`, provide the code text, and save the generated image.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "ASPOSE COMPANY"
);

generator.save("code128_quick.png", BarCodeImageFormat.PNG);
```

The default automatic encoding mode selects suitable Code 128 code sets for the supplied data.

## Configure human-readable text

The human-readable code text can be positioned below the bars and formatted through the `CodetextParameters` object returned by `getCodeTextParameters()`.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "PRODUCT-789"
);

CodetextParameters code_text_parameters = generator.getParameters()
        .getBarcode()
        .getCodeTextParameters();

code_text_parameters.setLocation(CodeLocation.BELOW);
code_text_parameters.setFontMode(FontMode.MANUAL);

code_text_parameters.getFont().setFamilyName("Arial");
code_text_parameters.getFont().setStyle(FontStyle.REGULAR);
code_text_parameters.getFont().getSize().setPoint(12);

code_text_parameters.getSpace().setPoint(2);

generator.save("code128_with_text.png", BarCodeImageFormat.PNG);
```

`FontMode.MANUAL` is required when the font size should be taken from the configured `FontUnit`. In automatic font mode, the library calculates the font size based on the barcode dimensions.

The value returned by `getSpace()` defines the distance between the bars and the human-readable text.

The selected font family must be available in the runtime environment. Otherwise, Java may substitute another installed font.

## Prepare a barcode for 300 dpi output

Use `setResolution` to define the output resolution. The following example also defines an image bounding box and uses `AutoSizeMode.NEAREST` to fit the barcode while preserving its aspect ratio.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "PRINT-READY-001"
);

generator.getParameters().setResolution(300.0f);
generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);
generator.getParameters().getImageWidth().setPixels(400);
generator.getParameters().getImageHeight().setPixels(150);

generator.save("code128_300dpi.png", BarCodeImageFormat.PNG);
```

`AutoSizeMode.NEAREST` selects the nearest barcode size that fits within the specified image dimensions while preserving the default aspect ratio.

The resolution value is especially important when barcode dimensions are specified in physical units such as millimeters, inches, or points. When image dimensions are specified directly in pixels, increasing the resolution value does not by itself increase the number of pixels in the image.

## Configure colors, padding, and border

Barcode appearance can be customized through common generation parameters.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "STYLE-2025"
);

// Colors
generator.getParameters().setBackColor(Color.WHITE);
generator.getParameters().getBarcode().setBarColor(Color.BLACK);

// Blank margins around the barcode
generator.getParameters().getBarcode().getPadding().getLeft().setPixels(12);
generator.getParameters().getBarcode().getPadding().getRight().setPixels(12);
generator.getParameters().getBarcode().getPadding().getTop().setPixels(6);
generator.getParameters().getBarcode().getPadding().getBottom().setPixels(6);

// Border
generator.getParameters().getBorder().setVisible(true);
generator.getParameters().getBorder().setColor(Color.GRAY);
generator.getParameters().getBorder().getWidth().setPixels(2);

generator.save("code128_styled.png", BarCodeImageFormat.PNG);
```

Left and right padding create blank margins that can be used to reserve space for the required quiet zones. The required quiet-zone width depends on the X-dimension and the applicable barcode specification, so fixed pixel values should be validated for the intended output size and scanning environment.

A visible border must not intrude into the required quiet zones.

## Rotate a Code 128 barcode

Call `setRotationAngle` to rotate the generated barcode image.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "ROTATE-ME"
);

generator.getParameters().setRotationAngle(90.0f);
generator.save("code128_rotate_90.png", BarCodeImageFormat.PNG);
```

Rotation is applied to the complete generated image, including the bars, human-readable text, and padding.

The API accepts arbitrary rotation angles. However, right-angle rotations such as 90, 180, and 270 degrees are generally easier for barcode scanners to read.

## Encode numeric, mixed, and lowercase content

In automatic encoding mode, Aspose.BarCode selects Code 128 code sets according to the supplied data.

### Numeric content

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "123456789012"
);

generator.save("code128_numeric.png", BarCodeImageFormat.PNG);
```

Code set C can encode pairs of digits efficiently, making it suitable for long numeric sequences.

### Mixed content

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "ABC1234567890def"
);

generator.save("code128_mixed.png", BarCodeImageFormat.PNG);
```

The long numeric sequence allows automatic encoding mode to use code set C for the numeric part and another code set for the alphabetic parts.

### Lowercase text

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "product-code"
);

generator.save("code128_lowercase.png", BarCodeImageFormat.PNG);
```

Lowercase letters are encoded using code set B.

## Create a compact Code 128 image

To fit a barcode into a small image bounding box, hide the human-readable text, reduce vertical padding, enable `AutoSizeMode.NEAREST`, and specify the target image dimensions.

```java
BarcodeGenerator generator = new BarcodeGenerator(
        EncodeTypes.CODE_128,
        "SIZE-DEMO-123"
);

generator.getParameters()
        .getBarcode()
        .getCodeTextParameters()
        .setLocation(CodeLocation.NONE);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getTop()
        .setPixels(1);

generator.getParameters()
        .getBarcode()
        .getPadding()
        .getBottom()
        .setPixels(1);

generator.getParameters().setAutoSizeMode(AutoSizeMode.NEAREST);
generator.getParameters().getImageWidth().setPixels(300);
generator.getParameters().getImageHeight().setPixels(60);

generator.save("code128_tiny_no_text.png", BarCodeImageFormat.PNG);
```

When `AutoSizeMode.NEAREST` is enabled, the library determines the effective X-dimension and bar height required to fit the barcode into the target image box. Explicit `XDimension` and `BarHeight` values are ignored in this mode.

To control X-dimension and bar height directly, keep `AutoSizeMode.NONE` and do not specify a fixed image bounding box.

Compact layouts should always be tested with the intended recognition device, printing process, and output medium.
