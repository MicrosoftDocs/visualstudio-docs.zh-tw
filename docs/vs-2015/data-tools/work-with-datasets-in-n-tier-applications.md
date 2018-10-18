---
title: 使用多層式架構應用程式中的資料集 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d05204edfd7c3cd5daecad3a1cb21ba5ba7e60d8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205968"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>使用多層式架構 (N-Tier) 應用程式中的資料集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
多層式架構資料應用程式 * 是以資料為中心的應用程式，而且分成多個邏輯層 (或*層*)。 換句話說，多層式架構資料應用程式是分成多個專案的應用程式，而其專屬專案中各有資料存取層、商務邏輯層和呈現層。 如需詳細資訊，請參閱 <<c0> [ 多層式架構資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)。  
  
 具類型資料集已獲增強，因此可將 TableAdapter 和資料集類別產生為離散專案。 這提供快速分隔應用程式層以及產生多層式架構資料應用程式的能力。  
  
 具類型資料集中的多層式架構支援可讓反覆開發的多層式架構設計的應用程式架構。它也會移除以手動方式將程式碼分成多個專案的需求。 開始使用來設計資料層[建立和編輯具類型資料集](../data-tools/creating-and-editing-typed-datasets.md)。 當你準備好要接受至多層式設計的應用程式架構時，請設定**資料集 Project**至不同的專案產生的資料集類別的資料集屬性。  
  
## <a name="in-this-section"></a>本節內容  
 [將資料集和 TableAdapter 分成不同的專案](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 描述如何將產生的資料集類別移出含有產生的 TableAdapter 類別的專案，以及產生為新的專案。  
  
 [將程式碼新增至多層式架構 (N-Tier) 應用程式中的 TableAdapter](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 描述如何產生部分類別，而使用部分類別可以加入多層式架構 TableAdapter 的程式碼。  
  
 [將程式碼新增至多層式架構 (N-Tier) 應用程式中的資料集](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 描述如何產生部分類別，而使用部分類別可以加入多層式架構資料集的程式碼。  
  
 [將驗證新增至多層式架構 (N-Tier) 資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 描述在何處加入程式碼，以執行資料變更驗證。  
  
 [逐步解說：建立多層式架構 (N-Tier) 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 提供用於建立具類型資料集以及將 TableAdapter 和資料集程式碼分成多個專案的逐步指示。  
  
 [逐步解說： 將驗證新增至多層式架構資料應用程式](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
 提供將驗證加入 n-tier 資料應用程式逐步解說中所建立的應用程式的逐步指示。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## <a name="related-sections"></a>相關章節  
 [多層式架構 (N-Tier) 資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)  
  
 [階層式更新](../data-tools/hierarchical-update.md)  
  
 [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)  
  
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)  
  
 [使用 LINQ to SQL 的多層式架構和遠端應用程式](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

