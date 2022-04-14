---
title: Barcode Generation and Recognition Tutorial
type: docs
weight: 80
url: /java/barcode-generation-and-recognition-tutorial/
---
This tutorial explains how to use ***Aspose.BarCode for Java*** to generate a PDF417 barcode image and then read a barcode from this image.

In the task considered in this tutorial, we use Eclipse as the IDE, which is free and could be downloaded at:
<http://www.eclipse.org/downloads/>

## **Barcode Generation**
1. Start Eclipse and create a new Java project

   **Creating a new Java project** 

![todo:image_alt_text](barcode-generation-and-recognition-tutorial_1.png)

1. Call the project Demo and click **Finish**    
   We will configure the library later.

   **Naming the project** 

![todo:image_alt_text](barcode-generation-and-recognition-tutorial_2.png)

1. Right-click on the project we have just created and select required properties

   **Setting project properties** 

![todo:image_alt_text](barcode-generation-and-recognition-tutorial_3.png)

1. Click on the **Java Build Path** item and select the **Libraries** tab
1. Click **Add external Jars**
1. In the opened file dialog, locate Aspose.BarCode.jar and Servlet-api.jar. They are available in the lib directory of the download package of Aspose.BarCode for Java

   **Adding references** 

![todo:image_alt_text](barcode-generation-and-recognition-tutorial_4.png)

{{% alert color="primary" %}} 

You can use your own Servlet-api.jar if available.

{{% /alert %}}

1. Right-click on the Demo project and select **New** and then **Class** at Package Explorer.

   **Creating a new class** 

![todo:image_alt_text](barcode-generation-and-recognition-tutorial_5.png)

1. Let this new class be an Applet and name it "Test"

   **Setting properties for the new class** 

![todo:image_alt_text](barcode-generation-and-recognition-tutorial_6.png)

1. Add the code to generate a PDF417 barcode:

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-TwoD_barcodes-basic_features-Test-GenerateBarCodeDemoApplet.java" >}}

1. Right-click on this class in the package explorer and select **Run As** and **Java Applet**

![todo:image_alt_text](barcode-generation-and-recognition-tutorial_7.png)

1. Save the image to a file. Continuing the sample above, add this code to save the generated barcode image to a file:

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-TwoD_barcodes-basic_features-Test-SaveToDisk.java" >}}

## **Barcode Recognition**
Continuing the sample above, we can add the code to read a barcode from an image:

{{< gist "aspose-com-gists" "9dea2dd38be50330a824dd05da062a97" "Examples-src-main-java-com-aspose-barcode-examples-barcode_recognition-basic_features-Barcode_Recognition-Barcode_Recognition.java" >}}

The evaluation version of Aspose.BarCode for Java allows decoding only Code 39 barcodes without limitations. To test the reading speed and accuracy for other symbologies, please use the demo JAR provided in the download package.

{{% alert color="primary" %}} 

If creating an instance of class BarCodeReader throws an exception, it is probably because the image format is not supported. Download the free JAI library to load the image from [www.java.net](http://www.java.net).

{{% /alert %}}
