---
title: 執行緒 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ac9293807f280efff21fb8e8a5f97ed2cf0f96a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937505"
---
# <a name="threads"></a>執行緒
在偵錯工具架構中，*執行緒*:  
  
-   是計算的基本單位。 執行緒會以循序方式執行其指示的內容中的單一呼叫堆疊，從一個程式碼內容移至下一步。  
  
-   可以識別本身，以及在執行的程式。 執行緒可以命名為、 擱置，而且繼續。 執行緒也可以列舉其相關聯的堆疊框架，並在某些情況下可以移至另一個堆疊框架。 指定的堆疊框架的內容，執行緒可以傳回其相關聯的邏輯執行緒，如果有的話。 執行緒必須屬性，例如暫停計數，可顯示在**執行緒**在 IDE 的視窗。  
  
-   由[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)通常所偵錯引擎 (DE) 或由於執行程式的虛擬機器建立的介面。  
  
## <a name="see-also"></a>另請參閱  
 [程式](../../extensibility/debugger/programs.md)   
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [工作階段偵錯管理員](../../extensibility/debugger/session-debug-manager.md)