---
title: 終止程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f82a8238b542ce9aa9f5489df38553410e1326d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331351"
---
# <a name="terminating-a-program"></a>終止程式
下節描述了單一的程式，而且其中一個執行緒終止。

## <a name="termination-process"></a>終止程序

1. DE 傳送[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)的有效[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)。

2. DE 傳送[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)的有效[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)。

   IDE 會進入設計模式。 執行階段環境呼叫的偵錯引擎[IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)來移除連接埠的程式。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)