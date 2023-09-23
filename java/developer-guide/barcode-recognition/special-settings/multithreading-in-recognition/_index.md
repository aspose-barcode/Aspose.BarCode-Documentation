---
title: Multithread Barcode Reading
type: docs
description: "This article explains how to set mulithread barcode recognition"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Multithread Barcode Reading, Barcode Recognition Multithreading, Aspose.BarCode, Read Barcode in Java"
weight: 50
url: /java/multithread-barcode-reading/
aliases:
- /java/loading-barcode-images/
---
  
## **Overview**
***Aspose.BarCode for Java*** contains class [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) that is intended to perform barcode reading based on machine vision algorithms. This type of algorithm allows developers to implement parallel processing and thus increase recognition speed by distributing calculations across several CPU cores.  

To perform multithread barcode reading, class [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) includes a special class called [*ProcessorSettings*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/ProcessorSettings) that allows optimizing the load of available CPU cores. Multithreading settings can be managed for all [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) objects and usually do not need special tuning.  
  
<!--***Aspose.BarCode for Java*** implements multithreading based on a special system parameter called **ThreadPoolExecutor**. Minimum and maximum values of cores that can be used for multithreading can be specified using **setCorePoolSize()** and **setMaximumPoolSize()** system methods.--> 

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/java/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Manual Multithread Settings**
To manage multithread barcode reading manually, developers can use the following methods:
-	*setUseAllCores* and *setUseOnlyThisCoresCount* methods allow setting the maximum number of CPU cores available to complete one reading operation. The number of required threads is defined automatically.  
-	*setMaxAdditionalAllowedThreads* sets the maximum number of threads available for parallel processing of all active [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) instances. The recommended value of this parameter is twice than the value of *setUseOnlyThisCoresCount* or the overall number of CPU cores when *setUseAllCores.TRUE* is enabled.

## **Single-Thread Recognition**
If only single-thread barcode reading is available and the use of additional CPU cores should be blocked, developers can implement corresponding settings using *setUseAllCores*, *UseOnlyThisCoresCount*, and *setMaxAdditionalAllowedThreads* of class [*ProcessorSettings*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/ProcessorSettings)<!--, as shown in the code snippet below-->.
  
<!--{{< highlight csharp>}}
Console.WriteLine("ReadMTSingleCore:");

//Set single-thread recognition
BarCodeReader.ProcessorSettings.UseAllCores = false;
BarCodeReader.ProcessorSettings.UseOnlyThisCoresCount = 1;
BarCodeReader.ProcessorSettings.MaxAdditionalAllowedThreads = 0;

//read barcode image
using (BarCodeReader read = new BarCodeReader($"{path}many_pdf417.png", DecodeType.Pdf417))
{
    Stopwatch watch = Stopwatch.StartNew();
    read.ReadBarCodes();
    watch.Stop();
    Console.WriteLine($"Barcodes read: {read.FoundCount}, Recognition time:{(int)watch.ElapsedMilliseconds} ms");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->

## **Use Fixed Number of Cores**
To fix the number of CPU cores available for barcode reading processes, developers can apply corresponding settings through *setUseAllCores*, *setUseOnlyThisCoresCount*, and *setMaxAdditionalAllowedThreads* methods of class [*ProcessorSettings*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/ProcessorSettings)<!--, as shown in the code sample below-->. 
<!--This code sample demonstrates how to enable maximum multithread performance.

{{< highlight Java>}}
 
 //this allows to use all cores for single BarCodeReader call
 BarCodeReader.getProcessorSettings().setUseAllCores(true);
 //this allows to use the current count of cores
 BarCodeReader.getProcessorSettings().setUseAllCores(false);
 BarCodeReader.getProcessorSettings().setUseOnlyThisCoresCount(Math.max(1, Environment.getProcessorCount() / 2));
{{< /highlight >}}-->

## **Automated Maximal Capacity Settings**
To enable automated allocation of the maximally possible multithreading, corresponding settings can be applied<!--, as explained in the code sample below-->. Class [*BarCodeReader*](https://reference.aspose.com/barcode/java/com.aspose.barcode.barcoderecognition/BarCodeReader) determines the number of cores automatically.

<!--{{< highlight csharp>}}
Console.WriteLine("ReadMTAllCores:");

//Init ThreadPool options
int workerThreads;
int completionPortThreads;
ThreadPool.GetMaxThreads(out workerThreads, out completionPortThreads);
ThreadPool.SetMaxThreads(Math.Max(Environment.ProcessorCount * 4, workerThreads), completionPortThreads);
ThreadPool.GetMinThreads(out workerThreads, out completionPortThreads);
ThreadPool.SetMinThreads(Math.Max(Environment.ProcessorCount * 4, workerThreads), completionPortThreads);

//Set multithread recognition using all available cores
BarCodeReader.ProcessorSettings.UseAllCores = true;
BarCodeReader.ProcessorSettings.MaxAdditionalAllowedThreads = Environment.ProcessorCount * 2;

//Read barcode image
using (BarCodeReader read = new BarCodeReader($"{path}many_pdf417.png", DecodeType.Pdf417))
{
    Stopwatch watch = Stopwatch.StartNew();
    read.ReadBarCodes();
    watch.Stop();
    Console.WriteLine($"Barcodes read: {read.FoundCount}, Recognition time:{(int)watch.ElapsedMilliseconds} ms");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}-->
