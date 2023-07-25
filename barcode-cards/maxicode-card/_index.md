---
title: MaxiCode Information Card
linktitle: MaxiCode
description: "General Overview on MaxiCode Barcode Type"
keywords: "DataMatrix, data matrix, data matrix symbology, Create datamatrix barcodes, Read data matrix, what is data matrix, data matrix barcodes, generate datamatrix, matrix barcodes, 2D barcode, data matrix specification, data matrix generator, data matrix reader, recognize data matrix, scan data matrix"
type: docs
weight: 70
url: /info-cards/maxicode/
---

## **Overview**

MaxiCode is a two-dimensional (2D) barcode type developed by United Parcel Service (UPS) to be used in transportation and logistics for efficient package sorting and tracking. It has a unique hexagonal bull's-eye pattern for quick and accurate scanning at high speeds. Its large data capacity and strong error correction capabilities make it suitable for automated sorting systems, ensuring reliable and precise data capture, thus enhancing overall shipping and logistics efficiency.

  
<p align="center"><img alt="MaxiCode Barcode" src="maxicode.png"></p>

This information card describes main properties of MaxiCode, its encoding set, structure, size dimensions, capacity, and the error correction mechanism. Code samples for generation and reading through the ***Aspose.BarCode*** library can be found [further](#asposesamples).

  
<details>  
<summary>Read more</summary>
  
MaxiCode barcodes consist of different regions with specific functions. The primary data region contains the essential information encoded in the barcode, such as destination ZIP code, shipment weight, and other package-related details. Secondary regions can be added to store auxiliary data, for example, a special message field used for custom applications.  
  
UPS is an American multinational package delivery and supply chain management company. UPS is one of the world's largest and most well-known logistics companies, providing a wide range of services, including domestic and international package delivery, freight transportation, and supply chain solutions. 

</details>

{{% alert color="primary" %}}You can find additional information of classes and properties that are used in ***Aspose.BarCode*** for MaxiCode generation and recognition:
- [**MaxiCode Barcodes**](https://docs.aspose.com/barcode/net/maxicode/)

{{% /alert %}} 


## **Usage Scenarios**
MaxiCode is widely used for three primary applications: package sorting and tracking in transportation and logistics, freight and shipping labeling for large packages and containers, and marking items in automated warehouse management systems. Its high data capacity allows encoding detailed package data, including destination ZIP code, shipment weight, and information about the sender and the recipient. This enables automated sorting systems to quickly process and route packages, ensuring efficient and accurate delivery. MaxiCode barcodes are often printed on product labels and packages to encode item details, storage locations, and inventory levels, and thus facilitate inventory management processes.

## **Characteristics**
### **Encoding Character Set**
The MaxiCode encoding set includes all 256 ASCII characters, covering a wide range of alphanumeric symbols, digits (0-9), uppercase and lowercase letters (A-Z, a-z), and special characters. The supported character set allows encoding various types of information, such as destination addresses, tracking numbers, package details, and other alphanumeric data relevant to transportation and logistics. 

### **Barcode Structure**
MaxiCode barcodes comprise a central bull's-eye finder pattern formed by three concentric black circles, six orientation patterns, and 33 rows featuring alternating arrangements of 29 or 30 hexagonal modules per row. With a data capacity of up to 93 characters, one barcode can accommodate both primary and secondary messages.  
  
The key components of the MaxiCode structure include the following:

- Central bull's-eye symbol. The core is designed as a hexagonal bull's-eye pattern. This central locator enables scanners to quickly identify and orient the barcode, providing rapid scanning even at a high speed.

- Finder patterns. These elements surround the central bull's-eye part and assist in locating the barcode during scanning. They facilitate barcode capturing from various orientations and angles.

- Clock track. This part encircles the finder patterns and consists of alternating black and white segments. It helps establish the timing and synchronization for accurate data decoding.

- Mode message. This data region is placed outside the clock track. It contains information about the format and data encoded in a barcode, providing instructions for the decoding process.

- Primary data region. This data region occupies the largest part of a barcode. It encodes the critical information about package or shipment, such as destination ZIP code, package weight, and routing details.

- Secondary data regions. Multiple smaller secondary data regions can surround the primary data region. These regions store additional data, such as special messages or supplementary information about the shipment.

<details>  
<summary>Read more</summary>

MaxiCode supports several data modes designed to process specific types of information. These modes determine how the encoded data is structured within a barcode. The following data modes are supported by MaxiCode:

- Mode 2: This is the default data mode used for most MaxiCode applications, which allows encoding up to 93 characters of data, including both a primary message and a secondary message. 
- Mode 3: This mode is intended for work with numeric data only. It supports storing up to 77 digits in a barcode and is suitable for applications where only numerical data needs to be encoded, such as tracking numbers or numeric identifiers.
- Mode 4: This mode is suitable to encode alphanumeric data. It enables encoding up to 77 alphanumeric characters, including uppercase letters, lowercase letters, digits, and special characters. This mode is useful when the encoded data includes a combination of letters and numbers, such as product codes or customer names.

</details>

### **Size Dimensions**
MaxiCode offers flexibility in terms of size parameters, supporting different configurations based on the input data. The maximum size barcode is determined by the number of modules it can contain. A module refers to the smallest unit in the barcode grid. The standard MaxiCode configuration contains 33 rows of hexagonal modules, with each row having either 29 or 30 modules. The total number of modules in a standard MaxiCode barcode is around 882.

<details>  
<summary>Read more</summary>

MaxiCode is a fixed-size barcode type, so each symbol has a standard size of 1.11 x 1.054 inch (or 26.38 x 25.39 mm) including the quiet zone. The nominal element is a hexagon with the size of 0.035 x 0.041 inch. The bull's-eye part has a standardized size of 07.74 mm. During printing, the tolerance of around 5% from the nominal size is accepted, providing some flexibility in precise dimensions while maintaining adherence to the standard. 

</details>

### **Encoding Capacity and Data Density**
MaxiCode has a high encoding capacity and data density, supporting up to 93 characters in Mode 2. Its compact form efficiently stores extensive information, making it ideal for transportation and logistics industries. Its data density is optimized by efficiently utilizing the available space in its fixed-size symbology, resulting in a barcode that can accommodate significant data while maintaining a compact form.

### **Error Correction**
MaxiCode uses Reed-Solomon error correction, enabling it to maintain data integrity despite damage or distortion. Error correction can be adjusted based on requirements, ensuring reliable data capture for transportation and logistics applications.

## **Advantages and Limitations**
Advantages of MaxiCode:

- High data capacity for extensive information storage.
- Reliable scanning and error correction capabilities.
- Fixed-size symbology for consistency and predictability.
- Suitable for package sorting, tracking, and logistics applications.

<details>  
<summary>Read more</summary>
  
Limitations of MaxiCode:

- Not widely used outside the transportation and logistics industry.
- Requires specific scanning equipment for proper decoding.
- Fixed-size may not be ideal for applications with limited space.
</details>

{{% alert color="primary" %}}[Read](https://products.aspose.app/barcode/recognize/mmaxicode) and [Generate](https://products.aspose.app/barcode/generate/maxicoded) MaxiCode barcodes online. You can test ***Aspose.BarCode*** functionality and view results.{{% /alert %}}


## **How to Generate and Read MaxiCode Barcodes**

<a name="asposesamples"></a>

### **Generation Code Samples**

{{< tabs tabTotal="3" tabID="1" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

```csharp

aaa

```

{{< /tab >}}

{{< tab tabNum="2" >}}

```java

aaa

```

{{< /tab >}}

{{< tab tabNum="3" >}}

```cpp

aaa

```
    
{{< /tab >}}

{{< /tabs >}}

### **Recognition Code Samples**

{{< tabs tabTotal="3" tabID="2" tabName1="C#" tabName2="Java" tabName3="C++" >}}

{{< tab tabNum="1" >}}

```csharp

aaa

```

{{< /tab >}}

{{< tab tabNum="2" >}}

```java

aaa

``` 

{{< /tab >}}

{{< tab tabNum="3" >}}

```cpp

aaa

```

{{< /tab >}}

{{< /tabs >}}