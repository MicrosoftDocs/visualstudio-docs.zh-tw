---
title: 資料庫相容性
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 94ce946f7c14706b57618f3d9aeb90cc207fcf04
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648297"
---
# <a name="compatible-database-systems-for-visual-studio"></a>適用於 Visual Studio 相容的資料庫系統

若要在 Visual Studio 中開發資料連線的應用程式，您通常會在本機開發電腦上安裝資料庫系統，然後將應用程式和資料庫部署到準備就緒的生產環境。 Visual Studio 會在您的電腦上安裝 SQL Server Express LocalDB，做為**資料儲存和處理**工作負載的一部分。 這個 LocalDB 實例非常適合用來快速且輕鬆地開發資料連線的應用程式。

若要讓資料庫系統可從 .NET 應用程式存取，並在 Visual Studio data tools 視窗中顯示，它必須有 ADO.NET 的資料提供者。 如果您打算在 .NET 應用程式中使用實體資料模型，提供者必須特別支援 Entity Framework。 許多提供者都是透過 NuGet 套件管理員或 Visual Studio Marketplace 提供。

如果您使用 Azure 儲存體 Api，請在開發期間于本機電腦上安裝 Azure 儲存體模擬器，以避免產生費用，直到您準備好部署至生產環境為止。 如需詳細資訊，請參閱[使用 Azure 儲存體模擬器進行開發和測試](/azure/storage/common/storage-use-emulator)。

下列清單包含一些可在 Visual Studio 專案中使用的較熱門資料庫系統。 此清單並不完整。 如需提供 ADO.NET 資料提供者的協力廠商廠商清單，使其能夠與 Visual Studio 工具進行深入整合，請參閱[ADO.NET 資料提供者](/dotnet/framework/data/adonet/data-providers)。

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server 是 Microsoft 旗艦版資料庫供應專案。 SQL Server 2016 提供突破性的效能、先進的安全性，以及豐富的整合式報告和分析。 它隨附于針對不同用途而設計的各種版本：從可高度擴充、高效能的商務分析，到單一電腦上使用。 SQL Server Express 是針對轉散發和內嵌量身打造的完整功能版 SQL Server。  LocalDB 是簡化版的 SQL Server Express，不需要任何設定，而且會在應用程式的進程中執行。 您可以從[SQL Server Express 下載 頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)下載一或兩個產品。 本節中的許多 SQL 範例都使用 SQL Server LocalDB。 SQL Server Management Studio （SSMS）是獨立的資料庫管理應用程式，其功能比在 Visual Studio SQL Server 物件總管中提供的還多。 您可以從上一個連結取得 SSMS。

## <a name="oracle"></a>Oracle

您可以從 [ [oracle 技術網路](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html)] 頁面下載 oracle 資料庫的付費或免費版本。 如需 Entity Framework 和 Tableadapter 的設計階段支援，您將需要[Oracle Developer tools for Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html)。 其他官方 Oracle 產品，包括 Oracle 立即用戶端，則可透過 NuGet 套件管理員取得。 您可以遵循[oracle 線上檔](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)中的指示，下載 oracle 範例架構。

## <a name="mysql"></a>MySQL

MySQL 是受歡迎的開放原始碼資料庫系統，廣泛用於企業和網站。 適用于 MySQL 的下載、適用于 Visual Studio 的 MySQL，以及相關產品位於[Windows 上的 mysql](http://www.mysql.com/why-mysql/windows/)。 協力廠商提供適用于 MySQL 的各種 Visual Studio 延伸模組和獨立管理應用程式。 您可以在 NuGet 套件管理員中流覽供應專案（[**工具**]  > **nuget 套件管理員** > **管理解決方案的 nuget 套件**）。

## <a name="postgresql"></a>PostgreSQL

于 postgresql 是免費的開放原始碼物件關係資料庫系統。 若要將它安裝在 Windows 上，您可以從[于 postgresql 下載頁面](http://www.postgresql.org/download/windows/)下載。 您也可以從原始程式碼建立于 postgresql。 于 postgresql core 系統包含 C 語言介面。 許多協力廠商會提供 NuGet 套件，以便從 .NET 應用程式使用於 postgresql。 您可以在 NuGet 套件管理員中流覽供應專案（[**工具**]  > **nuget 套件管理員** > **管理解決方案的 nuget 套件**）。 也許，最受歡迎的套件是由[npgsql.org](http://www.npgsql.org)所提供。

## <a name="sqlite"></a>SQLite

SQLite 是內嵌的 SQL database 引擎，會在應用程式本身的進程中執行。 您可以從[SQLite 下載頁面](http://www.sqlite.org/download.html)下載。 也有許多適用于 SQLite 的協力廠商 NuGet 套件。 您可以在 NuGet 套件管理員中流覽供應專案（[**工具**]  > **nuget 套件管理員** > **管理解決方案的 nuget 套件**）。

## <a name="firebird"></a>Firebird

Firebird 是開放原始碼的 SQL 資料庫系統。 您可以從[Firebird 下載頁面](http://firebirdsql.org/en/downloads/)下載。 您可以透過 NuGet 套件管理員取得 ADO.NET 資料提供者。

## <a name="see-also"></a>請參閱

- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
- [如何判斷 SQL Server 及其元件的版本](http://support.microsoft.com/kb/321185)