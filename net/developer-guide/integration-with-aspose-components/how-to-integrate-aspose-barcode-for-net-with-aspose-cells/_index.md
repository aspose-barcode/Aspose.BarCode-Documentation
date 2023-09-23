---
title: Integrate Aspose.BarCode for .NET with Aspose.Cells
linktitle: Integration with Aspose.Cells
description: "How to Intergrate Aspose.BarCode with Aspose.Cells"
keywords:
type: docs
weight: 50
url: /net/integrate-with-aspose-cells/
aliases:
- /net/how-to-integrate-aspose-barcode-for-net-with-aspose-cells/
---

## **Overview**

Adding barcodes into MS Excel documents is a requested feature that makes Excel reports machine-readable. A barcode label can be inserted into a cell in the format of raster (Raster graphics) or vector (Windows Metafile) images.  
For raster image formats, an appropriate resolution value needs to be selected. The standard resolution equals 96 dpi, but for high-quality printing, it should be set in a range from 300 to 600 dpi.  
For vector formats, the resolution does not have a significant influence on the printing quality. This parameter is important to accurately covert millimeters and inches to internal vector units determining the size of fonts and barcode elements. The vector EMF format might not be fully supported on non-Windows systems. In some cases, the raster format may suit better to work with barcode images despite the convenience of the vector format.  
  
