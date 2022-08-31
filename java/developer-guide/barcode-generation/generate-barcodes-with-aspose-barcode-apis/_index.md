---
title: Barcode Generation in Aspose.BarCode API for Java
linktitle: Barcode Generation API
type: docs
weight: 70
url: /java/generate-barcodes-with-aspose-barcode-apis/
---

## **Generate Barcode in Java Console Application**
Developers might need to generate barcode images at the back end programmatically. This requirement can be useful to:

- generate barcode images and then save them to a database
- save barcode images in some other locations after creating them at runtime
- integrate the barcode generation feature into some other applications

There can be plenty of other reasons to work with barcodes at the back end which depend upon the developer's requirements.

[Aspose.BarCode](https://www.aspose.com/products/barcode/java) provides class [*BarcodeGenerator*](https://reference.aspose.com/barcode/java/com.aspose.barcode.generation/BarcodeGenerator) to generate barcodes. Developers can create an instance of this class, set properties, and save the barcode image to any location.

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-barcode-basic_features-SetCodeText-.java" >}}
  
The resulting barcode image generated by the code above can be seen below.
  
|![todo:image_alt_text](http://i.imgur.com/eZ68GPM.jpg)|
| :- |
|**Output image**|
  
## **Generate Barcode in Java Swing application**
Follow the steps below to use Aspose.BarCode in Java Swing applications:
1. Design your Swing application as shown in the figure below using your choice of the GUI tool. For example, Netbeans or Eclipse.
  
|![todo:image_alt_text](http://i.imgur.com/djVeP0U.png)|
| :- |
|**Basic Swing application**|
  
2. [Activate the license](/barcode/java/licensing/) to the control to avoid the evaluation watermark in the barcode image. The code that enables the license can be added to the constructor or some custom initialization method of the form.

3. Add the code to the project:

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-ApplyALicense-ApplyALicense.java" >}}

4. On the button event handler method, write the following code to generate the barcode image and save it to disk. Then, use the Graphics object to render the image on the frame.

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-barcode_image-rendering_features-RenderBarcodeToGraphicsObject-.java" >}}

5. Run the application. You should get output similar to the screenshot below.
  
|![todo:image_alt_text](http://i.imgur.com/iaTvIL8.png)|
| :- |
|**Output barcode image**|
  