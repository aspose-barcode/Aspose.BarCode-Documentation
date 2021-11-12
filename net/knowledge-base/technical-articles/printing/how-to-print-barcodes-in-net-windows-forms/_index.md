---
title: How to Print Barcodes in .NET Windows Forms
type: docs
weight: 10
url: /net/how-to-print-barcodes-in-net-windows-forms/
---

## **How to Print Barcodes in .NET Windows Forms**
In this article, we will learn about using printing controls (provided by Microsoft .NET Framework) to print barcodes generated by [Aspose.BarCode](https://products.aspose.com/barcode/net). We have practiced only two printing controls of Microsoft .NET Framework for demonstration purposes as follows:

- PrintDocument control that represents a document to print.
- PrintPreviewDialog control that allows users to preview the document before printing.

We simply create a barcode image using Aspose.BarCode control for windows forms that is [BarCodeGeneratorControl](https://apireference.aspose.com/barcode/net/aspose.barcode.windows.forms/barcodegeneratorcontrol) then we use that barcode image generated by BarCodeControl to print on the page using PrintDocument control. We will learn all this with the help of an application. Let's create a windows application step by step using Visual Studio.NET that will demonstrate the printing of barcodes.
### **Step 1: Creating New Project**
Open Visual Studio.NET IDE and create a New Project using any desired .NET language. We have chosen Visual C#.NET language for this project but all code snippets for this article are provided in both C# and VB.NET languages for the ease of developers.
### **Step 2: Adding BarCodeControl to Form**
After a project is created, an empty windows form will be visible to you. Firstly, we have to design the front end of our application. So, drag a BarCodeControl from the Toolbox and drop on the empty windows form's surface. A barcode with default Code text and symbology will be displayed on the windows form.
### **Step 3: Adding Buttons to Form**
Now, it's time to add buttons on the windows form to finish the design of our application's front end. We will add two buttons on the form:

- Print Barcode button that will be used to print barcode when clicked.
- Preview Barcode button that will create a preview of the barcode before printing.
### **Step 4: Final Front End of our Application**
Once a BarCodeControl and all required buttons are added to windows form and desired properties (like Text to display on buttons etc.) are set then the front end design of our application would be finished.
### **Step 5: Adding PrintDocument Control to Form**
After finishing the look and feel of our application, it's time to get prepared for the back end functionality. Now, we start adding printing-related controls to our windows form by dragging a PrintDocument control from Toolbox to the windows form. PrintDocument is not a GUI based control so, you cannot view it on the surface of windows form like BarCodeControl. When we add PrintDocument control to the windows form, an instance ( printDocument1 ) of PrintDocument is created in the windows form and the name of the instance is displayed on a separate pane of the Visual Studio.NET to confirm its presence in the Form.
### **Step 6: Adding PrintPreviewDialog Control to Form**
PrintPreviewDialog control is not necessary for printing but it's better to preview a barcode before printing so that you may visualize that how would it be printed. That's why, we have added PrintPreviewDialog control also in our application. Like PrintDocument, PrintPreviewDialog control is also Non-GUI based. It is added to the Form in the same way as that of PrintDocument control.
### **Step 7: Implement Print Button Functionality**
Now, we will implement the Print Barcode button functionality. To do so, we will double click the Print Barcode button and the source code editor will be opened. The Click event of a button would be created automatically by Visual Studio.NET IDE runtime. All you have to do, is to add some code to this Click event of the Print Barcode button. We remember that in Step 5, we added a PrintDocument control to our Form. PrintDocument control has a method, Print , which should be called to initiate the printing process. So, call the Print method in the Click event of the Print Barcode button as shown below:

{{< gist "aspose-barcode" "2224aabcdb4d2a259b10" "Examples-CSharp-printButton_Click-printButton_Click.cs" >}}
### **Step 8: Implement PrintPage Event of PrintDocument Control**
When the Print method of PrintDocument control is called then the PrintPage event of the PrintDocument control is automatically triggered to print the page information (such as barcode). But the main Issues are:

- How can we get the barcode image generated by BarCodeControl which is visible on the Form?
- How to draw that barcode image to the printing page?
#### **Issue No.1**
The barcode image (generated by BarCodeControl) can be obtained by using the BitmapImage property of the BarCodeControl class.
#### **Issue No.2**
PrintPage event of the PrintDocument control takes an instance of [PrintPageEventArgs](http://msdn.microsoft.com/library/en-us/cpref/html/frlrfsystemdrawingprintingprintpageeventargsclasstopic.asp) class, e as a parameter. The PrintPageEventArgs, e contains the Device Contexts [e.Graphics](http://msdn.microsoft.com/library/en-us/cpref/html/frlrfsystemdrawingprintingprintpageeventargsclassgraphicstopic.asp) that is used to draw barcode to the printer. e.Graphics has a method [DrawImage](http://msdn.microsoft.com/library/en-us/cpref/html/frlrfsystemdrawinggraphicsclassdrawimagetopic.asp) that is used to draw barcode image at some specified Horizontal X and Vertical Y location on the page. We have used X=350 and Y=40 in our application as follows:

{{< gist "aspose-barcode" "2224aabcdb4d2a259b10" "Examples-CSharp-printDocument1_PrintPage-printDocument1_PrintPage.cs" >}}
### **Step 9: Implement Preview Button Functionality**
To implement the Preview Barcode button functionality, we will double click the Preview Barcode button and the source code editor will be opened. The Click event of a button would be created automatically by Visual Studio.NET IDE runtime as we discussed earlier. All you have to do, is to add some code to this Click event of Preview Barcode button.

In Step 6, we added PrintPreviewDialog control to our Form for adding the support to preview barcode before printing in our application. PrintPreviewDialog control has a property, [Document](http://msdn.microsoft.com/library/en-us/cpref/html/frlrfsystemwindowsformsprintpreviewdialogclassdocumenttopic.asp) that encapsulates the document to be previewed. So, we pass the PrintDocument instance (printDocument1) to the Document property of PrintPreviewDialog control and finally call [ShowDialog](http://msdn.microsoft.com/library/en-us/cpref/html/frlrfsystemwindowsformsformclassshowdialogtopic.asp) method to show the dialog as shown below:

{{< gist "aspose-barcode" "2224aabcdb4d2a259b10" "Examples-CSharp-previewButton_Click-previewButton_Click.cs" >}}
### **Step 10: Running & Testing Print Function of Application**
Once all things are set up, now you are ready to build/compile your application source code. Once your project is built, run your application and click the Print Barcode button. Once the Print Barcode button is clicked, a Printing dialog appears for a short interval of time and then disappears. A page containing a barcode drawn on it, is queued up into the printing queue of your system. If you have a printer attached to your system then a print request for the page will be sent to the default printer of your system.
### **Step 11: Running & Testing Preview Function of Application**
If you don't have a printer and feeling curious to see the page with a barcode on it using your computer then you can click the Preview Barcode button. Once the button is clicked, a Print preview form will be opened in front of you that will be showing the page containing a barcode image on it. You can set the zoom level of the page also if you want to enlarge the page view. We previewed our page at 150% zoom level.
## **Conclusion**
Aspose.BarCode provides a barcode image that gives full freedom to developers to make use of that barcode image in any kind of application in any way. Printing of barcodes using printing control provided by Microsoft .NET Framework, is one of the uses of barcode image in a useful manner.