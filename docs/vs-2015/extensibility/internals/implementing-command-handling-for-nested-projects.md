---
title: 實作的命令處理巢狀專案 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea27ea6f1b1ef49174b555fb9b1aae0d4c54dd23
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500244"
---
# <a name="implementing-command-handling-for-nested-projects"></a>實作巢狀專案的命令處理
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[實作處理巢狀專案的命令](https://docs.microsoft.com/visualstudio/extensibility/internals/implementing-command-handling-for-nested-projects)。  
  
IDE 可以傳遞命令，會傳遞<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>而<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>巢狀的專案，或父專案的介面可以篩選或覆寫命令。  
  
> [!NOTE]
>  您可以篩選通常由父專案的命令。 命令，例如**建置**並**部署**，都由 IDE 無法進行篩選。  
  
 下列步驟描述實作命令處理的程序。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-implement-command-handling"></a>若要實作命令處理  
  
1.  當使用者選取巢狀的專案或節點中的巢狀專案：  
  
    1.  IDE 呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。  
  
     — 或 —  
  
    1.  如果此命令，在 階層 視窗中，例如在 方案總管的捷徑功能表命令產生 IDE 便會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>專案的父代上的方法。  
  
2.  父專案可以檢查傳遞給參數`QueryStatus`，這類`pguidCmdGroup`和`prgCmds`，以決定父專案是否應該篩選命令。 如果父專案來篩選命令來實作，它應該設定：  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     則應傳回父專案`S_OK`。  
  
     如果父專案不會篩選命令，它應該只傳回`S_OK`。 在此情況下，IDE 會自動將命令路由至子專案。  
  
     若要將命令路由傳送至子專案沒有父專案。 IDE 會執行此工作...  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [命令、 功能表和工具列](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [巢狀專案](../../extensibility/internals/nesting-projects.md)

