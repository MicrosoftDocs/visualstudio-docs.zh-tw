---
title: 考量卸載及重新載入巢狀專案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f22575c4affa6e6a13ea80b32674a3e517202fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>卸載並重新載入巢狀專案的考量

當您實作巢狀的專案類型時，您必須執行額外步驟，當您卸除並重新載入專案。 若要正確通知方案的事件接聽程式，您必須正確地提高`OnBeforeUnloadProject`和`OnAfterLoadProject`事件。

引發這些事件的原因之一是用於原始程式碼控制 (SCC)。 您不想從伺服器刪除的項目，然後將它們加入至 SCC 返回當成*新*如果沒有`Get`SCC 作業。 在此情況下，新的檔案會超出 SCC 載入。 您必須要卸載並重新載入所有檔案，以防不同。

來源的程式碼控制呼叫`ReloadItem`。 實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>介面呼叫`OnBeforeUnloadProject`和`OnAfterLoadProject`刪除專案，然後重新建立它。 當您以這種方式實作的介面時，SCC 會收到通知，暫時刪除並重新加入專案。 因此，SCC 無法在專案上如同專案*實際上*刪除再重新加入。

## <a name="reloading-projects"></a>重新載入專案

若要支援的巢狀專案重新載入，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>方法。 在您實作`ReloadItem`，您關閉巢狀的專案，然後再重新建立。

通常會重新載入專案，IDE 會引發<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>事件。 不過，巢狀專案刪除並重新載入，父專案流程一開始，不會在 IDE。 由於父專案不會引發方案事件，且 IDE 沒有初始化程序的相關資訊，不會引發事件。

若要處理程序中，父專案呼叫`QueryInterface`上<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>介面。 `IVsFireSolutionEvents` 具有函式，以指示 IDE 引發`OnBeforeUnloadProject`卸載巢狀的專案，然後再引發事件`OnAfterLoadProject`重新載入專案相同的事件。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [巢狀專案](../../extensibility/internals/nesting-projects.md)