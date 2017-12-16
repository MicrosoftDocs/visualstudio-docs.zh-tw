---
title: "Visual Studio 資料庫相容性 |Microsoft 文件"
ms.custom: 
ms.date: 09/06/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 2b3a551f19e3410b5f56ebe994676666cdc3d4e1
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2017
---
# <a name="compatible-database-systems-for-visual-studio"></a>適用於 Visual Studio 相容的資料庫系統

若要開發 Visual Studio 中的資料連接的應用程式，您通常安裝在您的本機開發電腦上的 資料庫系統，然後部署應用程式和資料庫至生產環境時，他們就可以。 Visual Studio 在您的電腦上安裝 SQL Server Express LocalDB 的一部分**資料儲存和處理**工作負載。 這個 LocalDB 執行個體可用於快速且輕鬆地開發資料連接的應用程式。

可以從.NET 應用程式存取，並會顯示在 Visual Studio 資料工具視窗的資料庫系統，它必須有 ADO.NET 資料提供者。 如果您打算使用實體資料模型中的.NET 應用程式，提供者必須特別支援 Entity Framework。 許多提供者會提供 NuGet 封裝管理員，或透過 Visual Studio Marketplace。

如果您使用 Azure 儲存體 Api，安裝的 Azure 儲存體模擬器在本機電腦上在開發期間才能避免產生費用，直到您準備好要部署到生產環境。 如需詳細資訊，請參閱[使用 Azure 儲存體模擬器進行開發和測試](https://azure.microsoft.com/en-us/documentation/articles/storage-use-emulator/)。

下列清單包含常見可用的資料庫系統的某些 Visual Studio 專案中。 清單未全部列出。 如需第三方廠商，提供可讓 Visual Studio 工具與深度整合 ADO.NET 資料提供者的清單，請參閱[ADO.NET 資料提供者](/dotnet/framework/data/adonet/data-providers)。

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server 是 Microsoft 頭號資料庫供應項目。 SQL Server 2016 提供突破性的效能、 進階的安全性，和豐富、 整合式報告和分析。 它隨附在專為使用不同的各種版本： 從高度可調整且高效能商業分析，在單一電腦上使用。 SQL Server Express 是專供轉散布與內嵌的 SQL 伺服器的全功能版本。  LocalDB 是簡化的版本的 SQL Server Express，不需要設定您的應用程式處理序中執行。 您可以下載或兩個產品[的 SQL Server Express 下載頁面](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)。 許多 SQL 範例，本節中使用 SQL Server LocalDB。 SQL Server Management Studio (SSMS) 是有更多的功能比 Visual Studio SQL Server 物件總管 中所提供的獨立資料庫管理應用程式。 您可以取得 SSMS，先前的連結。

## <a name="oracle"></a>Oracle

您可以下載的付費或免費版本的 Oracle 資料庫[Oracle 技術網路](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html)頁面。 針對 Entity Framework 和 Tableadapter 的設計階段支援，您將需要[Oracle Developer Tools for Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html)。 其他官方 Oracle 產品，包括 Oracle Instant Client，可透過 NuGet 套件管理員。  您可以下載 Oracle 範例結構描述中的指示[Oracle 線上文件](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)。

## <a name="mysql"></a>MySQL

MySQL 是廣泛使用在企業和網站的熱門的開放原始碼資料庫系統。 下載用於 MySQL 的項目，如 Visual Studio 和相關的產品的 MySQL 位於[Windows 上的 MySQL](http://www.mysql.com/why-mysql/windows/)。  第三方提供各種 Visual Studio 擴充功能和用於 MySQL 的獨立管理應用程式。 您可以瀏覽供應項目在 NuGet 套件管理員 (**工具** > **NuGet 套件管理員** > **管理方案的 NuGet 套件**).

## <a name="postgresql"></a>PostgreSQL

PostgreSQL 是免費的開放原始碼的物件關聯式資料庫系統。 若要在 Windows 上安裝它，您可以下載從[PostgreSQL 下載頁面](http://www.postgresql.org/download/windows/)。  您也可以建置 PostgreSQL 的原始程式碼。  PostgreSQL 核心系統包含 C 語言介面。 許多協力廠商提供使用.NET 應用程式從 PostgreSQL NuGet 封裝。  您可以瀏覽供應項目在 NuGet 套件管理員 (**工具** > **NuGet 套件管理員** > **管理方案的 NuGet 套件**). 可能是最受歡迎的套件係由[npgsql.org](http://www.npgsql.org)。

## <a name="sqlite"></a>SQLite

SQLite 是內嵌的 SQL 資料庫引擎執行的應用程式本身的處理序。 您可以下載從[SQLite 下載頁面](http://www.sqlite.org/download.html)。 SQLite 的許多協力廠商 NuGet 套件也會提供。 您可以瀏覽供應項目在 NuGet 套件管理員 (**工具** > **NuGet 套件管理員** > **管理方案的 NuGet 套件**).

## <a name="firebird"></a>Firebird

Firebird 是開放原始碼 SQL 資料庫系統。 您可以下載從[Firebird 下載頁面](http://firebirdsql.org/en/downloads/)。 透過 NuGet 套件管理員中使用的 ADO.NET 資料提供者。

## <a name="see-also"></a>請參閱

[存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)  
[如何判斷 SQL Server 和其元件的版本](http://support.microsoft.com/kb/321185)