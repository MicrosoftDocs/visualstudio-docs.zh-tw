---
title: "在 Visual Studio 中存取資料 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: "100"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: 585f021bf88dd6005a82643c5d182bd1fcbf8e91
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="accessing-data-in-visual-studio"></a>存取 Visual Studio 中的資料
在 Visual Studio 中，您可以建立連接至幾乎任何的資料庫產品或服務，任何形式、 任何位置中資料的應用程式，在本機電腦、 區域網路上，或 public、 private 或混合式雲端中。  
  
JavaScript、 Python、 PHP、 Ruby、 或 c + + 中的應用程式，您連接到資料就像任何其他，取得程式庫，然後撰寫程式碼。 對於.NET 應用程式，Visual Studio 會提供您可用來瀏覽資料來源，建立要儲存和操作資料在記憶體中，並將資料繫結至使用者介面的物件模型的工具。 Microsoft Azure 提供 Sdk for.NET、 Java、 Node.js、 PHP、 Python、 Ruby、 和行動裝置應用程式，以及 Visual Studio 中的工具連接到 Azure 儲存體。  
  
下列清單顯示幾個可以用於許多資料庫和儲存體系統從 Visual Studio。 [Microsoft Azure](https://azure.microsoft.com/)供應項目是資料服務，其中包含所有佈建和管理的基礎資料存放區。  [Azure Tools for Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx)是可讓您能夠使用 Azure 的資料存放區，直接從 Visual Studio 的選用元件。 可以在本機電腦上，在本機網路上，或在 Microsoft Azure 中虛擬機器上裝載大部分的其他 SQL 或 NoSQL 資料庫產品此處所列。 在此案例中，您負責管理資料庫本身。  
  
**Microsoft Azure**  
  
||||  
|-|-|-|  
|SQL 資料庫|DocumentDB|儲存體 （blob、 資料表、 佇列、 檔案）|  
|SQL 資料倉儲|SQL Server Stretch Database|StorSimple|  
  
等等...  
  
**SQL**  
  
||||  
|-|-|-|  
|SQL Server 2005-2016，包括 Express 和 LocalDB|Firebird|MariaDB|  
|MySQL|Oracle|PostgreSQL|  
|SQLite|||  
  
等等...  
  
**NoSQL**  
  
||||  
|-|-|-|  
|Apache Cassandra|CouchDB|MongoDB|  
|NDatabase|OrientDB|RavenDB|  
|VelocityDB|||  
  
等等...  
  
許多資料庫供應商和第三方 Visual Studio 整合支援 NuGet 封裝。 Nuget.org 上或透過 NuGet 封裝管理員 Visual Studio 中，您可以瀏覽供應項目 (**工具** > **NuGet 套件管理員** > **管理 nuget 封裝Packages for Solution**)。 做為擴充，與 Visual Studio 整合其他資料庫產品。 您可以瀏覽至瀏覽 Visual Studio Gallery 中的這些供應項目**工具** > **擴充功能和更新**，然後選取 **線上**方對話方塊的窗格。 如需詳細資訊，請參閱[安裝資料庫系統、 工具和範例](../data-tools/installing-database-systems-tools-and-samples.md)。  
  
> [!NOTE]
> 適用於 SQL Server 2005 的延伸的支援結束於 2016 年 4 月 12 日。 沒有在 Visual Studio 2015 和更新版本的資料工具會繼續使用 SQL Server 2005 此日期之後無法保證。 如需詳細資訊，請參閱[結束的支援公告，以取得 SQL Server 2005](https://www.microsoft.com/server-cloud/products/sql-server-2005/)。  
  
### <a name="net-languages"></a>.NET 語言  
所有的.NET 資料存取，包括在.NET Core 根據 ADO.NET 中，一組類別，定義用於存取任何種類的資料來源，關聯式和非關聯式的介面。 Visual Studio 有數個工具，可搭配 ADO.NET 為了連接到資料庫，設計工具操作資料，並將資料呈現給使用者。 本節中的文件描述如何使用這些工具。 您也可以直接針對 ado.net 指令程式。 如需直接呼叫 ADO.NET 應用程式開發介面的詳細資訊，請參閱[ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) MSDN Library 中。  
  
與 ASP.NET 特別相關的資料存取文件，請參閱[使用資料](http://www.asp.net/web-forms/overview/presenting-and-managing-data)ASP.NET 網站上。 如需使用 Entity Framework 搭配 ASP.NET MVC 的教學課程，請參閱[開始使用 Entity Framework 6 Code First 使用 MVC 5](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)。  
  
在 C# 或 Visual Basic 中的通用 Windows 平台 (UWP) 應用程式可以使用 Microsoft Azure SDK for.NET 來存取 Azure 儲存體和其他 Azure 服務。 Windows.Web.HttpClient 類別可讓與任何 RESTful 服務的通訊。 如需詳細資訊，請參閱[如何連接到 HTTP 伺服器使用 windows.web.http 應用程式開發](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx)。  
  
用於資料儲存在本機電腦上，建議的方法是使用 SQLite，會在應用程式相同的程序中執行。 如果需要的物件關聯式對應 (ORM) 層級，您可以使用 Entity Framework。 如需詳細資訊，請參閱[資料存取](https://msdn.microsoft.com/windows/uwp/data-access/index)Windows 開發人員中心。  
  
如果您要連接到 Azure 服務，請務必下載最新[Azure SDK 工具](https://azure.microsoft.com/downloads/)。  
  
#### <a name="data-providers"></a>資料提供者  
可供在 ADO.NET 中使用的資料庫，它必須能夠自訂*ADO.NET 資料提供者*或是其他必須公開 ODBC 或 OLE DB 介面。 Microsoft 提供[ADO.NET 資料提供者的清單](https://msdn.microsoft.com/data/dd363565)SQL Server 產品，以及 ODBC 和 OLE DB 提供者。  
  
#### <a name="data-modeling"></a>資料模型化  
在.NET 中，您具有模型及管理記憶體中的資料之後您從資料來源擷取它, 的三個選項：  
  
[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md)  
慣用的 Microsoft ORM 技術。 您可以針對關聯式資料的程式使用它做為第一級的.NET 物件。 對於新的應用程式，它應該是預設第一個選擇當模型是必要。 它需要自訂支援從基礎 ADO.NET 提供者。  
  
[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
先前產生的物件關聯式對應程式。 它適用於較不複雜的案例，但不再處於使用中的開發。  
  
[資料集](../data-tools/dataset-tools-in-visual-studio.md)  
最舊的三種模型技術。 它主要被針對快速開發 「 資料表單 」 應用程式中不是處理大量的資料或執行複雜的查詢或轉換。 DataTable 和 DataRow 邏輯上更多.NET 物件類似於 SQL 資料庫物件的物件所組成的資料集物件。 對於 SQL 資料來源為基礎的應用程式相當簡單，資料集仍然可能是不錯的選擇。  
  
沒有使用任何這些技術的需求。 在某些情況下，特別是在效能非常重要，您可以只使用 DataReader 物件從資料庫讀取，並將您所需要的值複製到集合的物件，例如清單\<T >。  
  
### <a name="native-c"></a>原生 C++  
連接到 SQL Server 的 c + + 應用程式應使用[Microsoft® ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339)在大部分情況下。 如果連結伺服器，則是必要的 OLE DB 和該使用[SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx)。 您可以使用來存取其他資料庫[ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx)或直接 OLE DB 驅動程式。 ODBC 是在目前的標準資料庫介面，但大部分資料庫系統提供無法透過 ODBC 介面來存取的自訂功能。 OLE DB 是傳統的 COM 資料存取技術，仍然支援，但不是建議用於新的應用程式。 如需詳細資訊，請參閱[Visual c + + 中的資料存取](https://docs.microsoft.com/cpp/data/)。  
  
使用 REST 服務的 c + + 程式可以使用[c + + REST SDK](https://github.com/Microsoft/cpprestsdk)。  
  
使用 Microsoft Azure 儲存體的 c + + 程式可以使用[Microsoft Azure 儲存體用戶端](http://www.nuget.org/packages/wastorage)。
  
資料模型化&mdash;Visual Studio c + + 不提供 ORM 圖層。 [ODB](http://www.codesynthesis.com/products/odb/)熱門的開放原始碼 ORM 為 c + +。  

若要深入了解從 c + + 應用程式連接到資料庫，請參閱[c + + 的 Visual Studio 資料工具](../data-tools/visual-studio-data-tools-for-cpp.md)。 如需舊版的 Visual c + + 資料存取技術的詳細資訊，請參閱[資料存取](http://msdn.microsoft.com/Library/a9455752-39c4-4457-b14e-197772d3df0b)。
  
### <a name="javascript"></a>JavaScript  
[Visual Studio 中的 JavaScript](https://msdn.microsoft.com/library/hh334522.aspx)是用於建置跨平台應用程式、 UWP 應用程式、 雲端服務、 網站及 web 應用程式的第一級語言。 您可以安裝您最愛的 JavaScript 程式庫和資料庫產品使用 Bower、 Grunt、 Gulp、 npm 及從 Visual Studio 中的 NuGet。 下載 Sdk，從連接到 Azure 儲存體和服務[Azure 網站](https://azure.microsoft.com/)。 Edge.js 是伺服器端 JavaScript (Node.js) 連接至 ADO.NET 資料來源的程式庫。  
  
### <a name="python"></a>Python  
安裝[Python Tools for Visual Studio](http://microsoft.github.io/PTVS/)以及您最愛的 Python 架構來建立 CPython 或 IronPython (.NET) 的應用程式。 適用於 Visual Studio 網站的 Python 工具已連接至資料，包括幾個教學課程[如 Django 和 azure SQL Database](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure)，[如 Django 和 Azure 上 MySQL](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure)和[Bottle 和 MongoDB 上Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure)。
  
## <a name="related-topics"></a>相關主題  
 [資料、 裝置和分析](https://msdn.microsoft.com/data-and-devices)  
 介紹 Microsoft 智慧型雲端，包括 Cortana Analytics suite 這套和物聯網的支援。  
  
 [Microsoft Azure 儲存體](https://azure.microCsoft.com/documentation/services/storage/)  
 描述 Azure 儲存體，以及如何使用 Azure blob、 資料表、 佇列和檔案建立應用程式。  
  
 [Azure SQL Database](https://azure.microsoft.com/documentation/services/sql-database/)  
 描述如何連接到 Azure SQL Database 的關聯式資料庫做為服務。  
  
 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)  
 說明的工具可簡化設計中，瀏覽、 測試和部署的資料連接的應用程式和資料庫。  
  
 [ADO.NET](/dotnet/framework/data/adonet/index)  
 描述 ADO.NET 架構以及如何使用 ADO.NET 類別來管理應用程式資料並與其互動的資料來源和 XML。  
  
 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef)  
 描述如何建立資料應用程式可讓開發人員針對概念模型而不是直接針對關聯式資料庫設計程式。  
  
 [WCF Data Services 4.5](/dotnet/framework/data/wcf/index)  
 描述如何使用[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]部署在 web 或內部網路上的資料服務可實作[開放式資料通訊協定 (OData)](http://go.microsoft.com/fwlink/?LinkID=182204)。  
  
 [Office 方案的資料](/office-dev/office-dev/data-in-office-solutions)  
 包含說明資料在 Office 方案中的運作方式的主題連結。 這包括結構描述導向的程式設計、 資料快取，以及伺服器端資料存取的相關資訊。  
  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 描述 C# 和 Visual Basic 中，以及通用模型來查詢關聯式資料庫、 XML 文件、 資料集和記憶體中集合內建查詢功能。
  
 [Visual Studio 中的 XML 工具](../xml-tools/xml-tools-in-visual-studio.md)  
 討論使用 XML 資料，偵錯 XSLT，.NET Framework XML 功能，以及 XML 查詢的架構。  
  
 [XML 文件和資料](/dotnet/standard/data/xml/index)  
 提供用於 .NET Framework 中 XML 文件和資料的全面性整合類別集合的概觀。