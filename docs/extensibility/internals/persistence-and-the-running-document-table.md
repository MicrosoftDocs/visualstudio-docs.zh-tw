---
title: 持續性和執行中的檔資料表 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f03836e1faaac03fbd89c0b93f37a698cbdcd56a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726087"
---
# <a name="persistence-and-the-running-document-table"></a>持續性與執行中的文件資料表
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 中，專案會完全負責管理其專案專案的持續性，它們會使用服務來完成，<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>。 檔是 Visual Studio 環境中的基本持續性單位。 專案會協調開啟、儲存和重新命名檔與執行中的檔資料表（RDT），這是追蹤所有已開啟檔狀態的資源。

## <a name="managing-persistence"></a>管理持續性
 專案會藉由執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 介面來控制環境的持續性服務。 雖然環境永遠不會直接要求檔本身保存，但它會要求擁有專案（或階層）來儲存檔。 這可讓專案將專案專案資料儲存到本機檔案、遠端檔案、資料庫、儲存機制或其他媒體中。

 全域環境會維護 RDT。 環境會維護 RDT 中所有開啟的視窗和檔的專案，讓他們可以接收特殊通知，例如關閉解決方案的時間。 此外，RDT 也可以讓環境在**方案總管**中追蹤其對應的節點。 RDT 會針對每個開啟的永久性物件維護一筆記錄，包括專案檔和專案專案檔案。

## <a name="see-also"></a>請參閱
- [執行中的文件資料表](../../extensibility/internals/running-document-table.md)
- [IDE 中的選取項目和貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)