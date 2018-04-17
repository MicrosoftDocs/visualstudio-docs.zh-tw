---
title: 實作命令處理巢狀專案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e4ed9efab34a51bdfaacea1773a33637437b2ced
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-command-handling-for-nested-projects"></a>實作處理巢狀專案命令
IDE 可以傳遞命令，都會通過<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，以巢狀的專案或父專案可以篩選或覆寫命令。  
  
> [!NOTE]
>  您可以篩選通常由父專案的命令。 這類命令**建置**和**部署**，由 IDE 無法進行篩選。  
  
 下列步驟描述實作命令處理的程序。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-implement-command-handling"></a>若要實作命令處理  
  
1.  當使用者選取巢狀的專案或節點的巢狀專案中：  
  
    1.  IDE 呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。  
  
     — 或 —  
  
    1.  如果在階層視窗中，例如在 方案總管的捷徑功能表命令的命令產生 IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>專案的父代上的方法。  
  
2.  父專案可以檢查傳遞給參數`QueryStatus`，例如`pguidCmdGroup`和`prgCmds`，以決定父專案是否應該篩選命令。 如果父專案來篩選命令實作時，它應該設定：  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     父專案應該傳回`S_OK`。  
  
     如果父專案不會篩選命令，它應該只傳回`S_OK`。 在此情況下，IDE 會自動將命令傳送至子專案。  
  
     若要將命令路由傳送至子專案沒有父專案。 IDE 會執行這項工作...  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [命令、 功能表和工具列](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [巢狀專案](../../extensibility/internals/nesting-projects.md)