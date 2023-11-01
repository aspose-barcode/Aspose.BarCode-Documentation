---
title: Licensing
type: docs
weight: 50
url: /python-java/licensing/
---

## **Overview**
The evaluation mode of ***Aspose.BarCode for Python via Java*** allows generating barcode images without restrictions. However, a watermark will be displayed on the resulting barcode image (words “Aspose”). The unlicensed version can be used to read barcodes of all supported types. Please note that only *Code 39* can be decoded without limitations; as a result of reading barcodes corresponding to other types, 30% of decoded text will be masked with " * ". All other actions with barcodes using ***Aspose.BarCode for Python via Java*** need setting a license. After purchasing a license, you will get access to the whole functionality of the library and the ability to perform barcode generation and reading without limitations and watermark placement.  

## **How to Obtain License**
If you want to try the full version of ***Aspose.BarCode for Python via Java***, you can try a temporary license that is valid for 30 days. Please read [How to get a Temporary License?](https://purchase.aspose.com/temporary-license) for more information. To use the library without limitations, purchasing a commercial license is necessary. You can get all information about pricing and conditions [here](https://purchase.aspose.com/admin/pricing/barcode/python-java). 

Each Aspose license enables a one-year subscription with free upgrades to any new releases or fixes that are published during this period. Technical support is provided for free unlimitedly both to licensed and evaluation users.

The license is a plain-text XML file that contains various information, such as the product name, the number of developers to access the license, subscription expiry date, and other details. The file is digitally signed, so it must not be modified, as adding an extra line break into the file invalidates the license. You need to set the license before generating barcodes without a watermark. You only have to set the license once per application (or process).  
  
License setting can be performed by calling the *set_license* method of class [*aspose.barcode.License*](https://reference.aspose.com/barcode/python-java/class/asposebarcode.assist.license/). This must be done before executing any actions with the library. The *set_license* method can be called in different ways: using a file *set_license(license_name)* or a stream *set_license(stream)*.
  
### **From File or Stream**
The license can be activated from a file or stream, as shown below.

***Setting the license from a file***  
  
```python
lic = aspose.barcode.License()

# Try to set license from the folder with the python script
try :
    lic.set_license("Aspose.BarCode.Python.Java.lic")
    print("License set successfully")
except RuntimeError as err :
    # We do not ship any license with this example, visit the Aspose site to obtain either a temporary or permanent license. 
    print("\nThere was an error setting the license: {0}".format(err))
```
  
***Setting the license from a stream***  

```python
lic = aspose.barcode.License()

# Try to set license from the stream.
try :
    lic_stream = io.FileIO("C:\\Temp\\Aspose.BarCode.Python.Java.lic")
    lic.set_license(lic_stream)
    lic_stream.close()
    print("License set successfully")
except RuntimeError as err :
    # We do not ship any license with this example, visit the Aspose site to obtain either a temporary or permanent license. 
    print("\nThere was an error setting the license: {0}".format(err))
```

## **Protection from License Theft**
If you share your software with the license applied outside of your organization without implementing any protection, unauthorized access to the license can become possible. To avoid this risk, we recommend encrypting the license source file.  
