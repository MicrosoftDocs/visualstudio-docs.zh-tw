---
title: 實體資料模型工具
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d663b86603145f8a665f189e5abfbfa2b0b360ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672386"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Visual Studio 中的實體資料模型工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entity Framework 是一種物件關聯式對應技術，可讓 .NET 開發人員使用網域特有的物件來處理關聯式資料。 有了 Entity Framework，開發人員便不再需要撰寫大多數必須撰寫的資料存取程式碼。 Entity Framework 是建議的物件關聯式對應， (ORM) 新 .NET 應用程式的模型化技術。

 從2016年3月起，最新發行的版本是 [Entity Framework 6](https://msdn.microsoft.com/data/ef) 。 [Entity Framework 7](https://docs.efproject.net/en/latest/) 處於發行前版本。

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 工具是設計來協助您建立 [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] 應用程式。 工具的完整檔 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 位於： [Entity Framework](https://msdn.microsoft.com/data/jj590134)。

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]您可以使用工具，從現有的資料庫建立*概念模型*，然後以圖形方式視覺化和編輯您的概念模型。 或者，您可以先以圖形方式建立概念模型，然後產生可支援該模型的資料庫。 無論使用哪一種方式，當基礎資料庫變更時，您都可以自動更新模型，而且可以自動產生應用程式的物件層程式碼。 資料庫產生和物件層程式碼產生皆可自訂。

 這些是在 Visual Studio 2015 中組成實體資料模型工具的特定工具：

- 您可以使用 [!INCLUDE[vstecado](../includes/vstecado-md.md)] ** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 設計**工具 (**Entity Designer**) ，以視覺化方式建立和修改實體、關聯、對應和繼承關聯性。 **Entity Designer**也會產生 [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] 或 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 物件層程式碼。

- 您可以使用** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 嚮導**從現有的資料庫產生概念模型，並將資料庫連接資訊加入至您的應用程式。

- 您可以使用 [ **建立資料庫嚮導]** 先建立概念模型，然後再建立支援該模型的資料庫。

- 當基礎資料庫進行變更時，您可以使用 [ **更新模型嚮導]** 來更新概念模型、儲存體模型和對應。

  > [!NOTE]
  > 從 Visual Studio 2010 開始， [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 工具並不支援 [!INCLUDE[ss2k](../includes/ss2k-md.md)] 。

  工具會產生或修改 .edmx 檔案。 此檔案包含描述概念模型、儲存體模型，以及它們之間的對應資訊。 如需詳細資訊，請參閱  [EDMX](https://msdn.microsoft.com/data/jj650889.aspx)。

  Entity Framework Power Tools 可協助您建立使用實體資料模型的應用程式。 這些工具可以產生概念模型、驗證現有的模型、產生包含以概念模型為基礎之物件類別的原始程式碼檔案，以及產生包含模型所產生之視圖的原始程式碼檔。 如需詳細資訊，請參閱 [預先產生的對應視圖](https://msdn.microsoft.com/data/dn469601.aspx)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[ADO.NET Entity Framework](https://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|說明如何使用 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 提供的工具 [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] 來建立應用程式。|
|[實體資料模型](https://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|提供使用內建的應用程式所使用之資料的連結和資訊 [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] 。|
|[消費者入門完整的 .NET (主控台、WinForms、WPF 等等 ) ](/ef/ef6/get-started)|提供有關如何建立使用 Entity Framework 7 的 .NET 桌面應用程式的教學課程。|
|[ASP.NET 5 應用程式新增至新資料庫](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|說明如何使用 Entity Framework 7 建立新的 ASP.NET 5 應用程式。|

## <a name="see-also"></a>另請參閱
 [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
