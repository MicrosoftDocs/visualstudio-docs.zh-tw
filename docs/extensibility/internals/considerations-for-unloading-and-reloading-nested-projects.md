---
title: 考量卸載及重新載入巢狀專案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5738a5e8cf01466dd632797c3f92ffd135a44
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861331"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>卸載及重新載入巢狀的專案的考量

當您實作巢狀的專案類型時，您必須執行額外步驟，當您卸除並重新載入專案。 若要正確通知方案事件的接聽程式，您必須正確地引發`OnBeforeUnloadProject`和`OnAfterLoadProject`事件。

若要引發這些事件的其中一個原因是進行原始程式碼控制 (SCC)。 您不想從伺服器刪除的項目，然後將它們新增至 SCC 回復為*新*如果沒有`Get`SCC 的作業。 在此情況下，新的檔案會載入 SCC 不足。 您必須在卸載並重新載入的所有檔案，以防它們不同。

來源的程式碼控制呼叫`ReloadItem`。 實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>介面來呼叫`OnBeforeUnloadProject`和`OnAfterLoadProject`刪除專案，然後重新建立它。 當您以這種方式實作的介面時，SCC 會告知專案已暫時刪除，並再次新增。 因此，SCC 不操作，在專案上與此專案*實際上*刪除並重新加入。

## <a name="reload-projects"></a>重新載入專案

若要支援的巢狀專案重新載入，您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>方法。 在您實作`ReloadItem`，關閉巢狀的專案，然後再重新建立它們。

通常當專案重新載入時，IDE 會引發<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>事件。 不過，巢狀專案的刪除或重新載入，父專案啟始的處理程序中，而不在 IDE。 父專案不會引發解決方案事件和 IDE 沒有任何資訊的程序初始化，因為未引發的事件。

若要處理這個程序，父專案呼叫`QueryInterface`上<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>介面。 `IVsFireSolutionEvents` 具有函式，告訴 IDE 引發`OnBeforeUnloadProject`事件，以卸載巢狀的專案，然後再引發`OnAfterLoadProject`事件，以重新載入相同的專案。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [巢狀專案](../../extensibility/internals/nesting-projects.md)