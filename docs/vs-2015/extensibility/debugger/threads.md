---
title: 執行緒 |Microsoft Docs
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
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bda2bc0c79f766b4c6322850a22d2a830499ff58
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188261"
---
# <a name="threads"></a>執行緒
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

偵錯工具就架構而言，**執行緒**:  
  
-   是計算的基本單位。 執行緒會以循序方式執行其指示的內容中的單一呼叫堆疊，從一個程式碼內容移至下一步。  
  
-   可以識別本身和它正在執行中，和可名為、 暫止，並繼續執行的程式。 執行緒也可以列舉其相關聯的堆疊框架，並在某些情況下可以移至另一個堆疊框架。 指定的堆疊框架的內容，執行緒可以傳回其相關聯的邏輯執行緒，如果有的話。 執行緒具有屬性，例如暫停計數，可以在 IDE 的 [執行緒] 視窗中顯示。  
  
-   由[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)通常所偵錯引擎 (DE) 或由於執行程式的虛擬機器建立的介面。  
  
## <a name="see-also"></a>另請參閱  
 [程式](../../extensibility/debugger/programs.md)   
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [偵錯引擎](../../extensibility/debugger/debug-engine.md)   
 [偵錯工具概念](../../extensibility/debugger/debugger-concepts.md)   
 [工作階段偵錯管理員](../../extensibility/debugger/session-debug-manager.md)

