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
### **Manual ZIP Installation**

If you do not want to use npm to install the package, you can download Aspose.BarCode for Node.js via Java as a ZIP archive from the  
<a href="https://releases.aspose.com/barcode/nodejs/" target="_blank">official Aspose website</a>.

#### **Steps:**

1. **Download** the ZIP file and extract its contents.

2. **Copy the extracted folder** (for example, `libs` or `barcode-lib`) into your project directory.  
   You can rename it if you wish (for example, to `barcode-lib`).

   **Example project structure:**

    your-project/
    ├── barcode-lib/
    │ ├── index.js
    │ └── lib/
    │ ├── AsposeBarcode.js
    │ ├── ...other .js files
    │ └── aspose-barcode-nodejs-25.5.jar
    ├── node_modules/
    ├── package.json
    ├── index.js
    └── ...
3. **Add the required dependency** to your project's `package.json` if it is not already there:
```json
"dependencies": {
  "java": "^0.12.1"
}
```
Then run:
```bash
npm install
```
4. Use the library in your code:

```javascript
const { AsposeBarcode } = require('./barcode-lib');
const { BarcodeGenerator, EncodeTypes, BarCodeImageFormat, BarCodeReader, License } = AsposeBarcode;
const license = new License();
license.setLicense('Aspose.Total.lic');
const generator = new BarcodeGenerator(EncodeTypes.CODE_11, "12345678");
const base64Image = generator.generateBarCodeImage(BarCodeImageFormat.PNG);
const reader = new BarCodeReader(base64Image);
const resultsArray = reader.readBarCodes();
const barCodeResult = resultsArray[0];
console.log("codeText", barCodeResult.getCodeText());
console.log("codeType", barCodeResult.getCodeTypeName());
```






This archive contains:

doc/ — API documentation
license/ — End User License Agreement and third-party licenses
libs/ — Java JAR file and supporting files
examples/ — code examples
readme.txt — general instructions



