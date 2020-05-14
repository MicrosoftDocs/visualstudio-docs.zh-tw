---
title: 持久性和正在運行的文件表 |微軟文件
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
ms.openlocfilehash: ba698f20b83d1a7af42aeca046aa2a8c943838ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706724"
---
# <a name="persistence-and-the-running-document-table"></a>持續性與執行中的文件資料表
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE中,專案完全負責管理其專案項的持久性,它們使用服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>完成。 文檔是可視化工作室環境中持久性的基本單元。 專案使用正在執行的文件表 (RDT) 協調文檔的打開、保存和重命名,這是追蹤所有打開文件狀態的資源。

## <a name="managing-persistence"></a>管理持久性
 項目通過實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>介面來控制環境的持久性服務。 雖然環境從不直接要求文檔持久化,但它要求擁有的專案(或層次結構)保存文檔。 這使得專案能夠將其專案項資料保存到本地檔案、遠端檔、資料庫、存儲庫或其他介質中。

 全域環境維護 RDT。 環境維護 RDT 中所有打開的視窗和文件的條目,這使他們能夠接收特殊通知,例如關閉解決方案時。 此外,RDT使環境能夠追蹤**其相應的節點在解決方案資源管理器**中。 RDT 維護每個打開的可持久物件一條記錄,包括專案檔和專案項目文檔。

## <a name="see-also"></a>另請參閱
- [執行中的文件資料表](../../extensibility/internals/running-document-table.md)
- [IDE 中的選取項目和貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)
