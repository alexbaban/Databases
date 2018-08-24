# SQL Server

## SQL Server 2017 for Windows
- Download SQL Server 2017 for Windows   
(https://www.microsoft.com/en-ca/sql-server/sql-server-downloads)

## SQL Server tools and connectors
- Download SQL Server Management Studio (SSMS)   
(https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms)

## Enable TCP/IP protocol for MS SQL Server
- Windows 10, to open SQL Server Configuration Manager, on the Start Page, type SQLServerManager13.msc (for SQL Server 2016 (13.x)). For previous versions of SQL Server replace 13 with a smaller number. 
- Windows 7, run SQL Server Configuration Manager from "All Programs"  

(https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/scm-services-configure-server-startup-options?view=sql-server-2017)

On the "TCP/IP Properties" window, select "IP Addresses" tab, scroll down to "IPAll", enter "TCP Port" value 1433.
