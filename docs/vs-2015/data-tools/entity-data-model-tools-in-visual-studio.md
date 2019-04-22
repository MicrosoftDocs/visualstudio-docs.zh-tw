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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db58bb1826aab9a26dcec6a9475c49fc99057891
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661097"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>在 Visual Studio 中的實體資料模型工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entity Framework 是一種物件關聯式對應技術，可讓.NET 開發人員使用網域特有物件來處理關聯式資料。 它不需要開發人員通常需要撰寫的大部分資料存取程式碼。 Entity Framework 是模型對於新的.NET 應用程式的技術建議的物件關聯式對應 (ORM)。

 自 2016 年 3 月起為最新的發行的版本[Entity Framework 6](https://msdn.microsoft.com/data/ef) 。 [Entity Framework 7](https://docs.efproject.net/en/latest/)處於發行前版本。

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 工具的設計可協助您建置[!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)]應用程式。 完整文件[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]工具如下：[Entity Framework](https://msdn.microsoft.com/data/jj590134)。

 具有[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]工具，您可以建立*概念模型*從現有資料庫然後以圖形方式以視覺化方式檢視和編輯概念模型。 或者，您可以先以圖形方式建立概念模型，然後產生可支援該模型的資料庫。 無論使用哪一種方式，當基礎資料庫變更時，您都可以自動更新模型，而且可以自動產生應用程式的物件層程式碼。 資料庫產生和物件層程式碼產生皆可自訂。

 以下是 Visual Studio 2015 中的實體資料模型工具所組成的特定工具：

- 您可以使用[!INCLUDE[vstecado](../includes/vstecado-md.md)]  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]設計師**(**Entity Designer**) 以視覺化方式建立和修改實體、 關聯、 對應和繼承關聯性。 **Entity Designer**也會產生[!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)]或[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]物件層程式碼。

- 您可以使用**[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]精靈**從現有資料庫產生概念模型，並將資料庫連接資訊加入至您的應用程式。

- 您可以使用**建立資料庫精靈**要先建立概念模型，然後再建立支援該模型的資料庫。

- 您可以使用**更新模型精靈**變更已對基礎資料庫時，更新您的概念模型、 儲存體模型和對應。

  > [!NOTE]
  >  從 Visual Studio 2010[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]工具不支援[!INCLUDE[ss2k](../includes/ss2k-md.md)]。

  工具會產生，或修改.edmx 檔案。 此檔案包含描述概念模型、 儲存模型，以及它們之間的對應的資訊。 如需詳細資訊，請參閱 < [EDMX](https://msdn.microsoft.com/data/jj650889.aspx)。

  Entity Framework Power Tools 可協助您建置使用 Entity Data Model 的應用程式。 工具可以產生概念模型、 驗證現有模型、 產生含有以概念模型中，為基礎的物件類別的原始程式碼檔案和產生原始程式檔，包含將模型產生的檢視。 如需詳細資訊，請參閱 < [Pre-Generated 對應檢視](https://msdn.microsoft.com/data/dn469601.aspx)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|描述如何使用[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]工具，其中[!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)]提供，若要建立應用程式。|
|[實體資料模型](http://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|提供用於處理資料所建置的應用程式使用的資訊和連結[!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)]。|
|[使用者入門 （主控台、 WinForms、 WPF 等等） 的完整.NET](/ef/ef6/get-started)|提供有關如何建立使用 Entity Framework 7 的.NET 桌面應用程式的教學課程。|
|[ASP.NET 5 應用程式到新的資料庫](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|描述如何使用 Entity Framework 7 以建立新的 ASP.NET 5 應用程式。|

## <a name="see-also"></a>另請參閱
 [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
