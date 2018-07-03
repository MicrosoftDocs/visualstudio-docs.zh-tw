---
title: Visual Studio 中的 entity Framework 工具
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b1d98422d9527220b54232d1180ae4b91a28e6b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="entity-framework-tools-in-visual-studio"></a>Visual Studio 中的 entity Framework 工具
Entity Framework 是一種物件關聯式對應技術，可讓.NET 開發人員使用網域特有物件來處理關聯式資料。 它不需要開發人員通常需要撰寫的大部分資料存取程式碼。 Entity Framework 是模型對於新的.NET 應用程式的技術建議的物件關聯式對應 (ORM)。

Entity Framework 工具專門設計來協助您建置 Entity Framework (EF) 應用程式。 以下是 Entity Framework 的完整文件： [EF Core 和 EF 6](/ef/)。

您可以使用 Entity Framework 工具，建立*概念模型*從現有資料庫以及然後以圖形方式以視覺化方式檢視和編輯您的概念模型。 或者，您可以先以圖形方式建立概念模型，然後產生可支援該模型的資料庫。 無論使用哪一種方式，當基礎資料庫變更時，您都可以自動更新模型，而且可以自動產生應用程式的物件層程式碼。 資料庫產生和物件層程式碼產生皆可自訂。

Entity Framework 工具會安裝的一部分**資料儲存和處理**在 Visual Studio 安裝程式工作負載。 您也可以安裝為 indvidual 元件下**Sdk、 程式庫，以及架構**類別目錄。

這些是 Visual Studio 中的 Entity Framework 工具所組成的特定工具：

-   您可以使用[!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]設計師**(**Entity Designer**) 以視覺化方式建立及修改實體、 關聯、 對應和繼承關聯性。 **Entity Designer**也會產生[!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)]或[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]物件層程式碼。

-   您可以使用**[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]精靈**產生概念模型，從現有的資料庫，並將資料庫連接資訊加入至您的應用程式。

-   您可以使用**建立資料庫精靈**第一次建立概念模型，然後建立支援模型的資料庫。

-   您可以使用**更新模型精靈**變更已對基礎資料庫時，更新您的概念模型、 儲存體模型和對應。

    > [!NOTE]
    >  從 Visual Studio 2010 開始，Entity Framework 工具不支援[!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)]。

這些工具產生，或修改.edmx 檔案。 這個.edmx 檔案包含描述概念模型、 儲存模型，以及它們之間的對應資訊。 如需詳細資訊，請參閱[EDMX](https://msdn.microsoft.com/data/jj650889.aspx)。

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4)幫助您建立使用實體資料模型的應用程式。 電源工具可以產生概念模型、 驗證現有模型、 產生含有以概念模型中，為基礎的物件類別的原始程式檔和產生包含檢視模型所產生的原始程式碼檔案。 如需詳細資訊，請參閱[Pre-Generated 對應檢視](https://msdn.microsoft.com/data/dn469601.aspx)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index)|描述如何使用[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]工具，其中[!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]提供，若要建立應用程式。|
|[實體資料模型](/dotnet/framework/data/adonet/entity-data-model)|提供使用上建置的應用程式所使用的資料的資訊和連結[!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]。|
|[Entity Framework (EF) 文件）](https://msdn.microsoft.com/library/ee712907(v=vs.113).aspx)|提供視訊、 教學課程和進階文件可協助您充分利用 Entity Framework 的索引。|
|[ASP.NET 5 應用程式到新的資料庫](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|描述如何使用 Entity Framework 7，建立新的 ASP.NET 5 應用程式。|

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)