---
title: Licensing
description:
type: docs
weight: 50
url: /python-net/licensing/
---

## **Evaliation Mode**
***Aspose.BarCode for Python via .NET*** provides an evaluation mode that allows generating barcodes without restrictions. A watermark will be placed on the resulting barcode image (words “Aspose”). The unlicensed version can be also used to read all supported barcode types. Only *Code 39* can be decoded without limitations; as a result of reading barcodes corresponding to other types, 30% of decoded text will be masked with " * ". All other actions with barcodes using ***Aspose.BarCode for Python via .NET*** need setting a license. After purchasing a license, you will get access to the whole functionality of the library and the ability to perform barcode generation and reading without limitations and watermark placement.  

## **Temporary License**
To try the fully functional version of ***Aspose.BarCode for Python via .NET***, you can get a 30-day temporary license. Please refer to [How to get a Temporary License?](https://purchase.aspose.com/temporary-license) for more information. To use the barcode library without limitations, buying a commercial license is required. You can get all information about pricing and conditions [here](https://purchase.aspose.com/admin/pricing/barcode/net). 

## **License Setting**
The license is a plain-text XML file that contains various information, such as the product name, the number of developers to access the license, subscription expiry date, and other details. The file is digitally signed, so it must not be modified, as adding an extra line break into the file invalidates the license. You need to set the license before generating barcodes without a watermark. You only have to set the license once per application (or process).  
  
License setting can be performed by calling the *set_license* method of class [*Aspose.BarCode.License*](https://reference.aspose.com/barcode/net/aspose.barcode/license). This must be done before executing any actions with the library. The *set_license* method can be called in different ways: using a file *set_license(license_name)* or a stream *set_license(stream)*.
  
### **From File or Stream**
The license can be activated from a file or stream, as shown below.

***Setting the license from a file***  
  
```python
lic = aw.License()

# Try to set license from the folder with the python script
try :
    lic.set_license("Aspose.Words.Python.NET.lic")
    print("License set successfully.")
except RuntimeError as err :
    # We do not ship any license with this example, visit the Aspose site to obtain either a temporary or permanent license. 
    print("\nThere was an error setting the license: {0}".format(err))
```
  
***Setting the license from a stream***  

```python
lic = aw.License()

# Try to set license from the stream.
try :
    lic_stream = io.FileIO("C:\\Temp\\Aspose.Words.Python.NET.lic")
    lic.set_license(lic_stream)
    lic_stream.close()
    print("License set successfully.")
except RuntimeError as err :
    # We do not ship any license with this example, visit the Aspose site to obtain either a temporary or permanent license. 
    print("\nThere was an error setting the license: {0}".format(err))
```

## **Protection from License Theft**
If you share your software with the license applied outside of your organization without implementing any protection, unauthorized access to the license can become possible. To avoid this risk, we recommend encrypting the license source file.  

## **Setting Metered License**
***Aspose.BarCode for Python via .NET*** supports the metered license for the developers who want to be billed based on the usage of the API features. See [Metered Licensing FAQ](https://purchase.aspose.com/faqs/licensing/metered) for more details.

To activate the metered license, class [*Metered*](https://reference.aspose.com/barcode/python-net/aspose.barcode/metered) needs to be used, as shown below.   

``` python

# Set metered public and private keys
metered = aw.Metered()
# Access the setMeteredKey property and pass public and private keys as parameters
metered.set_metered_key("*****", "*****")

# Load the document from disk.
doc = aw.Document(docs_base.my_dir + "Document.docx")
#Get the page count of document
print(doc.page_count)

```