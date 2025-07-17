---
title: How to Save Retrieve Barcodes to and from Database in .NET
linktitle: Store Barcodes in Database
type: docs
ai_search_scope: "barcode_dotnet_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 10
feedback: BARCODECOM
url: /net/how-to-save-retrieve-barcodes-to-and-from-database-in-net/
aliases: 
- /net/databases/
---

## **Overview**

It is possible to save a barcode as an image file using [Aspose.BarCode](https://products.aspose.com/barcode/net). Developers can use this feature to generate a barcode image and then save it to some location in a network or a local machine. In some cases, it may be required to store barcodes in a database.

This article discusses two approaches to manage barcodes in databases:
- Store the information about barcodes
- Store barcode images

Each of these approaches has advantages and limitations. Developers can decide which method fulfills their requirements better.

## **Save and Retrieve Barcode Information**
The most simple way to manage barcodes in a database is to store barcode information, such as barcode text and type. Instead of loading original barcode images, only their details are saved in a database. When a barcode needs to be displayed, this information is retrieved from the database and the corresponding barcode image is generated at runtime. This approach is illustrated by the code sample provided further.

### **Create Database**
First, it is required to create a database using any DBMS, such as Oracle, SQL Server, MS Access, etc. In the provided examples, Microsoft SQL Server has been used to create a database. Then, a table with three columns has been inserted. In the first column, the bid denotes the Numeric Primary Key and Table Identity Column. It means that the bid column will automatically generate its primary key (unique) values. The other two columns named "code text" and "symbology" have the varchar type, meaning that they can store characters of variable length.

### **Save Barcode Information to Database**
To implement an application that generates barcode images according to user inputs, an instance of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/) needs to be created specifying the required [*BarcodeType*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/barcodetype/) in the constructor and input text to the [*CodeText*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/codetext/) property. To save barcode information in the database, it is needed to open a database connection using [*SqlConnection*](https://docs.microsoft.com/en-us/dotnet/api/system.data.sqlclient.sqlconnection?view=dotnet-plat-ext-6.0) and insert the barcode text and type into the table by calling the [*ExecuteNonQuery*](https://docs.microsoft.com/en-us/dotnet/api/system.data.sqlclient.sqlcommand.executenonquery?view=dotnet-plat-ext-6.0) method of [*SqlCommand*](https://docs.microsoft.com/en-us/dotnet/api/system.data.sqlclient.sqlcommand?view=dotnet-plat-ext-6.0). To improve the efficiency of this operation, it is possible to use a Parameterized SQL Query by defining @Codetext and @Symbology as parameters.  
  
{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-BarcodeWithDatabase-StoreInDB.cs" >}}

### **Retrieve Barcode Information from Database**
To display the barcode image from the database, the information about this barcode has to be retrieved, and the barcode is generated at runtime accordingly. To do this, it is necessary to connect to the database and select the data for the barcode to be generated. Then, it is needed to fill the DataTable with this data using [*SqlDataAdapter*](https://docs.microsoft.com/en-us/dotnet/api/system.data.sqlclient.sqldataadapter?view=dotnet-plat-ext-6.0). An object of class [*BarcodeGenerator*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/) is created at runtime so that its [*CodeText*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/codetext/) and [*BarcodeType*](https://reference.aspose.com/barcode/net/aspose.barcode.generation/barcodegenerator/barcodetype/) properties are configured using the barcode information from DataTable.  

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-BarcodeWithDatabase-RetrieveFromDB.cs" >}}

This method can be also implemented in Windows Forms using [BarCodeControl](https://reference.aspose.com/barcode/net/aspose.barcode.windows.forms/barcodecontrol).
After dragging the [BarCodeControl](https://reference.aspose.com/barcode/net/aspose.barcode.windows.forms/barcodecontrol) element to the Controls collection of Panel, the barcode image gets visible.

### **Advantages**
This approach has the following advantages:
- Suitable for small and simple applications where only basic barcodes are generated
- More efficient as it allows storing barcode information as several text values in the database instead of saving the barcode image itself
- Efficient in terms of database memory resources
- Provides faster execution

### **Limitations**
If it is required to generate complex barcode images by customizing their parameters, such as forecolor, background color, bar height, wide-to-narrow ratio, X-dimension, and others, extra columns need to be added to the database table to store the information about all properties related to a barcode image. In this case, the following limitations would arise:
- It takes more database memory resources
- It requires updating not only the database but also the source code to store additional information about barcode images
    
## **Save and Load Barcodes from Database**
To avoid creating a large number of columns in a database table for complex barcodes, the other approach can be used. It allows saving barcode image files in the database. A barcode can be basic with just two parameters or complex with many customized properties.

### **Save Barcode Image to Database**
To save a barcode image to the database, it is necessary to create a varbinary data type column in the database table. The image must be saved as a MemoryStream and then converted to image bytes that are stored in the database column of the varbinary type, as demonstrated in the code example given below.  

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-BarcodeWithDatabase-StoreImageInDB.cs" >}}

### **Load Barcode Image from Database**
The following code sample demonstrates how to retrieve a barcode image from the database.  
  
{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-BarcodeWithDatabase-RetrieveImageFromDB.cs" >}}

The following code snippet shows how to call the *Save* and *Retrieve* methods.  

{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-BarcodeWithDatabase-BarcodeWithDatabase.cs" >}}

## **Conclusion**
Both approaches discussed so far have their advantages and limitations briefly described in the article. In simple applications, the first approach can be applied. In applications intended to create complex barcodes, the second option is more suitable.