---
title: 適用于 .NET 的 Visual Studio 資料工具 |Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d591595c65f00e0198ded9492ae0b8399e363e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670106"
---
# <a name="visual-studio-data-tools-for-net"></a>適用於 .NET 的 Visual Studio Data Tools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 和 .NET Framework 一起提供可連接到資料庫、在記憶體中建立資料模型，以及在使用者介面中顯示資料的廣泛 API 和工具支援。  提供資料存取功能的 .NET Framework 類別稱為 [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx)。 ADO.NET 和 Visual Studio 中的資料工具，最初是設計來支援關係資料庫和 XML。 這些天、許多 NoSQL 資料庫廠商或協力廠商提供 ADO.NET 的提供者。

 Visual Studio 2015 Update 2 包含            [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)的最新更新，可支援 Azure [SQL Database](https://azure.microsoft.com/services/sql-database/) 和 [SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016)的最新功能。 除了資料集和相關類型以外， [.Net Core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project)還支援 ADO.NET。 如果您是以 .NET Core 為目標，且需要 (ORM) 層的物件關聯式對應，請使用 [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx)。

 下圖顯示基本架構的簡化觀點：

 ![ADO.NET 架構](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata ADO.NET 架構圖表")

 一般工作流程如下：

1. 在本機電腦上安裝開發或測試資料庫。 請參閱 [安裝資料庫系統、工具和範例](../data-tools/installing-database-systems-tools-and-samples.md)。 如果您使用 Azure 資料服務，則不需要此步驟。

2. 測試 Visual Studio 中) 資料庫 (或服務或本機檔案的連接。 請參閱 [新增連接](../data-tools/add-new-connections.md)。

3.  (選擇性) 使用工具來產生及設定新的模型。 以 Entity Framework 為基礎的模型是新應用程式的預設建議。 無論您使用哪一個模型，它都是應用程式所互動的資料來源。 模型在邏輯上是在資料庫或服務和應用程式之間。  請參閱 [加入新的資料來源](../data-tools/add-new-data-sources.md)。

4. 將資料來源從 [ **資料來源** ] 視窗拖曳到 Windows Forms、ASP.NET 或 Windows Presentation Foundation 設計介面上，以產生資料系結程式碼，以您指定的方式將資料顯示給使用者。 請參閱 [將控制項系結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。

5. 針對商務規則、搜尋和資料驗證等專案加入自訂程式碼，或利用基礎資料庫所公開的自訂功能。

   您可以略過步驟3，並程式設計 .NET 應用程式，將命令直接發出至資料庫，而不是使用模型。 在此情況下，您會發現相關文件： [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx)。 請注意，當您在記憶體中填入您自己的物件，然後將 UI 控制項資料系結至這些物件時，您仍然可以使用「資料來源設定向導」和「設計工具」來產生資料系結程式碼。

## <a name="in-this-section"></a>本節內容

- [使用 ADO.NET 建立簡單的資料應用程式](../data-tools/create-a-simple-data-application-by-using-adonet.md)

- [新增連線](../data-tools/add-new-connections.md)

- [新增資料來源](../data-tools/add-new-data-sources.md)

- [Visual Studio 中的 Entity Data Model 工具](../data-tools/entity-data-model-tools-in-visual-studio.md)

- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

- [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)

- [用於疑難排解資料存取錯誤的其他資源](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

- [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- [在 Visual Studio 中建立和管理資料庫與資料層應用程式](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)

- [用於疑難排解資料存取錯誤的其他資源](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

## <a name="see-also"></a>另請參閱
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
