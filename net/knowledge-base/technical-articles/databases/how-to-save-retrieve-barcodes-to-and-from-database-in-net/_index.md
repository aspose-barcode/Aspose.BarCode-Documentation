---
title: How to Save Retrieve Barcodes to and from Database in .NET
type: docs
weight: 10
url: /net/how-to-save-retrieve-barcodes-to-and-from-database-in-net/
---

We know that it is possible to save a barcode as an image file using [Aspose.BarCode](https://products.aspose.com/barcode/net). Developers can use this feature to obtain a barcode image and then save it to some location on a network or a local machine. But sometimes, we need more flexibility. If you are working in some company and generate barcodes regularly then it can be great trouble for you to manage all these barcode images to some folder of your local or network-based storage device. In such circumstances, it would be better to store your barcodes in some database.

This article will discuss Two Approaches for developers to manage barcodes in databases as follows:

- Storing Barcode Information in Database
- Storing Barcode Image in Database

Every approach has its own merits and demerits. So, it's up to the developers to decide which approach fulfills their requirements.

## **Save and Retrieve Barcode Information**
The most simple approach to manage barcodes is to store barcode information in the database. This approach allows developers to store barcode information like its Code text and Symbology to the database. So, instead of barcode images, only barcode details are stored in a database. When a barcode is needed to display then those barcode details are retrieved from the database to generate a barcode image at runtime. To understand this approach, let's create a small application that generates a barcode, and the barcode's details such as its Code text and Symbology are stored in a SQL Server database.
### **Creating a Database**
First of all, we should create a database using any DBMS like Oracle, SQL Server, or MS Access, etc. For this article, we have used Microsoft SQL Server for creating the database.
We have created a table named barcodes in the database with three columns in it. In the first column, the bid is acting as a Numeric Primary Key and Table Identity Column as well. It means that the bid column will automatically generate its primary key (unique) values and we do not have to enter any unique values in it by ourselves. The other two columns, code text, and symbology are of varchar type, which means that these columns can store the variable length of characters.
### **Saving Barcode Details to Database**
Now, we have to create an application that generates a specific barcode image according to user inputs. We will generate a barcode by creating an instance of the BarcodeGenerator class. Define the BarcodeType in the constructor and assign the text of the barcode to the CodeText property. For saving barcode details in the database, we need to open a database connection using SqlConnection and insert the Code text and Symbology of the barcode into the database table by calling the ExecuteNonQuery method of SqlCommand. To enhance the efficiency of this insertion, you may use a Parameterized SQL Query by defining @Codetext and @Symbology as parameters:
{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-BarcodeWithDatabase-StoreInDB.cs" >}}
### **Retrieving Barcode Details from Database**
If it is required to display the barcode image from the information stored in the database, the details of that specific barcode are retrieved from the database and a barcode is generated at runtime according to those barcode details.

For this purpose, we need to connect to the database and select specific barcode details and fills the DataTable with those barcode details using SqlDataAdapter. A BarcodeGenerator is created at runtime. It's CodeText and SymbologyType properties are configured using barcode details in DataTable.
{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-BarcodeWithDatabase-RetrieveFromDB.cs" >}}

The above-mentioned method can be used with Windows Forms application using the [BarCodeControl](https://apireference.aspose.com/barcode/net/aspose.barcode.windows.forms/barcodecontrol).
After the BarCodeControl is added to the Controls collection of Panel, the barcode image gets visible.
### **Merits**
- This approach works great for small and simple applications where only simple barcodes are generated
- It's rather easy to store a barcode in the form of a few text values in the database than storing the barcode image
- Using this approach, developers can save their resources like database
- Applications work more faster
### **Demerits**
If you are creating more complex barcode images by also customizing there:* ForeColor

- Background Color
- Bar Height
- Wide to Narrow Ratio
- X-Dimension
  and other properties then you would have to create extra columns in your database table to store the information about all properties related to a barcode. Then this approach would depict the following problems:
- More columns in the table would be created that will consume more storage resources
- Whenever some new information about the barcode would be needed to be stored, changes will be made to not only database but also to the source code
- Increasing the number of columns in the database table would also take more efforts by you to write more lines of code
  Just assume some extra properties of the barcode that would be required to be stored in the database.

## **Save and Retrieve Barcode Image**
To save yourself from writing more lines of source code and creating a large number of columns in a database table, there is another approach and it is to store the barcode image itself to the database. A barcode can be simple with just two properties or complex with more number of properties.

### **Saving Barcode Image to Database**
Using this approach, any barcode image can be stored in a database ranging from the simplest to the most complex one. For saving an image to the database, we need to create a Varbinary datatype column in our database table. To store a barcode image in the database, the image shall be saved to a MemoryStream and then will be converted to image bytes. The image bytes will be stored in the database column of the Varbinary type as demonstrated in the code example given below.
{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-BarcodeWithDatabase-StoreImageInDB.cs" >}}

### **Retrieving Barcode Image from Database**
The following code example demonstrates how to retrieve a barcode image from the database.
{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-BarcodeWithDatabase-RetrieveImageFromDB.cs" >}}

The following code example demonstrates how to initiate the Save and Retrieve methods.
{{< gist "aspose-com-gists" "f801733f5eb53b0777dd38da9db8366a" "Examples-CSharp-TechnicalArticles-BarcodeWithDatabase-BarcodeWithDatabase.cs" >}}

## **Conclusion**
Both approaches discussed so far, have their advantages and disadvantages which are briefly described in the article. Generally, for simple applications where simple and identical barcodes are generated, the first approach can work better whereas, for such applications that allow users to create complex and different kinds of barcodes, the second approach can do its best. But still, developers can make efficient use of any approach in any kind of application according to their requirements.