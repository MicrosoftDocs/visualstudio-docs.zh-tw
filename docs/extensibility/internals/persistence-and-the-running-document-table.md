---
title: 持續性與執行中的檔資料表 |Microsoft Docs
description: 瞭解專案如何在執行中的檔資料表中協調檔的開啟、儲存和重新命名，以追蹤 Visual Studio IDE 中的檔狀態。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfc480c8b4a41fe29900681289ad08c54d3c1f31
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875956"
---
# <a name="persistence-and-the-running-document-table"></a>持續性與執行中的文件資料表
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 中，專案會完全負責管理其專案專案的持續性，而這些專案專案是使用服務來完成 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> 。 檔是 Visual Studio 環境中的基本持續性單位。 專案會協調檔的開啟、儲存和重新命名，以及執行中的檔資料表 (RDT) ，此資源會追蹤所有開啟檔的狀態。

## <a name="managing-persistence"></a>管理持續性
 專案會藉由執行介面來控制環境的持續性服務 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 。 雖然環境永遠不會直接要求檔保存，但是它會要求擁有專案 (或階層) 儲存檔。 如此一來，專案就可以將專案專案資料儲存至本機檔案、遠端檔案、資料庫、儲存機制或其他媒體。

 全域環境會維護 RDT。 環境會維護 RDT 中所有開啟的視窗和檔的專案，讓他們可以接收特殊通知，例如關閉方案時。 此外，RDT 可讓環境在 **方案總管** 中追蹤對應的節點。 RDT 會維護每個 open、永久性物件的一筆記錄，包括專案檔和專案專案檔案。

## <a name="see-also"></a>請參閱
- [執行中的文件資料表](../../extensibility/internals/running-document-table.md)
- [IDE 中的選取項目和貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)
