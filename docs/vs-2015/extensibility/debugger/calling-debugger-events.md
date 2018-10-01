---
title: 呼叫偵錯工具事件 |Microsoft Docs
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
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86c48d072baa53cf3f8ba0a6d903021e6c396afa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489611"
---
# <a name="calling-debugger-events"></a>呼叫偵錯工具事件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[呼叫偵錯工具事件](https://docs.microsoft.com/visualstudio/extensibility/debugger/calling-debugger-events)。  
  
在偵錯工作階段的事件會發生特定的順序。  
  
## <a name="discussion"></a>討論  
 若要了解的偵錯引擎 (DE) 和工作階段的偵錯管理員 (SDM) 之間的呼叫模式，下列表示一般的偵錯工作階段中發生的事件的呼叫順序：  
  
1.  [附加和中斷連結至程式](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [啟動偵錯工具](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [終止程式](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [建立中斷點](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [當中斷點繫結或變成未繫結](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [中斷點錯誤](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [叫用中斷點](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [刪除中斷點](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [進入中斷模式](../../extensibility/debugger/entering-break-mode.md)  
  
10. [在中斷模式中逐步執行](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [在中斷模式中的運算式評估](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [例外狀況處理](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>另請參閱  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)

