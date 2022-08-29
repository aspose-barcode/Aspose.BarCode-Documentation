---
title: Generate Barcodes using Custom Classes
type: docs
weight: 50
url: /jasperreports/generate-barcodes-using-custom-class/
aliases:
- /jasperreports/generate-barcodes-using-barcodeattributesfactory/
---

The BarCodeAttributesFactory class is also included in the com.aspose.barcode.jr package. This class provides the static overloaded method Create() which accepts arguments, such as input text, barcode type, and so on. 

### **Generate BarCodes using BarCodeAttributesFactory**
The BarCodeAttributesFactory.Create() method can be called directly in a JRCML file for generating barcodes. It’s used in the <image> tag, as shown below:

``` csharp

 <image hAlign="Center">

  <reportElement x="0" y="100" width="500" height="250" />

    <imageExpression class="net.sf.jasperreports.engine.JRRenderable">

<![CDATA[new com.aspose.barcode.jr.BarCodeRenderer(com.aspose.barcode.jr.BarCodeAttributesFactory.Create("codetext","DataMatrix",java.awt.Color.RED))]]>

</imageExpression>

</image>

```

The above code sample is included into a JRXML file that renders a Data Matrix barcode image with the barcode text “codetext” and red foreground colour.

#### **Creating Custom Classes**
Generating barcodes using the BarCodeAttributesFactory.Create() method is feasible in those cases when you only need to pass input text, barcode type, and forecolor as parameters. If you want to change other properties, say the border color, background color, bar height, caption, xDimension, or yDimension, do it using a custom class. 

Create a static method in the custom class and create an instance of BarCodeAttributes. You may further call any available setxxx() methods from the BarCodeAttributes class to generate barcodes according to your specific requirements. 

Below is sample code required in the JRXML file for using the custom class.

``` csharp

 <image>

  <reportElement x="0" y="600"  width="500" height="250" />

  <imageExpression class="net.sf.jasperreports.engine.JRRenderable">

<![CDATA[new com.aspose.barcode.jr.BarCodeRenderer(MyAttributesFactory.Create("test-123","qr",java.awt.Color.RED, "caption above", "caption below"))]]>

</imageExpression>

</image>

```

In the above JRXML code snippet, we use a new class called *MyAttributesFactory*. The *Create()* method takes five arguments:

1. Input text
1. Barcode type
1. Foreground color
1. Caption above the barcode
1. Caption below the barcode

Next, we will create the **MyAttributesFactory.java** file to create the new class. Below is the code for the *MyAttributesFactory* class. 

``` csharp

 import com.aspose.barcode.jr.BarCodeAttributes;

import java.awt.*;

/**

 * A sample factory class to create BarCodeAttributes instances for reports

 */

public class MyAttributesFactory {

    public static BarCodeAttributes Create(String text, String symbology, Color foreColor, String captionAbove, String captionBelow) {

        BarCodeAttributes b = new BarCodeAttributes();

        b.setCodeText(text);

        b.setSymbology(symbology);

        b.setForeColor(foreColor);

        b.setCodeTextVisible(false);

        b.setCaptionAbove(new Caption(captionAbove));

        b.setCaptionBelow(new Caption(captionBelow));

        b.setAutoSize(true);

        return b;

    }

}

```

The *Create()* method in the above class returns an instance of type *BarCodeAttributes*. Since we are creating the instance ourselves, we can call any available method of the BarCodeAttributes class to customize the barcode image. 
