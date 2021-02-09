---
title: 使用多層式架構 (N-Tier) 應用程式中的資料集
description: 瞭解如何使用多層式應用程式中的資料集。 多層式資料應用程式是以資料為中心的應用程式，這些應用程式會分成多個邏輯層 (或層級) 。
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 93a221640ff7383b39bfdec73cbaa9659156e33f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858068"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>使用多層式架構 (N-Tier) 應用程式中的資料集

多 *層式資料應用程式* 是以資料為中心的應用程式，這些應用程式會分成多個邏輯層 (或 *層級*) 。 換句話說，多層式架構資料應用程式是分成多個專案的應用程式，而其專屬專案中各有資料存取層、商務邏輯層和呈現層。 如需詳細資訊，請參閱多 [層式資料應用程式總覽](../data-tools/n-tier-data-applications-overview.md)。

具類型資料集已獲增強，因此可將 TableAdapter 和資料集類別產生為離散專案。 這提供快速分隔應用程式層以及產生多層式架構資料應用程式的能力。

具類型資料集中的多層式支援可讓您將應用程式架構反復開發至多層式設計。此外，也不需要手動將程式碼分隔成一個以上的專案。 使用 **DataSet 設計工具** 開始設計資料層。 當您準備好為應用程式架構採用多層式架構 (N-Tier) 設計時，請設定資料集的 [資料集專案] 屬性，以將資料集類別產生成不同的專案。

## <a name="reference"></a>參考

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>另請參閱

- [多層式資料應用程式總覽](../data-tools/n-tier-data-applications-overview.md)
- [逐步解說：建立多層式資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [將驗證新增至多層式架構 (N-Tier) 資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [將資料集和 TableAdapter 分成不同的專案](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [階層式更新](../data-tools/hierarchical-update.md)
- [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
- [建立和設定 TableAdapter](../data-tools/create-and-configure-tableadapters.md)
- [具有 LINQ to SQL 的多層式和遠端應用程式](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)
