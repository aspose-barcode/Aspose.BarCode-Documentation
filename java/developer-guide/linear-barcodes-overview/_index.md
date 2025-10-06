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

---

### **How They Work**
- **Data Encoding**: The varying widths of bars and spaces represent different symbols. Standardized encoding schemes
  (such as Code 128, EAN-13, or UPC-A) define how each character is represented.
- **Reading Mechanism**: A laser or CCD scanner shines light onto the barcode and converts the reflected pattern into
  the encoded data.
- **Limited Capacity**: Linear barcodes store data only in one direction (horizontally). As more characters are added,
  the symbol grows in length. They hold significantly less data than 2D barcodes.

---

### **Supported Standards**
Aspose.BarCode for Java supports both **generation** and **recognition** of all major 1D symbologies, including:
- **EAN/UPC family**: EAN-8, EAN-13, UPC-A, UPC-E, ISBN, ISSN
- **Code family**: Code 39 (standard & extended), Code 93, Code 128 (A/B/C), GS1-128
- **Interleaved formats**: Interleaved 2 of 5, ITF-14, Matrix 2 of 5
- **Postal 1D**: Postnet, Planet, Intelligent Mail (IMb), Pharmacode, MSI, Standard2of5

---

### **Common Applications**
- **Retail**: Product identification and price lookup at checkout (UPC, EAN).
- **Shipping & Logistics**: Package tracking and warehouse inventory (Code 128, ITF-14).
- **Product Identification**: Encoding GTINs and similar identifiers.
- **Limitations**: Linear barcodes are constrained by their one-dimensional nature, which limits their data capacity
  compared to 2D codes.

---

### **Key Characteristics**
- One-dimensional: data is arranged in a single row.
- Vertical bars and spaces are the core visual element.
- Encodes alphanumeric data, typically short identifiers.
- Easy to scan and recognize even if partially damaged (scratches, dirt), which makes them highly reliable.

---

### **Examples**
- **UPC (Universal Product Code)** – ubiquitous in retail.
- **EAN (European Article Number)** – global standard for products.
- **Code 128** – versatile, full ASCII support, common in logistics.
- **ITF-14** – used for packaging and shipping containers.