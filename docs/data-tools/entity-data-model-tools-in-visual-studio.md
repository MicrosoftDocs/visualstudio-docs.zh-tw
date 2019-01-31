---
title: Entity Framework Tools
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 0058d3e7106e7af3bf2b417a512b19ce87c52c57
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014636"
---
# <a name="entity-framework-tools-in-visual-studio"></a>在 Visual Studio 中的 entity Framework 工具

Entity Framework 是一種物件關聯式對應技術，可讓.NET 開發人員使用網域特有物件來處理關聯式資料。 它不需要開發人員通常需要撰寫的大部分資料存取程式碼。 Entity Framework 是模型對於新的.NET 應用程式的技術建議的物件關聯式對應 (ORM)。

Entity Framework 工具專門設計來協助您建置 Entity Framework (EF) 應用程式。 Entity Framework 的完整文件位於這裡：[EF Core 和 EF 6](/ef/)。

您可以使用 Entity Framework 工具，建立*概念模型*從現有資料庫然後以圖形方式以視覺化方式檢視和編輯概念模型。 或者，您可以先以圖形方式建立概念模型，然後產生可支援該模型的資料庫。 無論使用哪一種方式，當基礎資料庫變更時，您都可以自動更新模型，而且可以自動產生應用程式的物件層程式碼。 資料庫產生和物件層程式碼產生皆可自訂。

Entity Framework 工具安裝的一部分**資料儲存和處理**Visual Studio 安裝程式中的工作負載。 您也可以安裝它們作為個別的元件底下**Sdk、 程式庫和架構**類別目錄。

以下是 Visual Studio 中的 Entity Framework 工具所組成的特定工具：

- 您可以使用[!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]設計師**(**Entity Designer**) 以視覺化方式建立和修改實體、 關聯、 對應和繼承關聯性。 **Entity Designer**也會產生[!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)]或[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]物件層程式碼。

- 您可以使用**[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]精靈**從現有資料庫產生概念模型，並將資料庫連接資訊加入至您的應用程式。

- 您可以使用**建立資料庫精靈**要先建立概念模型，然後再建立支援該模型的資料庫。

- 您可以使用**更新模型精靈**變更已對基礎資料庫時，更新您的概念模型、 儲存體模型和對應。

  > [!NOTE]
  > 從 Visual Studio 2010 開始，Entity Framework 工具不支援[!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)]。

工具會產生或修改 *.edmx*檔案。 這 *.edmx*檔案包含描述概念模型、 儲存模型，以及它們之間的對應的資訊。 如需詳細資訊，請參閱 < [EDMX](https://docs.microsoft.com/ef/ef6/)。

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4)幫助您建置使用 Entity Data Model 的應用程式。 Power 工具可以產生概念模型、 驗證現有模型、 產生含有以概念模型中，為基礎的物件類別的原始程式碼檔案和產生原始程式檔，包含將模型產生的檢視。 如需詳細資訊，請參閱 < [Pre-Generated 對應檢視](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views)。

## <a name="related-topics"></a>相關主題

| 標題 | 說明 |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | 描述如何使用[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]工具，其中[!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]提供，若要建立應用程式。 |
| [實體資料模型](/dotnet/framework/data/adonet/entity-data-model) | 提供用於處理資料所建置的應用程式使用的資訊和連結[!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]。 |
| [Entity Framework (EF) 文件）](https://docs.microsoft.com/ef/ef6/get-started) | 提供影片、 教學課程中，並可協助您充分利用 Entity Framework 的進階文件的索引。 |
| [ASP.NET 5 應用程式到新的資料庫](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | 描述如何使用 Entity Framework 7 以建立新的 ASP.NET 5 應用程式。 |

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)