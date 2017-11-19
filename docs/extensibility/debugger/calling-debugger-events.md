---
title: "呼叫偵錯工具事件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3acccf7233e62ca45d450a5e33c21a286ca4a204
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="calling-debugger-events"></a>呼叫偵錯工具事件
偵錯工作階段中的事件會以特定順序發生。  
  
## <a name="discussion"></a>討論  
 若要了解的偵錯引擎 (DE) 和工作階段的偵錯管理員 (SDM) 之間的呼叫模式，下列表示呼叫的典型的偵錯工作階段中發生的事件順序：  
  
1.  [附加和中斷連結至程式](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [啟動偵錯工具](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [終止程式](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [建立的中斷點](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [中斷點會繫結，或成為未繫結](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [中斷點錯誤](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [叫用中斷點](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [刪除中斷點](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [進入中斷模式](../../extensibility/debugger/entering-break-mode.md)  
  
10. [在中斷模式中逐步執行](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [在中斷模式中的運算式評估](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [例外狀況處理](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>另請參閱  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)