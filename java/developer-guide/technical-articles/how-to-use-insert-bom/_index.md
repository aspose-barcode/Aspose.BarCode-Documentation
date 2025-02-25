---
title: How to use insertBom parameter in the method BarcodeGenerator.setCodeText
type: docs
weight: 150
feedback: BARCODECOM
url: /java/how-to-use-insert-bom-parameter/
---

## **Use insertBom parameter in the BarcodeGenerator.setCodeText method**

In version 25.2, the setCodeText(String codeText, Charset encoding, boolean insertBOM) method was introduced in the 
BarcodeGenerator class.  
This method allows setting the code text with a specified encoding and optionally inserting a BOM (Byte Order Mark)
at the beginning of the string.

Usage examples of method.

{{< highlight java >}}
 public class ExampleUsageInsertBom
 {

    private static final String folderPath = "PathToFolder");

    @Test
    public void test() throws IOException
    {
        Path fullPath = Paths.get(folderPath, "barcode1.png");
        BarcodeGenerator generator1 = new BarcodeGenerator(EncodeTypes.CODE_128);
        generator1.setCodeText("123ABCD", StandardCharsets.US_ASCII,true);
        generator1.save(fullPath.toString(), BarCodeImageFormat.PNG);

        BarcodeGenerator generator2 = new BarcodeGenerator(EncodeTypes.CODE_128);
        generator2.setCodeText("123ABCD", StandardCharsets.ISO_8859_1);
        generator2.save(Paths.get(folderPath, "barcode2.png").toString(), BarCodeImageFormat.PNG);

        BarcodeGenerator generator3 = new BarcodeGenerator(EncodeTypes.QR);
        generator3.setCodeText("123ABCD", StandardCharsets.UTF_8, true);
        generator3.save(Paths.get(folderPath, "barcode3.png").toString(), BarCodeImageFormat.PNG);

        BarcodeGenerator generator4 = new BarcodeGenerator(EncodeTypes.QR);
        generator4.setCodeText("123ABCD", StandardCharsets.UTF_8, false);
        generator4.save(Paths.get(folderPath, "barcode4.png").toString(), BarCodeImageFormat.PNG);
    }
 }
{{< /highlight >}}

### **Impact of `insertBOM` on Barcode Generation**
The insertBOM parameter affects the generated barcode image only in specific cases.

#### **Combinations of Barcode types and encodings where `insertBOM` affects the generated image**

| **Barcode Type**           | **Encoding**          | **Does `insertBOM` Affect?** | **Reason for Impact**                                                        |
|---------------------------|----------------------|----------------------------|------------------------------------------------------------------------------|
| **QR Code**               | UTF-8 / UTF-16 / UTF-32 | ✅ Yes                 | BOM adds extra bytes at the beginning of data, altering the encoded content. |
| **Micro QR Code**         | UTF-8 / UTF-16 / UTF-32 | ✅ Yes                 | Same as QR Code.                                                             |
| **DataMatrix**            | UTF-8 / UTF-16 / UTF-32 | ✅ Yes                 | Encoding with BOM modifies encoded data.                                     |
| **GS1 DataMatrix**        | UTF-8 / UTF-16 / UTF-32 | ✅ Yes                 | Similar to DataMatrix.                                                       |
| **PDF417**                | UTF-8 / UTF-16 / UTF-32 | ✅ Yes                 | Encoding changes affect data representation.                                 |
| **MicroPDF417**           | UTF-8 / UTF-16 / UTF-32 | ✅ Yes                 | Same as PDF417.                                                              |
| **Aztec**                 | UTF-8 / UTF-16 / UTF-32 | ✅ Yes                 | BOM adds bytes, altering encoded data.                                       |
| **MaxiCode**              | UTF-8 / UTF-16 / UTF-32 | ✅ Yes                 | Encoding changes impact the final representation.                            |
| **Code 128**              | UTF-8 / UTF-16 / UTF-32 | ✅ Yes                 | BOM affects the encoded text by adding extra bytes.                          |
| **GS1-128 (UCC/EAN-128)** | UTF-8 / UTF-16 / UTF-32 | ✅ Yes                 | Similar to Code 128.                                                         |

---

#### **Combinations of Barcode types and encodings where `insertBOM` does not affect the generated image**

| **Barcode Type**          | **Encoding**       | **Does `insertBOM` Affect?** | **Reason for No Impact**                            |
|--------------------------|-------------------|-----------------------------|-----------------------------------------------------|
| **Code 39**             | Any               | ❌ No                       | Supports only ASCII characters, BOM is ignored.     |
| **Code 93**             | Any               | ❌ No                       | Same as Code 39.                                    |
| **EAN-13 / EAN-8**      | Any               | ❌ No                       | Only numeric data, BOM does not apply.              |
| **UPC-A / UPC-E**       | Any               | ❌ No                       | Only digits, encoding does not matter.              |
| **Interleaved 2 of 5**  | Any               | ❌ No                       | Only numeric data, encoding does not affect output. |
| **MSI**                 | Any               | ❌ No                       | Only numeric data.                                  |
| **Codabar**             | Any               | ❌ No                       | Limited character set, encoding has no effect.      |
| **ITF (Interleaved 2 of 5)** | Any          | ❌ No                       | Only numbers, encoding does not change the result.  |

---

### ***Summary***

- **`insertBOM` affects** the barcode image when using **UTF-8, UTF-16, or UTF-32** encodings in barcodes that support multibyte characters (**QR Code, DataMatrix, PDF417, Aztec, MaxiCode, Code 128, etc.**).
- **`insertBOM` does not affect** the barcode if the barcode type supports **only numeric characters or a restricted character set** (**EAN-13, UPC, Code 39, Codabar, etc.**).

---


