---
title: 使用多層式架構 (N-Tier) 應用程式中的資料集
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 23dc346ac1d8495c3aef191ee3228087e1b222c3
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37116961"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>使用多層式架構 (N-Tier) 應用程式中的資料集

*多層式架構資料應用程式*是以資料為中心的應用程式，而且分成多個邏輯層 (或*層*)。 換句話說，多層式架構資料應用程式是分成多個專案的應用程式，而其專屬專案中各有資料存取層、商務邏輯層和呈現層。 如需詳細資訊，請參閱 <<c0> [ 多層式架構資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)。

具類型資料集已獲增強，因此可將 TableAdapter 和資料集類別產生為離散專案。 這提供快速分隔應用程式層以及產生多層式架構資料應用程式的能力。

具類型資料集中的多層式架構支援可讓反覆開發的多層式架構設計的應用程式架構。它也會移除以手動方式將程式碼分成多個專案的需求。 開始使用來設計資料層**Dataset 設計工具**。 當你準備好要接受至多層式設計的應用程式架構時，請設定**資料集 Project**至不同的專案產生的資料集類別的資料集屬性。

## <a name="reference"></a>參考資料

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>另請參閱

- [多層式架構資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)
- [逐步解說： 建立 n-tier 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [將驗證新增至多層式架構 (N-Tier) 資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [將資料集和 TableAdapter 分成不同的專案](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [階層式更新](../data-tools/hierarchical-update.md)
- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
- [建立和設定 TableAdapter](../data-tools/create-and-configure-tableadapters.md)
- [多層式架構和遠端的應用程式使用 LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)