---
title: Installation
type: docs
weight: 60
url: /java/installation/
---

## **Installing Aspose.BarCode for Java from Maven Repository**
Aspose hosts all Java APIs at [Maven repository](https://releases.aspose.com/java/repo/com/aspose/). You can easily use [Aspose.BarCode for Java](https://releases.aspose.com/java/repo/com/aspose/aspose-barcode/) API directly in your Maven Projects using simple configurations.

### **Specify Maven Repository Configuration**
First, you need to specify Aspose Maven Repository configuration/location in your Maven **pom.xml** as follows:

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
Then, it is required to define Aspose.BarCode for Java API dependency in your **pom.xml** as follows:

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

After completing the above steps, Aspose.BarCode for Java dependency will be defined in your Maven Project.

## Aspose.BarCode for Android via Java

Aspose.BarCode for Android via Java is platform-independent so it can be used on any platform where the Android Runtime environment is installed and will run on Android systems based on Android OS 2.0 or greater. At present, the component has been tested on:
- Android 5.1 v 22

### **Installation**
1. Download the latest version of Aspose.BarCode for Android via Java from [Aspose Artifactory](https://repository.aspose.com/webapp/#/artifacts/browse/tree/General/repo/com/aspose/aspose-barcode/)
1. Unzip the installation package and copy the aspose-barcode-android-20.10.jar file to your Java application
1. Provide a reference to the aspose-barcode-android-20.10.jar file so the compiler can find it

### **Install Aspose.BarCode for Android via Java from Maven Repository**
1. Add maven repository into your build.gradle
1. Add 'Aspose.BarCode for Android via Java' JAR as a dependency

{{< highlight java >}}
 // 1. Add maven repository into your build.gradle
 repositories {
    mavenCentral()
    maven { url "https://releases.aspose.com/java/repo/" }
 }

 // 2. Add 'Aspose.BarCode for Android via Java' JAR as a dependency
 dependencies {
    ...
    ...
    compile (group: 'com.aspose', name: 'aspose-barcode', version: '20.10', classifier: 'android.via.java')
 }
{{< /highlight >}}

## Aspose.BarCode for Node JS via Java

### **System Requirements**
Aspose.BarCode for Node.js via Java is a platform-independent API and can be used on any platform (Windows, Linux, etc.) where [Node.js](https://nodejs.org/en/download/) and [node-java](https://github.com/joeferner/node-java) bridge are installed. The machine must have Oracle JDK 7 or greater versions before setting up the installation.

### **Installation**
To install and use Aspose.BarCode for Node.js via Java, follow the instructions below:

#### **Linux**
- Download and install Node.js
- Install Oracle JDK (1.8 and higher) for Linux and then configure the JAVA_HOME environment variable
- Install Python 3.x
- Install aspose.barcode: 'npm i aspose.barcode'  
- You can also download "Aspose.BarCode for Node.js via Java" from https://downloads.aspose.com/barcode/nodejs and extract it
- You can go to examples directory and launch examples

#### **Windows**
- Download and install Node.js and add node.exe to PATH
- Install Oracle JDK (1.8 and higher) for Windows and then configure the JAVA_HOME environment variable
- Install Python 3.x and add python.exe to PATH
- Install aspose.barcode: 'npm i aspose.barcode'
- You can also download "Aspose.BarCode for Node.js via Java" from https://downloads.aspose.com/barcode/nodejs and extract it
- You can go to examples directory and view examples

#### **MacOS**
- Download and install Node.js and configure environment variables
- Install Oracle JDK 1.8 and higher for MacOS and then configure the JAVA_HOME environment variable
- Install Python 3.x and configure environment variables
- Modify <key>JVMCapabilities</key> section in "/Library/Java/JavaVirtualMachines/jdk1.8.0_152.jdk/Contents/Info.plist" with root privilege. ("jdk1.8.0_152.jdk" depends on your jdk version)
- Install aspose.barcode: 'npm i aspose.barcode'
- You can also download "Aspose.BarCode for Node.js via Java" from https://downloads.aspose.com/barcode/nodejs and extract it
- You can go to examples directory and launch examples

## Aspose.BarCode for PHP via Java

Aspose.BarCode for PHP via Java is a platform-independent API that can be used on any platform (Windows, Linux, etc.) where PHP and Java Bridge are installed.

### **System Requirements**
- Tomcat Server 8.0 or above is installed
- PHP/JavaBridge is configured
- FastCGI is installed
- Aspose.Barcode component is downloaded

### **Supported Platforms**
- PHP 5.x or 7.x
- Java 1.8 or above

### **Installation**
**Method 1**
- Clone the Repository
{{< highlight php >}}
git clone git@github.com:asposemarketplace/Aspose-Barcode-Java-for-PHP.git
{{< /highlight >}}

- Setup the project using composer
{{< highlight php >}}
composer install
{{< /highlight >}}

**Method 2**
- Add the following lines to the composer.json file of your PHP project
{{< highlight php >}}
{    
    "require": {        
        "asposebarcode/aspose_barcode_java_for_php": "dev-master"    
    }
}
{{< /highlight >}}

- Run the install command
{{< highlight php >}}
composer install
{{< /highlight >}}

{{% alert color="primary" %}}

Read more about composer on http://www.getcomposer.com

{{% /alert %}}
