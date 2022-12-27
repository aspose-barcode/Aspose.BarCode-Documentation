---
title: Reading Barcode Properties and Metadata
type: docs
description: "This article describes how to read barcode parameters and encoded metadata"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Read PDF417 Barcode, Read PDF417 Metadata, Read Qr Code, Read QR Code Metadata, QR Code Structured Append, Aspose.BarCode, Read Barcodes in Python"
weight: 40
url: /python-net/read-barcode-properties/

---
 
## **Overview**
***Aspose.BarCode for Python via .NET*** not only enables reading information encoded in a barcode but also provides a possibility to analyze its technical properties, including barcode type, orientation angle, position, and metadata. This data is stored in objects of class [*BarCodeResult*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/) and can be fetched using properties described further in this article.  


{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/python-net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Barcode Type and Encoded Data**
To obtain input barcode data and its type, *code_text* and *code_type* properties of class [*BarCodeResult*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/) can be used. The other property called *code_type_name* returns the text name of the barcode type.

## **Barcode Position and Orientation Angle**
To obtain the position of a source barcode and its orientation angle, class [*BarCodeRegionParameters*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderegionparameters/) can be used. This class allows getting the information about the barcode region in the following forms:
-	quadrangle – a quadrangle object that bounds a barcode
-	rectangle - a rectangle object that bounds a barcode
-	points – an array of points constituting a barcode
-	angle – an orientation angle in degrees

## **Reading Barcode Data as Byte Stream**
It is possible to load barcode data as a byte stream using a property of class [*BarCodeResult*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/) that is called *code_bytes*. 
  
## **Quality Check of Recognition Results**
Developers may need to check whether barcode reading outputs are accurate and complete. For this purpose, class [*BarCodeResult*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcoderesult/) contains two properties: *confidence* and *reading_quality*.  
Depending of the quality of barcode reading results, the *confidence* property returns a instance of the [*BarCodeConfidence*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/barcodeconfidence/) enum that denotes the recognition confidence level. This enumeration contains values *STRONG*, *NONE*, and *MODERATE* that are discussed below. The *reading_quality* property returns an estimate of recognition quality corresponding to the confidence level, as explained in the table below.
  
|Confidence Level|Quality Value|Description|
|---|---|---|
|*NONE*|0|If the confidence level is *None*, it indicates that the barcode is invalid and its information has been read with errors. If required, it is possible to get its type and position in the image and decode barcode information partially|
|*MODERATE*|80|This confidence level may be returned for linear and postal barcode types with weak or absent checksum controls. Furthermore, it is necessary to analyze the result of the *reading_quality* property. The absolute correctness of barcode reading results is not assured|
|*STRONG*|100|This confidence level is returned for all 2D types with Reed-Solomon error correction. It means that barcode text has been recognized accurately|
  

## **Barcode Metadata**

### **Reading Metadata from 1D Barcodes**
Some 1D barcode types, i.e. *EAN 13*, allow separating barcode input information itself from the checksum value. To do this, class [*OneDExtendedParameters*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/onedextendedparameters/) provides the *value* property that allows getting 1D barcode text and the *check_sum* property that returns the result of checksum computation.

### **Reading Metadata from QR Codes with Structured Append**
To fetch metadata from *QR Code* barcodes with structured append, the barcode library provides a class called [*QRExtendedParameters*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/qrextendedparameters/) that enables reading the information from structured append used to combine several *QR Code* barcodes into one. This data can be obtained using the following properties:

- *qr_structured_append_mode_bar_code_index* - returns the sequence number of the current barcode (starting from 0)
- *qr_structured_append_mode_bar_codes_quantity* - returns the number of barcodes in a composite *QR Code* barcode taht can take values from 2 to 16
- *qr_sructured_append_mode_parity_data* - returns the checksum identifier byte that is usually computed as *XOR* of all bytes in which UTF16BE characters are encoded in two bytes  
    
### **Getting Raw Data from Code 128 Barcodes**
Input data stored in *Code 128* barcodes can be encoded in three ways: A, B, or C. Class [*Code128ExtendedParameters*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/code128extendedparameters/) provides a property called *code_128_data_portions* that returns decoded parts of barcode input information and the encoding mode.

### **Reading Metadata from DataBar Barcodes with 2D Components**
Metadata from *DataBar* barcodes with 2D components can be obtained using class called [*DataBarExtendedParameters*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/databarextendedparameters/) that provides a property called *is_2d_composite_component*. This property allows enabling or disabling a 2D component in *DataBar* barcodes. 

### **Reading Macro PDF417 and Macro PDF417 Metadata**
Metadata from *PDF417* barcodes can be obtained using the properties of class [*Pdf417ExtendedParameters*](/barcode/python-net/api-reference/aspose.barcode.barcoderecognition/pdf417extendedparameters/) listed below.
  
|PDF417 Metadata Property|Description|
|---|---|
|*pdf_417_macro_file_id*|Gets the unique identifier of a barcode series or a PDF417 file|
|*pdf_417_macro_segment_id*|Gets the current identifier of a segment|
|*pdf_417_macro_segments_count*|Returns the number of barcodes in a series|
|*pdf_417_macro_file_name*|Returns the name of a file|
|*pdf_417_macro_checksum*|Gets the checksum value computed using CCITT-16 polynomial|
|*pdf_417_macro_file_size*|Returs the total size of bytes in a series|
|*pdf_417_macro_time_stamp*|Returns the time spent to generate/send the file|
|*pdf_417_macro_addressee*|Gets the address of the file sender|
|*pdf_417_macro_sender*|Returns the name of the file sender|
  
## **Decoding Barcode Text in Unicode**
For barcodes in which the barcode data is encoded in a Unicode encoding, the barcode library provides the *get_code_text(encoding)* method that can be used to enable the required encoding.  