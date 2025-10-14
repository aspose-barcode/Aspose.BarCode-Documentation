---
title: Quick Recognition Examples
type: docs
weight: 20
url: /java/developer-guide/quick-start/quick-recognition-examples/
---

# Quick Recognition Examples (Java)

This page shows **concise, runnable TestNG tests** for barcode recognition using Aspose.BarCode for Java.
Each snippet below is a test method — copy them into your test class or use the complete class at the end.

> **Test data location**
> The examples assume images are placed under a resource folder resolved by your helper, e.g.  
> `ExampleAssist.getResourceFolderPath("quick_start/recognition")` and file names like `code128.png`, `qrcode.png`, etc.

---

## Imports and Test Class Skeleton

```java
import com.aspose.barcode.barcoderecognition.*;
import com.aspose.barcode.guide.common.ExampleAssist;
import com.aspose.barcode.guide.common.LicenseAssist;
import org.testng.Assert;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.Test;

import java.nio.file.Path;
import java.nio.file.Paths;

public class QuickRecognitionExamplesTest {

    private static final String folder = ExampleAssist.getResourceFolderPath("quick_start/recognition");

    @BeforeClass
    public void setUp() {
        LicenseAssist.setupLicense();
    }

    // Place test methods here...
}
```

---

## 1) Read Code 128 (single type)

```java
@Test
public void read_Code128_singleType() throws Exception {
    String img = Paths.get(folder, "code128.png").toString();
    try (BarCodeReader reader = new BarCodeReader(img, DecodeType.CODE_128)) {
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length > 0, "Nothing recognized in code128.png");
        // Optional sanity checks
        // Assert.assertEquals(results[0].getCodeTypeName(), "Code128");
        // System.out.println(results[0].getCodeText());
    }
}
```

## 2) Read QR Code (single type)

```java
@Test
public void read_QR_singleType() throws Exception {
    String img = Paths.get(folder, "qrcode.png").toString();
    try (BarCodeReader reader = new BarCodeReader(img, DecodeType.QR)) {
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length > 0, "Nothing recognized in qrcode.png");
    }
}
```

## 3) Read Data Matrix (single type)

```java
@Test
public void read_DataMatrix_singleType() throws Exception {
    String img = Paths.get(folder, "datamatrix.png").toString();
    try (BarCodeReader reader = new BarCodeReader(img, DecodeType.DATA_MATRIX)) {
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length > 0, "Nothing recognized in datamatrix.png");
    }
}
```

## 4) Read PDF417 (single type)

```java
@Test
public void read_PDF417_singleType() throws Exception {
    String img = Paths.get(folder, "pdf417.png").toString();
    try (BarCodeReader reader = new BarCodeReader(img, DecodeType.PDF_417)) {
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length > 0, "Nothing recognized in pdf417.png");
    }
}
```

## 5) Read GS1-128 (single type)

```java
@Test
public void read_GS1_128_singleType() throws Exception {
    String img = Paths.get(folder, "gs1_128.png").toString();
    try (BarCodeReader reader = new BarCodeReader(img, DecodeType.GS1_CODE_128)) {
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length > 0, "Nothing recognized in gs1_128.png");
        // If you need to assert parentheses AI format, check the text pattern:
        // Assert.assertTrue(results[0].getCodeText().contains("(01)"));
    }
}
```

## 6) Auto-detect (all supported types)

```java
@Test
public void read_AutoDetect_AllSupported() throws Exception {
    String img = Paths.get(folder, "mixed.png").toString(); // image may contain any supported symbology
    try (BarCodeReader reader = new BarCodeReader(img, DecodeType.ALL_SUPPORTED_TYPES)) {
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length > 0, "Nothing recognized in mixed.png");
        // for (BarCodeResult r : results) {
        //     System.out.println(r.getCodeTypeName() + " -> " + r.getCodeText());
        // }
    }
}
```

## 7) Quality presets (performance vs quality)

