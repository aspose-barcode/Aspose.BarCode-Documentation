---
title: Installation
type: docs
ai_search_scope: "barcode_python-java_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 30
url: /python-java/installation/
---

### **Platform and Compatibility**

**Aspose.BarCode for PHP via Java** is a platform-independent product that can be used on any operating system — including **Windows**, **Linux**, and **Solaris** — where both PHP and Java are installed.

### **System Requirements**

- **Python**: Version 3.7 or higher
- **Java**: JDK 1.8 or higher

It requires Java SE 1.8 or later and works with various JDK distributions, 
including but not limited to:

- **Oracle JDK**
- **BellSoft Liberica JDK**
- **Amazon Corretto**
- **OpenJDK**
- **Other compatible distributions**

This flexibility ensures that **Aspose.BarCode for Python via Java** can integrate seamlessly into most environments, whether for development, testing, or production.

### **Installation Options**

You have several options to install the product:

#### **1. Install via pypi.org**
Install from
<a href="https://pypi.org/project/aspose-barcode-for-python-via-java/" target="_blank">Aspose.Barcode for Python via Java Repository</a>
Install latest version:
```bash
pip install aspose-barcode-for-python-via-java
```
Install specific version to particular environment
```bash
pip install aspose-barcode-for-python-via-java==25.6.0 --upgrade -t ./venv_external
```
#### **2. Download from Aspose Website**

Download the ZIP archive from the <a href="https://releases.aspose.com/barcode/python-java/" target="_blank">Aspose website</a>.  
This archive contains:

- `doc` — includes `aspose-barcode-python-xx.x-api-docs.zip`, the compressed API docs
- `license` — contains the End User License Agreement and third-party licenses
- `lib` — contains Python source files and the product's JAR file
- `readme.txt` — general instructions

Steps:
1. Unzip the Package
   Unzip the downloaded archive to any directory on your computer.
   This will create a folder containing the following structure:
<pre>
lib
├── asposebarcode/
    ├── jlib/
    │   └── aspose-barcode-python-xx.x.jar
    ├── __init__.py
    ├── Assist.py
    ├── ComplexBarcode.py
    ├── Generation.py
    └── Recognition.py
</pre>
2. Install Required Python Version
 Make sure you have Python 3.7 installed on your system.
 You can check your Python version with:
```python
 python --version
```
3. Add the lib Folder to Your Project.
   The lib folder contains all necessary Python files. 
   Make sure to keep this directory in your project root, 
   or do not change its location after unzipping.
<pre>
lib
├── asposebarcode/
    ├── jlib/
    │   └── aspose-barcode-python-xx.x.jar
    ├── __init__.py
    ├── Assist.py
    ├── ComplexBarcode.py
    ├── Generation.py
    └── Recognition.py
</pre>

### **Running and Testing**
Run a basic Python test:

```python
import sys
import os
import unittest

from asposebarcode.Recognition import BarCodeReader, DecodeType, QualitySettings

sys.path.insert(0, "./lib")

from asposebarcode import Assist, ComplexBarcode, Generation, Recognition
from asposebarcode.Generation import BarcodeGenerator, EncodeTypes


class BarcodeTests(unittest.TestCase):
	def __init__(self):
		self.folder = "testdata"
		self.image_path = os.path.join(self.folder, "code_128.png")
		self.pythonLicensePath = os.path.join(self.folder, "Aspose.BarCode.Python.Java.lic")

	def test_generate_barcode_image(self):
		license = Assist.License()
		license.setLicense(self.pythonLicensePath)
		generator = BarcodeGenerator(EncodeTypes.CODE_128, "123456")
		image = generator.generateBarCodeImage()
		generator.save(self.image_path, Generation.BarCodeImageFormat.PNG)

	def test_recognize_barcode_image(self):
		license = Assist.License()
		license.setLicense(self.pythonLicensePath)
		barcodeReader = BarCodeReader(self.image_path,None, DecodeType.CODE_128)
		barcodeReader.setQualitySettings(QualitySettings.getMaxQuality())
		results = barcodeReader.readBarCodes()
		for result in results:
			print("Code Type:", result.getCodeTypeName())
			print("Code Text:", result.getCodeText())
```
