---
title: License Setting
linktitle: Setting Aspose Licence through GUI
type: docs
description: "Barcode Generation in Aspose.BarCode for .NET through C# GUI-based frameworks: Windows Forms and WPF"
keywords: "Generate Barcodes, How to Generate Barcodes in C# .NET, Create Barcodes in WinForms, Generate Barcode WPF, C# Framework, Aspose.BarCode for .NET, C#"
weight: 10
url: /net/gui-license-setting/
---

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## License Setting

To work with ***Aspose.BarCode for .NET*** through GUI-based tools, it is necessary to activate the product license in the application code. General information about how to buy a license or get a trial period is available in [Licensing](/barcode/net/licensing/). In this case, the recommended way to install the license is to do that through lazy initialization using the Singleton pattern that serves to call the license setting code through the form initialization constructor, as shown in the code sample below.  

{{% alert color="primary" %}} 
Before starting development with the use of GUI-based frameworks, it is necessary to have installed .NET Framework 2.0 for WinForms and .NET Framework 3.0 for WPF. Please note that .NET Core does not support this option.
{{% /alert %}} 


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

The following code snippets illustrate how to call license installation code in WinForms and WPF.  

**Calling License Setting Code in WinForms**
  
  {{< highlight csharp>}}
public Form1()
{
    //set license
	LicenseSingleton.SetLicense();
    InitializeComponent();
}
{{< /highlight >}}

**Calling License Setting Code in WPF**
  
{{< highlight csharp>}}
public MainWindow()
{
    //set license
    LicenseSingleton.SetLicense();
    InitializeComponent();
}
{{< /highlight >}}
