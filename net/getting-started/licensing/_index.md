---
title: Licensing
type: docs
weight: 70
description: "Setting the License for Aspose.BarCode for .NET"
keywords: "Generate Barcodes, Read Barcodes, How to Generate Barcodes in C# .NET, Aspose.BarCode License, Aspose.BarCode Licensing, Get License for Aspose.Barcode, C#"
url: /net/licensing/
---
## **Overview**
***Aspose.BarCode for .NET*** without the license can be used to generate barcode labels without restrictions; in this case, a watermark will be placed on the resulting barcode image (words “Aspose”). Moreover, the unlicensed version of the library allows reading all types of barcodes; however, only the *Code39* symbology can be used without limitations; for all other barcode types, 30% of the decrypted text will be masked with "*". 
All other actions with barcodes through ***Aspose.BarCode for .NET*** require setting the license first.  
The license activates access to the entire functionality of the library so that you can perform barcode generation and recognition without any limitations and watermarks.  
## **How to Obtain the License**
If you want to try the fully functional version of ***Aspose.BarCode for .NET***, you can request a 30-day temporary license. Please refer to [How to get a Temporary License?](https://purchase.aspose.com/temporary-license) for more information.
To obtain the possibility to use the library without limitations, a commercial license is required. You can get all information about pricing and conditions [here](https://purchase.aspose.com/admin/pricing/barcode/net). 

## **License Setting**

The license is a plain-text XML file that contains various information, such as the product name, the number of developers to access the license, subscription expiry date, and other details. The file is digitally signed, so it must not be modified, as adding an extra line break into the file invalidates the license. You need to set the license before generating barcodes without a watermark. You only have to set the license once per application (or process).  
License setting can be performed by calling the *SetLicense* method of class [*Aspose.BarCode.License*](https://apireference.aspose.com/barcode/net/aspose.barcode/license). This must be done before executing any actions with the library. The *SetLicense* method can be invoked in different ways: in the initialization section of an application (or a web application), using Singleton, or through a file/stream.
  
The details on how to set the license using these methods are provided below in this article.

### **Using Singleton**
The best approach is to implement the license through lazy initialization using Singleton in the key points of code. See below how to do that by adding several lines of code to your project.  
  
{{< highlight csharp>}}
internal class LicenseSingleton
{
    private static LicenseSingleton _instance = new LicenseSingleton();
    private LicenseSingleton()
    {
        // init the license
        (new Aspose.BarCode.License()).SetLicense(@"{path}Aspose.Total.Product.Family.lic");
    }

    public static void SetLicense()
    {
        LicenseSingleton local = _instance;
    }
}
	
	//lazy initialization before using the library
	LicenseSingleton.SetLicense();
{{< /highlight >}} 

### **From File or Stream**
License setting can be also performed from a file or stream, as demonstrated below.

***Setting the license from file***  
{{< highlight csharp>}}
//set path to file
(new Aspose.BarCode.License()).SetLicense(@"{path}Aspose.Total.Product.Family.lic");
{{< /highlight >}}
  
***Setting the license from stream***  
{{< highlight csharp>}}
System.IO.MemoryStream ms = new System.IO.MemoryStream();
//load license data to stream
//set license as stream
(new Aspose.BarCode.License()).SetLicense(ms);
{{< /highlight >}}

### **From Application Resource**
The other way to add the license into an application is to include it as an embedded resource into one of the assemblies that call ***Aspose.BarCode for .NET***. In this way, the license can be embedded into an application as a resource and then loaded from the resource as a stream. See below how license setting can be performed in this mode.  

***Embedding the license as a resource***  
  
{{< highlight xml>}}
<ItemGroup>
	<EmbeddedResource Include="{path}Aspose.Total.Product.Family.lic" LogicalName="Aspose.Total.Product.Family.lic"/>
</ItemGroup>
{{< /highlight >}}  

***Loading the license as stream***  
  
{{< highlight csharp>}}
using (System.IO.Stream stream = System.Reflection.Assembly.GetExecutingAssembly().GetManifestResourceStream("Aspose.Total.Product.Family.lic"))
	(new Aspose.BarCode.License()).SetLicense(stream);
{{< /highlight >}}

### **Additional Ways**
Additionally, the license can be set using the name of the corresponding file or embedded resource. If the license name is passed to the *SetLicense* method without specifying the full path, the library will search it in the following locations:  
- Root directory of the .exe file
- Folder that contains the *Aspose.BarCode.dll* library
- Folder that contains the assembly calling *Aspose.BarCode.dll*
- Embedded resources of the application where the resource name matches with the specified license name 
  
{{< highlight csharp>}}
//license name, file, or resource
(new Aspose.BarCode.License()).SetLicense("Aspose.Total.Product.Family.lic");
{{< /highlight >}}

## **Protection from License Theft**

If you share your software with the license applied outside of your organization without implementing any protection, unauthorized access to the license can become possible. To avoid this risk, we recommend encrypting the license source file. See below the example of how to implement such protection. 
  
{{< highlight csharp>}}
//load the license from a file to stream
System.IO.MemoryStream originalStream = null;
using (System.IO.FileStream fs = new System.IO.FileStream(@"{path}Aspose.Total.Product.Family.lic", System.IO.FileMode.Open))
{
    byte[] buf = new byte[fs.Length];
    fs.Read(buf, 0, buf.Length);
    originalStream = new System.IO.MemoryStream(buf);
}

//ENCRYPT LICENSE FILE
//encription key
byte[] encriptionKey = { 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08 };
//initialization vector
byte[] ivKey = { 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16 };
System.IO.MemoryStream encryptedStream = null;
using (System.Security.Cryptography.DES des = System.Security.Cryptography.DES.Create())
{
    //set intialization value and key
    des.Key = encriptionKey;
    des.IV = ivKey;
    //encrypt
    System.IO.MemoryStream dataStream = new System.IO.MemoryStream();
    using (System.Security.Cryptography.CryptoStream csEncrypt = new System.Security.Cryptography.CryptoStream(dataStream, des.CreateEncryptor(),
        System.Security.Cryptography.CryptoStreamMode.Write))
    {
        //file length
        csEncrypt.Write(System.BitConverter.GetBytes((int)originalStream.Length), 0, 4);
        //file data
        csEncrypt.Write(originalStream.ToArray(), 0, (int)originalStream.Length);
    }
    encryptedStream = new System.IO.MemoryStream(dataStream.ToArray());
}

//DECRYPT LICENSE FILE
//same encription key and initialization vector
System.IO.MemoryStream decryptedStream = null;
using (System.Security.Cryptography.DES des = System.Security.Cryptography.DES.Create())
{
    //set the intialization value and the key
    des.Key = encriptionKey;
    des.IV = ivKey;
    //decrypt
    System.IO.MemoryStream dataStream = new System.IO.MemoryStream(encryptedStream.ToArray());
    dataStream.Position = 0;
    using (System.Security.Cryptography.CryptoStream csDecrypt = new System.Security.Cryptography.CryptoStream(dataStream, des.CreateDecryptor(),
        System.Security.Cryptography.CryptoStreamMode.Read))
    {
        //read length
        byte[] buffLen = new byte[4];
        csDecrypt.Read(buffLen, 0, buffLen.Length);
        int dataLen = System.BitConverter.ToInt32(buffLen, 0);
        //read data
        byte[] buf = new byte[dataLen];
        csDecrypt.Read(buf, 0, buf.Length);
        decryptedStream = new System.IO.MemoryStream(buf);
    }
}

//set license
(new Aspose.BarCode.License()).SetLicense(decryptedStream);
{{< /highlight >}}

## **Setting the Metered License**
[Aspose.BarCode for .NET API](/barcode/net/) allows developers to apply the metered key. It is a new licensing mechanism that can be used along with one of the existing licensing methods. The customers who want to be billed based on the usage of the API features can apply metered licensing. For more details, please refer to [Metered Licensing FAQ](https://purchase.aspose.com/faqs/licensing/metered).

New class [*Metered*](https://apireference.aspose.com/barcode/net/aspose.barcode/metered) has been introduced to apply the metered key. The sample code demonstrating how to set metered public and private keys is provided below.
  
{{< highlight csharp >}}
    // set metered public and private keys
    Aspose.BarCode.Metered metered = new Aspose.BarCode.Metered();

    // Access the setMeteredKey property and pass the public and private keys as parameters
    metered.SetMeteredKey("*****", "*****");
    
    // DO PROCESSING
    
    // get the metered data amount
    decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
    
    // Display information
    Console.WriteLine("Amount Consumed : " + amount.ToString());
{{< /highlight >}}
