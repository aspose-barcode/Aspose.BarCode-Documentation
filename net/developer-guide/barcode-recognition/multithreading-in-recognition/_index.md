---
title: Multi-Threading in Barcode Recognition
type: docs
description: ""
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Many Barcodes in One Image, Aspose.BarCode, Read Barcode C#"
weight: 30
url: /net/multithreading-in-recognition/
---

{{% alert color="primary" %}}[Read barcodes online](https://products.aspose.app/barcode/recognize). You can test the quality of ***Aspose.BarCode*** recognition functionality and view the results online.{{% /alert %}}
  
## Overview
For barcode recognition, ***Aspose.BarCode for .NET*** provides class [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) that relies on machine vision algorithms. Such algorithms are suitable for parallel execution, and in this way, allow speeding up the recognition process by utilizing several CPU cores simultaneously.  

To implement multi-thread barcode reading, class [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) provides a group of properties called [*ProcessorSettings*](https://apireference.aspose.com/barcode/net/aspose.barcode.common/processorsettings) that can be used to set all necessary parameters to optimize CPU core usage. Such parameters are initialized globally for all [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) objects and in most cases do not require additional settings.  
  
In ***Aspose.BarCode for .NET***, multithreading is based on the system parameter called [**ThreadPool**](https://docs.microsoft.com/dotnet/api/system.threading.threadpool); therefore, to enable efficient use of multi-threading, it is necessary to set minimal and maximal values of available cores through system methods [**SetMinThreads**](https://docs.microsoft.com/dotnet/api/system.threading.threadpool.setminthreads) and [**SetMaxThreads**](https://docs.microsoft.com/dotnet/api/system.threading.threadpool.setmaxthreads), respectively. 

## Manual Multi-Thread Recognition Settings
To define multi-thread recognition settings manually, the following parameters can be used:
-	[*UseAllCores*](https://apireference.aspose.com/barcode/net/aspose.barcode.common/processorsettings) and [*UseOnlyThisCoresCount*](https://apireference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useonlythiscorescount) are intended to indicate the maximal number of additional CPU cores allowed for use in a single reading operation while identification of the required number of threads is performed automatically for each concrete case.  
-	[*MaxAdditionalAllowedThreads*](https://apireference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/maxadditionalallowedthreads) is used to set the maximal number of threads allowed for simultaneous execution across all [*BarCodeReader*](https://apireference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) instances in case of necessity during multi-thread recognition. Usually, it is recommended to set the value that equals 2 x the value of [*UseOnlyThisCoresCount*](https://apireference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useonlythiscorescount) or 2 x overall number of CPU cores when [*UseAllCores*](https://apireference.aspose.com/barcode/net/aspose.barcode.common/processorsettings) is set to *True*.

## Single-Thread Recognition

<p align="center"><img src="many_pdf417.png" height="75%" width="75%""></p>

{{< highlight csharp>}}
Console.WriteLine("ReadMTSingleCore:");

//Set single-threaded recognition
BarCodeReader.ProcessorSettings.UseAllCores = false;
BarCodeReader.ProcessorSettings.UseOnlyThisCoresCount = 1;
BarCodeReader.ProcessorSettings.MaxAdditionalAllowedThreads = 0;

//recognize image
using (BarCodeReader read = new BarCodeReader($"{path}many_pdf417.png", DecodeType.Pdf417))
{
    Stopwatch watch = Stopwatch.StartNew();
    read.ReadBarCodes();
    watch.Stop();
    Console.WriteLine($"Barcodes read: {read.FoundCount}, Recognition time:{(int)watch.ElapsedMilliseconds} ms");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
</details>

## Using Fixed Number of Cores for Recognition


{{< highlight csharp>}}
Console.WriteLine("ReadMTRestrictedCores:");

//allowed cores
int AllowedCores = 2;

//Init ThreadPool options
int workerThreads;
int completionPortThreads;
ThreadPool.GetMaxThreads(out workerThreads, out completionPortThreads);
ThreadPool.SetMaxThreads(Math.Max(AllowedCores * 4, workerThreads), completionPortThreads);
ThreadPool.GetMinThreads(out workerThreads, out completionPortThreads);
ThreadPool.SetMinThreads(Math.Max(AllowedCores * 4, workerThreads), completionPortThreads);

//Set multi-threadeded all-cores recognition
BarCodeReader.ProcessorSettings.UseAllCores = false;
BarCodeReader.ProcessorSettings.UseOnlyThisCoresCount = AllowedCores;
BarCodeReader.ProcessorSettings.MaxAdditionalAllowedThreads = AllowedCores;

//recognize image
using (BarCodeReader read = new BarCodeReader($"{path}many_pdf417.png", DecodeType.Pdf417))
{
    Stopwatch watch = Stopwatch.StartNew();
    read.ReadBarCodes();
    watch.Stop();
    Console.WriteLine($"Barcodes read: {read.FoundCount}, Recognition time:{(int)watch.ElapsedMilliseconds} ms");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
</details>


## Automated Settings with Allocating Maximal Capacity for Recognition

{{< highlight csharp>}}
Console.WriteLine("ReadMTAllCores:");

//Init ThreadPool options
int workerThreads;
int completionPortThreads;
ThreadPool.GetMaxThreads(out workerThreads, out completionPortThreads);
ThreadPool.SetMaxThreads(Math.Max(Environment.ProcessorCount * 4, workerThreads), completionPortThreads);
ThreadPool.GetMinThreads(out workerThreads, out completionPortThreads);
ThreadPool.SetMinThreads(Math.Max(Environment.ProcessorCount * 4, workerThreads), completionPortThreads);

//Set multi-threadeded all-cores recognition
BarCodeReader.ProcessorSettings.UseAllCores = true;
BarCodeReader.ProcessorSettings.MaxAdditionalAllowedThreads = Environment.ProcessorCount * 2;

//recognize image
using (BarCodeReader read = new BarCodeReader($"{path}many_pdf417.png", DecodeType.Pdf417))
{
    Stopwatch watch = Stopwatch.StartNew();
    read.ReadBarCodes();
    watch.Stop();
    Console.WriteLine($"Barcodes read: {read.FoundCount}, Recognition time:{(int)watch.ElapsedMilliseconds} ms");
    foreach (BarCodeResult result in read.FoundBarCodes)
        Console.WriteLine($"{result.CodeTypeName}:{result.CodeText}");
}
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
</details>