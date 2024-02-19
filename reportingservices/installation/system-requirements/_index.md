---
title: System Requirements
type: docs
weight: 10
url: /reportingservices/system-requirements/
---
## **Overview**
***BarcodeGenerator visual component*** is based on [Custom Report Items](https://docs.microsoft.com/sql/reporting-services/custom-report-items/custom-report-items) technology from Microsoft which allows to add functionality of own controls to the reports.

Visual component consists from two main parts: run-time component and the design-time component. ***Aspose.BarCode for Reporting Services*** run-time component is deployed to the server and renders barcode images from data stored in RDL-file. The design-time component requires Visual Studio with installed [SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt), [Microsoft Reporting Services Projects Extension](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio) or [Microsoft Reporting Services Projects 2022](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio2022) to allow designing barcode parameters visually.{{% alert color="primary" %}} 
[Microsoft Report Builder](https://www.microsoft.com/en-us/download/details.aspx?id=53613) does not allow to edit Custom Report Item component parameters and designed to edit reports with only basic RDL types. In this way it is unusable with Aspose.BarCode for Reporting Services visual component. However, it is usable with BarcodeGenerator Custom Code class with non-visual barcode generation.
{{% /alert %}} 
In this way, to develop and deploy reports with ***BarcodeGenerator visual component*** you need SQL Server Reporting Services (SSRS) as a Server runtime environment and Visual Studio as development environment. Visual Studio also can preview report results without SSRS server. This article tells system requirements for the Server and for the Client environments.

## **Deploying Reports on SQL Server Reporting Services**
[SQL Server Reporting Services](https://docs.microsoft.com/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports) requires runtime version of Aspose.BarCode for Reporting Services component and allows to only render developed reports.

{{% alert color="primary" %}} 
SQL Server Express Editions don't support Custom Report Items technology and accordingly to this, they don't support ***BarcodeGenerator visual component. However it supports ***BarcodeGenerator class*** with ***Custom Code***.
{{% /alert %}}

### **Deploying Reports on SQL Server 2008**
- .NET Framework 3.5 with its latest service pack.
- Microsoft SQL Server 2008 with its latest service pack.
- Microsoft SQL Server 2008 Reporting Services native with its latest service pack.
- Aspose.BarCode for Reporting Services component from ***SSRS2008*** folder.

### **Deploying Reports on SQL Server 2008R2**
- .NET Framework 3.5 with its latest service pack.
- Microsoft SQL Server 2008R2 with its latest service pack.
- Microsoft SQL Server 2008R2 Reporting Services native with its latest service pack.
- Aspose.BarCode for Reporting Services component from ***SSRS2008R2*** folder.

### **Deploying Reports on SQL Server 2012**
- .NET Framework 3.5 with its latest service pack.
- Microsoft SQL Server 2012 with its latest service pack.
- Microsoft SQL Server 2012 Reporting Services native with its latest service pack.
- Aspose.BarCode for Reporting Services component from ***SSRS2012*** folder.

### **Deploying Reports on SQL Server 2014**
- .NET Framework 3.5 with its latest service pack.
- Microsoft SQL Server 2014 with its latest service pack.
- Microsoft SQL Server 2014 Reporting Services native with its latest service pack.
- Aspose.BarCode for Reporting Services component from ***SSRS2014*** folder.

### **Deploying Reports on SQL Server 2016**
- .NET Framework 4.6 with its latest service pack.
- Microsoft SQL Server 2016 with its latest service pack.
- Microsoft SQL Server 2016 Reporting Services native with its latest service pack.
- Aspose.BarCode for Reporting Services component from ***SSRS2016*** folder.

### **Deploying Reports on SQL Server 2017**
- .NET Framework 4.6 with its latest service pack.
- Microsoft SQL Server 2017 with its latest service pack.
- Microsoft SQL Server 2017 Reporting Services with its latest service pack.
- Aspose.BarCode for Reporting Services component from ***SSRS2017*** folder.

### **Deploying Reports on SQL Server 2019**
- .NET Framework 4.8 with its latest service pack.
- Microsoft SQL Server 2019 with its latest service pack.
- Microsoft SQL Server 2019 Reporting Services with its latest service pack.
- Aspose.BarCode for Reporting Services component from ***SSRS2019*** folder.

### **Deploying Reports on SQL Server 2022**
- .NET Framework 4.8 with its latest service pack.
- Microsoft SQL Server 2022 with its latest service pack.
- Microsoft SQL Server 2022 Reporting Services with its latest service pack.
- Aspose.BarCode for Reporting Services component from ***SSRS2022*** folder.

## **Developing Reports with Visual Studio**
Visual Studio allows to develop RDL-reports, preview them locally or deploy them on SSRS server. For this it needs installed [SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt), [Microsoft Reporting Services Projects Extension](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio) or [Microsoft Reporting Services Projects 2022](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio2022).

### **Developing Reports with Visual Studio 2022**
Visual Studio 2022 supports development and deploying reports up to SQL Server 2022.
- Visual Studio 2022 Community+ Edition with last updates.
- [Microsoft Reporting Services Projects 2022](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio2022).
- Aspose.BarCode for Reporting Services component from ***VS2022SSRS16*** folder.

### **Developing Reports with Visual Studio 2019**
Visual Studio 2019 supports development and deploying reports up to SQL Server 2019.
- Visual Studio 2019 Community+ Edition with last updates.
- [Microsoft Reporting Services Projects Extension](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio).
- Aspose.BarCode for Reporting Services component from ***VS2019SSRS15*** folder.

### **Developing Reports with Visual Studio 2017**
Visual Studio 2017 supports development and deploying reports up to SQL Server 2019.
- Visual Studio 2017 Community+ Edition with last updates.
- [Microsoft Reporting Services Projects Extension](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio) or [SQL Server Data Tools for Visual Studio 2017](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).
- Aspose.BarCode for Reporting Services component from ***VS2017SSRS14*** or ***VS2017SSRS15*** folders.

### **Developing Reports with Visual Studio 2015**
Visual Studio 2015 supports development and deploying reports up to SQL Server 2017.
- Visual Studio 2015 with last updates.
- [SQL Server Data Tools for Visual Studio 2015](https://docs.microsoft.com/sql/ssdt/previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi).
- Aspose.BarCode for Reporting Services component from ***VS2015SSRS13*** or ***VS2015SSRS14*** folders.

### **Developing Reports with Visual Studio 2013**
Visual Studio 2013 supports development and deploying reports up to SQL Server 2014.
- Visual Studio 2013 with last updates.
- [SQL Server Data Tools for Visual Studio 2013](https://docs.microsoft.com/sql/ssdt/previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi).
- Aspose.BarCode for Reporting Services component from ***VS2013SSRS12*** folder.

### **Developing Reports with Visual Studio 2012**
Visual Studio 2012 supports development and deploying reports up to SQL Server 2012.
- Visual Studio 2012 with last updates.
- [SQL Server Data Tools for Visual Studio 2012](https://docs.microsoft.com/sql/ssdt/previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi).
- Aspose.BarCode for Reporting Services component from ***VS2012SSRS11*** folder.