[***Aspose.Cell***](https://products.aspose.com/cells/net/) library is the most suitable tool to work with documents like Excel spreadsheets. The procedure to insert barcode images into an Excel document includes the following steps:
1.	Create or open an Excel document using [**Aspose.Cells.Workbook**](https://reference.aspose.com/cells/net/aspose.cells/workbook/) and  then add or select the required sheet
2.	Generate barcode images in raster or vector formats using class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) 
3.	Insert a barcode into a cell of the active Excel sheet of an [*Aspose.Cells.Worksheet*](https://reference.aspose.com/cells/net/aspose.cells/worksheet/) document and get an object of type [*Aspose.Cells.Drawing.Picture*](https://reference.aspose.com/cells/net/aspose.cells.drawing/picture/)
4.	Set sizing parameters of the cell or the [*Picture*](https://reference.aspose.com/cells/net/aspose.cells.drawing/picture/) object
5.	Save the document
  
Even though the size of Excel cells themselves can be modified, barcodes inside those cells are not just abstract images but representations of machine-readable data in a graphic format. 1D and 2D barcodes have strict requirements for sizing parameters and the aspect ratio to remain readable. Minor geometric distortions are acceptable but significant ones may hinder barcode readability.

## **How to Add Barcode into Excel Document** 

### **Manual Barcode Resizing**

This example demonstrates how to insert a barcode image with a specific resolution created through [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) into a cell of an object of [*Aspose.Cells.Worksheet*](https://reference.aspose.com/cells/net/aspose.cells/worksheet/) representing an Excel sheet. Here, the cell size is predefined to fit the size of the barcode image wrapped in an object of [Aspose.Cells.Drawing.Picture](https://reference.aspose.com/cells/net/aspose.cells.drawing/picture/) that gets positioned in the center of the cell.  
  
The following code sample illustrates how to implement this method. The resulting Excel file is provided below. 
  
{{< highlight csharp>}}
int Resolution = 300;//300 dpi high resolution of the barcode image
int CellRow = 5;
int CellColumn = 3;

//create an Excel book
Aspose.Cells.Workbook excelBook = new Aspose.Cells.Workbook();
Aspose.Cells.Worksheet excelSheet = excelBook.Worksheets[0];

//resize the cell where we will insert the barcode to random size (can be any)
excelSheet.Cells.SetRowHeightPixel(CellRow, 200);
excelSheet.Cells.SetColumnWidthPixel(CellColumn, 500);

//create a barcode image
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Pdf417, "Aspose.Barcode Pdf417 Example");
generator.Parameters.Resolution = Resolution;//set the barcode image resolution
generator.Parameters.Barcode.CodeTextParameters.Location = CodeLocation.None;//make the codetext invisible
Bitmap image = generator.GenerateBarCodeImage();
MemoryStream imageStream = new MemoryStream();
//can be in Png as raster image format
//generator.Save(imageStream, BarCodeImageFormat.Png);
//emf is a vector image format, but it can be not fully supported on non-Windows systems
generator.Save(imageStream, BarCodeImageFormat.Emf);
imageStream.Position = 0;

//insert the barcode image into the cell
Aspose.Cells.Drawing.Picture excelPicture = excelSheet.Pictures[excelSheet.Pictures.Add(CellRow, CellColumn, CellRow + 1, CellColumn + 1, imageStream)];
//set the image as resizible with cell size changing
excelPicture.Placement = Aspose.Cells.Drawing.PlacementType.MoveAndSize;

//resize and place it proportionally in the cell center
double columnWidth = excelSheet.Cells.GetColumnWidthPixel(CellColumn);
double rowHeight = excelSheet.Cells.GetRowHeightPixel(CellRow);
double sizeMultiplier = Math.Min(columnWidth / image.Width, rowHeight / image.Height);
excelPicture.Width = (int)Math.Round(image.Width * sizeMultiplier);
excelPicture.Height = (int)Math.Round(image.Height * sizeMultiplier);
excelPicture.Left = (int)Math.Round((columnWidth - excelPicture.Width) / 2);
excelPicture.Top = (int)Math.Round((rowHeight - excelPicture.Height) / 2);

//save the Excel book
excelBook.Save($"{path}AddBarcodeToExcelDocumentWithManualResizing.xlsx", Aspose.Cells.SaveFormat.Xlsx);
{{< /highlight >}}
  
[**Sample Outputs for Manual Barcode Resizing**](addbarcodetoexceldocumentwithmanualresizing.xlsx)
  
## **Proportional Adjustment of Cell Size**

This example explains how to add a barcode image with a specific resolution generated using [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) into a cell of an Excel sheet linked to an object of [*Aspose.Cells.Worksheet*](https://reference.aspose.com/cells/net/aspose.cells/worksheet/) so that the cell size is adjusted proportionally to the size of the barcode image represented as an object of [Aspose.Cells.Drawing.Picture](https://reference.aspose.com/cells/net/aspose.cells.drawing/picture/).  
  
The following code snippet shows how to work with this option. The resulting Excel file is given below. 
  
{{< highlight csharp>}}
int Resolution = 300;//300 dpi high resolution of the barcode image
int CellRow = 5;
int CellColumn = 3;

//create an Excel book
Aspose.Cells.Workbook excelBook = new Aspose.Cells.Workbook();
Aspose.Cells.Worksheet excelSheet = excelBook.Worksheets[0];

//create a barcode image
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Pdf417, "Aspose.Barcode Pdf417 Example");
generator.Parameters.Resolution = Resolution;//set the barcode image resolution
generator.Parameters.Barcode.CodeTextParameters.Location = CodeLocation.None;//make the codetext invisible
Bitmap image = generator.GenerateBarCodeImage();
MemoryStream imageStream = new MemoryStream();

//EMF is a vector image format but it can be not fully supported on non-Windows systems
generator.Save(imageStream, BarCodeImageFormat.Emf);
imageStream.Position = 0;

//resize the cell to the proportional image size, 96 dpi is the standard screen resolution
int cellWidth = (96 * image.Width) / 300;
int cellHeight = (96 * image.Height) / 300;
excelSheet.Cells.SetColumnWidthPixel(CellColumn, cellWidth);
excelSheet.Cells.SetRowHeightPixel(CellRow, cellHeight);

//insert the barcode image to the resized cell
Aspose.Cells.Drawing.Picture excelPicture = excelSheet.Pictures[excelSheet.Pictures.Add(CellRow, CellColumn, CellRow + 1, CellColumn + 1, imageStream)];
//set the image as resizible with cell size changing
excelPicture.Placement = Aspose.Cells.Drawing.PlacementType.MoveAndSize;

//save the Excel book
excelBook.Save($"{path}AddBarcodeToExcelDocumentWithCellResizing.xlsx", Aspose.Cells.SaveFormat.Xlsx);
{{< /highlight >}}
  
[**Sample Outputs for Proportional Adjustment of Cell**](addbarcodetoexceldocumentwithcellresizing.xlsx)

## **Adjustment of Barcode Size**

This example shows how to include a barcode image with a specific resolution created through [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) into a cell of an Excel sheet represented as an object of [*Aspose.Cells.Worksheet*](https://reference.aspose.com/cells/net/aspose.cells/worksheet/). Here, the cell size is fixed, and the barcode image is adjusted to fit in this cell. This can be done through class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator) that allows generating barcode images with strict size settings.  
  
The following code sample demonstrates how to implement this approach. The resulting Excel file can be viewed using the link below. 
    
{{< highlight csharp>}}
int Resolution = 300;//300 dpi high resolution of the barcode image
int CellRow = 5;
int CellColumn = 3;

//create the Excel book
Aspose.Cells.Workbook excelBook = new Aspose.Cells.Workbook();
Aspose.Cells.Worksheet excelSheet = excelBook.Worksheets[0];

//resize the cell where we will insert the barcode to random size (can be any)
excelSheet.Cells.SetRowHeightPixel(CellRow, 200);
excelSheet.Cells.SetColumnWidthPixel(CellColumn, 500);

//create the barcode image
BarcodeGenerator generator = new BarcodeGenerator(EncodeTypes.Pdf417, "Aspose.Barcode Pdf417 Example");
generator.Parameters.Barcode.CodeTextParameters.Location = CodeLocation.None;//make the codetext invisible
generator.Parameters.ImageWidth.Pixels = (Resolution * excelSheet.Cells.GetColumnWidthPixel(CellColumn)) / 96;//96 is standard resolution
generator.Parameters.ImageHeight.Pixels = (Resolution * excelSheet.Cells.GetRowHeightPixel(CellRow)) / 96;//96 is standard resolution
generator.Parameters.AutoSizeMode = Aspose.BarCode.Generation.AutoSizeMode.Nearest;
MemoryStream imageStream = new MemoryStream();

//EMF is a vector image format but it can be not fully supported on non-Windows systems
generator.Save(imageStream, BarCodeImageFormat.Emf);
imageStream.Position = 0;

//insert the barcode image into the cell
Aspose.Cells.Drawing.Picture excelPicture = excelSheet.Pictures[excelSheet.Pictures.Add(CellRow, CellColumn, CellRow + 1, CellColumn + 1, imageStream)];

//set the image as resizable with cell size changing
excelPicture.Placement = Aspose.Cells.Drawing.PlacementType.MoveAndSize;

//save the Excel book
excelBook.Save($"{path}AddBarcodeToExcelDocumentWithImageFitting.xlsx", Aspose.Cells.SaveFormat.Xlsx);
{{< /highlight >}}
  
[**Sample Outputs for Image Fitting**](addbarcodetoexceldocumentwithimagefitting.xlsx)
  