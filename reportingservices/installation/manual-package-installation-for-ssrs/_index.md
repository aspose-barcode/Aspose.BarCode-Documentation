---
title: Manual Package Installation for SSRS
type: docs
weight: 60
url: /reportingservices/manual-package-installation-for-ssrs/
---
## **Overview**
The easiest way to install ***Aspose.BarCode for Reporting Services*** library for SQL Server Reporting Services is using ***ConfigTool*** utility. However, you can install the library manually. To do this you need to:
- Select required version of ***Aspose.BarCode.ReportingServices.dll*** from ***Bin*** folder.
- Copy it to Report Server binary folder. You need to locate it, at first.
- Add proper options to ***rsreportserver.config*** and ***rssrvpolicy.config*** configuration files.

After this you can use Aspose.BarCode for Reporting Services library with Report Server.

## **Locate dll directory**
You need proper ***Aspose.BarCode for Reporting Services*** library version which is matched with SQL Server Reporting Services version. You need to copy the library to Report Server binary folder. Following package folders contain SSRS versions:
- The **SSRS 2008** assembly is located in the ***Bin\SSRS2008*** directory.
- The **SSRS 2008 R2** assembly is located in the ***Bin\SSRS2008R2*** directory.
- The **SSRS 2012** assembly is located in the ***Bin\SSRS2012*** directory.
- The **SSRS 2014** assembly is located in the ***Bin\SSRS2014*** directory.
- The **SSRS 2016** assembly is located in the ***Bin\SSRS2016*** directory. 
- The **SSRS 2017** assembly is located in the ***Bin\SSRS2017*** directory.
- The **SSRS 2019** assembly is located in the ***Bin\SSRS2019*** directory.
- The **SSRS 2022** assembly is located in the ***Bin\SSRS2022*** directory.

## **Locate and copy dll to Report Server installation directory**
You need to copy proper Aspose.BarCode for Reporting Services library to Report Server directory. You can locate Report Server directories by following paths:
- The **SSRS 2008** binary folder is located in the ***C:\Program Files\Microsoft SQL Server\MSRS10.X\Reporting Services\ReportServer\bin*** directory.
- The **SSRS 2008R2** binary folder is located in the ***C:\Program Files\Microsoft SQL Server\MSRS10_50.X\Reporting Services\ReportServer\bin*** directory.
- The **SSRS 2012** binary folder is located in the ***C:\Program Files\Microsoft SQL Server\MSRS11.X\Reporting Services\ReportServer\bin*** directory.
- The **SSRS 2014** binary folder is located in the ***C:\Program Files\Microsoft SQL Server\MSRS12.X\Reporting Services\ReportServer\bin*** directory.
- The **SSRS 2016** binary folder is located in the ***C:\Program Files\Microsoft SQL Server\MSRS13.X\Reporting Services\ReportServer\bin*** directory.
- The **SSRS 2017**, **SSRS 2019** and **SSRS 2022** binary folder is located in the same ***C:\Program Files\Microsoft SQL Server Reporting Services\SSRS\ReportServer\bin*** directory.

## **Register Visual Component**
To use visual component, you need to register it in configuration file ***rsreportserver.config*** which is located in Report Server installation directory. You need to add the following rows:
{{< highlight xml>}}
<Configuration>
	<Extensions>
		<!-- Start config of Aspose.BarCode for Reporting Services-->
		<ReportItems>
			<ReportItem Name="BarcodeGenerator" Type="Aspose.BarCode.ReportingServices.BarCodeReportItem, Aspose.BarCode.ReportingServices"/>
		</ReportItems>
		<!-- End of config -->
	</Extensions>
</Configuration>
{{< /highlight >}}

## **Add Permission to Execute**
To use visual component, you need to add execution permission. You can do this by editing ***rssrvpolicy.config*** file in Report Server installation directory. You need to add following lines to the file:
{{< highlight xml>}}
<configuration>
	<mscorlib>
		<security>
			<policy>
				<PolicyLevel version="1">
					<CodeGroup class="FirstMatchCodeGroup" version="1" PermissionSetName="Nothing">
						<CodeGroup class="FirstMatchCodeGroup" version="1" PermissionSetName="Execution" Description="This code group grants MyComputer code Execution permission. ">
							<!-- Start config of Aspose.BarCode for Reporting Services-->
							<CodeGroup class="UnionCodeGroup" version="1" PermissionSetName="FullTrust" Name="BarcodeGenerator" Description="Aspose.BarCode for Reporting Services">
								<IMembershipCondition class="StrongNameMembershipCondition" version="1" PublicKeyBlob="00240000048000009400000006020000002400005253413100040000010001005542E99CECD28842DAD186257B2C7B6AE9B5947E51E0B17B4AC6D8CECD3E01C4D20658C5E4EA1B9A6C8F854B2D796C4FDE740DAC65E834167758CFF283EED1BE5C9A812022B015A902E0B97D4E95569EB8C0971834744E633D9CB4C4A6D8EDA03C12F486E13A1A0CB1AA101AD94943236384CBBF5C679944B994DE9546E493BF"/>
							</CodeGroup>
							<!-- End of config -->
						</CodeGroup>
					</CodeGroup>
				</PolicyLevel>
			</policy>
		</security>
	</mscorlib>
</configuration>
{{< /highlight >}}