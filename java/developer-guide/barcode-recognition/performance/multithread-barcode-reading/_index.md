---
title: Multithread Barcode Reading
description: "How to scale recognition throughput by running independent BarCodeReader instances in parallel."
type: docs
weight: 80
url: /java/developer-guide/barcode-recognition/performance/multithread-barcode-reading
---

# Multithread Barcode Reading

If you need high throughput, you can process multiple images in parallel.

## Thread Safety

**Important:** `BarCodeReader` instances are **not thread-safe**.
*   You **cannot** use the same `BarCodeReader` instance concurrently in multiple threads.
*   You **can** reuse a single instance sequentially (e.g. recognize Image A, then set Image B, then recognize Image B) in the same thread.
*   For parallel processing, you must create a separate `BarCodeReader` instance for each thread (or each task).

## Single-thread baseline (batch loop)

Reuse a single reader instance for sequential processing.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;

String[] files = {
        "barcode1.png",
        "barcode2.png",
        "barcode3.png"
};

BarCodeReader reader = new BarCodeReader();
reader.setBarCodeReadType(DecodeType.ALL_SUPPORTED_TYPES);

for (String file : files) {
    // Reuse the same reader: just switch the input
    reader.setBarCodeImage(file);

    for (BarCodeResult result : reader.readBarCodes()) {
        System.out.println(file + " -> " + result.getCodeTypeName() + ": " + result.getCodeText());
    }
}
```

## Parallel processing pattern (one reader per task)

For parallel execution, instantiate a new `BarCodeReader` inside the task or use a `ThreadLocal` reader.

```java
import com.aspose.barcode.barcoderecognition.BarCodeReader;
import com.aspose.barcode.barcoderecognition.BarCodeResult;
import com.aspose.barcode.barcoderecognition.DecodeType;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

ExecutorService pool = Executors.newFixedThreadPool(Runtime.getRuntime().availableProcessors());

List<String> files = Arrays.asList("barcode1.png", "barcode2.png", "barcode3.png");

List<Future<List<String>>> futures = new ArrayList<>();
for (String file : files) {
    futures.add(pool.submit(() -> {
        // Create a dedicated reader for this task
        BarCodeReader reader = new BarCodeReader(file, DecodeType.ALL_SUPPORTED_TYPES);
        List<String> out = new ArrayList<>();
        for (BarCodeResult r : reader.readBarCodes()) {
            out.add(r.getCodeTypeName() + ": " + r.getCodeText());
        }
        return out;
    }));
}

for (int i = 0; i < files.size(); i++) {
    try {
        List<String> results = futures.get(i).get();
        for (String line : results) {
            System.out.println(files.get(i) + " -> " + line);
        }
    } catch (Exception e) {
        e.printStackTrace();
    }
}

pool.shutdown();
```
