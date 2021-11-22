---
title: Generate Barcodes with Aspose.BarCode APIs
type: docs
description: "Aspose.BarCode for .NET allows generating barcode in C# Console Applications, Windows Forms, and WPF."
keywords: "How to Generate Barcodes in C# .NET, Generate a Simple Barcode or QR, Use Advanced Settings to Style and Customize your Barcode, Implement Complex Barcodes, Generate Barcode in C#, Aspose.BarCode, C#"
weight: 10
url: /net/generate-barcodes-with-aspose-barcode-apis/
---

## **Generate Barcode in C# Console Applications**
In some cases, developers may be interested in generating barcode labels on the backend through programming rather than creating them using Windows Forms. This may be necessary to implement the following requirements:
- Save generated barcode labels to a database
- Store barcode labels to some other locations after creating them at runtime
- Integrate the barcode generation feature into external applications

Working with barcodes on the backend can be necessary in many other cases depending on particular requirements. To address this need, ***Aspose.BarCode for .NET*** provides a non-GUI class that is called [BarcodeGenerator](https://apireference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator). Developers can create an instance of this class, set some properties, and then save the generated barcode label to any location according to their customized settings. The example illustrating how to use this class is provided below.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-ManageBarCodes-SetCodeText-SetCodeText.cs" >}}

## **Generate Barcode in C# Windows Forms**
***Aspose.BarCode for .NET*** contains a control class that is called [BarCodeGeneratorControl](https://apireference.aspose.com/barcode/net/aspose.barcode.windows.forms/barcodegeneratorcontrol) and is inherited from *System.Windows.Forms.Control* class. *BarcodeGeneratorControl* class plays the major role in creating barcode labels using Windows Forms. Follow the steps below to implement ***Aspose.BarCode for .NET*** in this mode:
- Drag *BarCodeControl* from Toolbox to your Windows Form
- Set the license to the control so that you can generate a barcode label without a watermark. The code to set the license can be added to the Load event of the Windows Form, as demonstrated in the example below.

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "HowToApplyLicense.cs" >}}

- Set the CodeText of the barcode using the Properties window.

{{% alert color="primary" %}} 

If Aspose.BarCode controls are not available in the Toolbox of Visual Studio.NET, you can check the article [How to Integrate Aspose.BarCode with Visual Studio.NET?](/barcode/net/integrate-with-visual-studio-net/).

{{% /alert %}}  
## **Generate Barcode in C# WPF**
***Aspose.BarCode for .NET*** is compatible with the DLL for the Microsoft WPF framework to enable building WPF-based applications. It is necessary to reference *Aspose.BarCode.WPF.dll* in WPF applications to enable barcode generation and recognition functionality. To deploy the library in such a way, follow the steps described below.

1. Create a new WPF application in Visual Studio 2008.
1. Add a reference to *Aspose.BarCode.WPF.dll* by right-clicking on the project and selecting *Add Reference*.
1. Locate the DLL in the folder where you have installed ***Aspose.BarCode for .NET***.
1. Add *Aspose.BarCode control* to the Toolbox:
   1. Right-click on the Toolbox and select *Choose Items*
   1. Select *WPF Components* tab and then choose *Aspose.BarCode.WPF.dll* (located in the “bin” folder of the Aspose.BarCode installation directory)
   1. Click **OK**
   1. Drag the control to the form
   1. Right-click on the control and select *Properties*
   1. Adjust barcode properties, such as CodeText, Symbology Type, Fonts, Colors, etc.

Now you can modify barcode properties at design time without programming and then generate a barcode label following the steps as in the example provided below:

1. Set **CodeText** to ABC-123
1. Change **BackColor** to Silver and run the application

Otherwise, you can insert code to generate a barcode label, as specified in the corresponding example:

1. Drag a button control to the form
1. Add the following code to its Click event


The code below is used to define the required symbology and set CodeText. Then, the barcode control is updated automatically.
{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Sets-Symbology-And-Codetext.cs" >}}


## **See Also**
<!--For more WPF samples, please refer to the **Downloads** section in [www.aspose.com](http://www.aspose.com/).-->
