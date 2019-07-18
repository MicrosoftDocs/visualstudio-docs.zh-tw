---
title: 安裝資料庫系統、 工具和範例 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 63d9dd0844cb3e7422f8d78a0ee2e3cb4e0b1fab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196064"
---
# <a name="installing-database-systems-tools-and-samples"></a>安裝資料庫系統、工具和範例
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 本身不包含任何資料庫系統，除了它會在內部使用。 若要開發 Visual Studio 中連接資料的應用程式，您通常安裝在您的本機開發電腦上的 資料庫系統，然後部署應用程式和資料庫到生產環境時，他們就可以。 可從.NET 應用程式，並會顯示在 Visual Studio 資料工具視窗的資料庫系統，它必須能夠為 ADO.NET 資料提供者。 如果您打算在.NET 應用程式中使用實體資料模型，提供者必須特別支援 Entity Framework。     許多提供者會提供透過 NuGet 套件管理員，或透過 Visual Studio 組件庫。  
  
 適用於 SQL 開發，請確定您有 Visual Studio 中安裝的 SQL Server Data Tools。 按一下 **檢視**功能表。 如果看不到 SQL Server 物件總管 中，移至 控制台 並變更 Visual Studio。 在 安裝程式中，選取**Microsoft SQL Server Data Tools**。  
  
 如果您使用 Azure 儲存體 Api，安裝 Azure 儲存體模擬器在本機電腦上在開發期間以避免產生費用，直到您準備好要部署到生產環境。 如需詳細資訊，請參閱 <<c0> [ 使用 Azure 儲存體模擬器進行開發和測試](https://azure.microsoft.com/documentation/articles/storage-use-emulator/)。  
  
 下列清單會包含一些較受歡迎的資料庫系統，可以使用 Visual Studio 專案中。 清單不完整。 如需提供 ADO.NET 資料提供者可讓 Visual Studio 工具與深入整合的協力廠商提供的清單，請參閱 < [ADO.NET 資料提供者](https://msdn.microsoft.com/library/dd363565.aspx)。  
  
### <a name="microsoft-sql-server"></a>Microsoft SQL Server  
 SQL Server 是 Microsoft 旗艦資料庫供應項目。 SQL Server 2016 提供突破性的效能、 進階的安全性和豐富的整合式報告和分析。 針對不同的用途所設計的各種版本中附隨： 從高度可擴充、 高效能的商務分析，在單一電腦上使用。 SQL Server Express 是功能完整的 SQL Server 版本，適合轉散發和內嵌。  LocalDB 是簡化的版的 SQL Server Express，不需要設定，並在您的應用程式處理程序中執行。 您可以下載從任一個或兩個產品[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)。 許多 SQL 範例，在這一節中使用 SQL Server LocalDB。 SQL Server Management Studio (SSMS) 是有更多的功能比 Visual Studio SQL Server 物件總管 中所提供的獨立資料庫管理應用程式。 您可以取得 SSMS，從先前的連結。  
  
### <a name="oracle"></a>Oracle  
 您可以下載付費或免費版本的 Oracle 資料庫[Oracle 技術網路](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html)頁面。 如需 Entity Framework 和 Tableadapter 的設計階段支援，您必須[Oracle Developer Tools for Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html)。 其他正式的 Oracle 產品，包括 Oracle Instant Client，可透過 NuGet 套件管理員。  您可以依照下列中的指示來下載 Oracle 範例結構描述[Oracle 線上文件](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)。  
  
### <a name="mysql"></a>MySQL  
 MySQL 是廣泛使用於企業和網站的受歡迎的開放原始碼資料庫系統。 下載適用於 MySQL 的項目，是在 Visual Studio 中，與相關的產品的 MySQL[在 Windows 上的 MySQL](http://www.mysql.com/why-mysql/windows/)。  第三方提供各種 Visual Studio 擴充功能和適用於 MySQL 的獨立管理應用程式。 您可以瀏覽供應項目在 NuGet 套件管理員 (**工具** > **NuGet 套件管理員** > **管理解決方案的 NuGet 套件**).  
  
### <a name="postgresql"></a>PostgreSQL  
 PostgreSQL 是免費的開放原始碼物件關聯式資料庫系統。 若要將它安裝在 Windows 中，您可以下載從[PostgreSQL 下載頁面](http://www.postgresql.org/download/windows/)。  您也可以從原始程式碼建置 PostgreSQL。  PostgreSQL 核心系統包含 C 語言介面。 許多協力廠商提供的 NuGet 套件從.NET 應用程式中使用 PostgreSQL。  您可以瀏覽供應項目在 NuGet 套件管理員 (**工具** > **NuGet 套件管理員** > **管理解決方案的 NuGet 套件**). 最受歡迎的套件所提供的或許[npgsql.org](http://www.npgsql.org)。  
  
### <a name="sqlite"></a>SQLite  
 SQLite 是內嵌的 SQL 資料庫引擎，應用程式本身的處理序中執行。 您可以下載從[SQLite 下載頁面](http://www.sqlite.org/download.html)。 Sqlite 的許多協力廠商 NuGet 套件也會提供。 您可以瀏覽供應項目在 NuGet 套件管理員 (**工具** > **NuGet 套件管理員** > **管理解決方案的 NuGet 套件**).  
  
### <a name="firebird"></a>Firebird  
 Firebird 是開放原始碼 SQL 資料庫系統。 您可以下載從[Firebird 下載頁面](http://firebirdsql.org/en/downloads/)。 ADO.NET 資料提供者可透過 NuGet 套件管理員。  
  
## <a name="see-also"></a>另請參閱  
 [如何判斷 SQL Server 及其元件的版本](http://support.microsoft.com/kb/321185)
