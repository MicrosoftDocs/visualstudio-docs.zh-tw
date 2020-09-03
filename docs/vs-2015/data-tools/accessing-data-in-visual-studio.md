---
title: 存取資料
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- "80025080"
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 103
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 78d950b777d866835ef516c4910180b21de295e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544998"
---
# <a name="accessing-data-in-visual-studio"></a>存取 Visual Studio 中的資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，您可以建立應用程式，以幾乎任何格式（不論是本機電腦、區域網路或在公用、私人或混合式雲端）連接到任何資料庫產品或服務中的資料。

 針對 JavaScript、Python、PHP、Ruby 或 c + + 中的應用程式，您可以藉由取得程式庫及撰寫程式碼，來連接到任何其他資料。 針對 .NET 應用程式，Visual Studio 提供的工具可讓您用來流覽資料來源、建立物件模型以儲存和操作記憶體中的資料，以及將資料系結至使用者介面。     Microsoft Azure 提供適用于 .NET、JAVA、Node.js、PHP、Python、Ruby 和行動裝置應用程式的 Sdk，以及 Visual Studio 中用來連接到 Azure 儲存體的工具。

 下列清單顯示可從 Visual Studio 使用的許多資料庫和儲存系統的其中一部分。 [Microsoft Azure](https://azure.microsoft.com/)供應專案是資料服務，包括基礎資料存放區的所有布建和管理。  [適用于 Visual Studio 的 Azure Tools](https://www.visualstudio.com/features/azure-tools-vs.aspx) 是選擇性元件，可讓您直接從 Visual Studio 使用 azure 資料存放區。 此處所列的其他 SQL 和 NoSQL 資料庫產品，可裝載于本機電腦、區域網路或虛擬機器上的 Microsoft Azure。 在此案例中，您必須負責管理資料庫本身。

 **Microsoft Azure**

- SQL Database

- DocumentDB

-儲存體 (blob、資料表、佇列、檔案) 

- SQL 資料倉儲

- SQL Server Stretch Database

- StorSimple

 等等。

 **SQL**

- SQL Server 2005 –2016，包括 Express 和 LocalDB
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite

 等等。

 **NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB
- RavenDB
- VelocityDB

 等等。

 許多資料庫廠商和協力廠商都支援 NuGet 套件的 Visual Studio 整合。 您可以在 nuget.org 上探索這些供應專案，或透過 Visual Studio (**工具**  >  **nuget 封裝管理員**  >  **管理方案) 的 nuget 套件**中的 nuget 封裝管理員。 其他資料庫產品會以擴充功能與 Visual Studio 整合。   您可以流覽至 [**工具**  >  **擴充功能和更新**]，然後在對話方塊的左窗格中選取 [**線上**]，以流覽 Visual Studio 資源庫中的這些供應專案。  如需詳細資訊，請參閱 [安裝資料庫系統、工具和範例](../data-tools/installing-database-systems-tools-and-samples.md)。

> [!NOTE]
> SQL Server 2005 的延長支援已於 2016 年 4 月 12 日結束。   在此日期之後，不保證 Visual Studio 2015 和更新版本中的資料工具將繼續使用 SQL Server 2005。 如需詳細資訊，請參閱 [SQL Server 2005 的終止支援公告](https://www.microsoft.com/sql-server/sql-server-2005)。

### <a name="net-languages"></a>.NET 語言
 所有 .NET 資料存取（包括 .NET Core 中的 .NET 資料存取）是以 ADO.NET 為基礎，這是一組類別，可定義存取任何資料來源（關聯式和非關聯式）的介面。 Visual Studio 有數種工具和設計工具，可與 ADO.NET 搭配使用，協助您連接到資料庫、運算元據，以及向使用者呈現資料。 本節中的檔說明如何使用這些工具。 您也可以直接針對 ADO.NET 命令物件進行程式設計。 如需直接呼叫 ADO.NET Api 的詳細資訊，請參閱 MSDN Library 中的 [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) 。

 如需與 ASP.NET 特別相關的資料存取檔，請參閱使用 ASP.NET 網站上的  [資料](/aspnet/web-forms/overview/presenting-and-managing-data/) 。 如需搭配使用 Entity Framework 與 ASP.NET MVC 的教學課程，請參閱使用 [mvc 5 的 Entity Framework 6 Code First 消費者入門](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)。

 通用 Windows 平臺 (以 c # 或 Visual Basic 使用的 UWP) 應用程式，可以使用 Microsoft Azure SDK for .NET 來存取 Azure 儲存體和其他 Azure 服務。 HttpClient 類別可讓您與任何 RESTful 服務進行通訊。 如需詳細資訊，請參閱 [如何使用 HTTP.sys 連接至 HTTP 伺服器](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx)。

 若為本機電腦上的資料存放區，建議的方法是使用 SQLite，此程式會在與應用程式相同的進程中執行。 如果需要 (ORM) 層的物件關聯式對應，您可以使用 Entity Framework。 如需詳細資訊，請參閱 Windows 開發人員中心的 [資料存取](https://msdn.microsoft.com/windows/uwp/data-access/index) 。

 如果您要連接到 Azure 服務，請務必下載最新的 [AZURE SDK 工具](https://azure.microsoft.com/downloads/)。

#### <a name="data-providers"></a>資料提供者
 針對可在 ADO.NET 中使用的資料庫，它必須有自訂 *ADO.NET 資料提供者* ，否則必須公開 ODBC 或 OLE DB 介面。 Microsoft 針對 SQL Server 產品以及 ODBC 和 OLE DB 提供者提供了 [ADO.NET 的資料提供者清單](https://msdn.microsoft.com/data/dd363565) 。

#### <a name="data-modeling"></a>資料模型化
 在 .NET 中，當您從資料來源取出資料之後，有三個選項可供您在記憶體中建立資料模型和操作：

 Entity Framework 慣用的 Microsoft ORM 技術。 您可以使用它來針對關聯式資料進行程式設計，以做為第一級的 .NET 物件。 針對新的應用程式，它應該是需要模型時的預設第一個選擇。 它需要基礎 ADO.NET 提供者的自訂支援。

 LINQ to SQL 早期產生的物件關聯式對應程式。 它適用于較不復雜的案例，但已不再進行開發。

 資料集最舊的三種模型化技術。 它的設計主要是用於快速開發「資料的表單」應用程式，而這些應用程式不會處理大量資料，也不會執行複雜的查詢或轉換。 DataSet 物件是由資料表和 DataRow 物件所組成，這些物件在邏輯上類似 SQL database 物件，遠遠超過 .NET 物件。 針對以 SQL 資料來源為基礎的相對簡單應用程式，資料集可能仍然是不錯的選擇。

 不需要使用這些技術。 在某些情況下，尤其是當效能很重要時，您可以直接使用 DataReader 物件從資料庫讀取，並將您需要的值複製到集合物件（例如清單）中 \<T> 。

### <a name="native-c"></a>Native C++
 連接到 SQL Server 的 c + + 應用程式應該使用 [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx)。 您可以直接使用 [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) 或 OLE DB 驅動程式來存取其他資料庫。 ODBC 是目前的標準資料庫介面，但大部分的資料庫系統都提供無法透過 ODBC 介面存取的自訂功能。  OLE DB 是一種舊版的 COM 資料存取技術，仍支援但不建議用於新的應用程式。  如需詳細資訊，請參閱 [資料存取](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)。

 使用 REST 服務的 c + + 程式可以使用 [c + + REST SDK](https://github.com/Microsoft/cpprestsdk)。

 搭配 Microsoft Azure 儲存體使用的 c + + 程式可以使用 [Microsoft Azure 儲存體用戶端](https://www.nuget.org/packages/wastorage)。

#### <a name="data-modeling"></a>資料模型化
 Visual Studio 不會提供 c + + 的 ORM 層。  [ODB](https://www.codesynthesis.com/products/odb/) 是適用于 c + + 的熱門開放原始碼 ORM。

 如需舊版 Visual C++ 資料存取技術的詳細資訊，請參閱  [資料存取](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 [Visual Studio 中的 JavaScript](https://msdn.microsoft.com/library/hh334522.aspx) 是建立跨平臺應用程式、UWP 應用程式、雲端服務、網站和 web 應用程式的第一級語言。 您可以使用 Visual Studio 內的 Bower、Grunt、Gulp、npm 和 NuGet 來安裝您最愛的 JavaScript 程式庫和資料庫產品。 從 [azure 網站](https://azure.microsoft.com/)下載 sdk，以連接到 azure 儲存體和服務。  Edge.js 是將伺服器端 JavaScript ( # A1) 連接到 ADO.NET 資料來源的程式庫。

### <a name="python"></a>Python
 安裝  [適用於 Visual Studio 的 Python 工具](http://microsoft.github.io/PTVS/) 以及您最愛的 Python 架構，以建立 ( .net) 應用程式的 CPython 或 IronPython。  適用於 Visual Studio 的 Python 工具網站有幾個連接到資料的教學課程，包括 azure 上的 [Django 和 SQL Database](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure)、azure 上的 [Django 和 MySQL](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) ，以及 azure 上的 [瓶和 MongoDB](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure)。

## <a name="in-this-section"></a>本節內容
 [安裝資料庫系統、工具和範例](../data-tools/installing-database-systems-tools-and-samples.md) 討論如何取得資料庫產品以及支援這些產品的 Visual Studio 延伸模組或驅動程式，以及尋找範例資料庫以供實驗和學習之用。

 [適用于 .net 的 Visual Studio 資料工具](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) 描述如何使用 Visual Studio 的工具視窗來連接至資料來源、建立資料集或 Entity Framework 模型，以及將資料系結至使用者介面控制項。

## <a name="related-topics"></a>相關主題
 [資料、裝置及分析](https://msdn.microsoft.com/data-and-devices) 提供 Microsoft 智慧型雲端的簡介，包括 Cortana Analytics Suite 和物聯網支援。

 [Microsoft Azure 儲存體](/azure/storage/) 描述 Azure 儲存體，以及如何使用 Azure blob、資料表、佇列和檔案來建立應用程式。

 [Azure SQL Database](https://azure.microsoft.com/documentation/services/sql-database/) 描述如何連接到 Azure SQL Database，也就是關係資料庫即服務。

 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) 描述可簡化資料連線應用程式和資料庫之設計、探索、測試和部署的工具。

 [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) 描述 ADO.NET 架構，以及如何使用 ADO.NET 類別來管理應用程式資料，以及與資料來源和 XML 互動。

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) 描述如何建立資料應用程式，讓開發人員能夠針對概念模型進行程式設計，而不是直接針對關係資料庫進行程式設計。

 [WCF Data Services 4.5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) 說明如何使用在 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] web 或內部網路上部署資料服務，以執行 [開放式資料通訊協定 (OData) ](https://www.odata.org/)。

 [Office 方案中的資料](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) 包含主題的連結，這些主題說明如何在 Office 方案中使用資料。 這包括架構導向的程式設計、資料快取，以及伺服器端資料存取的相關資訊。

 [LINQ (語言整合式查詢) ](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) 描述 c # 和 Visual Basic 內建的查詢功能，以及用來查詢關係資料庫、XML 檔、資料集和記憶體中集合的一般模型。

 [Visual Studio 中的 XML 工具](../xml-tools/xml-tools-in-visual-studio.md) 討論使用 XML 資料、偵測 XSLT、.NET Framework XML 功能，以及 XML 查詢的架構。

 [XML 檔和資料](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) 提供一組完整且整合的類別，以使用 .NET Framework 中的 XML 檔和資料。
