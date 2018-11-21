---
title: 考量卸載及重新載入巢狀專案 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 28c5ba7dffecd73556a5f963c471910bb190f1db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756957"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>卸載並重新載入巢狀專案的考量
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當您實作巢狀的專案類型時，您必須執行額外步驟，當您卸除並重新載入專案。 若要正確通知方案事件的接聽程式，您必須正確地引發`OnBeforeUnloadProject`和`OnAfterLoadProject`事件。  
  
 您必須引發這些事件，以這種方式的其中一個原因是您不想原始程式碼控制 (SCC) 來從伺服器刪除的項目，然後將它們新增為新的項目是否有`Get`SCC 的作業。 在此情況下，從 SCC 會載入新的檔案，而且您必須卸載並重新載入的所有檔案，萬一它們有不同。 SCC 呼叫`ReloadItem`。 您的實作，該呼叫的是刪除專案，然後重新建立它一次實作`IVsFireSolutionEvents`來呼叫`OnBeforeUnloadProject`和`OnAfterLoadProject`。 當您執行這項實作時，SCC 會告知專案已暫時刪除，並再次新增。 因此，SCC 無法運作的專案上專案已從伺服器中實際刪除且然後再次新增。  
  
## <a name="reloading-projects"></a>重新載入專案  
 若要支援的巢狀專案重新載入，您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>方法。 在您實作`ReloadItem`，關閉巢狀的專案，然後再重新建立它們。  
  
 通常當專案重新載入時，IDE 會引發<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A>而`M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)`事件。 不過，巢狀專案，將會刪除並重新載入，父專案啟始的處理程序中，而不在 IDE。 因為父專案不會引發方案的事件，且 IDE 沒有任何資訊的程序初始化，將不會引發事件。  
  
 若要處理這個程序，父專案呼叫`QueryInterface`上<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>關閉介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>介面。 `IVsFireSolutionEvents` 具有函式，告訴 IDE 引發`OnBeforeUnloadProject`事件，以卸載巢狀的專案，然後再引發`OnAfterLoadProject`事件，以重新載入相同的專案。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [巢狀專案](../../extensibility/internals/nesting-projects.md)

