---
title: Installation
type: docs
weight: 60
feedback: BARCODECOM
url: /java/installation/
---
## **Ways to Obtain the Product**

You can obtain ***Aspose.BarCode for Java*** using two methods:

### **1. Download the ZIP File from the Website**

You can get the product directly from the <a href="https://releases.aspose.com/barcode/java/" target="_blank">official 
website</a>.

For example, if you want to download
<a href="https://releases.aspose.com/barcode/java/25-1/#package-explorer" target="_blank">aspose-barcode-25.1-java.zip</a>,
you can do so from the link above.

This ZIP file contains the library, API documentation as a JAR file, and other artifacts such as the README and
license-related files.

### **2. Get from Maven Repository**

Aspose hosts all Java APIs in the Maven repository.  
Alternatively, you can obtain the library from the Maven repository:
<a href="https://repository.aspose.com/repo/com/aspose/aspose-barcode/" target="_blank">Aspose.BarCode for Java</a>.

You can easily integrate the product into your Gradle projects by adding the following configurations to `pom.xml`.

{{<highlight xml>}}
<repositories>
   <repository>
     <id>aspose-barcode-java</id>
     <name>Aspose Barcode Java</name>
     <url>https://releases.aspose.com/java/repo/</url>
  </repository>
</repositories>
{{< /highlight >}}

{{<highlight xml>}}
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-barcode</artifactId>
        <version>25.1</version>
    </dependency>
</dependencies>
{{</highlight>}}
or
{{<highlight xml>}}
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-barcode</artifactId>
        <version>25.1</version>
        <classifier>jdk18</classifier>
    </dependency>
</dependencies>
{{</highlight>}}

and JavaDoc
{{<highlight xml>}}
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-barcode</artifactId>
        <version>25.1</version>
        <classifier>javadoc</classifier>
        <scope>provided</scope>
    </dependency>
{{</highlight>}}

For Gradle-based applications, you should use the following settings:

{{<highlight gradle>}}
repositories {
    maven {
        url "https://repository.aspose.com/repo/"
    }
}
dependencies {
    implementation group: 'com.aspose', name: 'aspose-barcode', version: '25.1'
    // Alternative version with JDK 18 classifier
    implementation group: 'com.aspose', name: 'aspose-barcode', classifier: 'jdk18', version: '25.1'
    // JavaDoc dependency
    implementation group: 'com.aspose', name: 'aspose-barcode', classifier: 'javadoc', version: '25.1'
}

{{< /highlight >}}

