---
title: Multithread Barcode Reading
type: docs
description: "This article explains how to set mulithread barcode recognition"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Multithread Barcode Reading, Barcode Recognition Multithreading, Aspose.BarCode, Read Barcode C#"
weight: 50
feedback: BARCODECOM
url: /net/multithread-barcode-reading/
---
  
## **Overview**
To perform barcode recognition, ***Aspose.BarCode for .NET*** provides class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) that relies on machine vision algorithms. Such algorithms are suitable for parallel execution, and as such, allow speeding up the recognition process by utilizing several CPU cores simultaneously.  

To perform multithread barcode reading, class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) provides a group of properties called [*ProcessorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings) that can be used to set all necessary parameters to optimize CPU core usage. Such parameters are initialized globally for all [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) objects and in most cases do not require additional tuning.  
  
In ***Aspose.BarCode for .NET***, multithreading is based on the system parameter called [**ThreadPool**](https://docs.microsoft.com/dotnet/api/system.threading.threadpool); therefore, to enable efficient use of multithreading, it is necessary to set minimal and maximal values of available cores through system methods [**SetMinThreads**](https://docs.microsoft.com/dotnet/api/system.threading.threadpool.setminthreads) and [**SetMaxThreads**](https://docs.microsoft.com/dotnet/api/system.threading.threadpool.setmaxthreads), respectively. 

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/net/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Manual Multithread Recognition Settings**
To define multithread recognition settings manually, the following parameters can be used:
-	[*UseAllCores*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useallcores) and [*UseOnlyThisCoresCount*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useonlythiscorescount) are intended to indicate the maximal number of additional CPU cores allowed for use in a single reading operation while identification of the required number of threads is performed automatically for each concrete case.  
-	[*MaxAdditionalAllowedThreads*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/maxadditionalallowedthreads) is used to set the maximal number of threads allowed for simultaneous execution across all [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) instances in case of necessity during multithread recognition. Usually, it is recommended to set the value that is twice larger than the value of [*UseOnlyThisCoresCount*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useonlythiscorescount) or twice greater than the overall number of CPU cores when [*UseAllCores*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useallcores) is set to *True*.

## **Single-Thread Recognition**
In cases when there is a reason not to use additional CPU cores and to perform single-thread barcode recognition, this can be implemented by setting corresponding parameters [*UseAllCores*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useallcores), [*UseOnlyThisCoresCount*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useonlythiscorescount), and [*MaxAdditionalAllowedThreads*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/maxadditionalallowedthreads) of class [*ProcessorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings) as demonstrated in the code sample provided below.
  
{{< highlight csharp>}}
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
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
  
ReadMTSingleCore:  
Barcodes read: 6,  
Recognition time:604 ms  
Pdf417:Aspose PDF417 Diag 02  
Pdf417:Aspose PDF417 Diag 01  
Pdf417:Aspose PDF417 02  
Pdf417:Aspose PDF417 01  
Pdf417:Aspose PDF417 03  
Pdf417:Aspose PDF417 04  
  
</details>

## **Using Fixed Number of Cores for Recognition**
To fix the number of CPU cores that can be allocated for barcode recognition, it is required to apply specific settings to multithreading parameters [*UseAllCores*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useallcores), [*UseOnlyThisCoresCount*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useonlythiscorescount), and [*MaxAdditionalAllowedThreads*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/maxadditionalallowedthreads) of class [*ProcessorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings) as explained in the code sample given below.

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

//Set multithread recognition using all available cores
BarCodeReader.ProcessorSettings.UseAllCores = false;
BarCodeReader.ProcessorSettings.UseOnlyThisCoresCount = AllowedCores;
BarCodeReader.ProcessorSettings.MaxAdditionalAllowedThreads = AllowedCores;

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
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
  
ReadMTRestrictedCores:  
Barcodes read: 6,  
Recognition time:400 ms  
Pdf417:Aspose PDF417 Diag 02  
Pdf417:Aspose PDF417 Diag 01  
Pdf417:Aspose PDF417 02  
Pdf417:Aspose PDF417 01  
Pdf417:Aspose PDF417 03  
Pdf417:Aspose PDF417 04  
  
</details>


## **Automated Settings with Allocating Maximal Capacity for Recognition**
To set automated allocation of the maximal possible number of cores for barcode recognition, the following settings need to be applied as shown in the code sample below. In this case, class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) defines the number of required cores without the need for explicit manual instructions.

{{< highlight csharp>}}
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
{{< /highlight >}}

<details>  
<summary>View the results of code execution</summary>
  
ReadMTAllCores:  
Barcodes read: 6,   
Recognition time:244 ms  
Pdf417:Aspose PDF417 Diag 02  
Pdf417:Aspose PDF417 Diag 01  
Pdf417:Aspose PDF417 02  
Pdf417:Aspose PDF417 01  
Pdf417:Aspose PDF417 03  
Pdf417:Aspose PDF417 04  
  
</details>