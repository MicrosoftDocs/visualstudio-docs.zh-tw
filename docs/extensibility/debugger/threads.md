---
title: "執行緒 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 150e27c4b8df06784848829bfe713773cf9d48a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="threads"></a>執行緒
偵錯工具就架構而言，**執行緒**:  
  
-   是計算的基本單位。 執行緒以循序方式執行，其指示的內容中的單一呼叫堆疊，從一種程式碼的內容移到下一步。  
  
-   可識別本身以及程式它正在執行中，和名為、 暫停，並繼續。 執行緒也可以列舉其相關聯的堆疊框架，而且在某些情況下，可以移到另一個堆疊框架。 指定堆疊框架的內容，執行緒可以傳回其相關聯的邏輯執行緒，如果有的話。 執行緒有屬性，例如暫停計數，可以顯示在 IDE 的 [執行緒] 視窗中。  
  
-   由[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)介面，通常由偵錯引擎 (DE) 或由於執行程式的虛擬機器所建立。  
  
## <a name="see-also"></a>另請參閱  
 [程式](../../extensibility/debugger/programs.md)   
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [工作階段偵錯管理員](../../extensibility/debugger/session-debug-manager.md)