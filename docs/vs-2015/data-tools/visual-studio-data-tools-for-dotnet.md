---
title: 適用於.NET 的 visual Studio 資料工具 |Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b42617892e377dcf750e9f5cafc914759b7d0c13
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110918"
---
# <a name="visual-studio-data-tools-for-net"></a>適用於 .NET 的 Visual Studio Data Tools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 和.NET Framework 一起提供廣泛的 API 和工具連線到資料庫、 模型化資料在記憶體中，以及在使用者介面中顯示資料的支援。  .NET Framework 類別提供資料存取功能，稱為[ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx)。 ADO.NET，以及工具在 Visual Studio 中的資料是原本被設計為支援關聯式資料庫和 XML。 如今，許多 NoSQL 資料庫廠商或第三方，會提供 ADO.NET 提供者。  
  
 Visual Studio 2015 Update 2 包含的最新的更新[SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)，可支援在 Azure 中的最新功能[SQL Database](https://azure.microsoft.com/services/sql-database/)和[SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016). [.NET core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project)支援 ADO.NET 資料集和相關的類型除外。 如果您以.NET Core 為目標，而且需要的物件關聯式對應 (ORM) 層級，使用[Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx)。  
  
 下圖顯示簡單的檢視的基本架構：  
  
 ![ADO.NET 架構](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata ADO.NET 架構圖")  
  
 典型的工作流程如下：  
  
1. 在本機電腦上安裝開發或測試資料庫。 請參閱[安裝資料庫系統、 工具和範例](../data-tools/installing-database-systems-tools-and-samples.md)。 如果您使用 Azure 資料服務，就不需要此步驟。  
  
2. 在 Visual Studio 中測試資料庫 （或服務或本機檔案） 的連線。 請參閱[新增連線](../data-tools/add-new-connections.md)。  
  
3. （選擇性）您可以使用工具來產生和設定新的模型。 Entity Framework 為基礎的模型是新的應用程式提供預設建議。 模型中，您使用，一個是應用程式互動的資料來源。 模型會以邏輯方式位於資料庫或服務與應用程式。  請參閱[加入新的資料來源](../data-tools/add-new-data-sources.md)。  
  
4. 拖曳的資料來源**Zdroje dat**視窗拖曳至 Windows Form、 ASP.NET 或 Windows Presentation Foundation 的設計介面，以產生資料繫結程式碼，會在您指定的方法中對使用者顯示的資料。 請參閱[控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
5. 新增項目，例如商務規則、 搜尋、 資料驗證，或利用基礎資料庫公開 （expose） 的自訂功能的自訂程式碼。  
  
   您可以略過步驟 3 和程式的.NET 應用程式，以發出命令，直接與資料庫，而不是使用模型。 在此情況下，您會找到相關的文件：[ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx)。 請注意，您仍然可以使用的資料來源組態精靈和設計工具來產生資料繫結程式碼，當您填入自己的記憶體，然後將 UI 控制項資料繫結至這些物件的物件。  
  
## <a name="in-this-section"></a>本節內容  
  
- [使用 ADO.NET 建立簡單的資料應用程式](../data-tools/create-a-simple-data-application-by-using-adonet.md)  
  
- [新增連線](../data-tools/add-new-connections.md)  
  
- [新增資料來源](../data-tools/add-new-data-sources.md)  
  
- [Visual Studio 中的 Entity Data Model 工具](../data-tools/entity-data-model-tools-in-visual-studio.md)  
  
- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)  
  
- [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Visual Studio 中的 LINQ to SQL 工具)  
  
- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)  
  
- [用於疑難排解資料存取錯誤的其他資源](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
- [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)  
  
- [在 Visual Studio 中建立和管理資料庫與資料層應用程式](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)  
  
- [用於疑難排解資料存取錯誤的其他資源](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
## <a name="see-also"></a>另請參閱  
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
