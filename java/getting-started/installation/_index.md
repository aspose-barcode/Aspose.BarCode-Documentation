---
title: Installation
type: docs
weight: 60
feedback: BARCODECOM
url: /java/installation/
---

## **Install Aspose.BarCode for Java from Maven Repository**

Aspose hosts all Java APIs in the <a href="https://repository.aspose.com/repo/" target="_blank">Maven repository</a>.  
You can easily use <a href="https://repository.aspose.com/repo/com/aspose/aspose-barcode/" target="_blank">Aspose.BarCode for Java</a>  
API directly in your Maven projects by adding the following configurations to `pom.xml`.

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

