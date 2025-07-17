---
title: Customize Barcode Color Scheme in C++
linktitle: Customize Barcode Color Scheme
type: docs
ai_search_scope: "barcode_cpp_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 40
description: "How to Customize Color of Barcode Elements in C++"
feedback: BARCODECOM
keywords: "create barcode c#, barcode color, bar color c#, barcode text color, barcode caption C++, Generate Barcodes, Customize Barcode Image, Change Barcode Color, Set Barcode Color, Generate Colored Barcodes, Barcode Color in Aspose.BarCode for C++, Work with Barcode Image in Aspose.BarCode for C++"
url: /cpp/customize-barcode-color/
---
This article describes the options provided by ***Aspose.BarCode for C++*** to adjust the color scheme of a barcode image and its main elements.

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Overview**
Generally, barcode images are created in black and white colors. To generate barcode labels of different colors, ***Aspose.BarCode for C++*** enables customizing system RGB color for key barcode elements, such as:
- Background
- Bars
- Borders
- Barcode text
- Top and bottom captions

## **Set Barcode Background Color**
Setting color for barcode background can be done by initializing the *BackColor* property of [*BaseGenerationParameters*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.base_generation_parameters/) class. The default background color is set to *White*.  
  
The barcode image generated with adjusted background color settings (*Color.Green*) is demonstrated below.
   
<p align="center"><image src="colorbackground.png"></p>

```cpp
// The path to the documents directory.
System::String dataDir = RunExamples::GetDataDir_ManageBarCodesImages();
System::String dst = dataDir + u"colorize-barcode_out.jpg";

// Instantiate barcode object and differnt properties
System::SharedPtr<BarcodeGenerator> generator = System::MakeObject<BarcodeGenerator>(EncodeTypes::Code128, u"1234567"); 
						
generator->get_Parameters()->set_BackColor(System::Drawing::Color::get_Yellow());
generator->get_Parameters()->get_Barcode()->set_ForeColor(System::Drawing::Color::get_Blue());
generator->get_Parameters()->get_Border()->set_Color(System::Drawing::Color::get_Red());
generator->get_Parameters()->get_Barcode()->get_CodeTextParameters()->set_Color(System::Drawing::Color::get_Red());

generator->Save(dst, BarCodeImageFormat::Jpeg);
System::Console::WriteLine(System::Environment::get_NewLine() + u"Barcode saved at " + dataDir);
```

## **Set Bar Color**
To customize the color of bars in a barcode image, it is necessary to set the value to the *BarColor* property of [*BarcodeParameters*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.barcode_parameters/) class. The default bar color is *Black*.  
  
The following image represents the barcode label generated with the customized bar color settings (*Color.Green*).
  
<p align="center"><image src="colorbarcode.png"></p>

```cpp
// The path to the documents directory.
System::String dataDir = RunExamples::GetDataDir_ManageBarCodesImages();

// Instantiate barcode object
{
	System::SharedPtr<BarcodeGenerator> generator = System::MakeObject<BarcodeGenerator>(EncodeTypes::Code128, u"TEXT");
	// Clearing resources under 'using' statement
	System::Details::DisposeGuard<1> __dispose_guard_0({ generator });
	// ------------------------------------------

	try
	{
		generator->get_Parameters()->get_Barcode()->set_FilledBars(false);
		generator->Save(dataDir + u"ControlBarsFillingofOneDBarcodes_out.png");
	}
	catch (...)
	{
		__dispose_guard_0.SetCurrentException(std::current_exception());
	}
}
```
  

## **Set Barcode Border Color**
It is possible to vary barcode border color by setting the *Color* property of class [*BorderParameters*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.border_parameters/). By default, the color of borders is set to *Black*. The barcode image provided below has been created setting border color to (*Color.Green*).
  
<p align="center"><image src="colorborder.png"></p>
  
## **Set Barcode Text Color**
The color of barcode text that may be placed on a barcode image can be adjusted as well. To do this, it is required to initialize the *Color* property in property group [*CodeTextParameters*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.codetext_parameters). By default, the color of barcode text is set to *Black*. The sample barcode image shown below has been generated with the customized barcode text color setting (*Color.Green*).
  
<p align="center"><image src="colorcodetext.png"></p>

```cpp
// The path to the documents directory.
System::String dataDir = RunExamples::GetDataDir_ManageBarCodesImages();

// Instantiate barcode object and set differnt barcode properties
System::SharedPtr<BarcodeGenerator> generator = System::MakeObject<BarcodeGenerator>(EncodeTypes::Code128, u"1234567");

generator->get_Parameters()->get_Barcode()->get_CodeTextParameters()->set_Color(System::Drawing::Color::get_Red());
generator->Save(dataDir + u"barcode-SetForeColorText_out.jpg", BarCodeImageFormat::Jpeg);
System::Console::WriteLine(System::Environment::get_NewLine() + u"Barcode saved at " + dataDir);
```

## **Set Barcode Caption Color**
Barcode images created using ***Aspose.BarCode for C++*** may have top and/or bottom captions according to the will of a developer. The color of these elements can be adjusted by setting the value to the *TextColor* property in property group [*CaptionParameters*](https://reference.aspose.com/barcode/cpp/class/aspose.bar_code.generation.base_generation_parameters/). The following barcode images have been generated using the customized caption color settings (*Color.Green*).
  
|Adjusting Caption Color|   |
|:--| :-: |
|<image src="colorcaptionabove.png">|<image src="colorcaptionbelow.png">|
  