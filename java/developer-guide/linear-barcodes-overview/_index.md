---
title: Linear Barcodes Overview
type: docs
ai_search_scope: "barcode_java_doc"
ai_search_endpoint: "https://docsearch.api.aspose.cloud/ask"
weight: 10
url: /java/developer-guide/linear-barcodes-overview
---

## **Overview**

**Linear barcodes (1D barcodes)** encode data into a sequence of vertical bars and spaces of varying width. A scanner
reads these bars horizontally, interpreting the reflected light pattern as encoded characters. This makes linear
symbologies the most common and recognizable barcode type, widely used across retail, logistics, and product labeling.

Aspose.BarCode for Java fully supports generation and recognition of popular linear standards such as:
- **EAN/UPC family**: EAN-8, EAN-13, UPC-A, UPC-E, ISBN, ISSN
- **Code family**: Code 39 (standard & extended), Code 93, Code 128 (A/B/C), GS1-128
- **Interleaved formats**: Interleaved 2 of 5, ITF-14, Matrix 2 of 5
- **Postal 1D**: Postnet, Planet, Intelligent Mail (IMb), Pharmacode, MSI, Standard2of5

---

### **How They Work**
- **Data Encoding**: The widths of bars and spaces correspond to digits or letters.
- **Reading Mechanism**: A laser or CCD scanner shines light onto the barcode and converts the reflected pattern into
  data.
- **Limited Capacity**: Because information is stored in one direction only, linear barcodes expand horizontally as more
  characters are added, and they can hold less data than 2D codes.

### **Common Applications**
- **Retail**: Product identification and price lookup at checkout (UPC, EAN).
- **Shipping & Logistics**: Package tracking and warehouse inventory (Code 128, ITF-14).
- **Product Identification**: Encoding GTINs and similar identifiers.

### **Key Characteristics**
- One-dimensional (data arranged in a single row).
- Distinctive vertical bars and spaces.
- Encodes alphanumeric data, often short identifiers.

### **Examples**
- **UPC (Universal Product Code)** – ubiquitous in retail.
- **EAN (European Article Number)** – global standard for products.
- **Code 128** – versatile, full ASCII support, common in logistics.