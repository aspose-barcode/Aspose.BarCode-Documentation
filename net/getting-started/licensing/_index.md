---
title: Licensing
type: docs
weight: 60
url: /net/licensing/
---
## **Overview**
***Aspose.BarCode for .NET*** without license can be used to generate barcode labels without restrictions; in this case, a watermark is placed on the resulting barcode image (words “Aspose”). Moreover, the unlicensed version of the library allows recognizing all types of barcodes; however, only the Code39 symbology can be used without limitations; for all other barcode types, the 30 % of resulting text is masked with *. All other actions with barcodes through Aspose.BarCode for .NET require getting the license first.  
The license activates the access to the entire functionality of the library, so that you can perform barcode generation and recognition without any limitations and watermarks.
## **How to Obtain the License**
If you want to try the fully functional version of ***Aspose.BarCode for .NET***, you can request a 30-day temporary license. Please refer to [How to get a Temporary License?](https://purchase.aspose.com/temporary-license) for more information.
To obtain the possibility to use the library without limitations, commercial license is required. You can get all information about pricing and conditions [here](https://purchase.aspose.com/admin/pricing/barcode/net). 

## **License Setting**

The license is a plain-text XML file that contains information about the product name, the number of developers to access the license, subscription expiry date, and others. The file is digitally signed, so it must not be modified, as adding an extra line break into the file invalidates the license. You need to set the license before generating barcodes without watermark. You only have to apply the license once per application (or process).  
License setting can be realized through calling the method *SetLicense* of the class *Aspose.BarCode.License*. This must be done before any actions with the library. The method *SetLicense* can be invoked in different ways: in the initialization section of you application (or web application), using singletones, through file or stream.
  
The details on how to apply the license through these methods are provided below in this article.

### **Using Singleton**
The best approach is to implement the license through lazy initialization using Singleton in the key points of code. See below how to do that with adding several lines of code to your project.  

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
License setting can be also performed from file or stream, as demonstrated below.

***Setting the license from file***
{{< highlight csharp>}}
//set path to file
(new Aspose.BarCode.License()).SetLicense(@"{path}Aspose.Total.Product.Family.lic");
{{< /highlight >}}
  
***Setting the license from file***  


{{< highlight csharp>}}
System.IO.MemoryStream ms = new System.IO.MemoryStream();
//load license data to stream
//set license as stream
(new Aspose.BarCode.License()).SetLicense(ms);
{{< /highlight >}}

### **From Application Resource**
The other way of implementing the license with the application is to include it as an embedded resource into one of the assemblies that call Aspose.BarCode for .NET. In this way, the license can be embedded into your application as a resource and then, be loaded from the resource as stream. See below how this license mode setting can be realized.  
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
Additionally, the license can be set using the name of the corresponding file or embedded resource. If the license name is called without specifying the full path, the library will search it in the following locations:  
- Explicit path;
- The folder that contains Aspose.BarCode.dll;
- The folder that contains the assembly that called Aspose.BarCode.dll;
- The folder that contains the entry assembly (the target .exe);
- An embedded resource in the assembly that is called by Aspose.BarCode.dll.


## **Protection from License Theft**

If you share your software with the license applied outside of your organization without applying any protection, the unauthorized access to your license can become possible. To avoid this risk, we recommend to encrypt the file with license. See below the example of how to implement such protection. 

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
    //set intialization value and key
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

A new class **Metered** has been introduced to apply the metered key. Following is the sample code demonstrating how to set metered public and private keys.

{{< highlight csharp >}}
    // set metered public and private keys
    Aspose.BarCode.Metered metered = new Aspose.BarCode.Metered();

    // Access the setMeteredKey property and pass public and private keys as parameters
    metered.SetMeteredKey("*****", "*****");
    
    // DO PROCESSING
    
    // get metered data amount
    decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
    
    // Display information
    Console.WriteLine("Amount Consumed : " + amount.ToString());
{{< /highlight >}}

<!--## **Evaluation Version Limitations**
### **Evaluate Aspose.BarCode**
You can easily download an evaluation version of Aspose.BarCode for .NET from the [download page](https://www.nuget.org/packages/Aspose.barcode/). The evaluation version provides the same capabilities as the licensed version of the component. Furthermore, the evaluation version is licensed by simply buying a license and adding a couple of lines of code to your projects. The evaluation version of Aspose.BarCode (that is, the application without a license applied) provides full barcode generation functionality but puts an evaluation watermark (the words Aspose) on the barcode image. If you want to try Aspose.BarCode without evaluation version limitations, you can also request a 30-day temporary license. Please refer to [How to get a Temporary License?](https://purchase.aspose.com/temporary-license) for more information.
### **Code39 Recognition Only**
The evaluation version of Aspose.BarCode only supports Code39 barcode recognition, however, a full-featured demo application is provided for all supported barcode symbologies. If you want to test Aspose.BarCode without evaluation version limitations, you can also request a 30-day temporary license. Please refer to [How to get a Temporary License?](https://purchase.aspose.com/temporary-license) for more information.
## **Applying a License**
When you call the SetLicense method, the license name should be the same as that of your license file name. For example, you may change the license file name to "Aspose.BarCode.lic.xml". Then in your code, you should use the modified license name (that is Aspose.BarCode.lic.xml) for the SetLicense method.
### **Setting a License in Aspose.BarCode for .NET**
The license is a plain-text XML file that contains details such as the product name, number of developers it is licensed for, subscription expiry date and so on. The file is digitally signed, so do not modify it. Even inadvertently adding an extra line break into the file invalidates it. You need to apply a license before generating barcodes without the evaluation watermark. You only have to apply a license once per application (or process). The license can be loaded from a [file](https://docs.aspose.com/barcode/net/licensing/#applying-a-license-from-file-or-stream), [stream](https://docs.aspose.com/barcode/net/licensing/#applying-a-license-from-file-or-stream) or an [embedded resource](https://docs.aspose.com/barcode/net/licensing/#setting-a-license-using-an-embedded-resource).

Aspose.BarCode tries to find the license in the following locations:

- Explicit path.
- The folder that contains Aspose.BarCode.dll.
- The folder that contains the assembly that called Aspose.BarCode.dll.
- The folder that contains the entry assembly (your .exe).
- An embedded resource in the assembly that called Aspose.BarCode.dll.
### **Applying a License**
#### **Applying a License from File or Stream**
The easiest way to apply a license is to put the license file in the same folder as that of Aspose.BarCode.dll and specify just the file name without a path.
**C#**
{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ApplyingLicenseUsingFile.cs" >}}

It is also possible to load a license from a stream.
**C#**
{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ApplyingLicenseUsingStream.cs" >}}

#### **Setting a License Using an Embedded Resource**
Another neat way of packaging the license with the application and making sure it is not lost, is to include it as an embedded resource into one of the assemblies that calls Aspose.BarCode. To include the license file as an embedded resource, perform the following steps:

1. In Visual Studio .NET, include the license (.lic) file into the project by selecting **Add Existing Item** from the **File** menu.
1. Select the file in Solution Explorer.
1. Set **Build Action to Embedded Resource** in the Properties window.

To access the license embedded in the assembly (as an embedded resource), it is not necessary to call the Microsoft .NET Framework's System.Reflection.Assembly class' GetExecutingAssembly and GetManifestResourceStream methods. Instead, just add the license file as an embedded resource to your project and pass the name of the license file into the SetLicense method. The License class automatically finds the license file in the embedded resources.
**C#**
{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ApplyingLicenseUsingFile.cs" >}}
#### **Recommended Place to Set the License in the Source Code**
The license needs to be set only once per application or process. For desktop applications, it is recommended to set the license in the Initialize() method of the main form. And for web applications, it should be in global.asax file’s Session_Start() method.
### **Applying Metered Key**
[Aspose.BarCode for .NET API](/barcode/net/) allow developers to apply metered key. It is a new licensing mechanism. The new licensing mechanism will be used along with the existing licensing method. Those customers who want to be billed based on the usage of the API features can use the metered licensing. For more details, please refer to [Metered Licensing FAQ](https://purchase.aspose.com/faqs/licensing/metered) section.

A new class **Metered** has been introduced to apply the metered key. Following is the sample code demonstrating how to set metered public and private keys.

{{< highlight csharp >}}
    // set metered public and private keys
    Aspose.BarCode.Metered metered = new Aspose.BarCode.Metered();

    // Access the setMeteredKey property and pass public and private keys as parameters
    metered.SetMeteredKey("*****", "*****");
    
    // DO PROCESSING
    
    // get metered data amount
    decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
    
    // Display information
    Console.WriteLine("Amount Consumed : " + amount.ToString());
{{< /highlight >}}
-->
