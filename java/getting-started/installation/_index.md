---
title: Installation
type: docs
weight: 60
url: /java/installation/
---

## **Install Aspose.BarCode for Java from Maven Repository**
Aspose hosts all Java APIs at [Maven repository](https://releases.aspose.com/java/repo/com/aspose/). You can easily use [Aspose.BarCode for Java](https://releases.aspose.com/java/repo/com/aspose/aspose-barcode/) API directly in your Maven Projects using simple configurations.

### **Specify Maven Repository Configuration**
First, you need to specify an Aspose Maven Repository configuration/location in your Maven **pom.xml** as follows:

{{< highlight java >}}

 <repositories>

    <repository>

        <id>AsposeJavaAPI</id>

        <name>Aspose Java API</name>

        <url>https://releases.aspose.com/java/repo/</url>

    </repository>

</repositories>

{{< /highlight >}}

### **Define Aspose.BarCode for Java API Dependency**
Then, it is required to define an ***Aspose.BarCode for Java*** API dependency in your **pom.xml** as follows:

{{< highlight java >}}

 <dependencies>

    <dependency>

        <groupId>com.aspose</groupId>

        <artifactId>aspose-barcode</artifactId>

        <version>20.10</version>

		<classifier>jdk17</classifier>

    </dependency>

</dependencies>

{{< /highlight >}}

After completing the above steps, the ***Aspose.BarCode for Java*** dependency will be defined in your Maven Project.

