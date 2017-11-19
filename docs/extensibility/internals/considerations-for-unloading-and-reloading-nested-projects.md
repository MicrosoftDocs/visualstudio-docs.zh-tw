---
title: "考量卸載及重新載入巢狀專案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf34a3fe708a6ecab200262224da395b9fa37ecb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>卸載並重新載入巢狀專案的考量
當您實作巢狀的專案類型時，您必須執行額外步驟，當您卸除並重新載入專案。 若要正確通知方案的事件接聽程式，您必須正確地提高`OnBeforeUnloadProject`和`OnAfterLoadProject`事件。  
  
 您必須引發這些事件，以這種方式的其中一個原因是您不想原始程式碼控制 (SCC) 才能從伺服器刪除的項目，然後將它們加入為新項目是否有`Get`SCC 作業。 在此情況下，會載入新的檔案超出 SCC，而且您具有卸載再重新載入所有檔案，以防不相同。 SCC 呼叫`ReloadItem`。 您的實作，該呼叫的是刪除專案，並重新建立它一次實作`IVsFireSolutionEvents`呼叫`OnBeforeUnloadProject`和`OnAfterLoadProject`。 當您執行這項實作時，SCC 會收到通知，暫時刪除並重新加入專案。 因此，SCC 不能進行專案時，如果專案已從伺服器中實際刪除，然後再次加入。  
  
## <a name="reloading-projects"></a>重新載入專案  
 若要支援的巢狀專案重新載入，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>方法。 在您實作`ReloadItem`，您關閉巢狀的專案，然後再重新建立。  
  
 通常會重新載入專案，IDE 會引發<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A>和`M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)`事件。 不過，巢狀專案，將刪除並重新載入，父專案流程一開始，不會在 IDE。 由於父專案不會引發方案事件，且 IDE 沒有初始化程序的相關資訊，都不會引發事件。  
  
 若要處理程序中，父專案呼叫`QueryInterface`上<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>介面關閉<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>介面。 `IVsFireSolutionEvents`具有函式，以指示 IDE 引發`OnBeforeUnloadProject`卸載巢狀的專案，然後再引發事件`OnAfterLoadProject`重新載入專案相同的事件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [巢狀專案](../../extensibility/internals/nesting-projects.md)