---
title: How to Use Aspose.BarCode .NET in Crystal Report
type: docs
weight: 10
url: /net/how-to-use-aspose-barcode-net-in-crystal-report/
---

## **How to Use Aspose.BarCode .NET in Crystal Report**
In this article, we will demonstrate how to display barcodes generated by Aspose.BarCode in Crystal Report files (*.rpt). Displaying images in Crystal Report could be rather baffling, in fact, it's full of pits and falls. This article is dedicated to clearly explains how to do so. The easiest way to display the image in the crystal report is directly reading images from the database, to do that, just drag the image field to your report. However, most of the time we want to provide or change the image at run time. Then we need a dataset to store the dynamic image and feed it to the report.

Aspose.BarCode offers .NET developers the ability to create barcode images quickly and fully control the images including : background color, bar color, image quality, rotation angle and etc. Moreover, Aspose.BarCode also supports exporting the images to multiple image formats, and save the images to disks or stream instances. We could save the image into a dataset through a stream object and bind it to a crystal report.
### **Hands on example**
#### **Step 1: Create a dataset with an image field**
First of, add a new items to your web project and choose dataset, name it DataSet_BarCode. Now a xsd file DataSet_BarCode is created, this xsd file represents the dataset which will contain two fields, a string CodeText field and a Base64Binary image field. To do so, either edit this dataset in designer or in the xml tab directly:

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-DataSetBarCode-DataSetBarCode.cs" >}}

The data schema is as followed:
{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-Data Schema.xml" >}}


This dataset will provide for the report to display the image you stored in it. Now build the project to check it out.
#### **Step 2: Create a crystal report**
Add a new report to your project, use the default settings, just click next. Next, the standard report expert dialog shows up, on the data tab, choose Project data/ADO.NET DataSets, insert our newly created table: DataTable. Next, choose fields to display. If the report is not created by the Report Expert, you could go to Field Explorer to add the data table.
#### **Step 3: Edit report**
Now edit the report. Make sure there is enough space for the BarCodeImage to display properly.
#### **Step 4: Add report viewer**
Add a report viewer to the default page.
#### **Step 5: Coding**
In the page load method, create a barcode builder, generate the barcode image and store it into the dataset.
#### **Step 6 Build and run**

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-Report-Report.cs" >}}

*DataSet_BarCode is defined in XSD file, we could treat it as a classCrystalReport1.rpt will define a class named CrystalReport1, we could treat it as a class*
### **Issues**
If the deployment machine does not have visual studio installed on it, (only frame work installed) then you will have to do some extra settings to make it work.
### **Conclusion**
Aspose.BarCode provides a barcode image that gives developers the freedom to apply any application under any situation.
### **About Author**
This article is written by Kyle Huang (Team Leader, Aspose Pty Ltd.). He is responsible for product development and technical support in Aspose Guangzhou. He is a certified Microsoft Certified Solution Developer (MCSD) and providing consultancy services on .NET platforms. [Contact Author](/barcode/net/mailto-kyle-huang@aspose-com/) This article is then edited by Aspose service team. Who are responsible for technical and non-technical support for Aspose.com [Contact Service Team.](/barcode/net/mailto-guangzhou@aspose-com/).