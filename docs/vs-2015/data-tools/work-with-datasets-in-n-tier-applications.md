---
title: 使用多層式應用程式中的資料集 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f7be307ec94b15871da20ace8055fc7121d5d92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657807"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>使用多層式架構 (N-Tier) 應用程式中的資料集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

多層式資料應用程式 * 是以資料為中心的應用程式，可 (或 *層*) 分成多個邏輯層。 換句話說，多層式架構資料應用程式是分成多個專案的應用程式，而其專屬專案中各有資料存取層、商務邏輯層和呈現層。 如需詳細資訊，請參閱多 [層式資料應用程式總覽](../data-tools/n-tier-data-applications-overview.md)。

 具類型資料集已獲增強，因此可將 TableAdapter 和資料集類別產生為離散專案。 這提供快速分隔應用程式層以及產生多層式架構資料應用程式的能力。

 具類型資料集中的多層式支援可讓您將應用程式架構反復開發至多層式設計。此外，也不需要手動將程式碼分隔成一個以上的專案。 使用 DataSet 設計工具開始設計資料層。 當您準備好為應用程式架構採用多層式架構 (N-Tier) 設計時，請設定資料集的 [資料集專案]**** 屬性，以將資料集類別產生成不同的專案。

## <a name="in-this-section"></a>本節內容
 將[資料集和 tableadapter 分成不同的專案](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)描述如何將產生的資料集類別移出包含產生之 TableAdapter 類別的專案，並移至新的專案中。

 [將程式碼新增至多層式應用程式中的 tableadapter](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md) 描述如何產生部分類別，其中可針對多層式 TableAdapter 加入程式碼。

 [將程式碼新增至多層式應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md) 描述如何產生部分類別，以便在其中加入多層式資料集的程式碼。

 [將驗證加入至多層式資料集](../data-tools/add-validation-to-an-n-tier-dataset.md) 描述要加入程式碼以執行變更資料驗證的位置。

 [逐步解說：建立多層式資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md) 提供逐步指示，說明如何建立具類型的資料集，並將 TableAdapter 和資料集程式碼分隔為多個專案。

 [逐步解說：將驗證加入至多層式資料應用程式](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265) 提供逐步指示，說明如何將驗證新增至在多層式資料應用程式逐步解說中所建立的應用程式。

## <a name="reference"></a>參考
 <xref:System.Data.DataSet>

 <xref:System.Data.TypedTableBase%601>

## <a name="related-sections"></a>相關章節

- [多層式資料應用程式總覽](../data-tools/n-tier-data-applications-overview.md)
- [階層式更新](../data-tools/hierarchical-update.md)
- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
- [多層式架構和遠端應用程式以及 LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)