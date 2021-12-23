---
title: Install Package with ConfigTool
type: docs
weight: 30
url: /reportingservices/install-package-with-configtool/
---
## **Overview**
***ConfigTool*** utility is created to install proper version of ***Aspose.BarCode.ReportingServices.dll*** with configuration files setup. In main case, you need just run ***ConfigTool*** utility and select products where Aspose.BarCode for Reporting Services should be installed.

***ConfigTool*** installs Aspose.BarCode for Reporting Services package for SQL Server Reporting Services as well as for Visual Studio with SQL Server Data Tools installed.

## **Aspose.BarCode for Reporting Services package installation with ConfigTool utility**
1. ***Run ConfigTool utility.***
You need to run ***ConfigTool*** utility from ***{Package folder}\Tools\*** folder. Full path is ***{Package folder}\Tools\ConfigTool.exe***. Other way utility running from start menu ***Aspose\SSRS Configuration Tool***.

<img style="border:1px solid black;" src="configtool_from_menu.png" alt="ConfigTool from Start menu" />

2. ***Install Aspose.BarCode for Reporting Services package.***
As you can see, you need to select “Configure Aspose Barcode for Reporting Services”.

<img style="border:1px solid black;" src="installer_config_02.png" alt="ConfigTool utility Configure operation" />

On next screen you can select SQL Server Reporting Services version where Aspose.BarCode for Reporting Services library will be installed.

<img style="border:1px solid black;" src="installer_config_03.png" alt="ConfigTool utility Report Servers selection" />

And on this screen, you can select Visual Studio versions with SQL Server Data Tools installed.  The same version of Visual Studio can contain different versions of SSRS engine. As an example, Visual Studio 2017 can contain SSRS 14.x and 15.x version. Utility analyzes SSRS libraries and, in main case, selects right version of Aspose.BarCode for Reporting Services library.

<img style="border:1px solid black;" src="installer_config_04.png" alt="ConfigTool utility Visual Studio selection" />

## **Aspose.BarCode for Reporting Services package uninstalling with ConfigTool utility**
1. ***Run ConfigTool utility.***
You need to run ***ConfigTool*** utility from ***{Package folder}\Tools\ConfigTool.exe*** or from Start menu ***Aspose\SSRS Configuration Tool***.

<img style="border:1px solid black;" src="configtool_from_menu.png" alt="ConfigTool from Start menu" />

2. ***Uninstall Aspose.BarCode for Reporting Services library.***
For this operation you have to select “Remove Aspose Barcode for Reporting Services configuration”.

<img style="border:1px solid black;" src="uninstaller_config_01.png" alt="ConfigTool utility Remove operation" />

On next screen you can select SQL Server Reporting Services versions where Aspose.BarCode for Reporting Services library will be removed.

<img style="border:1px solid black;" src="uninstaller_config_02.png" alt="ConfigTool utility Report Servers remove" />

And on this screen, you can select Visual Studio versions with SQL Server Data Tools installed, where Aspose.BarCode for Reporting Services library will be removed. 

<img style="border:1px solid black;" src="uninstaller_config_03.png" alt="ConfigTool utility Visual Studio remove" />