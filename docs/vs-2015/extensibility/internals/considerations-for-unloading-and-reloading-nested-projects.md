---
title: 卸載和重載嵌套專案的考慮 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65145530c8cd6b68b82391a09b395bb8c9a61117
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197005"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>卸載並重新載入巢狀專案的考量
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當您執行嵌套專案類型時，當您卸載並重載專案時，必須執行額外的步驟。 若要正確通知接聽程式的解決方案事件，您必須正確地引發 `OnBeforeUnloadProject` 和 `OnAfterLoadProject` 事件。  
  
 您必須以這種方式引發這些事件的原因之一，就是您不想要原始程式碼控制 (SCC) 刪除伺服器中的專案，然後將它們新增回新的專案（如果有 `Get` 來自 SCC 的作業）。 在此情況下，新的檔案會從 SCC 載入，而您必須卸載並重載所有檔案，以防它們不同。 SCC 呼叫 `ReloadItem` 。 該呼叫的實作為刪除專案，並藉由實作為呼叫和重新建立它 `IVsFireSolutionEvents` `OnBeforeUnloadProject` `OnAfterLoadProject` 。 當您執行這項作業時，系統會通知 SCC，表示已暫時刪除專案並再次新增。 因此，SCC 無法在專案上操作，就像是實際從伺服器刪除專案，然後再重新加入一樣。  
  
## <a name="reloading-projects"></a>重載專案  
 若要支援重載嵌套專案，請執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 方法。 在的執行中 `ReloadItem` ，您會關閉嵌套專案，然後重新建立它們。  
  
 通常在重載專案時，IDE 會引發 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> 和 `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` 事件。 不過，對於將要刪除和重載的嵌套專案，父專案會起始進程，而不是 IDE。 因為父專案不會引發方案事件，而且 IDE 沒有進程初始化的相關資訊，所以不會引發事件。  
  
 為了處理這個進程，父專案會在介面上呼叫介面 `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> 。 `IVsFireSolutionEvents` 的函式會告訴 IDE 引發 `OnBeforeUnloadProject` 事件以卸載嵌套的專案，然後引發 `OnAfterLoadProject` 事件以重載相同的專案。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [巢狀專案](../../extensibility/internals/nesting-projects.md)
