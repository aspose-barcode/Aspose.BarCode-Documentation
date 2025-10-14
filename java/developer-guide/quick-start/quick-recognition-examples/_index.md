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

## 1) Read Code 128 (single type)

```java
@Test
public void read_Code128_singleType() throws Exception {
    String img = Paths.get(folder, "code128.png").toString();
    BarCodeReader reader = new BarCodeReader(img, DecodeType.CODE_128);
    try {
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length > 0, "Nothing recognized in code128.png");
    } finally {
        reader.close();
    }
}
```

## 2) Read QR Code (single type)

```java
@Test
public void read_QR_singleType() throws Exception {
    String img = Paths.get(folder, "qrcode.png").toString();
    BarCodeReader reader = new BarCodeReader(img, DecodeType.QR);
    try {
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length > 0, "Nothing recognized in qrcode.png");
    } finally {
        reader.close();
    }
}
```

## 3) Read Data Matrix (single type)

```java
@Test
public void read_DataMatrix_singleType() throws Exception {
    String img = Paths.get(folder, "datamatrix.png").toString();
    BarCodeReader reader = new BarCodeReader(img, DecodeType.DATA_MATRIX);
    try {
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length > 0, "Nothing recognized in datamatrix.png");
    } finally {
        reader.close();
    }
}
```

## 4) Read PDF417 (single type)

```java
@Test
public void read_PDF417_singleType() throws Exception {
    String img = Paths.get(folder, "pdf417.png").toString();
    BarCodeReader reader = new BarCodeReader(img, DecodeType.PDF_417);
    try {
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length > 0, "Nothing recognized in pdf417.png");
    } finally {
        reader.close();
    }
}
```

## 5) Read GS1-128 (single type)

```java
@Test
public void read_GS1_128_singleType() throws Exception {
    String img = Paths.get(folder, "gs1_128.png").toString();
    BarCodeReader reader = new BarCodeReader(img, DecodeType.GS1_CODE_128);
    try {
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length > 0, "Nothing recognized in gs1_128.png");
        // If you need to assert AI parentheses format, check text pattern:
        // Assert.assertTrue(results[0].getCodeText().contains("(01)"));
    } finally {
        reader.close();
    }
}
```

## 6) Auto-detect (all supported types)

```java
@Test
public void read_AutoDetect_AllSupported() throws Exception {
    String img = Paths.get(folder, "mixed.png").toString(); // image may contain any supported symbology
    BarCodeReader reader = new BarCodeReader(img, DecodeType.ALL_SUPPORTED_TYPES);
    try {
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length > 0, "Nothing recognized in mixed.png");
        // for (BarCodeResult r : results) {
        //     System.out.println(r.getCodeTypeName() + " -> " + r.getCodeText());
        // }
    } finally {
        reader.close();
    }
}
```

## 7) Quality presets (performance vs quality)

```java
@Test
public void read_HighPerformance() throws Exception {
    String img = Paths.get(folder, "challenging.png").toString();
    BarCodeReader reader = new BarCodeReader(img, DecodeType.ALL_SUPPORTED_TYPES);
    try {
        reader.setQualitySettings(QualitySettings.getHighPerformance());
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length >= 0, "Call should complete (even if 0 results)");
    } finally {
        reader.close();
    }
}

@Test
public void read_HighQuality() throws Exception {
    String img = Paths.get(folder, "challenging.png").toString();
    BarCodeReader reader = new BarCodeReader(img, DecodeType.ALL_SUPPORTED_TYPES);
    try {
        reader.setQualitySettings(QualitySettings.getHighQuality());
        BarCodeResult[] results = reader.readBarCodes();
        Assert.assertTrue(results.length >= 0, "Call should complete (even if 0 results)");
    } finally {
        reader.close();
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
        BarCodeReader reader = new BarCodeReader(img, DecodeType.CODE_128);
        try {
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length > 0, "Nothing recognized in code128.png");
        } finally {
            reader.close();
        }
    }

    @Test
    public void read_QR_singleType() throws Exception {
        String img = Paths.get(folder, "qrcode.png").toString();
        BarCodeReader reader = new BarCodeReader(img, DecodeType.QR);
        try {
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length > 0, "Nothing recognized in qrcode.png");
        } finally {
            reader.close();
        }
    }

    @Test
    public void read_DataMatrix_singleType() throws Exception {
        String img = Paths.get(folder, "datamatrix.png").toString();
        BarCodeReader reader = new BarCodeReader(img, DecodeType.DATA_MATRIX);
        try {
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length > 0, "Nothing recognized in datamatrix.png");
        } finally {
            reader.close();
        }
    }

    @Test
    public void read_PDF417_singleType() throws Exception {
        String img = Paths.get(folder, "pdf417.png").toString();
        BarCodeReader reader = new BarCodeReader(img, DecodeType.PDF_417);
        try {
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length > 0, "Nothing recognized in pdf417.png");
        } finally {
            reader.close();
        }
    }

    @Test
    public void read_GS1_128_singleType() throws Exception {
        String img = Paths.get(folder, "gs1_128.png").toString();
        BarCodeReader reader = new BarCodeReader(img, DecodeType.GS1_CODE_128);
        try {
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length > 0, "Nothing recognized in gs1_128.png");
        } finally {
            reader.close();
        }
    }

    @Test
    public void read_AutoDetect_AllSupported() throws Exception {
        String img = Paths.get(folder, "mixed.png").toString();
        BarCodeReader reader = new BarCodeReader(img, DecodeType.ALL_SUPPORTED_TYPES);
        try {
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length > 0, "Nothing recognized in mixed.png");
        } finally {
            reader.close();
        }
    }

    @Test
    public void read_HighPerformance() throws Exception {
        String img = Paths.get(folder, "challenging.png").toString();
        BarCodeReader reader = new BarCodeReader(img, DecodeType.ALL_SUPPORTED_TYPES);
        try {
            reader.setQualitySettings(QualitySettings.getHighPerformance());
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length >= 0, "Call should complete (even if 0 results)");
        } finally {
            reader.close();
        }
    }

    @Test
    public void read_HighQuality() throws Exception {
        String img = Paths.get(folder, "challenging.png").toString();
        BarCodeReader reader = new BarCodeReader(img, DecodeType.ALL_SUPPORTED_TYPES);
        try {
            reader.setQualitySettings(QualitySettings.getHighQuality());
            BarCodeResult[] results = reader.readBarCodes();
            Assert.assertTrue(results.length >= 0, "Call should complete (even if 0 results)");
        } finally {
            reader.close();
        }
    }
}
```
