---
title: Licensing
type: docs
weight: 60
url: /net/licensing/
---
## **Overview**


<!--Getting a license is required to obtain the access to some advance properties of Aspose.BarCode for .NET. The evaliuation mode allows generating barcodes without any restrictions; however, a watermark is placed on the resulting image. The evaluation version of Aspose.BarCode only supports recognizing Code39 barcodes. To test how recognition works, a full-featured demo is available for all supported barcode symbologies. If you want to try Aspose.BarCode without limitations, you can request a 30-day temporary license. Please refer to [How to get a Temporary License?](https://purchase.aspose.com/temporary-license) for more information.-->

## **How to Obtain a License**

## **License Setting**

### **Using Singleton**

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

{{< highlight csharp>}}
//set path to file
(new Aspose.BarCode.License()).SetLicense(@"{path}Aspose.Total.Product.Family.lic");
{{< /highlight >}}

{{< highlight csharp>}}
System.IO.MemoryStream ms = new System.IO.MemoryStream();
//load license data to stream
//set license as stream
(new Aspose.BarCode.License()).SetLicense(ms);
{{< /highlight >}}

### **From Application Resource**

{{< highlight xml>}}
<ItemGroup>
	<EmbeddedResource Include="{path}Aspose.Total.Product.Family.lic" LogicalName="Aspose.Total.Product.Family.lic"/>
</ItemGroup>
{{< /highlight >}}

{{< highlight csharp>}}
using (System.IO.Stream stream = System.Reflection.Assembly.GetExecutingAssembly().GetManifestResourceStream("Aspose.Total.Product.Family.lic"))
	(new Aspose.BarCode.License()).SetLicense(stream);
{{< /highlight >}}

### **Additional Ways**

The license is a plain-text XML file that contains details such as the product name, number of developers it is licensed for, subscription expiry date and so on. The file is digitally signed, so do not modify it. Even inadvertently adding an extra line break into the file invalidates it. You need to apply a license before generating barcodes without the evaluation watermark. You only have to apply a license once per application (or process). The license can be loaded from a [file](https://docs.aspose.com/barcode/net/licensing/#applying-a-license-from-file-or-stream), [stream](https://docs.aspose.com/barcode/net/licensing/#applying-a-license-from-file-or-stream) or an [embedded resource](https://docs.aspose.com/barcode/net/licensing/#setting-a-license-using-an-embedded-resource).

Aspose.BarCode tries to find the license in the following locations:

- Explicit path.
- The folder that contains Aspose.BarCode.dll.
- The folder that contains the assembly that called Aspose.BarCode.dll.
- The folder that contains the entry assembly (your .exe).
- An embedded resource in the assembly that called Aspose.BarCode.dll.


## **Protection from License Theft**



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
