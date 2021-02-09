---
title: Entity Framework Tools
description: 瞭解 Visual Studio 中的 Entity Framework Tools。 Entity Framework Tools 的設計目的是協助您建立 Entity Framework (EF) 應用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ee4bb5e56c5ae9ffb5f5266c8ef80804c8e96597
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866979"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Visual Studio 中的 Entity Framework Tools

Entity Framework 是一種物件關聯式對應技術，可讓 .NET 開發人員使用網域特有的物件來處理關聯式資料。 有了 Entity Framework，開發人員便不再需要撰寫大多數必須撰寫的資料存取程式碼。 Entity Framework 是建議的物件關聯式對應， (ORM) 新 .NET 應用程式的模型化技術。

Entity Framework Tools 的設計目的是協助您建立 Entity Framework (EF) 應用程式。 Entity Framework 的完整檔位於： [總覽-EF 6](/ef/ef6/)。

  > [!NOTE]
  > 此頁面上所述的 Entity Framework Tools 用來產生 *.edmx* 檔，在 EF Core 中不受支援。 若要從現有的資料庫產生 EF Core 模型，請參閱 [反向工程-EF Core](/ef/core/managing-schemas/scaffolding)。 如需 EF 6 與 EF Core 之間差異的詳細資訊，請參閱 [比較 ef 6 和 EF Core](/ef/efcore-and-ef6/)。

使用 Entity Framework Tools，您可以從現有的資料庫建立 *概念模型* ，然後以圖形方式視覺化和編輯您的概念模型。 或者，您可以先以圖形方式建立概念模型，然後產生可支援該模型的資料庫。 無論使用哪一種方式，當基礎資料庫變更時，您都可以自動更新模型，而且可以自動產生應用程式的物件層程式碼。 資料庫產生和物件層程式碼產生皆可自訂。

Entity Framework 工具會安裝為 Visual Studio 安裝程式中 **資料儲存和處理** 工作負載的一部分。 您也可以將其安裝為 **sdk、程式庫和** 架構類別下的個別元件。

這些是在 Visual Studio 中組成 Entity Framework 工具的特定工具：

- 您可以使用 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] 設計** 工具 (**Entity Designer**) ，以視覺化方式建立和修改實體、關聯、對應和繼承關聯性。 **Entity Designer** 也會產生 [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] 或 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 物件層程式碼。

- 您可以使用 **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] 嚮導** 從現有的資料庫產生概念模型，並將資料庫連接資訊加入至您的應用程式。

- 您可以使用 [ **建立資料庫嚮導]** 先建立概念模型，然後再建立支援該模型的資料庫。

- 當基礎資料庫進行變更時，您可以使用 [ **更新模型嚮導]** 來更新概念模型、儲存體模型和對應。

  > [!NOTE]
  > 從 Visual Studio 2010 開始，Entity Framework 工具不支援 [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)] 。

工具會產生或修改 *.edmx* 檔案。 此 *.edmx* 檔案包含描述概念模型、儲存體模型，以及它們之間的對應資訊。 如需詳細資訊，請參閱 [EDMX](/ef/ef6/)。

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) 可協助您建立使用實體資料模型的應用程式。 Power tools 可以產生概念模型、驗證現有的模型、產生包含以概念模型為基礎之物件類別的原始程式碼檔案，以及產生包含模型所產生之視圖的原始程式碼檔。 如需詳細資訊，請參閱 [預先產生的對應視圖](/ef/ef6/fundamentals/performance/pre-generated-views)。

## <a name="related-topics"></a>相關主題

| 標題 | 描述 |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | 說明如何使用 [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] 提供的工具 [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] 來建立應用程式。 |
| [實體資料模型](/dotnet/framework/data/adonet/entity-data-model) | 提供使用內建的應用程式所使用之資料的連結和資訊 [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] 。 |
| [Entity Framework (EF) 檔) ](/ef/ef6/get-started) | 提供影片、教學課程和 advanced 檔的索引，以協助您充分利用 Entity Framework。 |
| [ASP.NET 5 應用程式新增至新資料庫](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | 說明如何使用 Entity Framework 7 建立新的 ASP.NET 5 應用程式。 |

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
