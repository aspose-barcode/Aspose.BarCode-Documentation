---
title: Installation
type: docs
weight: 30
feedback: BARCODECOM
url: /androidjava/installation/
---

## **Ways to Obtain the Product**

You can obtain ***Aspose.BarCode for Android via Java*** using two methods:

### **1. Download from the Website**

You can download the product directly from the official website:
<a href="https://releases.aspose.com/barcode/androidjava/" target="_blank">Aspose.BarCode for Android via Java Download
Page</a>.  
This is a ZIP file that contains the library in an AAR archive, API documentation as a JAR file, and other artifacts
such as the README and license-related files.

### **2. Get from Maven Repository**

Aspose hosts all Java APIs in the Maven repository.  
Alternatively, you can obtain the library from the Maven repository: 
<a href="https://releases.aspose.com/java/repo/com/aspose/aspose-barcode-android-java/" target="_blank">Aspose.BarCode
for Android via Java in the Maven Repository</a>.

You can easily integrate the product directly into your Gradle projects by adding the following configurations
to `build.gradle`.

{{<highlight gradle>}}
    repositories {
        maven {
          url "https://repository.aspose.com/repo/"
        }
     }
    dependencies {
        implementation group: 'com.aspose', name: 'aspose-barcode-android-java', version: '25.1', ext: 'aar'
        // JavaDoc dependency
        implementation group: 'com.aspose', name: 'aspose-barcode-android-java', classifier: 'javadoc', version: '25.1'
    }
    {{< /highlight >}}

