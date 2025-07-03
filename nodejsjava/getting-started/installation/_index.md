---
title: Installation
type: docs
weight: 30
url: /nodejsjava/installation/
---

### **Platform and Compatibility**

**Aspose.BarCode for Node.js via Java** is a cross-platform product that runs on any operating system (**Windows**, **Linux**, **macOS**, **Solaris**) where both **Node.js** and **Java** are installed.

### **System Requirements**

- **Node.js**: Version 18 or higher
- **Java**: JDK 1.8 or higher

It supports various JDK distributions, including but not limited to:
- **Oracle JDK**
- **BellSoft Liberica JDK**
- **Amazon Corretto**
- **OpenJDK**
- **Other compatible distributions**

### **Installation Options**

You can install the product in two main ways:

#### **1. Install via npm**
The recommended way is to install the package from npm:  
<a href="https://www.npmjs.com/package/aspose.barcode" target="_blank">Aspose.BarCode for Node.js on npm</a>

```bash
npm install aspose.barcode
```
or specific version
```bash
npm i aspose.barcode@25.6.0
```
The library will be installed to `node_modules`.
#### **2. Manual ZIP Installation**
   If you do not use npm for installation, you can download Aspose.BarCode for Node.js via Java as a ZIP archive from the
   <a href="https://releases.aspose.com/barcode/nodejs/" target="_blank">official Aspose website</a>.

Steps:
Download the ZIP file and extract its contents.

Copy the libs folder from the extracted archive into your project directory. 
You can rename it (e.g., to barcode-lib), but do not place it inside node_modules.
Example project structure:

your-project/
├── barcode-lib/
│   ├── index.js
│   ├── lib/
│   │   ├── AsposeBarcode.js
│   │   ├── Joint.js
│   │   ├── ...other .js files
│   │   └── aspose-barcode-nodejs-25.5.jar
│   └── package.json
├── node_modules/
├── package.json
├── index.js
└── ...



This archive contains:

doc/ — API documentation
license/ — End User License Agreement and third-party licenses
libs/ — Java JAR file and supporting files
examples/ — code examples
readme.txt — general instructions