```java
@Test
public void read_HighPerformance() throws Exception {
    String img = Paths.get(folder, "challenging.png").toString();
    try (BarCodeReader reader = new BarCodeReader(img, DecodeType.ALL_SUPPORTED_TYPES)) {
        reader.setQualitySettings(QualitySettings.getHighPerformance());
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length >= 0, "Call should complete (even if 0 results)");
    }
}

@Test
public void read_HighQuality() throws Exception {
    String img = Paths.get(folder, "challenging.png").toString();
    try (BarCodeReader reader = new BarCodeReader(img, DecodeType.ALL_SUPPORTED_TYPES)) {
        reader.setQualitySettings(QualitySettings.getHighQuality());
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length >= 0, "Call should complete (even if 0 results)");
    }
}
```

---

## Complete Test Class

```java
import com.aspose.barcode.barcoderecognition.*;
import com.aspose.barcode.guide.common.ExampleAssist;
import com.aspose.barcode.guide.common.LicenseAssist;
import org.testng.Assert;
import org.testng.annotations.BeforeClass;
import org.testng.annotations.Test;

import java.nio.file.Paths;

public class QuickRecognitionExamplesTest {

    private static final String folder = ExampleAssist.getResourceFolderPath("quick_start/recognition");

    @BeforeClass
    public void setUp() {
        LicenseAssist.setupLicense();
    }

    @Test
    public void read_Code128_singleType() throws Exception {
        String img = Paths.get(folder, "code128.png").toString();
        try (BarCodeReader reader = new BarCodeReader(img, DecodeType.CODE_128)) {
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length > 0, "Nothing recognized in code128.png");
        }
    }

    @Test
    public void read_QR_singleType() throws Exception {
        String img = Paths.get(folder, "qrcode.png").toString();
        try (BarCodeReader reader = new BarCodeReader(img, DecodeType.QR)) {
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length > 0, "Nothing recognized in qrcode.png");
        }
    }

    @Test
    public void read_DataMatrix_singleType() throws Exception {
        String img = Paths.get(folder, "datamatrix.png").toString();
        try (BarCodeReader reader = new BarCodeReader(img, DecodeType.DATA_MATRIX)) {
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length > 0, "Nothing recognized in datamatrix.png");
        }
    }

    @Test
    public void read_PDF417_singleType() throws Exception {
        String img = Paths.get(folder, "pdf417.png").toString();
        try (BarCodeReader reader = new BarCodeReader(img, DecodeType.PDF_417)) {
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length > 0, "Nothing recognized in pdf417.png");
        }
    }

    @Test
    public void read_GS1_128_singleType() throws Exception {
        String img = Paths.get(folder, "gs1_128.png").toString();
        try (BarCodeReader reader = new BarCodeReader(img, DecodeType.GS1_CODE_128)) {
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length > 0, "Nothing recognized in gs1_128.png");
        }
    }

    @Test
    public void read_AutoDetect_AllSupported() throws Exception {
        String img = Paths.get(folder, "mixed.png").toString();
        try (BarCodeReader reader = new BarCodeReader(img, DecodeType.ALL_SUPPORTED_TYPES)) {
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length > 0, "Nothing recognized in mixed.png");
        }
    }

    @Test
    public void read_HighPerformance() throws Exception {
        String img = Paths.get(folder, "challenging.png").toString();
        try (BarCodeReader reader = new BarCodeReader(img, DecodeType.ALL_SUPPORTED_TYPES)) {
            reader.setQualitySettings(QualitySettings.getHighPerformance());
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length >= 0, "Call should complete (even if 0 results)");
        }
    }

    @Test
    public void read_HighQuality() throws Exception {
        String img = Paths.get(folder, "challenging.png").toString();
        try (BarCodeReader reader = new BarCodeReader(img, DecodeType.ALL_SUPPORTED_TYPES)) {
            reader.setQualitySettings(QualitySettings.getHighQuality());
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length >= 0, "Call should complete (even if 0 results)");
        }
    }
}
```
