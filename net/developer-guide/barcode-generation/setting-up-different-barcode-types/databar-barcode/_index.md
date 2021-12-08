---
title: Databar Barcode
type: docs
weight: 20
url: /net/databar-barcode/
---

## Overview

## Barcode Height Settings

### Continuos Databar Standards
  
|Databar Barcode Height|30 Pixels|60 PIxels|
|:---:|:---:|:---:|
| |<img src="DatabarBarHeight30Pixels.png">|<img src="DatabarBarHeight60Pixels.png">|
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarOmniDirectional, "(01)12345678901231");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//set barheight 30 pixels
gen.Parameters.Barcode.BarHeight.Pixels = 30;
gen.Save($"{path}DatabarBarHeight30Pixels.png", BarCodeImageFormat.Png);
//set barheight 60 pixels
gen.Parameters.Barcode.BarHeight.Pixels = 60;
gen.Save($"{path}DatabarBarHeight60Pixels.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
### Stacked Databar Standards
  
|Databar Aspect Ratio|Is Set to 15|Is Set to 30|
|:---:|:---:|:---:|
| |<img src="DatabarAspectRatio15.png">|<img src="DatabarAspectRatio30.png">|
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarStackedOmniDirectional, "(01)12345678901231");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//set DataBar AspectRatio 15
gen.Parameters.Barcode.DataBar.AspectRatio = 15;
gen.Save($"{path}DatabarAspectRatio15.png", BarCodeImageFormat.Png);
//set DataBar AspectRatio 30
gen.Parameters.Barcode.DataBar.AspectRatio = 30;
gen.Save($"{path}DatabarAspectRatio30.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
## Setting Rows and Columns for Databar Expanded Stacked

|Databar Expanded Settings|4 Columns|3 Rows|6 Columns and 10 Rows|
|:---:|:---:|:---:|:---:|
| |<img src="DatabarCols4.png">|<img src="DatabarRows3.png">|<img src="DatabarCols6Rows10.png">|

{{< highlight csharp>}}
//set 4 columns
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarExpandedStacked, "Databar Expanded Stacked long");
gen.Parameters.Barcode.DataBar.Columns = 4;
gen.Save($"{path}DatabarCols4.png", BarCodeImageFormat.Png);
//set 3 rows
gen = new BarcodeGenerator(EncodeTypes.DatabarExpandedStacked, "Databar Expanded Stacked long");
gen.Parameters.Barcode.DataBar.Rows = 3;
gen.Save($"{path}DatabarRows3.png", BarCodeImageFormat.Png);
//set 6 columns 10 rows
gen = new BarcodeGenerator(EncodeTypes.DatabarExpandedStacked, "Databar Expanded Stacked long");
gen.Parameters.Barcode.DataBar.Columns = 6;
gen.Parameters.Barcode.DataBar.Rows = 10;
gen.Save($"{path}DatabarCols6Rows10.png", BarCodeImageFormat.Png);
{{< /highlight >}}
  
## Verifying Compatibility with GS1 components

  
|GS1 Compatibility|Matching Encoding|Incompatible Encoding|
|:---:|:---:|:---:|
| |<img src="DatabarGS1RightEncoding.png">|<img src="DatabarGS1VariableEncoding.png">|
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarExpanded, "");
//right codetext with GS1Encoding check
gen.CodeText = "(01)12345678901231";
gen.Parameters.Barcode.DataBar.IsAllowOnlyGS1Encoding = true;
gen.Save($"{path}DatabarGS1RightEncoding.png", BarCodeImageFormat.Png);
//variable codetext without GS1Encoding check
gen.CodeText = "ASPOSE";
gen.Parameters.Barcode.DataBar.IsAllowOnlyGS1Encoding = false;
gen.Save($"{path}DatabarGS1VariableEncoding.png", BarCodeImageFormat.Png);
//variable codetext with GS1Encoding check
try
{
    gen.CodeText = "ASPOSE";
    gen.Parameters.Barcode.DataBar.IsAllowOnlyGS1Encoding = true;
    gen.GenerateBarCodeImage();
}
catch (Exception e)
{
    Console.WriteLine(e.Message);
}
{{< /highlight >}}
  
## Enabling 2D Component

  
|2D Component|Is Disabled|Is Enabled|
|:---:|:---:|:---:|
| |<img src="Databar2DComponentDisabled.png">|<img src="Databar2DComponentEnabled.png">|
  
{{< highlight csharp>}}
BarcodeGenerator gen = new BarcodeGenerator(EncodeTypes.DatabarExpanded, "(01)12345678901231");
gen.Parameters.Barcode.XDimension.Pixels = 2;
//disable 2D component flag
gen.Parameters.Barcode.DataBar.Is2DCompositeComponent = false;
gen.Save($"{path}Databar2DComponentDisabled.png", BarCodeImageFormat.Png);
//enable 2D component flag
gen.Parameters.Barcode.DataBar.Is2DCompositeComponent = true;
gen.Save($"{path}Databar2DComponentEnabled.png", BarCodeImageFormat.Png);
{{< /highlight >}}