---
title: Generate Postal Barcodes
linktitle: Postal Barcodes
type: docs
weight: 170
url: /python-net/generate-postal-barcodes/

---
{{% alert color="primary" %}}[Generate USPS Planet and](https://products.aspose.app/barcode/generate/planet) [USPS Postnet Barcodes online](https://products.aspose.app/barcode/generate/postnet). You can check the quality of ***Aspose.BarCode*** generation for postal barcodes and view the results online.{{% /alert %}}

## **Overview**
Postal barcode types have been introduced to address some problems of 1D barcode types to facilitate postal operations. Such barcode types suggest encoding input information by altering the height of bars and not the width of bars and spaces as in 1D standards. Postal barcode standards usually ignore horizontal parameters to mitigate the risk of false-positive barcode detection.  
  
Many countries use their own barcode specifications for postal services. Generally, such barcode types are similar to each other in terms of design with some minor distinctions. Postal barcode standards can be classified into two main groups: two-state ones that can encode only numerical characters and four-state ones that allow encoding both numerical digits and uppercase English characters.  
  
***Aspose.BarCode for Python via .NET*** can be used to create and read various two- and four-state postal standards, i.e. *RM4SCC*, *Postnet*, *Planet*, *Dutch KIX*, *Australia Post*, *OneCode*, and *Mailmark*. Further, this article describes how to work with postal symbologies using the *Aspose.BarCode* library functional.
  
{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact Aspose [Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Bar Height Settings**
By default, ***Aspose.BarCode for Python via .NET*** enables automatic calculation of bar height and width for postal barcode standards depending on the *XDimension* value. It also enables manually customizing bar height regardless of barcode width using the *bar_height* property of class [*BarcodeParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/barcodeparameters/).  
  
Following *Planet* and *RM4SCC* barcode images have been created with varying bar height settings.  
  
|Bar Height Settings for **Planet**| | |
|---| :-: | :-: |
|Bar Height|Is Set to None|Is Set to 100 Pixels|
| |<img src="postalplanetbarheightnone.png">|<img src="postalplanetbarheight100pixels.png">|
  
|Bar Height Settings for **RM4SCC**| | |
|---| :-: | :-: |
|Bar Height|Is Set to None|Is Set to 100 Pixels|
| |<img src="postalrm4sccbarheightnone.png">|<img src="postalrm4sccbarheight100pixels.png">|
  
## **Bar Filling Options**
***Aspose.BarCode for Python via .NET*** enables adjusting the appearance of postal barcode images in terms of setting full or empty filling for bars. Developers can generate postal barcodes with empty bars using the *filled_bars* property of class [*BarcodeParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/barcodeparameters/). The default value of this parameter is *True*, meaning that the generated postal barcode image will have fully colored bars.  
  
Following *Planet* and *RM4SCC* barcode images have been generated using different bar filling settings.
  
|Bar Filling for **Planet** Barcodes| | |
|---| :-: | :-: |
|**Bar Filling Settings**|**Filled Bars**|**Empty Bars**|
| |<img src="postalplanetfilledbars.png">|<img src="postalplanetemptybars.png">|
  
|Bar Filling for **RM4SCC** Barcodes| | |
|---| :-: | :-: |
|**Bar Filling Settings**|**Filled Bars**|**Empty Bars**|
| |<img src="postalrm4sccfilledbars.png">|<img src="postalrm4sccemptybars.png">|
  

## **Two-State Postal Types**
In ***Aspose.BarCode for Python via .NET***, developers can generate barcodes using various two-state postal symbologies, i.e. *Postnet* and *Planet*. These barcode standards allow encoding only numerical characters and require obligatory checksum controls. Code snippets and sample barcode images provided further demonstrate how to create postal barcodes of *Planet* and *Postnet* types.  

### **Planet Standard**
*Planet* barcodes encode each character in five bars. Among them, three bars are full-length, and two bars are half-length.  
  
<p align="center"><img src="postalplanetbarcode.png"></p> 
  
### **Postnet Standard**
The *Postnet* type encodes each digit in five bars so that three bars are full-length and two bars are half-length.  
  
<p align="center"><img src="postalpostnetbarcode.png"></p>

## **Specific Properties of Two-State Barcode Generation**
The ***Aspose.BarCode*** library has several specificities in the way of working with two-state postal barcodes. They are associated with handling invalid barcode text and changing bar length. These special cases are outlined further.

### **Handling Invalid Barcode Text Exception**
When invalid barcode text is passed to the *code_text* property (in the case of *Postnet* and *Planet*, this means entering any characters besides numerical digits), the default approach implemented in class [*BarcodeGenerator*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/barcodegenerator/) implies the necessity to filter out erroneous symbols that do not comply with the specification and then to generate a barcode image encoding suitable characters only. If developers need to establish special controls for such situations, they can request throwing an exception upon entering invalid characters using the *code_text* property. In this case, it is necessary to initialize the *throw_exception_when_code_text_incorrect* property of class [*BarcodeParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/barcodeparameters/) with the *True* value.

### **Customizing Bar Height**
By design, two-state postal barcodes contain long and short bars in such a way that the shorter bars are half-length with respect to the longer bars. ***Aspose.BarCode for Python via .NET*** allows modifying bar height for short bars manually. To do this, the *postal_short_bar_height* property of class [*PostalParameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/postalparameters/) needs to be used.  
  
Following barcode images have been created with varying short bar heights.
  
|Short Bar Height|Is Set to 10 Pixels|Is Set to 30 Pixels|
| :-: | :-: | :-: |  
| |<img src="postalplanetshortbarheight10pixels.png">|<img src="postalplanetshortbarheight30pixels.png">|
  
   
## **Four-State Postal Types**
***Aspose.BarCode for Python via .NET*** enables generating and reading several four-state postal barcode standards, including *RM4SCC*, *Dutch KIX*, *OneCode*, *Australia Post*, and *Mailmark*. By design, four-state barcode types use four different bar types to encode data: tracker (T), descender (D), ascender (A), and full (F). Therefore, each symbol is encoded in four bars meaning that two bits are encoded in one character. In general, four-state symbologies are designed as variations of the *RM4SCC* standard and support encoding numerical characters and uppercase English letters. All aforementioned four-state barcode types except *Dutch KIX* contain checksum controls. In addition, *Mailmark* and *Australia Post* support Reed-Solomon error correction to enable data recovery. 

### **RM4SCC Standard**
The *RM4SCC* symbology can be used to encode numerical characters and uppercase English letters. In this barcode standard, each symbol in a barcode is encoded in four bars among which two bars are enlarged upwards and the other two bars - downwards. Using supported combinations of bars with different lengths, it is possible to encode up to 36 characters, i.e. 10 digits and 26 letters. *RM4SCC* contains obligatory checksum controls using the modulo 6 algorithm.
   
<p align="center"><img src="postalrm4sccbarcode.png"></p>
  
### **Dutch KIX Standard**
The Royal Dutch TPG Post of Netherlands uses the *Dutch KIX* barcode standard to facilitate automatic sorting of mails and process postal codes. It is similar to the RM4SCC symbology and allows encoding numerical digits and uppercase English letters. By design, it does not require checksum controls and does not contain start and stop symbols.
  
<p align="center"><img src="postaldutchkixbarcode.png"></p>
  
  
### **OneCode Standard**
The *OneCode* postal symbology allows encoding fixed-length sets of numerical characters, i.e. 20, 25, 29, or 31 digits. It supports eleven-bit cyclic redundancy verification to detect errors but does not include an error correction mechanism.  
  
|Number of Digits|20 Digits|25 Digits|29 Digits|31 Digits|
| :-: | :-: | :-: | :-: | :-: |  
| |<img src="postalonecodebarcode20digits.png">|<img src="postalonecodebarcode25digits.png">|<img src="postalonecodebarcode29digits.png">|<img src="postalonecodebarcode31digits.png">|
  

### **Australia Post Standard**
The *Australia Post* postal standard uses special two-digit format control code (FCC) fields and eight-digit sorting code (SC) fields to generate barcodes. FCC fields are intended to determine one of three supported subtypes that have various fixed lengths, i.e. 37, 52, or 67 bars. Moreover, barcodes may include a customer information (CI) field to specify one of the available encoding types (numerical or alphanumeric characters). These settings can be customized using the *australian_post_encoding_table* property of class [*AustralianPostPatrameters*](https://reference.aspose.com/barcode/python-net/aspose.barcode.generation/australianpostparameters/). Customer data can take 31 bars in barcodes with 67 bars or 16 bars in barcodes with 52 bars. *Australia Post* has checksum controls and supports Reed-Solomon error correction.  
  
Barcode data can be prepared using one of the supported formats as explained below.  
  
|FCC Field|Sorting Code Field|Customer Information Field|  
| :-: | :-: | :-: |
|11|8 digits|None|
|59|8 digits|16 bars|
|62|8 digits|31 bars|
  
The FCC field can be determined using the *australian_post_encoding_table* property that has to be called by passing one of the values from the *CustomerInformationInterpretingType* enum listed in the table below.
  
|Australia Post Encoding Table|Supported Symbols|
| :-: |---|
|CTable|0-9, A-Z, a-z, space symbol, and #|
|NTable|0-9|
|Other|0, 1, 2, and 3 that correspond to H, A, D, and T states, respectively|
  
Following barcode images have been created with varying FCC field settings.
  
|Australia Post Subtypes|FCC 11|FCC 59 Table|FCC 62N Table|FCC 62C Table|FCC 62C Other Table|
| :-: | :-: | :-: | :-: | :-: | :-: |  
| |<img src="postalaustraliapostfcc11.png">|<img src="postalaustraliapostfcc59ntable.png">|<img src="postalaustraliapostfcc62ntable.png">|<img src="postalaustraliapostfcc62ctable.png">|<img src="postalaustraliapostfcc62othertable.png">|
  

### **Mailmark Standard**
The *Mailmark* postal standard has been introduced by Royal Mail of the United Kingdom. In general, its design is similar to *RM4SCC*; however, it requires entering barcode information in a strict format and does not support adding customer data. This symbology can be used to encode numerical characters, uppercase English letters, and space. It has checksum controls and supports Reed-Solomon error correction.  
*Mailmark* has two main subtypes: 
- **Type L** - allows encoding 26 characters 
- **Type C** - allows encoding 22 characters
  
|Mailmark Subtype|Type C|Type L|
| :-: | :-: | :-: |  
| |<img src="postalmailmarkctype.png">|<img src="postalmailmarkltype.png">|
  
