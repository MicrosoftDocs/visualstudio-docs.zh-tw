---
title: 安裝資料庫系統、工具和範例 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- sample databases
- databases, samples
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 091338e411369e40f19e028cd19b6cb2e697718c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299603"
---
# <a name="installing-database-systems-tools-and-samples"></a>安裝資料庫系統、工具和範例
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 本身不包含任何非內部使用的資料庫系統。 若要在 Visual Studio 中開發資料連線的應用程式，您通常會在本機開發電腦上安裝資料庫系統，然後將應用程式和資料庫部署到實際執行環境。 若要讓資料庫系統可從 .NET 應用程式存取，並顯示在 Visual Studio data tools 視窗中，它必須有 ADO.NET 資料提供者。 如果您打算在 .NET 應用程式中使用實體資料模型，則提供者必須特別支援 Entity Framework。     許多提供者都是透過 NuGet 封裝管理員或透過 Visual Studio 資源庫提供。

 針對 SQL 開發，請確定您已 SQL Server Data Tools 安裝在 Visual Studio 中。 按一下 [ **View** ] 功能表。 如果您沒有看到 SQL Server 物件總管，請移至主控台並變更 Visual Studio。 在安裝程式中，選取 [ **Microsoft SQL Server Data Tools**]。

 如果您使用 Azure 儲存體 Api，請在開發期間于本機電腦上安裝 Azure 儲存體模擬器，以避免產生費用，直到您準備好部署至生產環境為止。 如需詳細資訊，請參閱 [使用 Azure 儲存體模擬器進行開發和測試](https://azure.microsoft.com/documentation/articles/storage-use-emulator/)。

 下列清單包含一些較熱門的資料庫系統，可用於 Visual Studio 專案。 這份清單並不完整。 如需提供 ADO.NET 資料提供者的協力廠商供應專案清單，以啟用與 Visual Studio 工具的深入整合，請參閱 [ADO.NET 資料提供者](https://msdn.microsoft.com/library/dd363565.aspx)。

### <a name="microsoft-sql-server"></a>Microsoft SQL Server
 SQL Server 是 Microsoft 旗艦版資料庫供應專案。 SQL Server 2016 提供突破性的效能、先進的安全性，以及豐富的整合式報告與分析。 它隨附于針對不同用途所設計的各種版本：從可高度擴充、高效能的商務分析，到單一電腦上使用。 SQL Server Express 是專為轉散發和內嵌量身打造的完整功能 SQL Server 版本。  LocalDB 是 SQL Server Express 的簡化版本，不需要任何設定，也不會在您的應用程式進程中執行。 您可以從 [SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)下載任一或兩項產品。 本節中的許多 SQL 範例都使用 SQL Server LocalDB。 SQL Server Management Studio (SSMS) 是獨立的資料庫管理應用程式，其功能比 Visual Studio SQL Server 物件總管中提供的還多。 您可以從先前的連結取得 SSMS。

### <a name="oracle"></a>Oracle
 您可以從 [ [Oracle 技術網路](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) ] 頁面下載 oracle 資料庫的付費或免費版本。 針對 Entity Framework 和 Tableadapter 的設計階段支援，您將需要 [Oracle Developer Tools for Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/)。 其他正式的 Oracle 產品（包括 Oracle 立即用戶端）可透過 NuGet 封裝管理員取得。  您可以遵循 [Oracle 線上檔](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)中的指示，下載 oracle 範例架構。

### <a name="mysql"></a>MySQL
 MySQL 是廣泛用於企業和網站的熱門開放原始碼資料庫系統。 適用于 MySQL 的下載、適用于 Visual Studio 的 MySQL，以及相關產品位於 [Windows 上的 mysql](https://www.mysql.com/why-mysql/windows/)。  協力廠商提供各種 Visual Studio 擴充功能和適用于 MySQL 的獨立管理應用程式。 您可以流覽 nuget 封裝管理員 (**工具**  >  **nuget 封裝管理員**  >  **管理解決方案) 的 nuget 套件**中的供應專案。

### <a name="postgresql"></a>PostgreSQL
 于 postgresql 是一個免費的開放原始碼物件關係資料庫系統。 若要將它安裝在 Windows 上，您可以從 [于 postgresql 下載頁面](http://www.postgresql.org/download/windows/)下載。  您也可以從來源程式碼建立于 postgresql。  于 postgresql 核心系統包含 C 語言介面。 許多協力廠商提供 NuGet 套件，可讓您從 .NET 應用程式使用於 postgresql。  您可以流覽 nuget 封裝管理員 (**工具**  >  **nuget 封裝管理員**  >  **管理解決方案) 的 nuget 套件**中的供應專案。 或許最受歡迎的封裝是由 [npgsql.org](http://www.npgsql.org/)所提供。

### <a name="sqlite"></a>SQLite
 SQLite 是在應用程式本身的進程中執行的內嵌 SQL database 引擎。 您可以從 [SQLite 下載頁面](http://www.sqlite.org/download.html)下載它。 您也可以使用 SQLite 的許多協力廠商 NuGet 套件。 您可以流覽 nuget 封裝管理員 (**工具**  >  **nuget 封裝管理員**  >  **管理解決方案) 的 nuget 套件**中的供應專案。

### <a name="firebird"></a>Firebird
 Firebird 是開放原始碼 SQL 資料庫系統。 您可以從 [Firebird 下載頁面](http://firebirdsql.org/en/downloads/)下載它。 ADO.NET 資料提供者可透過 NuGet 封裝管理員取得。

## <a name="see-also"></a>另請參閱
 [如何判斷 SQL Server 與其元件的版本 (Version) 與版本 (Edition)](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
