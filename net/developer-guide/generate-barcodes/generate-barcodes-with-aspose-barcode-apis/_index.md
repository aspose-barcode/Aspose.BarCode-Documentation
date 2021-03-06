---
title: Generate Barcodes with Aspose.BarCode APIs
type: docs
description: "Aspose.BarCode for .NET allows generating barcode in C# Console Applications, Windows Forms, and WPF."
keywords: "How to Generate Barcodes in C# .NET, Generate a Simple Barcode or QR, Use Advanced Settings to Style and Customize your Barcode, Implement Complex Barcodes, Generate Barcode in C#, Aspose.BarCode, C#"
weight: 10
url: /net/generate-barcodes-with-aspose-barcode-apis/
---

## **Generate Barcode in C# Console Applications**
Sometimes, developers are interested in generating barcode images on the back end programmatically rather than just showing them on Windows Forms. This requirement can be because of the following reasons:

- Developers need to generate barcode images and then save to the database
- Developers have to store barcode images to some other location after creating them at runtime
- Developers want to integrate barcode generation feature to some other application

There can be plenty of other reasons for working with barcodes on the back end depending upon the developer's requirements. Aspose.BarCode provides a Non-GUI based class, [BarcodeGenerator](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) that serves the purpose. Developers can create an instance of this class, set some properties and then save the barcode image to any location according to their customized settings. Please, review the example below to have a better idea.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarCodes-SetCodeText-SetCodeText.cs" >}}

## **Generate Barcode in C# Windows Forms**
Aspose.BarCode contains a control class, [BarCodeGeneratorControl](https://apireference.aspose.com/barcode/net/aspose.barcode.windows.forms/barcodegeneratorcontrol), which is inherited from System.Windows.Forms.Control class. The [BarCodeGeneratorControl](https://apireference.aspose.com/barcode/net/aspose.barcode.windows.forms/barcodegeneratorcontrol) class plays a major role in creating barcode images and drawing the images on the Windows Forms. Follow the steps below to use Aspose.BarCode in Windows Forms:

- Drag BarCodeControl from Toolbox to your Windows Form
- Set license to the control, therefore, you can avoid the evaluation watermark in the barcode image. The code for setting the license can be added to the Load event of the Form

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "HowToApplyLicense.cs" >}}

- Set the CodeText of the barcode using the Properties window

{{% alert color="primary" %}} 

If you can't see Aspose.BarCode controls in the Toolbox of Visual Studio.NET then learn about [How to Integrate Aspose.BarCode with Visual Studio.NET?](/barcode/net/integrate-with-visual-studio-net/)

{{% /alert %}} 
## **Generate Barcode in C# WPF**
Aspose.BarCode also ships with a DLL for the Microsoft WPF framework to make it possible to build WPF-based barcode applications. Aspose.BarCode.WPF.dll should be referenced in WPF applications for BarCode generation and recognition. To use barcode in the WPF application please follow the steps given below.

1. Create a new WPF application in Visual Studio 2008 as seen in the figure below.
1. Add a reference to Aspose.BarCode.WPF.dll by right-clicking the project and selecting **Add Reference**.
1. Locate the DLL in the folder you installed Aspose.BarCode to.
1. Add the Aspose.BarCode control on the toolbox:
   1. Right-click the toolbox and select **Choose Items**.
   1. Select the **WPF Components** tab and select the Aspose.BarCode.WPF.dll (located in the “bin” folder of the Aspose.BarCode installation directory).
   1. Click **OK**.
   1. Drag the control to the form.
   1. Right-click the control and select **Properties**.
   1. Adjust barcode properties like CodeText, Symbology Type, Fonts, Colors etc.

You can modify the properties at design time without using the code and generate the barcode:

1. Set **CodeText** to ABC-123.
1. Change **BackColor** to Silver and run the application.

And you can, of course, write code to generate the barcode:

1. Drag a button control to the form.
1. Add the following code to its Click event.


The code below sets the symbology and CodeText. The barcode control is updated automatically.
{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Sets-Symbology-And-Codetext.cs" >}}


## **See Also**
For more WPF samples, please view the **Downloads** section at [www.aspose.com](http://www.aspose.com/).
