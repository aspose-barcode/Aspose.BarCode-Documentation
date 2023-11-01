---
title: Multithread Barcode Reading
type: docs
description: "This article explains how to set mulithread barcode recognition"
keywords: "Read Barcode, Read Barcode from Stream, Scan Barcode from Image, Multithread Barcode Reading, Barcode Recognition Multithreading, Aspose.BarCode, Read Barcode C++"
weight: 50
feedback: BARCODECOM
url: /cpp/multithread-barcode-reading/
---
  
## **Overview**
To perform barcode recognition, ***Aspose.BarCode for C++*** provides class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) that relies on machine vision algorithms. Such algorithms are suitable for parallel execution, and as such, allow speeding up the recognition process by utilizing several CPU cores simultaneously.  

To perform multithread barcode reading, class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) provides a group of properties called [*ProcessorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings) that can be used to set all necessary parameters to optimize CPU core usage. Such parameters are initialized globally for all [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) objects and in most cases do not require additional tuning.  
  
In ***Aspose.BarCode for C++***, multithreading is based on the system parameter called [**ThreadPool**](https://docs.microsoft.com/dotnet/api/system.threading.threadpool); therefore, to enable efficient use of multithreading, it is necessary to set minimal and maximal values of available cores through system methods [**SetMinThreads**](https://docs.microsoft.com/dotnet/api/system.threading.threadpool.setminthreads) and [**SetMaxThreads**](https://docs.microsoft.com/dotnet/api/system.threading.threadpool.setmaxthreads), respectively. 

{{% alert color="primary" %}}*If you need any clarifications, feel free to reach out to [Aspose Technical Support](/barcode/cpp/technical-support/): ask your questions at [Aspose.Barcode Forum](https://forum.aspose.com/c/barcode/13) or contact [Aspose Paid Support Helpdesk](https://helpdesk.aspose.com/).*{{% /alert %}}

## **Manual Multithread Recognition Settings**
To define multithread recognition settings manually, the following parameters can be used:
-	[*UseAllCores*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useallcores) and [*UseOnlyThisCoresCount*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useonlythiscorescount) are intended to indicate the maximal number of additional CPU cores allowed for use in a single reading operation while identification of the required number of threads is performed automatically for each concrete case.  
-	[*MaxAdditionalAllowedThreads*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/maxadditionalallowedthreads) is used to set the maximal number of threads allowed for simultaneous execution across all [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) instances in case of necessity during multithread recognition. Usually, it is recommended to set the value that is twice larger than the value of [*UseOnlyThisCoresCount*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useonlythiscorescount) or twice greater than the overall number of CPU cores when [*UseAllCores*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useallcores) is set to *True*.

## **Single-Thread Recognition**
In cases when there is a reason not to use additional CPU cores and to perform single-thread barcode recognition, this can be implemented by setting corresponding parameters [*UseAllCores*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useallcores), [*UseOnlyThisCoresCount*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useonlythiscorescount), and [*MaxAdditionalAllowedThreads*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/maxadditionalallowedthreads) of class [*ProcessorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings).
  

## **Using Fixed Number of Cores for Recognition**
To fix the number of CPU cores that can be allocated for barcode recognition, it is required to apply specific settings to multithreading parameters [*UseAllCores*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useallcores), [*UseOnlyThisCoresCount*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/useonlythiscorescount), and [*MaxAdditionalAllowedThreads*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings/properties/maxadditionalallowedthreads) of class [*ProcessorSettings*](https://reference.aspose.com/barcode/net/aspose.barcode.common/processorsettings).


## **Automated Settings with Allocating Maximal Capacity for Recognition**
To set automated allocation of the maximal possible number of cores for barcode recognition, the following settings need to be applied. In this case, class [*BarCodeReader*](https://reference.aspose.com/barcode/net/aspose.barcode.barcoderecognition/barcodereader) defines the number of required cores without the need for explicit manual instructions.

