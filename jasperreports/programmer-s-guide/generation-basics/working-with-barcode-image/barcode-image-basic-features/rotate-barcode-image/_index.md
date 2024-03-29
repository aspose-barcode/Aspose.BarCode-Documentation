---
title: Rotate Barcode Image
type: docs
weight: 30
url: /jasperreports/rotate-barcode-image/
---

***Aspose.BarCode for JasperReports*** allows developers to rotate the barcode image by calling the setRotationAngle() method of the BarCodeAttributes class. 
The effects of some rotation angles are demonstrated in the figure below. 

**Figure: Demonstration of common rotation angles** 

![todo:image_alt_text](rotate-barcode-image_1.png)


### **Rotating Barcodes**
The barcode below is rotated 180 degrees. It is the output of the sample code shown below. 

**Barcode rotated 180 degrees** 

![todo:image_alt_text](rotate-barcode-image_2.png)

#### **Programming Sample**
**Java**

``` java

public class MyAttributes

{

    public static BarCodeAttributes Create(String text, String symbology)

    {

        BarCodeAttributes b = new BarCodeAttributes();

        b.setCodeText(text);

        b.setSymbology(symbology);

        //Roate clockwise for 180 degree (upside down)

        b.setRotationAngle(180);

        return b;

    }

}

```

**JRXML**

``` java

<image hAlign="Center">

<reportElement x="0" y="600"  width="500" height="250" />                

<imageExpression class="net.sf.jasperreports.engine.JRRenderable">

   <![CDATA[new com.aspose.barcode.jr.BarCodeRenderer(MyAttributes.Create(

      "12345678", "Code128")

   )]]>

</imageExpression>

</image>

```
