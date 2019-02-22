---
title: 終止程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 864141055487b598a8f91641f40fe4c027c53b6c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918429"
---
# <a name="terminating-a-program"></a>終止程式
下節描述了單一的程式，而且其中一個執行緒終止。  
  
## <a name="termination-process"></a>終止程序  
  
1. DE 傳送[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)的有效[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)。  
  
2. DE 傳送[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)的有效[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)。  
  
   IDE 會進入設計模式。 執行階段環境呼叫的偵錯引擎[IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)來移除連接埠的程式。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)